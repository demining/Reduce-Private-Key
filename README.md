# Reducing the private key through scalar multiplication using the ECPy + Google Colab library

<p>In this article, we will try to show how you can reduce the private key knowing only the leak from the&nbsp;<a href="https://pastebin.com/eLMYtzV8" target="_blank" rel="noreferrer noopener">«BLOCKCHAIN ​​FOLBIT LEAKS»</a>&nbsp;list and the public key from&nbsp;<a href="https://en.wikipedia.org/wiki/Unspent_transaction_output" target="_blank" rel="noreferrer noopener">«UTXO»</a>&nbsp;.<br>
In the experimental part, we will use&nbsp;<a href="https://github.com/demining/CryptoDeepTools/tree/main/08ReducePrivateKey" target="_blank" rel="noreferrer noopener">the 08ReducePrivateKey</a>&nbsp;scripts and restore the Bitcoin Wallet.</p>
<blockquote class="wp-block-quote"><p><em><u>Elliptic curve scalar multiplication</u></em>&nbsp;is the operation of adding a point<code>P</code>to the curve<code>k</code>times.</p>
<p><code>Q=kP=P+P+P, k times</code></p>
<p><code>P</code>is&nbsp;<em>a point on an elliptic curve</em>&nbsp;, and&nbsp;<code>k</code>is&nbsp;<em>a large natural number</em>&nbsp;.</p>
<p>In any primitive implementations,&nbsp;<code>ECC</code>scalar multiplication is the main computational operation.&nbsp;A key factor in improving efficiency&nbsp;<code>ECC</code>is the implementation of fast scalar multiplication.&nbsp;Therefore, many researchers have proposed various studies of&nbsp;<a href="https://habr.com/ru/post/680932/" target="_blank" rel="noreferrer noopener"><em><u>accelerated scalar multiplication</u></em></a>&nbsp;.</p></blockquote>
<h2>Let’s use the ECPy library</h2>
<h3>ECPy provides:</h3>
<ul>
<li>ECDSA signatures</li>
<li>Ed25519 signatures</li>
<li>ECSchnorr signatures</li>
<li>Borromean signatures</li>
<li>point operations</li>
</ul>
<blockquote class="wp-block-quote"><p><em>In many of our studies, we use the library&nbsp;</em><code>ECPy</code><em>and</em><code>Google Colab</code></p></blockquote>
<p>Open&nbsp;<a href="https://github.com/demining/TerminalGoogleColab" target="_blank" rel="noreferrer noopener"><strong>[TerminalGoogleColab]</strong></a></p>
<p><strong>Let’s use the </strong><a href="https://github.com/demining/CryptoDeepTools/tree/main/08ReducePrivateKey"><strong>«08ReducePrivateKey»</strong></a>&nbsp;repository</p>
<pre class="wp-block-code"><code>git clone https://github.com/demining/CryptoDeepTools.git

cd CryptoDeepTools/08ReducePrivateKey/

ls</code></pre>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy + Google Colab library - «CRYPTO DEEP TECH»_files/201da1f9f8e93fbbeae07e8e9af7723e.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<h3>Install the ECPy library:</h3>
<pre class="wp-block-code"><code>pip3 install ECPy</code></pre>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy + Google Colab library - «CRYPTO DEEP TECH»_files/d7c1d7b35f8246398d24a4e40744a43e.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<blockquote class="wp-block-quote"><p><em>Python</em>&nbsp;script:&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/maxwell.py" target="_blank" rel="noreferrer noopener">maxwell.py</a>&nbsp;,&nbsp;<em>save</em>&nbsp;<code>код</code>&nbsp;and run in terminal<code>Google Colab</code></p></blockquote>
<pre class="wp-block-code"><code>from ecpy.curves     import Curve,Point

