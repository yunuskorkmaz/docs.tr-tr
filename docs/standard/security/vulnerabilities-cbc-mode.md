---
title: CBC şifre çözme açığı
description: Dolgu kullanarak Şifreleme-Blok Zincirleme (CBC) modu simetrik şifre çözme modu ile zamanlama açıklarını nasıl algılayıp azalttınız öğrenin.
ms.date: 06/12/2018
author: blowdart
ms.openlocfilehash: 47520ea4c9c7d0ef4d79378c93c6ce1f2ba7dd6d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186093"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a>Doldurmayı kullanarak CBC modunda simetrik şifre çözmedeki zamanlama açıkları

Microsoft, çok özel durumlar dışında, doğrulanabilir dolgu uygulandığında, doğrulanabilir dolgu uygulaması uygulandığında, şifreleme-Blok Zincirleme (CBC) modu ile şifrelenmiş verilerin şifresini çözmenin artık güvenli olmadığına inanıyor Koşul -larda. Bu yargı şu anda bilinen kriptografik araştırmaya dayanmaktadır.

## <a name="introduction"></a>Giriş

Dolgu oracle saldırısı, saldırganın anahtarı bilmeden verilerin içeriğini çözmesini sağlayan şifrelenmiş verilere karşı bir saldırı türüdür.

Bir kahin, saldırgana yürüttüldettikleri eylemin doğru olup olmadığı hakkında bilgi veren bir "tell" anlamına gelir. Bir çocukla tahta veya kart oyunu oynadığınızı düşünün. Yüzleri büyük bir gülümsemeyle parlıyorçünkü iyi bir hamle yapmak üzere olduklarını düşündükleri nde, bu bir kahindir. Siz, rakip olarak, bir sonraki hamlenizi uygun bir şekilde planlamak için bu kahini kullanabilirsiniz.

Dolgu belirli bir şifreleme terimidir. Verilerinizi şifrelemek için kullanılan algoritmalar olan bazı şifreler, her bloğun sabit boyutta olduğu veri blokları üzerinde çalışır. Şifrelemek istediğiniz veriler blokları doldurmak için doğru boyutta değilse, verileriniz bunu yapana kadar doldurulur. Dolgu birçok formları, orijinal giriş doğru boyutta olsa bile, dolgu her zaman mevcut olmasını gerektirir. Bu, dolgunun şifre çözme üzerine her zaman güvenli bir şekilde kaldırılmasını sağlar.

İki şeyi bir araya getirerek, bir dolgu kahini ile bir yazılım uygulaması, şifresi çözülmüş verilerin geçerli dolguya sahip olup olmadığını ortaya çıkarır. Kahin, geçersiz bir bloğun aksine geçerli bir bloğu işlemek için ölçülebilir derecede farklı bir zaman almak gibi "Geçersiz dolgu" yazan bir değeri döndürmek kadar basit bir şey olabilir.

Blok tabanlı şifrelemeler, ilk bloktaki verilerin ikinci bloktaki verilerle ilişkisini belirleyen mod adı verilen başka bir özelliğe sahiptir. En sık kullanılan modlardan biri CBC'dir. CBC, Başlangıç Vektörü (IV) olarak bilinen bir başlangıç rasgele bloğu tanıtır ve önceki bloğu statik şifreleme nin sonucuyla birleştirerek aynı iletiyi aynı anahtarla şifrelemenin her zaman aynı şifreli çıktıyı oluşturmamasını sağlar.

Bir saldırgan, CBC verilerinin nasıl yapılandırıldığıyla birlikte, oracle'ı ortaya çıkaran koda biraz değiştirilmiş iletiler göndermek ve oracle verilerin doğru olduğunu söyleyene kadar veri göndermeye devam etmek için bir dolgu kahini kullanabilir. Bu yanıttan, saldırgan ileti bayt byşifresini çözebilir.

