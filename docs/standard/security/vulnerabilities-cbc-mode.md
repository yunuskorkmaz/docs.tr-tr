---
title: CBC şifre çözme güvenlik açığı
description: Doldurma kullanarak şifreleme blok zincirleme (CBC) modu simetrik şifre çözme ile zamanlama güvenlik açıklarını algılamayı ve etkilerini öğrenin.
ms.date: 06/12/2018
author: blowdart
ms.openlocfilehash: 87f8e3c53e4d06f6a4edc7670891ac83ec8d65ab
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705853"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a>Doldurmayı kullanarak CBC modunda simetrik şifre çözmedeki zamanlama açıkları

Microsoft, yalnızca belirli bir durum dışında, şifreli doldurma uygulandığında, şifreli şifrelemenin Şifre blok zincirleme (CBC) moduyla şifrelenmiş verilerin şifresinin çözülmesi için artık güvenli olduğunu düşünmektedir durumlarda. Bu, şu anda bilinen şifreleme araştırmasını temel alır. 

## <a name="introduction"></a>Giriş

Oracle saldırısı doldurma, şifrelenmiş verilere yönelik bir saldırı türüdür ve bu, anahtarı bilmeden, saldırganın verilerin içeriğini çözmesini sağlar.

Bir Oracle, yürütmekte olduğu eylemin doğru olup olmadığı hakkında bir saldırgan bilgisi veren bir "söyleme" anlamına gelir. Bir pano veya kart oyununu bir alt öğe ile çalınmasını düşünün. Yüz, büyük bir gülümseme ile ışıkdığında, bu, bir Oracle olan iyi bir taşıma yapmak üzere olduğunu düşündü. Bu şekilde, rakip olarak bir sonraki taşımayı uygun şekilde planlamak için bu Oracle 'ı kullanabilirsiniz.

Doldurma, belirli bir şifreleme terimidir. Verilerinizi şifrelemek için kullanılan algoritmalar olan bazı şifrelemeler, her bloğun sabit boyutta olduğu veri blokları üzerinde çalışır. Şifrelemek istediğiniz veriler blokları dolduracak doğru boyutta değilse, verileriniz tamamlanana kadar doldurulur. Birçok doldurma formu, özgün giriş doğru boyutta olsa bile, her zaman doldurma gerektirir. Bu, verilerin şifre çözme sırasında her zaman güvenli bir şekilde kaldırılmasına olanak sağlar.

İki şeyi birlikte koymak, Oracle içeren bir yazılım uygulamasının, şifresi çözülmüş verilerin geçerli bir doldurma içerip içermediğini gösterir. Oracle, "Geçersiz doldurma" ya da geçersiz bir bloğun aksine geçerli bir blok işlemek için farklı bir zaman yaşamları gibi bir değer döndürmek gibi basit bir şey olabilir.

Blok tabanlı şifrelemeler, ikinci bloktaki verilerin ilk bloğundaki verilerin ilişkisini belirleyen, mod adlı başka bir özelliğe sahiptir ve bu şekilde devam eder. En yaygın olarak kullanılan modlardan biri CBC ' dir. CBC, başlatma vektörü (IV) olarak bilinen bir başlangıç rastgele bloğunu tanıtır ve önceki bloğu, aynı anahtarla aynı iletiyi şifrelemek için aynı şifrelenmiş çıktıyı her zaman üretmediği için statik şifrelemenin sonucuyla birleştirir.

Bir saldırgan, CBC verilerinin nasıl yapılandırıldığı, Oracle 'ı kullanıma açan koda kısmen değiştirilen iletileri gönderme ve Oracle 'ın verilerin doğru olduğunu söyleene kadar veri göndermeye devam eden bir Oracle ile birlikte bir doldurma kullanabilir. Bu yanıttan saldırgan, ileti baytının bayt olarak şifresini çözebilir.