cv = Curve.get_curve('secp256k1')
G  = Point(0x79be667ef9dcbbac55a06295ce870b07029bfcdb2dce28d959f2815b16f81798,
           0x483ada7726a3c4655da4fbfc0e1108a8fd17b448a68554199c47d08ffb10d4b8,
           cv)
x  = 0x7fffffffffffffffffffffffffffffff5d576e7357a4501ddfe92f46681b20a1

PUBKEY  = x*G

print(PUBKEY)</code></pre>
<h3>Run command:</h3>
<pre class="wp-block-code"><code>python3 maxwell.py</code></pre>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy + Google Colab library - «CRYPTO DEEP TECH»_files/b6bc190fe89cda2172f7b29a30aeaf16.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<h3>Result:</h3>
<pre class="wp-block-code"><code>(0x3b78ce563f89a0ed9414f5aa28ad0d96d6795f9c63 , 0xc0c686408d517dfd67c2367651380d00d126e4229631fd03f8ff35eef1a61e3c)
</code></pre>
<h3>Pay attention to the x coordinate</h3>
<pre class="wp-block-code"><code>x value = 3b78ce563f89a0ed9414f5aa28ad0d96d6795f9c63

0200000000000000000000003B78CE563F89A0ED9414F5AA28AD0D96D6795F9C63</code></pre>
<blockquote class="wp-block-quote"><p>This&nbsp;<em>public key</em>&nbsp;is called&nbsp;<a href="https://bitcointalk.org/index.php?topic=1118704.msg11862486#msg11862486" target="_blank" rel="noreferrer noopener"><u>«Maxwell’s vanity public key»</u></a></p></blockquote>
<pre class="wp-block-code"><code>0x7fffffffffffffffffffffffffffffff5d576e7357a4501ddfe92f46681b20a0 --&gt; 0x3b78ce563f89a0ed9414f5aa28ad0d96d6795f9c63, 0x3f3979bf72ae8202983dc989aec7f2ff2ed91bdd69ce02fc0700ca100e59ddf3
0x7fffffffffffffffffffffffffffffff5d576e7357a4501ddfe92f46681b20a1 --&gt; 0x3b78ce563f89a0ed9414f5aa28ad0d96d6795f9c63, 0xc0c686408d517dfd67c2367651380d00d126e4229631fd03f8ff35eef1a61e3c

p = 0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141

((p-1)/2) = 0x7fffffffffffffffffffffffffffffff5d576e7357a4501ddfe92f46681b20a0