Modern bilgisayar ağları, bir saldırganın uzak sistemlerde yürütme süresi nde çok küçük (0,1 ms'den az) farklılıkları algılayabileceği kadar yüksek kalitededir.Başarılı bir şifre çözmenin ancak verilerle değiştirilmediği zaman gerçekleşebileceğini varsayan uygulamalar, başarılı ve başarısız şifre çözme farklılıklarını gözlemlemek üzere tasarlanmış araçlardan gelen saldırılara karşı savunmasız olabilir. Bu zamanlama farkı bazı dillerde veya kütüphanelerde diğerlerinden daha önemli olsa da, uygulamanın hataya yanıtı dikkate alındığında bunun tüm diller ve kitaplıklar için pratik bir tehdit olduğuna inanılmaktadır.

Bu saldırı, şifrelenmiş verileri değiştirme ve sonucu kahinle test etme yeteneğine dayanır. Saldırıyı tamamen azaltmanın tek yolu, şifrelenmiş verilerdeki değişiklikleri algılamak ve saldırı yla ilgili herhangi bir eylemde bulunmaktan reddetmektir. Bunu yapmanın standart yolu, veriler için bir imza oluşturmak ve herhangi bir işlem gerçekleştirilmeden önce bu imzayı doğrulamaktır. İmza doğrulanabilir olmalıdır, saldırgan tarafından oluşturulamaz, aksi takdirde şifrelenmiş verileri değiştirir, sonra değiştirilen verilere dayalı yeni bir imza hesaplar. Sık kullanılan bir tür uygun imza, anahtarlı karma ileti kimlik doğrulama kodu (HMAC) olarak bilinir. Bir HMAC, yalnızca HMAC'yi üreten kişi ve onu doğrulayan kişi tarafından bilinen gizli bir anahtar alması açısından bir kontrolumdan farklıdır. Anahtara sahip olmadan doğru bir HMAC üretemezsiniz. Verilerinizi aldığınızda, şifrelenmiş verileri alır, sizin ve gönderenin paylaştığı gizli anahtarı kullanarak HMAC'yi bağımsız olarak hesaplar, ardından gönderdikleri HMAC'yi hesapladığınız verilerle karşılaştırın. Bu karşılaştırma sabit bir zaman olmalıdır, aksi takdirde farklı bir saldırı türüne izin veren başka bir algılanabilir kahin eklediniz.

Özetle, yastıklı CBC blok şifrelerini güvenli bir şekilde kullanmak için, verilerin şifresini çözmeye çalışmadan önce sabit bir zaman karşılaştırması kullanarak doğruladığınız bir HMAC (veya başka bir veri bütünlüğü denetimi) ile birleştirmeniz gerekir. Değiştirilen tüm iletilerin yanıt vermek için aynı miktarda zaman aldığı için, saldırı önlenir.

## <a name="who-is-vulnerable"></a>Kimler savunmasız

Bu güvenlik açığı, kendi şifreleme ve şifre çözme gerçekleştiren hem yönetilen hem de yerel uygulamalar için geçerlidir. Bu, örneğin içerir:

- Sunucuda daha sonra şifre çözme için bir çerez şifreleyen bir uygulama.
- Kullanıcıların, sütunları daha sonra şifresi çözülmüş bir tabloya veri ekleme olanağı sağlayan bir veritabanı uygulaması.
- Aktarım sırasındaverileri korumak için paylaşılan bir anahtar kullanarak şifrelemeye dayanan bir veri aktarım uygulaması.
- TLS tünelinde iletileri "içinde" şifreleyen ve şifresini çözen bir uygulama.

TLS'yi tek başına kullanmanın bu senaryolarda sizi koruyamayabileceğini unutmayın.

Savunmasız bir uygulama:

- PKCS#7 veya ANSI X.923 gibi doğrulanabilir bir doldurma moduyla CBC şifreleme modunu kullanarak verilerin şifresini çözer.
- Şifre çözmeyi veri bütünlüğü denetimi gerçekleştirmeden (MAC veya asimetrik dijital imza yoluyla) gerçekleştirir.

Bu, Şifreleme İleti Sözdizimi (PKCS#7/CMS) EnvelopedData yapısı gibi bu ilkel lerin üzerine soyutlamaların üzerine inşa edilmiş uygulamalar için de geçerlidir.

## <a name="related-areas-of-concern"></a>İlgili ilgi alanları

Araştırmalar, Microsoft'un, ileti iyi bilinen veya öngörülebilir altbilgi yapısına sahip olduğunda ISO 10126 eşdeğeri dolgu ile eklenen CBC iletileri konusunda daha fazla endişe duymasına yol açmıştır. Örneğin, W3C XML Şifreleme Sözdizimi ve İşleme Önerisi (xmlenc, EncryptedXml) kuralları altında hazırlanan içerik. İletiyi imzalamak için W3C kılavuzu sonra şifreleme kıvranmak o anda uygun kabul edilirken, Microsoft şimdi her zaman şifre-sonra-imza yapma önerir.

Uygulama geliştiricileri, asimetrik bir anahtar la rasgele bir ileti arasında doğal bir güven ilişkisi olmadığından, asimetrik imza anahtarının uygulanabilirliğini doğrulamakonusunda her zaman dikkatli olmalıdırlar.

## <a name="details"></a>Ayrıntılar

Tarihsel olarak, HMAC veya RSA imzaları gibi araçları kullanarak önemli verileri şifrelemenin ve doğrulamanın önemli olduğu konusunda fikir birliği vardır. Ancak, şifreleme ve kimlik doğrulama işlemlerinin nasıl sıralandığıkonusunda daha az net kılavuz lar olmuştur. Bu makalede ayrıntılı güvenlik açığı nedeniyle, Microsoft'un kılavuzu artık her zaman "şifrele-sonra-işareti" paradigmasını kullanmaktır. Diğer bir şey, önce verileri simetrik bir anahtar kullanarak şifreleyin, ardından şifre metni (şifrelenmiş veriler) üzerinde bir MAC veya asimetrik imza hesaplayın. Verilerin şifresini çözerken, ters icra edin. Önce, MAC'i veya şifreleme metninin imzasını onaylayın, ardından şifresini çözün.

"Dolgu oracle saldırıları" olarak bilinen güvenlik açıkları sınıfının 10 yılı aşkın bir süredir var olduğu bilinmektedir. Bu güvenlik açıkları, bir saldırganın veri bloğu başına en fazla 4096 deneme kullanarak AES ve 3DES gibi simetrik blok algoritmaları tarafından şifrelenmiş verilerin şifresini çözmesine olanak sağlar. Bu güvenlik açıkları, blok şifrelerinin en sık sonunda doğrulanabilir dolgu verileriyle kullanıldığı gerçeğini kullanır. Bir saldırganın şifreleme metnini kurcalayıp, kurcalamanın sonundaki dolgu biçiminde bir hataya neden olup olmadığını öğrenebildiği tespit edildi, saldırgan verilerin şifresini çözebilir.

Başlangıçta, pratik saldırılar, ASP.NET güvenlik açığı [MS10-070](/security-updates/SecurityBulletins/2010/ms10-070)gibi dolgunun geçerli olup olmadığına bağlı olarak farklı hata kodları döndürecek hizmetlere dayanıyordu. Ancak Microsoft, geçerli ve geçersiz dolgu işleme arasındaki zamanlama farklılıklarını kullanarak benzer saldırılar gerçekleştirmenin pratik olduğuna inanmaktadır.

Şifreleme düzeninde bir imza istihdam edilmesi ve imza doğrulamasının belirli bir veri uzunluğu için sabit bir çalışma süresiyle gerçekleştirilmesi koşuluyla (içerikten bağımsız olarak), veri bütünlüğü bir [yan kanal](https://en.wikipedia.org/wiki/Side-channel_attack)üzerinden saldırgana herhangi bir bilgi yayan olmadan doğrulanabilir. Bütünlük denetimi değiştirilmiş iletileri reddettiğinden, dolgu oracle tehdidi azaltılır.

## <a name="guidance"></a>Rehber

Her şeyden önce Microsoft, gizlilik gerektiren tüm verilerin Secure Sockets Layer (SSL) yerine geçen Transport Layer Security (TLS) üzerinden iletilmesini önerir.

Ardından, uygulamanızı şu şekilde analiz edin:

- Kullandığınız şifrelemeyi tam olarak ve kullandığınız platformlar ve API'ler tarafından hangi şifrelemenin sağlandığını anlayın.
- CBC modunda, AES ve 3DES gibi simetrik [blok şifreleme algoritmasının](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers)her katmanındaki her kullanımda gizli anahtarlı veri bütünlüğü denetimi (asimetrik imza, HMAC veya şifreleme modunu GCM veya CCM gibi [kimlik doğrulamalı](https://en.wikipedia.org/wiki/Authenticated_encryption) şifreleme (AE) moduna değiştirmek için bir dizi kullanım da dahil olun.

Geçerli araştırmaya dayanarak, kimlik doğrulama ve şifreleme adımları AE olmayan şifreleme modları için bağımsız olarak gerçekleştirildiğinde, şifreleme metninin (şifreleme-sonra işareti) doğrulanmasının en iyi genel seçenek olduğuna inanılır. Ancak, şifrelemeye tek boyutlu uygun doğru bir cevap yoktur ve bu genelleme profesyonel bir kriptografın tavsiyeettiği kadar iyi değildir.

İleti biçimini değiştiremeyen ancak kimlik doğrulamalı CBC şifresini çözemeyen uygulamaların aşağıdakiler gibi azaltıcı etkenler dahil etmeye çalışması teşvik edilir:

- Şifre çözücünün dolguyu doğrulamasına veya kaldırmasına izin vermeden şifreyi çöz:
  - Uygulanan herhangi bir dolgu hala kaldırılması veya göz ardı edilmesi gerekir, uygulamanıza yük taşıyorsanız.
  - Bunun yararı, dolgu doğrulama ve kaldırma diğer uygulama veri doğrulama mantığına dahil edilebilir olmasıdır. Dolgu doğrulaması ve veri doğrulaması sürekli olarak yapılabiliyorsa, tehdit azalır.
  - Dolgu nun yorumlanması algılanan ileti uzunluğunu değiştirdiğinden, bu yaklaşımdan yayılan zamanlama bilgileri hala olabilir.
- Şifre çözme doldurma modunu ISO10126 olarak değiştirin:
  - ISO10126 şifre çözme dolgusu hem PKCS7 şifreleme dolgusu hem de ANSIX923 şifreleme dolgusu ile uyumludur.
  - Modu değiştirmek, dolgu oracle bilgisini tüm blok yerine 1 bayt'a düşürür. Ancak, içeriğin kapanış XML öğesi gibi iyi bilinen bir altbilgi varsa, ilgili saldırılar iletinin geri kalanına saldırmaya devam edebilir.
  - Bu, saldırganın aynı düz metni farklı bir ileti dışofmemiyle birden çok kez şifrelenmesi için zorladığı durumlarda düz metin kurtarmayı da engellemez.
- Zamanlama sinyalini azaltmak için şifre çözme çağrısının değerlendirmesini geçitle:
  - Bekleme süresinin hesaplanması, deşifre işleminin dolgu içeren herhangi bir veri kesimi için alacağı maksimum süreyi en az aşmalıdır.
  - Zaman [hesaplamaları, yüksek çözünürlüklü zaman damgaları edinme](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps)kılavuzuna göre,(roll-over/taşma ya da iki sistem zaman damgası (NTP ayarlama hatalarına tabi) çıkarılarak değil, <xref:System.Environment.TickCount?displayProperty=nameWithType> yapılmalıdır.
  - Zaman hesaplamaları, yönetilen veya C++ uygulamalarındaki tüm olası özel durumlar da dahil olmak üzere şifre çözme işlemini de kapsamalıdır, sadece sonuna kadar yastıklanmamalıdır.
  - Başarı veya başarısızlık henüz belirlenmişse, zamanlama kapısının süresi dolduğunda hatadöndürmesi gerekir.
- Kimlik doğrulamamış şifre çözme gerçekleştiren hizmetlerin, "geçersiz" iletiler selini niçin geldiğini algılamak için yerinde izleme leri olmalıdır.
  - Bu sinyalin hem yanlış pozitifleri (meşru olarak bozulmuş veriler) hem de yanlış negatifleri (saldırıyı tespitten kaçınmak için yeterince uzun bir süre boyunca yaydığını) taşıdığını unutmayın.

## <a name="finding-vulnerable-code---native-applications"></a>Güvenlik açığı olan kodu bulma - yerel uygulamalar

Windows Şifreleme: Yeni Nesil (CNG) kitaplığına karşı oluşturulmuş programlar için:

- Şifre çözme çağrısı [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt)için , `BCRYPT_BLOCK_PADDING` bayrak belirterek.
- Anahtar kolu [BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE) ayarlanmış [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) arayarak başlatılması `BCRYPT_CHAIN_MODE_CBC`olmuştur.
  - Varsayılan `BCRYPT_CHAIN_MODE_CBC` olduğu için, etkilenen kod `BCRYPT_CHAINING_MODE`için herhangi bir değer atamış olmayabilir.

Eski Windows Şifreleme API'sına karşı oluşturulmuş programlar için:

- Şifre çözme çağrısı ile [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) `Final=TRUE`için.
- Anahtar kolu [cryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) KP_MODE [olarak](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam) ayarlanmış arayarak `CRYPT_MODE_CBC`başlatılması olmuştur.
  - Varsayılan `CRYPT_MODE_CBC` olduğu için, etkilenen kod `KP_MODE`için herhangi bir değer atamış olmayabilir.

## <a name="finding-vulnerable-code---managed-applications"></a>Güvenlik açığı kodu bulma - yönetilen uygulamalar

- Şifre çözme çağrısı <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> veya <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> üzerinde <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>yöntemler.
  - Bu, .NET içinde aşağıdaki türetilmiş türleri içerir, ancak üçüncü taraf türleri de içerebilir:
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
- Özellik <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>veya <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.
  - Varsayılan <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> olduğundan, etkilenen kod <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> özelliği hiç atamış olabilir.
- Özellik <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> ayarlandı<xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>
  - Varsayılan <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> olduğundan, etkilenen kod <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> özelliği hiç atamış olabilir.

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a>Güvenlik açığı kodu bulma - şifreleme iletisözdizimi

Şifreli içeriği AES'nin CBC modunu kullanan kimliği doğrulanmamış cms zarflı veri iletisi (2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) veya RC2 (1.2.840.113549.3.2) yanı sıra CBC modunda başka bir blok şifreleme algoritmaları kullanarak iletileri savunmasız.

Akış şifrelemeleri bu özel güvenlik açığına duyarlı olmasa da, Microsoft ContentEncryptionAlgorithm değerini inceleyerek verileri her zaman doğrulamasını önerir.

Yönetilen uygulamalar için, cms envelopedData blob'a <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>geçirilen herhangi bir değer olarak algılanabilir.

Yerel uygulamalar için, bir CMS EnvelopedData blob, ortaya çıkan [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) `CMSG_ENVELOPED` ve/veya CMS kolu daha sonra [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol)üzerinden `CMSG_CTRL_DECRYPT` bir talimat gönderilir [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) üzerinden CMS koluna sağlanan herhangi bir değer olarak algılanabilir.

## <a name="vulnerable-code-example---managed"></a>Savunmasız kod örneği - yönetilen

Bu yöntem bir çerez okur ve şifresini çözer ve hiçbir veri bütünlüğü denetimi görünür. Bu nedenle, bu yöntemle okunan bir çerezin içeriği, bu çerezi alan kullanıcı veya şifrelenmiş çerez değerini elde eden herhangi bir saldırgan tarafından saldırıya uğrayabilir.

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

## <a name="example-code-following-recommended-practices---managed"></a>Önerilen uygulamaları takip eden örnek kod - yönetilen

Aşağıdaki örnek kod, standart olmayan bir ileti biçimi kullanır

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

`cipher_algorithm_id` ve `hmac_algorithm_id` algoritma tanımlayıcılarının bu algoritmaların uygulama yerel (standart olmayan) gösterimleri olduğu yer. Bu tanımlayıcılar, mevcut ileti iletişim günümüzde ki ileti nizaminin diğer bölümlerinde, çıplak bir şekilde bir bytestream olarak değil, anlamlı olabilir.

Bu örnekte, hem şifreleme anahtarı hem de HMAC anahtarı elde etmek için tek bir ana anahtar da kullanır. Bu, hem tek tuşlu bir uygulamayı çift tuşlu bir uygulamaya dönüştürmek hem de iki anahtarı farklı değerler olarak tutmayı teşvik etmek için sağlanır. Ayrıca HMAC anahtarı ve şifreleme anahtarının senkronizasyondan çıkamalarını garanti eder.

Bu örnek şifreleme veya <xref:System.IO.Stream> şifre çözme için kabul etmez. Geçerli veri biçimi, tek geçişli `hmac_tag` şifrelemeyi zorlaştırır, çünkü değer şifreleme metninden önce gelir. Ancak, bu biçim, başlangıçta ki tüm sabit boyutlu öğeleri parser'ı daha basit tutmak için tuttuğundan seçildi. Bu veri biçimi yle, tek geçişli şifre çözme mümkündür, ancak bir uygulayıcı GetHashAndReset'i aramak ve TransformFinalBlock'u aramadan önce sonucu doğrulamak için uyarılır. Akış şifrelemesi önemliyse, farklı bir AE modu gerekebilir.

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