Modern bilgisayar ağları, bir saldırganın uzak sistemlerde yürütme sırasında çok küçük (0,1 MS 'den az) farklılık algılayabildiği yüksek kaliteden oluşur. Başarılı bir şifre çözme işleminin yalnızca verilerin üzerinde oynanmadığı durumlarda olabileceği, başarılı ve şifre çözme farklılıklarını gözlemleyecek şekilde tasarlanan araçların saldırılarına karşı savunmasız olduğu varsayılarak uygulamalar. Bu zamanlama farkı, bazı dillerde veya kitaplıklarda diğerlerinden daha önemli olabilir, ancak bu durum, uygulamanın hata yanıtı hesaba alındıktan sonra bu, tüm diller ve kitaplıklar için pratik bir tehdit olduğunu düşünülüyor.

Bu saldırı, şifrelenen verileri değiştirme ve sonucu Oracle ile test etme yeteneğine bağımlıdır. Saldırıyı tamamen hafifletmenin tek yolu, şifrelenen verilerde yapılan değişiklikleri algılamadır ve üzerinde herhangi bir işlem gerçekleştirmeyi reddeder. Bunu yapmanın standart yolu, veriler için bir imza oluşturmak ve herhangi bir işlem gerçekleştirilmeden önce imzayı doğrulamak içindir. İmza doğrulanabilir olmalıdır, saldırgan tarafından oluşturulamaz, aksi takdirde şifrelenmiş verileri değiştirebilir, ardından değiştirilen verilere göre yeni bir imza hesaplar. Bir ortak uygun imza türü, anahtarlı karma ileti kimlik doğrulama kodu (HMAC) olarak bilinir. HMAC, yalnızca HMAC 'yi üreten kişi tarafından bilinen ve bunu doğrulayan kişiye ait gizli anahtar alan bir sağlama toplamıyla farklılık gösterir. Anahtarı elinde bulunmadan doğru bir HMAC oluşturamıyoruz. Verilerinizi aldığınızda, sizin ve gönderen paylaşımının gizli anahtarını kullanarak HMAC 'yi bağımsız olarak hesapladıktan sonra, sizin oluşturduğunuz bir parola ile gönderilen HMAC 'yi karşılaştırırsınız. Bu karşılaştırma sabit zamanlı olmalıdır, aksi takdirde başka bir algılanabilir Oracle eklediniz, farklı bir tür saldırıya izin verir.

Özet ' te, doldurulmuş CBC blok şifrelemelerini güvenle kullanmak için, verilerin şifresini çözmeyi denemeden önce sabit bir zaman karşılaştırması kullanarak doğruladığınız bir HMAC (veya başka bir veri bütünlüğü denetimi) ile birleştirmeniz gerekir. Değiştirilen tüm iletiler yanıt üretmek için aynı miktarda zaman aldığı için, saldırı engellenir.

## <a name="who-is-vulnerable"></a>Güvenlik açığı kimler

Bu güvenlik açığı, kendi şifrelemesini ve şifre çözmeyi gerçekleştiren hem yönetilen hem de yerel uygulamalar için geçerlidir. Bu, örneğin:

- Daha sonra sunucuda şifresinin çözülmesi için bir tanımlama bilgisi şifreleyen uygulama.
- Kullanıcıların, sütunları daha sonra şifresi çözülen bir tabloya veri eklemesine olanak sağlayan bir veritabanı uygulaması.
- Geçiş sırasında verileri korumak için paylaşılan bir anahtar kullanarak şifrelemeye dayalı bir veri aktarma uygulaması.
- TLS tünelinin "içindeki" iletilerini şifreleyen ve şifresini çözdüğü bir uygulama.

Bu senaryolarda yalnızca TLS kullanmanın sizi koruyamadığını unutmayın.

Savunmasız bir uygulama:

- , BHŞIFRE modunu kullanarak, PKCS # 7 veya ANSI X. 923 gibi bir doğrulanabilen doldurma moduyla verilerin şifresini çözer.
- Veri bütünlüğü denetimi gerçekleştirmeden (MAC veya asimetrik dijital imza aracılığıyla) şifre çözme gerçekleştirir.

Bu, şifreleme Iletisi sözdizimi (PKCS # 7/CMS) EnvelopedData yapısı gibi bu temel elemanların üst kısmında oluşturulan uygulamalar için de geçerlidir.

## <a name="related-areas-of-concern"></a>İlgili sorun bölgeleri

Araştırma, Microsoft 'un, iletinin iyi bilinen veya öngörülebilir bir altbilgi yapısına sahip olduğu durumlarda ISO 10126 ile doldurulmuş CBC iletileri hakkında daha fazla endişeniz olduğunu fark etti. Örneğin, W3C XML şifreleme söz dizimi ve Işleme önerisi (xmlenc, EncryptedXml) kuralları altında hazırlanan içerik. İletiyi imzalamak için W3C Kılavuzu, daha sonra şifreleyin ve bu süre içinde uygun kabul edilse de, Microsoft artık her zaman şifrelemeden sonra-ENTER ' ı önerir.

Asimetrik bir anahtarla rastgele bir ileti arasında herhangi bir güven ilişkisi bulunmadığından, uygulama geliştiricileri her zaman asimetrik imza anahtarının uygulanabilirliğini doğrulamak için en az olmalıdır.

## <a name="details"></a>Ayrıntılar

Tarihsel olarak, HMAC veya RSA imzaları gibi yollarla önemli verileri şifrelemek ve kimliklerini doğrulamak için önemli bir sorun oluştu. Ancak, şifreleme ve kimlik doğrulama işlemlerinin nasıl dizilebileceğine ilişkin daha az açık yönergeler vardır. Bu makalede açıklanan güvenlik açığı nedeniyle, Microsoft 'un artık "şifreleyin-then-imzala" paradigmasını her zaman kullanması gerekir. Diğer bir deyişle, önce simetrik anahtar kullanarak verileri şifreler, sonra şifreli bir MAC veya asimetrik imza (şifrelenmiş veriler) üzerinden işlem yapın. Verilerin şifresini çözerken, ters işlemini gerçekleştirin. İlk olarak, şifreli nesnelerin MAC veya imzasını onaylayın ve sonra şifresini çözün.

"Oracle saldırılarını doldurma" olarak bilinen bir güvenlik açığı sınıfı, 10 yıldan fazla bir süredir mevcut olduğu bilinmektedir. Bu güvenlik açıkları, bir saldırganın her veri bloğu için 4096 ' den fazla girişim kullanılarak AES ve 3DES gibi simetrik blok algoritmalarıyla şifrelenmiş verilerin şifresini çözmesine olanak tanır. Bu güvenlik açıkları, şifrelemelerin blok verileri sonunda en sık kullanılan doğrulanabilir doldurma verileriyle kullanımını engeller. Bir saldırgan şifreli ile oynayabilir ve yapılan bir hatanın sonda bir hata nedeniyle başarısız olup olmadığını fark etmeksizin, saldırganın verilerin şifresini çözebilmesini sağlayabilirsiniz.

Başlangıçta pratik saldırılar, ASP.NET güvenlik açığı [MS10-070](/security-updates/SecurityBulletins/2010/ms10-070)gibi doldurma 'nın geçerli olup olmadığına göre farklı hata kodları döndüren hizmetlere dayanmaktadır. Bununla birlikte, Microsoft artık işleme geçerli ve geçersiz doldurma arasındaki farkları kullanarak benzer saldırıları gerçekleştirmek için pratik olduğunu düşünmektedir.

Şifreleme şeması bir imza kullanır ve imza doğrulamasının belirli bir veri uzunluğu (içeriğinden bağımsız olarak) için sabit bir çalışma zamanı ile gerçekleştirildiğinden, veri bütünlüğü bir saldırgana bir [taraf kanal](https://en.wikipedia.org/wiki/Side-channel_attack)aracılığıyla herhangi bir bilgi yaymadan doğrulanabilir. Bütünlük denetimi, değiştirilen iletileri reddettiğinde, Oracle tehdidi doldurma işlemi azaltılmış olur.

## <a name="guidance"></a>Kılavuz

İlk ve daha önce, Microsoft, gizlilik ihtiyaçlarına sahip tüm verilerin Aktarım Katmanı Güvenliği (TLS) üzerinden aktarılması ve Güvenli Yuva Katmanı (SSL) ' nin ardıl olması önerilir.

Sonra, uygulamanızı şu şekilde çözümleyin:

- Hangi şifrelemeyi tam olarak kullandığınızı ve kullanmakta olduğunuz platformlar ve API 'Ler tarafından hangi şifrelemenin sağlandığını anlayın.
- Bir simetrik [blok şifre algoritmasındaki](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers)AES ve 3DES gibi her bir kullanımın, bir gizli anahtar veri bütünlüğü denetimi (asimetrik Imza, HMAC veya şifre modunu, GCM veya CCM gibi [kimliği doğrulanmış şifreleme](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE) modu olarak değiştirme) dahil edin.

Geçerli araştırmayı temel alan genellikle, kimlik doğrulama ve şifreleme adımları AE olmayan şifreleme modları için bağımsız olarak gerçekleştirildiğinde, en iyi genel seçenektir. Bununla birlikte, şifrelemeye en uygun yanıt yoktur ve bu Genelleştirme, profesyonel bir cryptotlv ile yönlendirilmiş tavsiyeler kadar iyi değildir.

Mesajlaşma biçimini değiştiremedik ancak kimliği doğrulanmamış CBC şifre çözme işlemini gerçekleştirmeye yönelik uygulamalar, şu gibi azaltıcı etkenleri kullanmayı denemenize önerilir:

- Şifre çözme, şifre çözücü 'ın doldurmayı doğrulamasına veya kaldırmasına izin vermeden çözülür:
  - Uygulanan herhangi bir doldurma hala kaldırılmalı veya yoksayıldı, bu da yükü uygulamanıza taşıyor olursunuz.
  - Bu avantaj, doldurma doğrulamanın ve kaldırmanın diğer uygulama verileri doğrulama mantığına dahil edilebilir olması olabilir. Doldurma doğrulaması ve veri doğrulaması sabit zamanlı olarak yapılabiliyorsanız, tehdit azalır.
  - Doldurma yorumu algılanan ileti uzunluğunu değiştirdiği için, bu yaklaşımdan alınan zamanlama bilgileri yine de olabilir.
- Şifre çözme doldurma modunu ISO10126 olarak değiştirin:
  - ISO10126 şifre çözme dolgusu, hem PKCS7 şifreleme dolgusu hem de ANSIX923 şifreleme dolgusu ile uyumludur.
  - Modunun değiştirilmesi, Oracle bilgisinin tüm blok yerine 1 bayta doldurmasını azaltır. Ancak içeriğin, kapanış XML öğesi gibi iyi bilinen bir altbilgisi varsa ilgili saldırılar da iletinin geri kalanına saldırmak için devam edebilir.
  - Bu Ayrıca, saldırganın aynı düz metin ile farklı bir ileti kaymasıyla birden çok kez şifrelenmesini engelleyebileceği durumlarda düz metin kurtarmayı engellemez.
- Zamanlama sinyalini sönmek için bir şifre çözme çağrısının değerlendirilmesine geçit:
  - Saklama zamanı hesaplamasının, doldurma işleminin bulunduğu tüm veri kesimlerine yönelik olarak en fazla bir şifre çözme işleminin gerçekleşmesi için en az sürede olması gerekir.
  - Zaman hesaplamaları, <xref:System.Environment.TickCount?displayProperty=nameWithType> (kullanıma alma/taşma) veya iki sistem zaman damgasını (NTP ayarlama hatalarıyla ilgili olarak) değil, [yüksek çözünürlüklü zaman damgaları](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps)elde etmek için yapılmalıdır.
  - Zaman hesaplamaları, yalnızca sonuna kadar değil, yönetilen veya C++ uygulamalardaki tüm olası özel durumlar dahil olmak üzere şifre çözme işleminin yerine eklenmelidir.
  - Başarı veya başarısızlık henüz belirlendiyse, zaman aşımı kapısı zaman aşımına uğradığında hata döndürmemelidir.
- Kimliği doğrulanmamış bir şifre çözme işlemi gerçekleştiren hizmetler, "geçersiz" iletilerinin bir taşın bir şekilde gelip gelmediğini tespit etmek için izlenmesi gerekir.
  - Bu sinyalin, hem hatalı pozitif sonuçları (meşru olmayan veriler) hem de yanlış negatifleri (atlatabilir algılama için çok uzun bir süre boyunca saldırıyı yayma) taşıdığını unutmayın.

## <a name="finding-vulnerable-code---native-applications"></a>Savunmasız koda yerel uygulamalar bulma

Windows şifrelemesi: yeni nesil (CNG) kitaplığı 'nda oluşturulan programlar için:

- Şifre çözme çağrısı, `BCRYPT_BLOCK_PADDING` bayrağını belirterek [Bcryptşifre çözmeye](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt)yapılır.
- Anahtar tanıtıcısı, [BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE) `BCRYPT_CHAIN_MODE_CBC`olarak ayarlanmış [bcryptsetproperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) çağırarak başlatıldı.
  - `BCRYPT_CHAIN_MODE_CBC` varsayılan olduğundan, etkilenen kod `BCRYPT_CHAINING_MODE`için herhangi bir değer atamalamayabilir.

Eski Windows şifreleme API 'sine karşı oluşturulan programlar için:

- Şifre çözme çağrısı, `Final=TRUE`ile [Cryptşifre çözme](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) işlemi yapılır.
- Anahtar tanıtıcısı, `CRYPT_MODE_CBC`olarak ayarlanmış [KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam) [Cryptsetkeyparad](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) çağırarak başlatıldı.
  - `CRYPT_MODE_CBC` varsayılan olduğundan, etkilenen kod `KP_MODE`için herhangi bir değer atamalamayabilir.

## <a name="finding-vulnerable-code---managed-applications"></a>Savunmasız koda göre yönetilen uygulamalar bulma

- Şifre çözme çağrısı, <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType><xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> veya <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> yöntemlerine bağlıdır.
  - Bu, .NET içinde aşağıdaki türetilmiş türleri içerir, ancak üçüncü taraf türlerini de içerebilir:
    - <xref:System.Security.Cryptography.Aes>
    - <xref:System.Security.Cryptography.AesCng>
    - <xref:System.Security.Cryptography.AesCryptoServiceProvider>
    - <xref:System.Security.Cryptography.AesManaged>
    - <xref:System.Security.Cryptography.DES>
    - <xref:System.Security.Cryptography.DESCryptoServiceProvider>
    - <xref:System.Security.Cryptography.RC2>
    - <xref:System.Security.Cryptography.RC2CryptoServiceProvider>
    - <xref:System.Security.Cryptography.Rijndael>
    - <xref:System.Security.Cryptography.RijndaelManaged>
    - <xref:System.Security.Cryptography.TripleDES>
    - <xref:System.Security.Cryptography.TripleDESCng>
    - <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> özelliği <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>veya <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>olarak ayarlanmıştır.
  - <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> varsayılan olduğundan, etkilenen koda hiçbir şekilde <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> özelliği atanmayabilir.
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> özelliği <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> olarak ayarlandı
  - <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> varsayılan olduğundan, etkilenen koda hiçbir şekilde <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> özelliği atanmayabilir.

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a>Güvenlik açığı kodu bulma-şifreleme iletisi sözdizimi

Şifrelenmiş içeriği AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) veya RC2 (1.2.840.113549.3.2) için CBC modunu kullanan, kimliği doğrulanmamış bir CMS EnvelopedData iletisi Ayrıca, CBC modunda başka bir blok şifre algoritmasını kullanan iletiler ve güvenlik açığı.

Akış şifrelemeleri bu belirli güvenlik açığına karşı savunmasız olmasa da, Microsoft, her zaman ContentEncryptionAlgorithm değerini inceleyerek verilerin kimlik doğrulamasını önerir.

Yönetilen uygulamalar için, <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>iletilen herhangi bir değer olarak bir CMS EnvelopedData blobu algılanabilir.

Yerel uygulamalar için, bir CMS EnvelopedData blobu, elde edilen [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) `CMSG_ENVELOPED` ve/veya CMS tanıtıcısı daha sonra [cryptmsgcontrol](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol)aracılığıyla bir `CMSG_CTRL_DECRYPT` yönergesini gönderdiyse [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) aracılığıyla bir CMS tanıtıcısına sağlanan herhangi bir değer olarak algılanabilir.

## <a name="vulnerable-code-example---managed"></a>Güvenlik açığı bulunan kod örneği-yönetilen

Bu yöntem bir tanımlama bilgisini okur ve şifresini çözer ve veri bütünlüğü denetimi görünmez. Bu nedenle, bu yöntem tarafından okunan bir tanımlama bilgisinin içeriği, kendisini alan Kullanıcı tarafından veya şifrelenmiş tanımlama bilgisi değerini almış olan herhangi bir saldırgan tarafından saldırıya uğrayılabilir.

```csharp
private byte[] DecryptCookie(string cookieName)
{
    HttpCookie cookie = Request.Cookies[cookieName];

    if (cookie == null)
    {
        return null;
    }

    using (ICryptoTransform decryptor = _aes.CreateDecryptor())
    using (MemoryStream memoryStream = new MemoryStream())
    using (CryptoStream cryptoStream =
        new CryptoStream(memoryStream, decryptor, CryptoStreamMode.Write))
    {
        byte[] readCookie = Convert.FromBase64String(cookie.Value);
        cryptoStream.Write(readCookie, 0, readCookie.Length);
        cryptoStream.FlushFinalBlock();
        return memoryStream.ToArray();
    }
}
```

## <a name="example-code-following-recommended-practices---managed"></a>Önerilen uygulamalar-yönetilen örnek kodu

Aşağıdaki örnek kod standart olmayan bir ileti biçimi kullanır

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

`cipher_algorithm_id` ve `hmac_algorithm_id` algoritma tanımlayıcıları, bu algoritmaların uygulama yerel (Standart olmayan) temsilleridir. Bu tanımlayıcılar, tam olarak birleştirilmiş bir bytestream yerine mevcut mesajlaşma protokolünün diğer bölümlerinde anlamlı olabilir.

Bu örnek ayrıca bir şifreleme anahtarı ve HMAC anahtarı türetmek için tek bir ana anahtar kullanır. Bu, listedir anahtarlı bir uygulamayı çift anahtarlı bir uygulamaya açmak ve iki anahtarı farklı değerler olarak korumak için kolaylık olarak sağlanır. Bu, HMAC anahtar ve şifreleme anahtarının eşitlememe dışı olmasını da güvence altına alır.

Bu örnek, şifreleme veya şifre çözme için <xref:System.IO.Stream> kabul etmez. Geçerli veri biçimi, `hmac_tag` değeri, şifreli dosyadan önce olduğundan tek geçişli şifrelemeyi zorlaştırır. Ancak, bu biçim, ayrıştırıcının daha kolay tutulmasını sağlamak için başındaki tüm sabit boyutlu öğeleri sakladığı için seçilmiştir. Bu veri biçimiyle, tek taramalı şifre çözme mümkün olsa da, bir uygulayıcının GetHashAndReset çağrısına ve TransformFinalBlock çağrılmadan önce sonucu doğrulamaya yönelik bir sorun vardır. Akış şifrelemesi önemliyse, farklı bir AE modu gerekebilir.

```csharp
// ==++==
//
//   Copyright (c) Microsoft Corporation.  All rights reserved.
//
//   Shared under the terms of the Microsoft Public License,
//   https://opensource.org/licenses/MS-PL
//
// ==--==

using System;
using System.Diagnostics;
using System.IO;
using System.Runtime.CompilerServices;
using System.Security.Cryptography;

namespace Microsoft.Examples.Cryptography
{
    public enum AeCipher : byte
    {
        Unknown,
        Aes256CbcPkcs7,
    }

    public enum AeMac : byte
    {
        Unknown,
        HMACSHA256,
        HMACSHA384,
    }

    /// <summary>
    /// Provides extension methods to make HashAlgorithm look like .NET Core's
    /// IncrementalHash
    /// </summary>
    internal static class IncrementalHashExtensions
    {
        public static void AppendData(this HashAlgorithm hash, byte[] data)
        {
            hash.TransformBlock(data, 0, data.Length, null, 0);
        }

        public static void AppendData(
            this HashAlgorithm hash,
            byte[] data,
            int offset,
            int length)
        {
            hash.TransformBlock(data, offset, length, null, 0);
        }

        public static byte[] GetHashAndReset(this HashAlgorithm hash)
        {
            hash.TransformFinalBlock(Array.Empty<byte>(), 0, 0);
            return hash.Hash;
        }
    }

    public static partial class AuthenticatedEncryption
    {
        /// <summary>
        /// Use <paramref name="masterKey"/> to derive two keys (one cipher, one HMAC)
        /// to provide authenticated encryption for <paramref name="message"/>.
        /// </summary>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <param name="message">The message to encrypt</param>
        /// <returns>
        /// A concatenation of
        /// [cipher algorithm+chainmode+padding][mac algorithm][authtag][IV][ciphertext],
        /// suitable to be passed to <see cref="Decrypt"/>.
        /// </returns>
        /// <remarks>
        /// <paramref name="masterKey"/> should be a 128-bit (or bigger) value generated
        /// by a secure random number generator, such as the one returned from
        /// <see cref="RandomNumberGenerator.Create()"/>.
        /// This implementation chooses to block deficient inputs by length, but does not
        /// make any attempt at discerning the randomness of the key.
        ///
        /// If the master key is being input by a prompt (like a password/passphrase)
        /// then it should be properly turned into keying material via a Key Derivation
        /// Function like PBKDF2, represented by Rfc2898DeriveBytes. A 'password' should
        /// never be simply turned to bytes via an Encoding class and used as a key.
        /// </remarks>
        public static byte[] Encrypt(byte[] masterKey, byte[] message)
        {
            if (masterKey == null)
                throw new ArgumentNullException(nameof(masterKey));
            if (masterKey.Length < 16)
                throw new ArgumentOutOfRangeException(
                    nameof(masterKey),
                    "Master Key must be at least 128 bits (16 bytes)");
            if (message == null)
                throw new ArgumentNullException(nameof(message));

            // First, choose an encryption scheme.
            AeCipher aeCipher = AeCipher.Aes256CbcPkcs7;

            // Second, choose an authentication (message integrity) scheme.
            //
            // In this example we use the master key length to change from HMACSHA256 to
            // HMACSHA384, but that is completely arbitrary. This mostly represents a
            // "cryptographic needs change over time" scenario.
            AeMac aeMac = masterKey.Length < 48 ? AeMac.HMACSHA256 : AeMac.HMACSHA384;

            // It's good to be able to identify what choices were made when a message was
            // encrypted, so that the message can later be decrypted. This allows for
            // future versions to add support for new encryption schemes, but still be
            // able to read old data. A practice known as "cryptographic agility".
            //
            // This is similar in practice to PKCS#7 messaging, but this uses a
            // private-scoped byte rather than a public-scoped Object IDentifier (OID).
            // Please note that the scheme in this example adheres to no particular
            // standard, and is unlikely to survive to a more complete implementation in
            // the .NET Framework.
            //
            // You may be well-served by prepending a version number byte to this
            // message, but may want to avoid the value 0x30 (the leading byte value for
            // DER-encoded structures such as X.509 certificates and PKCS#7 messages).
            byte[] algorithmChoices = { (byte)aeCipher, (byte)aeMac };
            byte[] iv;
            byte[] cipherText;
            byte[] tag;

            // Using our algorithm choices, open an HMAC (as an authentication tag
            // generator) and a SymmetricAlgorithm which use different keys each derived
            // from the same master key.
            //
            // A custom implementation may very well have distinctly managed secret keys
            // for the MAC and cipher, this example merely demonstrates the master to
            // derived key methodology to encourage key separation from the MAC and
            // cipher keys.
            using (HMAC tagGenerator = GetMac(aeMac, masterKey))
            {
                using (SymmetricAlgorithm cipher = GetCipher(aeCipher, masterKey))
                using (ICryptoTransform encryptor = cipher.CreateEncryptor())
                {
                    // Since no IV was provided, a random one has been generated
                    // during the call to CreateEncryptor.
                    //
                    // But note that it only does the auto-generation once. If the cipher
                    // object were used again, a call to GenerateIV would have been
                    // required.
                    iv = cipher.IV;

                    cipherText = Transform(encryptor, message, 0, message.Length);
                }

                // The IV and ciphertest both need to be included in the MAC to prevent
                // tampering.
                //
                // By including the algorithm identifiers, we have technically moved from
                // simple Authenticated Encryption (AE) to Authenticated Encryption with
                // Additional Data (AEAD). By including the algorithm identifiers in the
                // MAC, it becomes harder for an attacker to change them as an attempt to
                // perform a downgrade attack.
                //
                // If you've added a data format version field, it can also be included
                // in the MAC to further inhibit an attacker's options for confusing the
                // data processor into believing the tampered message is valid.
                tagGenerator.AppendData(algorithmChoices);
                tagGenerator.AppendData(iv);
                tagGenerator.AppendData(cipherText);
                tag = tagGenerator.GetHashAndReset();
            }

            // Build the final result as the concatenation of everything except the keys.
            int totalLength =
                algorithmChoices.Length +
                tag.Length +
                iv.Length +
                cipherText.Length;

            byte[] output = new byte[totalLength];
            int outputOffset = 0;

            Append(algorithmChoices, output, ref outputOffset);
            Append(tag, output, ref outputOffset);
            Append(iv, output, ref outputOffset);
            Append(cipherText, output, ref outputOffset);

            Debug.Assert(outputOffset == output.Length);
            return output;
        }

        /// <summary>
        /// Reads a message produced by <see cref="Encrypt"/> after verifying it hasn't
        /// been tampered with.
        /// </summary>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <param name="cipherText">
        /// The output of <see cref="Encrypt"/>: a concatenation of a cipher ID, mac ID,
        /// authTag, IV, and cipherText.
        /// </param>
        /// <returns>The decrypted content.</returns>
        /// <exception cref="ArgumentNullException">
        /// <paramref name="masterKey"/> is <c>null</c>.
        /// </exception>
        /// <exception cref="ArgumentNullException">
        /// <paramref name="cipherText"/> is <c>null</c>.
        /// </exception>
        /// <exception cref="CryptographicException">
        /// <paramref name="cipherText"/> identifies unknown algorithms, is not long
        /// enough, fails a data integrity check, or fails to decrypt.
        /// </exception>
        /// <remarks>
        /// <paramref name="masterKey"/> should be a 128-bit (or larger) value
        /// generated by a secure random number generator, such as the one returned from
        /// <see cref="RandomNumberGenerator.Create()"/>. This implementation chooses to
        /// block deficient inputs by length, but doesn't make any attempt at
        /// discerning the randomness of the key.
        ///
        /// If the master key is being input by a prompt (like a password/passphrase),
        /// then it should be properly turned into keying material via a Key Derivation
        /// Function like PBKDF2, represented by Rfc2898DeriveBytes. A 'password' should
        /// never be simply turned to bytes via an Encoding class and used as a key.
        /// </remarks>
        public static byte[] Decrypt(byte[] masterKey, byte[] cipherText)
        {
            // This example continues the .NET practice of throwing exceptions for
            // failures. If you consider message tampering to be normal (and thus
            // "not exceptional") behavior, you may like the signature
            // bool Decrypt(byte[] messageKey, byte[] cipherText, out byte[] message)
            // better.
            if (masterKey == null)
                throw new ArgumentNullException(nameof(masterKey));
            if (masterKey.Length < 16)
                throw new ArgumentOutOfRangeException(
                    nameof(masterKey),
                    "Master Key must be at least 128 bits (16 bytes)");
            if (cipherText == null)
                throw new ArgumentNullException(nameof(cipherText));

            // The format of this message is assumed to be public, so there's no harm in
            // saying ahead of time that the message makes no sense.
            if (cipherText.Length < 2)
            {
                throw new CryptographicException();
            }

            // Use the message algorithm headers to determine what cipher algorithm and
            // MAC algorithm are going to be used. Since the same Key Derivation
            // Functions (KDFs) are being used in Decrypt as Encrypt, the keys are also
            // the same.
            AeCipher aeCipher = (AeCipher)cipherText[0];
            AeMac aeMac = (AeMac)cipherText[1];

            using (SymmetricAlgorithm cipher = GetCipher(aeCipher, masterKey))
            using (HMAC tagGenerator = GetMac(aeMac, masterKey))
            {
                int blockSizeInBytes = cipher.BlockSize / 8;
                int tagSizeInBytes = tagGenerator.HashSize / 8;
                int headerSizeInBytes = 2;
                int tagOffset = headerSizeInBytes;
                int ivOffset = tagOffset + tagSizeInBytes;
                int cipherTextOffset = ivOffset + blockSizeInBytes;
                int cipherTextLength = cipherText.Length - cipherTextOffset;
                int minLen = cipherTextOffset + blockSizeInBytes;

                // Again, the minimum length is still assumed to be public knowledge,
                // nothing has leaked out yet. The minimum length couldn't just be calculated
                // without reading the header.
                if (cipherText.Length < minLen)
                {
                    throw new CryptographicException();
                }

                // It's very important that the MAC be calculated and verified before
                // proceeding to decrypt the ciphertext, as this prevents any sort of
                // information leaking out to an attacker.
                //
                // Don't include the tag in the calculation, though.

                // First, everything before the tag (the cipher and MAC algorithm ids)
                tagGenerator.AppendData(cipherText, 0, tagOffset);

                // Skip the data before the tag and the tag, then read everything that
                // remains.
                tagGenerator.AppendData(
                    cipherText,
                    tagOffset + tagSizeInBytes,
                    cipherText.Length - tagSizeInBytes - tagOffset);

                byte[] generatedTag = tagGenerator.GetHashAndReset();

                // The time it took to get to this point has so far been a function only
                // of the length of the data, or of non-encrypted values (e.g. it could
                // take longer to prepare the *key* for the HMACSHA384 MAC than the
                // HMACSHA256 MAC, but the algorithm choice wasn't a secret).
                //
                // If the verification of the authentication tag aborts as soon as a
                // difference is found in the byte arrays then your program may be
                // acting as a timing oracle which helps an attacker to brute-force the
                // right answer for the MAC. So, it's very important that every possible
                // "no" (2^256-1 of them for HMACSHA256) be evaluated in as close to the
                // same amount of time as possible. For this, we call CryptographicEquals
                if (!CryptographicEquals(
                    generatedTag,
                    0,
                    cipherText,
                    tagOffset,
                    tagSizeInBytes))
                {
                    // Assuming every tampered message (of the same length) took the same
                    // amount of time to process, we can now safely say
                    // "this data makes no sense" without giving anything away.
                    throw new CryptographicException();
                }

                // Restore the IV into the symmetricAlgorithm instance.
                byte[] iv = new byte[blockSizeInBytes];
                Buffer.BlockCopy(cipherText, ivOffset, iv, 0, iv.Length);
                cipher.IV = iv;

                using (ICryptoTransform decryptor = cipher.CreateDecryptor())
                {
                    return Transform(
                        decryptor,
                        cipherText,
                        cipherTextOffset,
                        cipherTextLength);
                }
            }
        }

        private static byte[] Transform(
            ICryptoTransform transform,
            byte[] input,
            int inputOffset,
            int inputLength)
        {
            // Many of the implementations of ICryptoTransform report true for
            // CanTransformMultipleBlocks, and when the entire message is available in
            // one shot this saves on the allocation of the CryptoStream and the
            // intermediate structures it needs to properly chunk the message into blocks
            // (since the underlying stream won't always return the number of bytes
            // needed).
            if (transform.CanTransformMultipleBlocks)
            {
                return transform.TransformFinalBlock(input, inputOffset, inputLength);
            }

            // If our transform couldn't do multiple blocks at once, let CryptoStream
            // handle the chunking.
            using (MemoryStream messageStream = new MemoryStream())
            using (CryptoStream cryptoStream =
                new CryptoStream(messageStream, transform, CryptoStreamMode.Write))
            {
                cryptoStream.Write(input, inputOffset, inputLength);
                cryptoStream.FlushFinalBlock();
                return messageStream.ToArray();
            }
        }

        /// <summary>
        /// Open a properly configured <see cref="SymmetricAlgorithm"/> conforming to the
        /// scheme identified by <paramref name="aeCipher"/>.
        /// </summary>
        /// <param name="aeCipher">The cipher mode to open.</param>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <returns>
        /// A SymmetricAlgorithm object with the right key, cipher mode, and padding
        /// mode; or <c>null</c> on unknown algorithms.
        /// </returns>
        private static SymmetricAlgorithm GetCipher(AeCipher aeCipher, byte[] masterKey)
        {
            SymmetricAlgorithm symmetricAlgorithm;

            switch (aeCipher)
            {
                case AeCipher.Aes256CbcPkcs7:
                    symmetricAlgorithm = Aes.Create();
                    // While 256-bit, CBC, and PKCS7 are all the default values for these
                    // properties, being explicit helps comprehension more than it hurts
                    // performance.
                    symmetricAlgorithm.KeySize = 256;
                    symmetricAlgorithm.Mode = CipherMode.CBC;
                    symmetricAlgorithm.Padding = PaddingMode.PKCS7;
                    break;
                default:
                    // An algorithm we don't understand
                    throw new CryptographicException();
            }

            // Instead of using the master key directly, derive a key for our chosen
            // HMAC algorithm based upon the master key.
            //
            // Since none of the symmetric encryption algorithms currently in .NET
            // support key sizes greater than 256-bit, we can use HMACSHA256 with
            // NIST SP 800-108 5.1 (Counter Mode KDF) to derive a value that is
            // no smaller than the key size, then Array.Resize to trim it down as
            // needed.

            using (HMAC hmac = new HMACSHA256(masterKey))
            {
                // i=1, Label=ASCII(cipher)
                byte[] cipherKey = hmac.ComputeHash(
                    new byte[] { 1, 99, 105, 112, 104, 101, 114 });

                // Resize the array to the desired keysize. KeySize is in bits,
                // and Array.Resize wants the length in bytes.
                Array.Resize(ref cipherKey, symmetricAlgorithm.KeySize / 8);

                symmetricAlgorithm.Key = cipherKey;
            }

            return symmetricAlgorithm;
        }

        /// <summary>
        /// Open a properly configured <see cref="HMAC"/> conforming to the scheme
        /// identified by <paramref name="aeMac"/>.
        /// </summary>
        /// <param name="aeMac">The message authentication mode to open.</param>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <returns>
        /// An HMAC object with the proper key, or <c>null</c> on unknown algorithms.
        /// </returns>
        private static HMAC GetMac(AeMac aeMac, byte[] masterKey)
        {
            HMAC hmac;

            switch (aeMac)
            {
                case AeMac.HMACSHA256:
                    hmac = new HMACSHA256();
                    break;
                case AeMac.HMACSHA384:
                    hmac = new HMACSHA384();
                    break;
                default:
                    // An algorithm we don't understand
                    throw new CryptographicException();
            }

            // Instead of using the master key directly, derive a key for our chosen
            // HMAC algorithm based upon the master key.
            // Since the output size of the HMAC is the same as the ideal key size for
            // the HMAC, we can use the master key over a fixed input once to perform
            // NIST SP 800-108 5.1 (Counter Mode KDF):
            hmac.Key = masterKey;

            // i=1, Context=ASCII(MAC)
            byte[] newKey = hmac.ComputeHash(new byte[] { 1, 77, 65, 67 });

            hmac.Key = newKey;
            return hmac;
        }

        // A simple helper method to ensure that the offset (writePos) always moves
        // forward with new data.
        private static void Append(byte[] newData, byte[] combinedData, ref int writePos)
        {
            Buffer.BlockCopy(newData, 0, combinedData, writePos, newData.Length);
            writePos += newData.Length;
        }

        /// <summary>
        /// Compare the contents of two arrays in an amount of time which is only
        /// dependent on <paramref name="length"/>.
        /// </summary>
        /// <param name="a">An array to compare to <paramref name="b"/>.</param>
        /// <param name="aOffset">
        /// The starting position within <paramref name="a"/> for comparison.
        /// </param>
        /// <param name="b">An array to compare to <paramref name="a"/>.</param>
        /// <param name="bOffset">
        /// The starting position within <paramref name="b"/> for comparison.
        /// </param>
        /// <param name="length">
        /// The number of bytes to compare between <paramref name="a"/> and
        /// <paramref name="b"/>.</param>
        /// <returns>
        /// <c>true</c> if both <paramref name="a"/> and <paramref name="b"/> have
        /// sufficient length for the comparison and all of the applicable values are the
        /// same in both arrays; <c>false</c> otherwise.
        /// </returns>
        /// <remarks>
        /// An "insufficient data" <c>false</c> response can happen early, but otherwise
        /// a <c>true</c> or <c>false</c> response take the same amount of time.
        /// </remarks>
        [MethodImpl(MethodImplOptions.NoInlining | MethodImplOptions.NoOptimization)]
        private static bool CryptographicEquals(
            byte[] a,
            int aOffset,
            byte[] b,
            int bOffset,
            int length)
        {
            Debug.Assert(a != null);
            Debug.Assert(b != null);
            Debug.Assert(length >= 0);

            int result = 0;

            if (a.Length - aOffset < length || b.Length - bOffset < length)
            {
                return false;
            }

            unchecked
            {
                for (int i = 0; i < length; i++)
                {
                    // Bitwise-OR of subtraction has been found to have the most
                    // stable execution time.
                    //
                    // This cannot overflow because bytes are 1 byte in length, and
                    // result is 4 bytes.
                    // The OR propagates all set bytes, so the differences are only
                    // present in the lowest byte.
                    result = result | (a[i + aOffset] - b[i + bOffset]);
                }
            }

            return result == 0;
        }
    }
}
```