0200000000000000000000003B78CE563F89A0ED9414F5AA28AD0D96D6795F9C63
</code></pre>
<h4>We’ll come back to this public key!</h4>
<h2>Let’s move on to the experimental part:</h2>
<p>We have three different Bitcoin Addresses with a balance&nbsp;<code>100 BTC</code>&nbsp;<em>or higher</em>&nbsp;from the&nbsp;<a href="https://bitinfocharts.com/top-100-richest-bitcoin-addresses.html" target="_blank" rel="noreferrer noopener"><strong>Bitcoin Rich List</strong></a></p>
<blockquote class="wp-block-quote"><p><strong><a href="https://www.blockchain.com/btc/address/1KpHWkpG7BGxDuSJKYPYVvNSC6womEZdTu" target="_blank" rel="noreferrer noopener">1KpHWkpG7BGxDuSJKYPYVvNSC6womEZdTu</a></strong></p>
<p><strong><a href="https://www.blockchain.com/btc/address/1MjGyKiRLzq4WeuJKyFZMmkjAv7rH1TABm" target="_blank" rel="noreferrer noopener">1MjGyKiRLzq4WeuJKyFZMmkjAv7rH1TABm</a></strong></p>
<p><strong><a href="https://www.blockchain.com/btc/address/1GrTCkqqcXhVTXoQkPJjU5LuFKgAvC3iqJ" target="_blank" rel="noreferrer noopener">1GrTCkqqcXhVTXoQkPJjU5LuFKgAvC3iqJ</a></strong></p></blockquote>
<p>Let&nbsp;<code>UTXO</code>‘s get these Bitcoin Addresses and now we have three signatures&nbsp;<code>ECDSA</code>&nbsp;<em>(Apply scripts&nbsp;</em><a href="https://github.com/demining/CryptoDeepTools/tree/main/01BlockchainGoogleDrive" target="_blank" rel="noreferrer noopener"><em>01BlockchainGoogleDrive</em></a><em>&nbsp;)</em></p>
<p><a href="https://blockchain.info/rawtx/c1ea2c9e48ce632488817781f89730d77cd4121f1c8f70a4be44d2a15e8e08d0?format=hex" target="_blank" rel="noreferrer noopener"><strong>c1ea2c9e48ce632488817781f89730d77cd4121f1c8f70a4be44d2a15e8e08d0</strong></a><br>
<a href="https://blockchain.info/rawtx/37dadae30c6f7c6c4a2c930db979494783005a8e94d6861039fed21e3fa859b9?format=hex" target="_blank" rel="noreferrer noopener"><strong>37dadae30c6f7c6c4a2c930db979494783005a8e94d6861039fed21e3fa859b9</strong></a><br>
<a href="https://blockchain.info/rawtx/9dacfc8243109475383d5b30e8d5f0ba23d023bd47649064c208d4586b278436?format=hex" target="_blank" rel="noreferrer noopener"><strong>9dacfc8243109475383d5b30e8d5f0ba23d023bd47649064c208d4586b278436</strong></a></p>
<p>Get&nbsp;<code>RawTX</code>for three different Bitcoin Addresses</p>
<pre class="wp-block-code"><code>01000000017fbdd4c9991d0ba4fb0a0c06f6933442c17678bce6dfa4bf80e22ed530bb933c010000008a47304402206d0ab626a7e477c27602ed63b2651517af077e6f3fafda671dd9952dfcb5f0b90220168eb51a48ce7496a699a800299f15638e0a7f36ae84e84e26df0cd2a280a70e014104b3fdc0e84cd77cd018ced1fdd3ea4110d6beb942cfd38c0f6feaffc246e08b97fe779e87e4743f55168a476433100abd4cac064be5915cf828185319480b3fb4feffffff0240597307000000001976a914211090b628fa6351fa8240232e3c2753fd5eece588ac700369d2050000001976a914ce639943ce1602e30b249faf74388ee0eeb1d3c588ac84b90700
01000000014666d430766d611cc7f2c21494e68e463ac4be8bb2f70b91693728324849e1c3010000008a473044022057a02a4abc38e2e3e1809b05402cf52faef7e101d6364d43bb0305f8796b0fb202203d1934a016c91072ffe137575734454161284ab3371a0cfc6767db7f27f24a75014104ea7c9e85d4fb089e0b2901cd5c77f3149aa4cf711ed29a3318a4e153a67ea9cd1a22c24c8e05b66eb122db74d26fddf2cb184033fb586743ea330e15eeb8240cffffffff01b0feea0b000000001976a9148300ab0caebb6e85cf9e6b287a57924d1ac7c82f88ac00000000
01000000019d8e5e1bfac780b813e41517926aca95048e1dea92cbbe2a98475ff53ad38ccd000000008c493046022100c7b76326879a5ec7df2ffedb292a45c13c6f154982fc2cd7e05f0d0d0dce2d05022100d7fd43416608eaeb6356f04b601ac6edd23e0f82de44689fe5a7aa2f576637a001410480edda62d055008c28de19f4908cd052ccf63a10d708b5866b7a5b340bde49e2b5e7be50412afb83a6c774ed5b45fdf9ad5cbbd98b7f1964f1cb180b7bc6d56cffffffff01a93de702000000001976a914119fb35bad07974c1a8d47d210ca3048bb13be8788ac00000000
</code></pre>
<h3>Install all the necessary modules:</h3>
<pre class="wp-block-code"><code>bitcoin
ecdsa
utils
base58


pip2 install -r requirements.txt</code></pre>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy + Google Colab library - «CRYPTO DEEP TECH»_files/489a485af916d20a567f6675da99fe06.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<p>Using the&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/breakECDSA.py" target="_blank" rel="noreferrer noopener">breakECDSA.py</a>&nbsp;script, we will find out the&nbsp;<em>public keys</em>&nbsp;for Bitcoin Addresses</p>
<pre class="wp-block-code"><code>python2 breakECDSA.py 01000000017fbdd4c9991d0ba4fb0a0c06f6933442c17678bce6dfa4bf80e22ed530bb933c010000008a47304402206d0ab626a7e477c27602ed63b2651517af077e6f3fafda671dd9952dfcb5f0b90220168eb51a48ce7496a699a800299f15638e0a7f36ae84e84e26df0cd2a280a70e014104b3fdc0e84cd77cd018ced1fdd3ea4110d6beb942cfd38c0f6feaffc246e08b97fe779e87e4743f55168a476433100abd4cac064be5915cf828185319480b3fb4feffffff0240597307000000001976a914211090b628fa6351fa8240232e3c2753fd5eece588ac700369d2050000001976a914ce639943ce1602e30b249faf74388ee0eeb1d3c588ac84b90700 &gt;&gt; PublicKeys.txt
python2 breakECDSA.py 01000000014666d430766d611cc7f2c21494e68e463ac4be8bb2f70b91693728324849e1c3010000008a473044022057a02a4abc38e2e3e1809b05402cf52faef7e101d6364d43bb0305f8796b0fb202203d1934a016c91072ffe137575734454161284ab3371a0cfc6767db7f27f24a75014104ea7c9e85d4fb089e0b2901cd5c77f3149aa4cf711ed29a3318a4e153a67ea9cd1a22c24c8e05b66eb122db74d26fddf2cb184033fb586743ea330e15eeb8240cffffffff01b0feea0b000000001976a9148300ab0caebb6e85cf9e6b287a57924d1ac7c82f88ac00000000 &gt;&gt; PublicKeys.txt
python2 breakECDSA.py 01000000019d8e5e1bfac780b813e41517926aca95048e1dea92cbbe2a98475ff53ad38ccd000000008c493046022100c7b76326879a5ec7df2ffedb292a45c13c6f154982fc2cd7e05f0d0d0dce2d05022100d7fd43416608eaeb6356f04b601ac6edd23e0f82de44689fe5a7aa2f576637a001410480edda62d055008c28de19f4908cd052ccf63a10d708b5866b7a5b340bde49e2b5e7be50412afb83a6c774ed5b45fdf9ad5cbbd98b7f1964f1cb180b7bc6d56cffffffff01a93de702000000001976a914119fb35bad07974c1a8d47d210ca3048bb13be8788ac00000000 &gt;&gt; PublicKeys.txt
</code></pre>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy + Google Colab library - «CRYPTO DEEP TECH»_files/afbec8169caf989b8550aadad4dd3e59.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<p>After launch, we receive&nbsp;<em>public keys</em>&nbsp;for all three Bitcoin Addresses.</p>
<h3>The result will be saved to a file: PublicKeys.txt</h3>
<pre class="wp-block-code"><code>Откроем файл: PublicKeys.txt

cat PublicKeys.txt</code></pre>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy + Google Colab library - «CRYPTO DEEP TECH»_files/7734e4670c08dae7004135f681bd0942.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<pre class="wp-block-code"><code>PUBKEY = 04b3fdc0e84cd77cd018ced1fdd3ea4110d6beb942cfd38c0f6feaffc246e08b97fe779e87e4743f55168a476433100abd4cac064be5915cf828185319480b3fb4
PUBKEY = 04ea7c9e85d4fb089e0b2901cd5c77f3149aa4cf711ed29a3318a4e153a67ea9cd1a22c24c8e05b66eb122db74d26fddf2cb184033fb586743ea330e15eeb8240c
PUBKEY = 0480edda62d055008c28de19f4908cd052ccf63a10d708b5866b7a5b340bde49e2b5e7be50412afb83a6c774ed5b45fdf9ad5cbbd98b7f1964f1cb180b7bc6d56c
</code></pre>
<h3>Let’s make these public keys in the form of coordinate points (x,y):</h3>
<pre class="wp-block-code"><code>(0xb3fdc0e84cd77cd018ced1fdd3ea4110d6beb942cfd38c0f6feaffc246e08b97 , 0xfe779e87e4743f55168a476433100abd4cac064be5915cf828185319480b3fb4)
(0xea7c9e85d4fb089e0b2901cd5c77f3149aa4cf711ed29a3318a4e153a67ea9cd , 0x1a22c24c8e05b66eb122db74d26fddf2cb184033fb586743ea330e15eeb8240c)
(0x80edda62d055008c28de19f4908cd052ccf63a10d708b5866b7a5b340bde49e2 , 0xb5e7be50412afb83a6c774ed5b45fdf9ad5cbbd98b7f1964f1cb180b7bc6d56c)
</code></pre>
<p>Save the coordinate points&nbsp;<code>(x,y)</code>in a file:&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/Coordinates.txt" target="_blank" rel="noreferrer noopener"><strong>Coordinates.txt</strong></a></p>
<h2>BLOCKCHAIN ​​FOLBIT LEAKS</h2>
<p>Let’s open the list of known blockchain leaks on&nbsp;<code>2019 год</code>&nbsp;<a href="https://pastebin.com/eLMYtzV8" target="_blank" rel="noreferrer noopener"><strong>«BLOCKCHAIN ​​FOLBIT LEAKS»</strong></a></p>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy + Google Colab library - «CRYPTO DEEP TECH»_files/5b1643cb05baa67368df5f79277135ae.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<h3>Let’s copy the value:</h3>
<pre class="wp-block-code"><code>dac19ec586ea8aa454fd2e7090e3244cdf75a73bdb1aa970d8b0878e75df3cae</code></pre>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy + Google Colab library - «CRYPTO DEEP TECH»_files/bbb497cfc8a2ec00af285f19851e6ce8.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<blockquote class="wp-block-quote"><p>Now let’s do the dot multiplication over all the coordinates of the points by&nbsp;<code>(x,y)</code>applying the leakage value&nbsp;<strong>:</strong></p></blockquote>
<p><a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/maxwell.py" target="_blank" rel="noreferrer noopener">Change the maxwell.py</a>&nbsp;code&nbsp;and change the name to&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/scalarEC.py" target="_blank" rel="noreferrer noopener">scalarEC.py</a></p>
<p>Let’s add<code>with open("Coordinates.txt", "rt") as base:</code></p>
<p>All new coordinates will be saved in a file:<code>SaveBase.txt</code></p>
<p><code>B = 0xdac19ec586ea8aa454fd2e7090e3244cdf75a73bdb1aa970d8b0878e75df3cae</code></p>
<p>Let’s add a value&nbsp;<code>B</code>from the list to the code and save it as a&nbsp;<em>Python</em>&nbsp;script:&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/scalarEC.py" target="_blank" rel="noreferrer noopener">scalarEC.py</a></p>
<pre class="wp-block-code"><code>from ecpy.curves     import Curve,Point

with open("Coordinates.txt", "rt") as base:
    for line in base.read().splitlines():
        Gx, Gy = map(lambda v: int(v, 16), line[1: -1].split(" , "))

        cv = Curve.get_curve('secp256k1')
    
        P  = Point(Gx,Gy,cv)

        B  = 0xdac19ec586ea8aa454fd2e7090e3244cdf75a73bdb1aa970d8b0878e75df3cae

        A  = B*P

        with open("SaveBase.txt", "a") as file:
            file.write(str(A))
            file.write("\n")</code></pre>
<hr class="wp-block-separator has-alpha-channel-opacity">
<h2>Let’s run the script:</h2>
<pre class="wp-block-code"><code>python3 scalarEC.py

Результат сохранился в файле: SaveBase.txt

Откроем файле: SaveBase.txt

cat SaveBase.txt
</code></pre>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy + Google Colab library - «CRYPTO DEEP TECH»_files/cf3657dd0b79a3ce0e5cdaa44120e4ba.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<pre class="wp-block-code"><code>(0x92b9eeebb8c4fa108359bd31367e36b7fe65b4a7e06d533b476dee097572a4c0 , 0x4d2beb1835a2f8b85e3f61d32094dbf0b4c7a212bee42ee4612193c0653c6e56)
(0x65304d24c0edc862843587a96ea700f86e9e70e7801ac7df9efd2de84230c3e7 , 0x7af6d83573849d2368a021e835c5768e1b791c0c1b4cfafb9795058df5f27958)
(0x433c15b724948371877dd3c1014d59d1a13d76a29e4948903623a74767736b97 , 0x13f15f3bb28a4766952e10da9717aa3cc0bad90b0414f483718531d584721ea3)
</code></pre>
<blockquote class="wp-block-quote"><p>After scalar multiplication by the leakage value over all coordinate points&nbsp;<code>(x,y)</code>, we&nbsp;<em><u>get new points</u></em></p></blockquote>
<h3>Now let’s rewrite these coordinates in the form of uncompressed public keys:</h3>
<h2>Let’s take a look at this public key:</h2>
<pre class="wp-block-code"><code>0465304d24c0edc862843587a96ea700f86e9e70e7801ac7df9efd2de84230c3e77af6d83573849d2368a021e835c5768e1b791c0c1b4cfafb9795058df5f27958
</code></pre>
<p><a href="https://cryptodeeptech.ru/kangaroo/" target="_blank" rel="noreferrer noopener">Now we use Pollard’s Kangaroo</a>&nbsp;method to find the private key</p>
<p>Previously, we published an article:&nbsp;<a href="https://cryptodeeptech.ru/kangaroo/" target="_blank" rel="noreferrer noopener"><em>«Pollard’s Kangaroo find solutions to the discrete logarithm of secp256k1 PRIVATE KEY + NONCES in a known range»</em></a></p>
<blockquote class="wp-block-quote"><p>Let’s use&nbsp;<em><u>the new code</u></em>&nbsp;<code>Pollard's Kangaroo</code>&nbsp;from&nbsp;<code>Telariust</code>&nbsp;<em>Python</em>&nbsp;-script:&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/kangaroo.py" target="_blank" rel="noreferrer noopener">kangaroo.py</a></p></blockquote>
<h3>Install the gmpy2 module with the command:</h3>
<pre class="wp-block-code"><code>sudo apt install python-gmpy2</code></pre>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy + Google Colab library - «CRYPTO DEEP TECH»_files/0f144812547a5d8e84cf66ee71b0c6d6.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy + Google Colab library - «CRYPTO DEEP TECH»_files/7646ac808066d138af9c5b5380baf507.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<p>Next, run the&nbsp;<em>Python</em>&nbsp;script:&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/kangaroo.py" target="_blank" rel="noreferrer noopener">kangaroo.py</a></p>
<pre class="wp-block-code"><code>python2 kangaroo.py 32 0465304D24C0EDC862843587A96EA700F86E9E70E7801AC7DF9EFD2DE84230C3E77AF6D83573849D2368A021E835C5768E1B791C0C1B4CFAFB9795058DF5F27958
</code></pre>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy + Google Colab library - «CRYPTO DEEP TECH»_files/25d4cddd4d35d1fc6331dca485cff638.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy + Google Colab library - «CRYPTO DEEP TECH»_files/617c1358faaf9104fc774fda67fbf9d1.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<p>In the terminal we see that we managed to get&nbsp;<code>"prvkey"</code>:</p>
<pre class="wp-block-code"><code>[prvkey#32] 0x00000000000000000000000000000000000000000000000000000000795f9c63
[pubkey#32] 0465304d24c0edc862843587a96ea700f86e9e70e7801ac7df9efd2de84230c3e77af6d83573849d2368a021e835c5768e1b791c0c1b4cfafb9795058df5f27958
</code></pre>
<h3>The result will be saved to a file: Privkey.txt</h3>
<pre class="wp-block-code"><code>Откроем файл командой: 

cat Privkey.txt</code></pre>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy + Google Colab library - «CRYPTO DEEP TECH»_files/94f1450a509aa57879f2864348d1fe4c.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<pre class="wp-block-code"><code>00000000000000000000000000000000000000000000000000000000795f9c63</code></pre>
<h3>We got a reduced private key for the public key:</h3>
<pre class="wp-block-code"><code>0465304D24C0EDC862843587A96EA700F86E9E70E7801AC7DF9EFD2DE84230C3E77AF6D83573849D2368A021E835C5768E1B791C0C1B4CFAFB9795058DF5F27958
</code></pre>
<h3>Pay attention to the private key:</h3>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy + Google Colab library - «CRYPTO DEEP TECH»_files/f8daaebb61f7ee1e398441c85ab85209.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<p>The latter&nbsp;matches the&nbsp;<code>8 цифр</code>public&nbsp;<em>key&nbsp;</em><a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/maxwell.py" target="_blank" rel="noreferrer noopener">«Maxwell’s vanity public key»</a><code>формате HEX</code></p>
<pre class="wp-block-code"><code>0200000000000000000000003B78CE563F89A0ED9414F5AA28AD0D96D6795F9C63</code></pre>
<hr class="wp-block-separator has-alpha-channel-opacity">
<pre class="wp-block-code"><code>A = 0x00000000000000000000000000000000000000000000000000000000795f9c63
B = 0xdac19ec586ea8aa454fd2e7090e3244cdf75a73bdb1aa970d8b0878e75df3cae</code></pre>
<blockquote class="wp-block-quote"><p>Now, in order to get a private key for one of the three Bitcoin Addresses, we need to do a modulo division&nbsp;<code>значение A</code>by<code>значение B</code></p>
<p><code>Privkey = ((A * modinv(B,N)) % N)</code></p></blockquote>
<p>Let’s use a&nbsp;<em>Python</em>&nbsp;script:&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/calculate.py" target="_blank" rel="noreferrer noopener">calculate.py</a></p>
<pre class="wp-block-code"><code>def h(n):
    return hex(n).replace("0x","")

def extended_gcd(aa, bb):
    lastremainder, remainder = abs(aa), abs(bb)
    x, lastx, y, lasty = 0, 1, 1, 0
    while remainder:
        lastremainder, (quotient, remainder) = remainder, divmod(lastremainder, remainder)
        x, lastx = lastx - quotient*x, x
        y, lasty = lasty - quotient*y, y
    return lastremainder, lastx * (-1 if aa &lt; 0 else 1), lasty * (-1 if bb &lt; 0 else 1)

def modinv(a, m):
    g, x, y = extended_gcd(a, m)
    if g != 1:
        raise ValueError
    return x % m

N = 0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141

A = 0x00000000000000000000000000000000000000000000000000000000795f9c63
B = 0xdac19ec586ea8aa454fd2e7090e3244cdf75a73bdb1aa970d8b0878e75df3cae


print (h(((A) * modinv(B,N)) % N))
</code></pre>
<p>Let ‘s run the&nbsp;<em>Python</em>&nbsp;script:&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/calculate.py" target="_blank" rel="noreferrer noopener">calculate.py</a></p>
<pre class="wp-block-code"><code>python3 calculate.py</code></pre>
<figure class="wp-block-image"><img title="As a result, we will receive a private key in the terminal in HEX format 38717b5161c2e817020a0933e1836dd0127bdef59732d77daca20ccfbf61a7ae" src="./Reducing the private key through scalar multiplication using the ECPy + Google Colab library - «CRYPTO DEEP TECH»_files/750f71837b11f35eb3f067cc0499c558.png" alt="As a result, we will receive a private key in the terminal in HEX format 38717b5161c2e817020a0933e1836dd0127bdef59732d77daca20ccfbf61a7ae"><figcaption>As a result, we will receive a private key in the terminal in HEX format 38717b5161c2e817020a0933e1836dd0127bdef59732d77daca20ccfbf61a7ae</figcaption></figure>
<p><a href="https://cryptodeeptech.ru/bitaddress.html" target="_blank" rel="noreferrer noopener">Let’s open bitaddress</a>&nbsp;and&nbsp;check:</p>
<pre class="wp-block-code"><code>ADDR: 1MjGyKiRLzq4WeuJKyFZMmkjAv7rH1TABm
WIF:  5JF9ME7zdGLDd3oyuMG7RfwgA1ByjZb2LbSwRMwM8ZKBADFLfCx
HEX:  38717b5161c2e817020a0933e1836dd0127bdef59732d77daca20ccfbf61a7ae</code></pre>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy + Google Colab library - «CRYPTO DEEP TECH»_files/eb4d76c11de49bd6114bcb2b5409cdc4.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<h2>Private Key Found!</h2>
<h2>Bitcoin Wallet Restored!</h2>
<figure class="wp-block-image"><img title="www.blockchain.com/btc/address/1MjGyKiRLzq4WeuJKyFZMmkjAv7rH1TABm" src="./Reducing the private key through scalar multiplication using the ECPy + Google Colab library - «CRYPTO DEEP TECH»_files/d05dfb7d1f9a7217cf7f88bd11b969e7.png" alt="www.blockchain.com/btc/address/1MjGyKiRLzq4WeuJKyFZMmkjAv7rH1TABm"><figcaption>www.blockchain.com/btc/address/1MjGyKiRLzq4WeuJKyFZMmkjAv7rH1TABm</figcaption></figure>
<p>This video was created for the&nbsp;&nbsp;<a href="https://cryptodeeptech.ru/" target="_blank" rel="noreferrer noopener"><strong>CRYPTO DEEP TECH</strong></a>&nbsp;portal &nbsp;to ensure the financial security of data and cryptography on elliptic curves&nbsp;&nbsp;<code>secp256k1</code>&nbsp;against weak signatures&nbsp;&nbsp;<code>ECDSA</code>&nbsp;in cryptocurrency&nbsp;<code>BITCOIN</code></p>
<p><a href="https://github.com/demining/CryptoDeepTools/tree/main/08ReducePrivateKey" target="_blank" rel="noreferrer noopener"><strong>Source</strong></a></p>
<p><a href="https://t.me/cryptodeeptech"><strong>Telegram</strong></a><strong>&nbsp;:&nbsp;&nbsp;</strong><a href="https://t.me/cryptodeeptech" target="_blank" rel="noreferrer noopener"><strong><u>https://t.me/cryptodeeptech</u></strong></a></p>
<p><a href="https://youtu.be/zu2yiaZ_LOs" target="_blank" rel="noreferrer noopener"><strong>Video: https://youtu.be/zu2yiaZ_LOs</strong></a></p>
<p><a href="https://cryptodeeptech.ru/reduce-private-key"><strong>Source:&nbsp;https://cryptodeeptech.ru/reduce-private-key</strong></a></p>
<hr class="wp-block-separator has-alpha-channel-opacity">
</div>

---


|  | Donation Address |
| --- | --- |
| ♥ __BTC__ | 1Lw2kh9WzCActXSGHxyypGLkqQZfxDpw8v |
| ♥ __ETH__ | 0xaBd66CF90898517573f19184b3297d651f7b90bf |

