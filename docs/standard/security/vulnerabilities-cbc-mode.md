---
title: Zamanlama açıklarıyla doldurmayı kullanarak CBC modunda simetrik şifre çözme
description: Algılanmasına ve zamanlama güvenlik açıkları dolgusu kullanılarak Şifre blok zincirleme (CBC) modunu simetrik şifre çözme ile öğrenin.
ms.date: 06/12/2018
author: blowdart
ms.author: mairaw
ms.openlocfilehash: 26f4d19f591ac02d792bebbd648e90b07d84de56
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208528"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a>Zamanlama açıklarıyla doldurmayı kullanarak CBC modunda simetrik şifre çözme

Microsoft düşündüğü artık doğrulanabilen doldurma ilk ciphertext bütünlüğünü dışında sağlama olmadan yapıldıysa simetrik şifreleme şifre blok zincirleme (CBC) modunu ile şifrelenmiş verilerin şifresini çözmek güvenli olduğunu belirli koşullar. Bu judgement üzerinde şu anda bilinen şifreleme araştırmaları temel alır. 

## <a name="introduction"></a>Giriş

Doldurma oracle saldırı, saldırganın anahtarı bilmeden veri içeriğinin şifresini çözmek şifrelenmiş veri saldırısı türüdür.

Bir oracle bir "bilgi" yürütme eylemi doğru olup olmamasına hakkında bir saldırganın bilgi veren ifade eder. Bir kart çalma düşünün veya bir çocuk oyun kartı. Ne zaman kendi yüz yanar ile büyük bir gülümseme gönderme aynen aynen taşıdığını düşündüğü çünkü bir oracle olan iyi bir ettirmek üzere. Bir sonraki uygun şekilde planlamak için bu oracle rakip kullanabilirsiniz.

Doldurma belirli bir şifreleme terimdir. Verilerinizi şifrelemek için kullanılan algoritmalar olan bazı şifrelemeleri blokların sabit bir boyuta olduğu veri blokları üzerinde çalışır. Şifrelemek istediğiniz veri blokları doldurmak için doğru boyutta değilse, bunu yapar kadar verilerinizi sıfır eklenir. Doldurma birçok forms özgün giriş uygun boyutta olsa bile her zaman, bulunması için dolgu gerektirir. Bu her zaman güvenli bir şekilde şifre çözme sırasında kaldırılacak doldurma sağlar.

İki şey bir araya getirilmesi, doldurma oracle yazılım uygulamasıyla şifresi çözülmüş veriler geçerli doldurma sahip olup olmadığını gösterir. Oracle "Geçersiz doldurma" belirten bir değer döndürme olarak basit bir şey ya da geçersiz bir blok aksine geçerli bir blok işlemek için sorunlarında farklı bir zaman ayırdığınız gibi daha karmaşık bir şey olabilir.

Şifre blok tabanlı veri ikinci blok verilerde ilk bloğundaki ilişki belirler, modu adlı başka bir özellik varsa ve benzeri. En yaygın kullanılan modlar CBC biridir. CBC başlatma vektörü (IV olarak), bilinen bir ilk rasgele blok tanıtır ve önceki blok aynı anahtar ile aynı iletiyi şifreleme her zaman aynı şifrelenmiş çıktı oluşturmuyor emin olmak için statik şifreleme sonucu ile birleştirir.

Oracle gösteren kodu için biraz değiştirilmiş iletilerini göndermek ve bunları oracle söyler kadar veri göndermeye devam verilerinin doğru olduğundan, bir saldırganın CBC verileri nasıl yapılandırıldığını ile birlikte bir doldurma oracle kullanabilirsiniz. Bu yanıt, saldırganın bayt ileti şifresini çözebilir.

Modern bilgisayar gibi kaliteli bir saldırganın çok küçük (değerinden 0,1 ms) yürütme farklılıkları uzak sistemlerde zaman algılayabilir ağlardır. Veri değiştirilmiş değildi ederken başarılı bir şifre çözme yalnızca ortaya çıkar varsayılarak uygulamaları başarılı ve başarısız şifre çözme farklılıkları izlemek için tasarlanmış Araçları'ndan saldırıya açık olabilir. Bu zamanlama fark diğerlerinden bazı dil ya da kitaplıkları daha önemli olsa da, bunu şimdi uygulamanın yanıt başarısızlık dikkate alındığında bu tüm diller ve kitaplıkları için kullanışlı bir tehdit olduğu düşünülen.

Bu saldırı şifrelenen verileri değiştirmek ve test sonucu oracle ile özelliği kullanır. Tam olarak saldırının etkisini azaltmak için yalnızca şifrelenmiş veriler üzerindeki değişiklikleri algılar ve herhangi bir eylem gerçekleştirmek Reddet yoludur. Bunu yapmak için standart verileri için imza oluşturma ve tüm işlemler gerçekleştirilir önce o imzayı doğrulamak için yoludur. İmza doğrulanabilen, saldırgan tarafından oluşturulamaz, aksi halde bunlar şifrelenmiş veriler değiştirin, sonra değiştirilen verileri temel alan yeni bir imza işlem. Bir ortak türü uygun imzalı bir anahtarlı karma ileti kimlik doğrulama kodu (HMAC) bilinir. Bir HMAC gizli bir anahtar yalnızca HMAC oluşturan kişiye ve bunu doğrulama kişiye bilinen sürdüğünü sağlama toplamı farklıdır. Anahtara sahip olan, doğru HMAC üretemiyor. Verilerinizi aldığınızda, şifrelenmiş veri almak, gizli anahtarı kullanarak HMAC ve gönderen paylaşımı sonra bunlar karşı bir gönderdiğiniz HMAC hesaplanan karşılaştırma bağımsız olarak işlem. Bu karşılaştırma sabit zaman olmalıdır, farklı türde bir saldırı sağlayan başka bir algılanabilir oracle, aksi takdirde ekledik.

Özet olarak, doldurulan güvenle CBC blok şifrelemeler kullanmak için bunları bir HMAC (veya başka bir veri bütünlüğü denetimi ile) kullanarak verileri şifrelemek için bir sabit zaman karşılaştırma denemeden önce doğrulayan birleştirebilirsiniz. Tüm değiştirilmiş iletileri bir yanıtı oluşturan aynı tutar zaman beri saldırı engellenir.

## <a name="who-is-vulnerable"></a>Güvenlik Açığı kim

Bu güvenlik açığından kendi şifreleme ve şifre çözme gerçekleştirme yönetilen ve yerel uygulamalar için geçerlidir. Bu, örneğin içerir:

- Tanımlama bilgisi sunucuda sonraki şifre çözme için şifreler bir uygulama.
- Kullanıcılara bir tabloya veri eklemek sütunları sağlayan bir veritabanı uygulaması daha sonra şifresi.
- Aktarımdaki verileri korumak için paylaşılan bir anahtar kullanarak şifreleme dayanan bir veri aktarımı uygulaması.
- Şifreler ve şifresini çözer "içindeki" TLS tüneli iletileri bir uygulama.

Tek başına TLS kullanarak, bu senaryolarda koruma sağlamaz olduğunu unutmayın.

Bir güvenlik açığı uygulama:

- PKCS #7 veya ANSI X.923 gibi bir doğrulanabilen doldurma modu CBC şifreleme modu kullanarak verilerin şifresini çözer.
- Şifre çözme veri bütünleştirme denetimi (MAC veya asimetrik bir dijital imza) üzerinden gerçekleştirilen olmadan gerçekleştirir.

Bu üst şifreleme iletisi söz dizimi (PKCS #7/CMS) EnvelopedData yapısı gibi bu elemanlar üzerinden soyutlamalar en üstünde oluşturulan uygulamalar için de geçerlidir.

## <a name="related-areas-of-concern"></a>Sorun ilgili alanlarını

Araştırma ISO 10126-ileti iyi bilinen veya tahmin edilebilir altbilgi yapısı olduğunda doldurma eşdeğerleriyle doldurulan CBC iletileri hakkında daha fazla endişe Microsoft'a açmıştır. Örneğin, işleme öneri (xmlenc, EncryptedXml) ve W3C XML şifreleme sözdizimi kurallarına altında hazırlanan içeriği. İletiyi şifrelemek için W3C Kılavuzu zaman uygun olarak kabul edildiği sırada Microsoft şimdi her zaman şifrelemek-ardından-oturum yapılması önerir.

Asimetrik anahtar ve rasgele bir ileti arasında bir devralınan güven ilişkisi olduğundan uygulama geliştiricileri her zaman bir asimetrik imza anahtarı uygulanabilirliğini doğrulanıyor dikkatli olmalıdır.

## <a name="details"></a>Ayrıntılar

Geçmişte, şifrelemek ve HMAC veya RSA İmza gibi yollarla kullanarak önemli verileri kimlik doğrulaması önemlidir anlaşma açıldı. Ancak, şifreleme ve kimlik doğrulama işlemleri sıralamak nasıl aldığını daha az Temizle Kılavuzu açıldı. Bu makalede ayrıntılı güvenlik açığı nedeniyle, Microsoft'un Kılavuzu şimdi her zaman "şifrelemek-ardından-oturum" kip kullanmaktır. Diğer bir deyişle, ilk simetrik anahtar kullanarak verileri şifrelemek ve sonra MAC ya da asimetrik imza (şifrelenmiş veriler) ciphertext işlem. Verilerin şifresini çözmek, ters gerçekleştirin. İlk olarak, MAC veya ciphertext imzası onaylayın, sonra şifresini.

Bir sınıf "oracle saldırıları doldurma" 10 yılı aşkın mevcut bilinmektedir olarak bilinen güvenlik açıklarının. Bu güvenlik açıkları, bir veri bloğunun başına en fazla 4096 denemeleri kullanarak AES ve 3DES ' gibi blok simetrik algoritmaları tarafından şifrelenmiş verilerin şifresini çözmek bir saldırganın. Bu güvenlik açıklarından olun şifrelemeleri engelleme olgu kullanımını sonunda doğrulanabilen doldurma verilerle en sık kullanılır. Bir saldırgan, ciphertext ile değiştirmesine ve olup kurcalama hata sonunda dolgunun biçiminde neden olduğunu bulmak, saldırganın verilerin şifresini çözebilen bulundu.

Başlangıçta, pratik doldurma gibi ASP.NET güvenlik açığı geçerli olup üzerinde farklı hata kodları döndürecektir Hizmetleri tabanlı saldırıları [MS10-070](https://technet.microsoft.com/library/security/ms10-070.aspx). Ancak, Microsoft artık yalnızca zamanlama geçersiz ve geçerli doldurma işleme arasındaki farklılıkları kullanan benzer saldırısı yapmanın pratik olduğunu düşünür.

İmza şifreleme şeması kullanır ve imza doğrulaması (yedeklemiş içeriği) veri belirli bir süre için sabit bir çalışma zamanı ile gerçekleştirilen koşuluyla, veri bütünlüğünü herhangi bir bilgi yayma olmadan doğrulanabilir bir Saldırgan aracılığıyla bir [yan kanal](https://en.wikipedia.org/wiki/Side-channel_attack). Değiştirilen herhangi bir ileti bütünlük denetimi reddeder beri doldurma oracle tehdit azalır.

## <a name="guidance"></a>Kılavuz

Öncelikle, Microsoft gizliliği sahip herhangi bir veriyi üzerinden Aktarım Katmanı Güvenliği (TLS), Güvenli Yuva Katmanı (SSL) için ardıl iletilmesi önerir.

Ardından, uygulamanıza çözümleyin:

- Gerçekleştirmekte olarak tam olarak hangi şifreleme anlayın ve hangi şifreleme platformlar ve API'ler, kullanmakta olduğunuz tarafından sağlanmaktadır.
- Belirli bir simetrik, her katmanda her kullanım olun [blok şifreleme algoritması](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), AES ve CBC modunda 3DES gizli anahtarlı veri bütünlüğü denetimi kullanımını birleştirmek gibi (bir HMAC asimetrik bir imza veya şifreleme modu değiştirmek için bir [şifreleme kimlik doğrulaması](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE) mod GCM veya CCM gibi).

Geçerli araştırmaya dayanarak, bu genellikle kimlik doğrulama ve şifreleme adımları bağımsız olarak şifreleme AE olmayan modları için gerçekleştirildiğinde, şifreli kimlik doğrulaması (şifrelemek-ardından-oturum) en iyi genel seçenek olduğunu düşünülen. Ancak, şifreleme için BT'ye bir doğru yanıt yok ve bu Genelleştirme profesyonel cryptographer kadar iyi yönlendirilmiş önerileri değil.

Kendi ileti biçimi değiştirebilirsiniz ancak kimlik doğrulamasız CBC şifre çözme gerçekleştirmek mümkün olan uygulamalar gibi Azaltıcı Etkenler içerecek şekilde denemek için önerilir:

- Doğrulamak veya doldurma kaldırmak şifre çözücü vermeden şifre çözme:
  - Uygulanan doldurma halen göz ardı veya kaldırılması gereken, uygulamanıza yükünü taşıma.
  - Avantajı, kaldırma ve doldurma doğrulama diğer uygulama veri doğrulama mantığı birleştirilebilir ' dir. Doldurma doğrulaması ve veri doğrulaması sabit zamanında yapılabilir, tehdit azalır.
  - Algılanan ileti uzunluğu doldurma yorumu değişiklikleri olduğundan, hala bu yaklaşımı yayılan zamanlama bilgi olabilir.
- Şifre çözme doldurma modu için ISO10126 değiştirin:
  - ISO10126 şifre çözme doldurma PKCS7 şifreleme doldurma ve ANSIX923 şifreleme doldurma ile uyumludur.
  - Modunu değiştirme doldurma oracle bilgi tüm blok yerine 1 bayt azaltır. Ancak, içerik XML öğesi, kapatma gibi iyi bilinen bir altbilgi varsa ilgili saldırıları iletinin kalan kısmını saldırmak devam edebilirsiniz.
  - Bu da saldırganın birden çok kez farklı ileti uzaklık ile şifrelenmesi için aynı düz metin burada zorlayacak durumlarda düz metin kurtarma engellemez.
- Ağ geçidi zamanlama sinyal Donuklaştır için bir şifre çözme çağrısı değerlendirmesi:
  - Tutma süresi hesaplama şifre çözme işlemi doldurma içeren veri kesimi için harcanacak en uzun süreyi aşan en az olmalıdır.
  - Saat hesaplamaları kılavuzunda göre yapılması [yüksek çözünürlüklü zaman damgaları alınırken](https://msdn.microsoft.com/library/windows/desktop/dn55340.aspx), kullanarak değil <xref:System.Environment.TickCount?displayProperty=nameWithType> (tabi Top-üzerinden/taşma) veya (tabi NTP ayarlama iki sistem zaman damgaları çıkarma hatalar).
  - Saat hesaplamaları tüm olası durumlar da dahil olmak üzere şifre çözme işlemi planlayacak yönetilmelidir ya da yalnızca bitiş doldurulan C++ uygulamaları.
  - Başarı veya başarısızlık henüz belirlendiyse, zamanlama kapısı süresi dolduğunda, hata döndürmesi gerekir.
- Kimliği doğrulanmamış şifre çözme işlemi Hizmetleri "geçersiz" iletilerinin sel geldiğini algılamak yerinde izleme olması gerekir.
  - Bu sinyal hatalı pozitif sonuç (yasal bozuk veri) ve (saldırı algılama alınmadan kurtulması için yeterince uzun bir süre içinde çıkış yayılmak) false negatif taşıyan aklınızda size aittir.

## <a name="finding-vulnerable-code---native-applications"></a>Güvenlik açığı kod - yerel uygulamalar bulma

Windows şifrelemesi karşı yerleşik programlar için: yeni nesil (CNG) kitaplığı:

- Şifre çözme çağrıdır [BCryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa375391.aspx), belirten `BCRYPT_BLOCK_PADDING` bayrağı.
- Anahtar tanıtıcısı çağırarak başlatıldı [BCryptSetProperty](https://msdn.microsoft.com/library/windows/desktop/aa375504.aspx) ile [BCRYPT_CHAINING_MODE](https://msdn.microsoft.com/library/windows/desktop/aa376211.aspx#BCRYPT_CHAINING_MODE) kümesine `BCRYPT_CHAIN_MODE_CBC`.
  - Bu yana `BCRYPT_CHAIN_MODE_CBC` etkilenen varsayılan kod atanmamıştır için herhangi bir değer `BCRYPT_CHAINING_MODE`.

Eski Windows şifreleme API'si karşı yerleşik programlar için:

- Şifre çözme çağrıdır [CryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa379913.aspx) ile `Final=TRUE`.
- Anahtar tanıtıcısı çağırarak başlatıldı [CryptSetKeyParam](https://msdn.microsoft.com/library/windows/desktop/aa380272.aspx) ile [KP_MODE](https://msdn.microsoft.com/library/windows/desktop/aa379949.aspx#KP_MODE) kümesine `CRYPT_MODE_CBC`.
  - Bu yana `CRYPT_MODE_CBC` etkilenen varsayılan kod atanmamıştır için herhangi bir değer `KP_MODE`.

## <a name="finding-vulnerable-code---managed-applications"></a>Bulma savunmasız kod - yönetilen uygulamalar

- Şifre çözme çağrıdır <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> veya <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> yöntemlere <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.
  - Bu, .NET içinde aşağıdaki türetilmiş türler içerir, ancak ayrıca üçüncü taraf türleri içerebilir:
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
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> Özelliği ayarlandığı <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, veya <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.
  - Bu yana <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> etkilenen varsayılan kod hiçbir zaman atamış <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> özelliği.
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> Özelliği ayarlandığı <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>
  - Bu yana <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> etkilenen varsayılan kod hiçbir zaman atamış <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> özelliği.

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a>Şifreleme iletisi söz dizimi savunmasız kod - bulma

Kimliği doğrulanmamış bir CMS EnvelopedData ileti şifrelenmiş içerikleri CBC modunda AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES kullanır (1.2.840.113549.3.7) veya RC2'yi (1.2.840.113549.3.2) değil güvenlik açığı, de gibi başka bir blok şifreleme algoritmaları CBC modunda iletileri.

Akış şifrelemeleri bu belirli açığı uygulanmadıkça değil, ancak Microsoft, her zaman veri ContentEncryptionAlgorithm değerini inceleyerek üzerinden kimlik doğrulaması yapan önerir.

Yönetilen uygulamalar için blob olabilir bir CMS EnvelopedData geçirilir olarak herhangi bir değer algılanan <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.

Yerel uygulamalar için bir CMS tanıtıcı sağlanan herhangi bir değer olarak bir CMS EnvelopedData blob algılanabilir [CryptMsgUpdate](https://msdn.microsoft.com/library/windows/desktop/aa380231.aspx) , elde edilen [CMSG_TYPE_PARAM](https://msdn.microsoft.com/library/windows/desktop/aa380227.aspx) olan `CMSG_ENVELOPED` ve/veya CMS tanıtıcısı Daha sonra gönderilen bir `CMSG_CTRL_DECRYPT` aracılığıyla yönerge [CryptMsgControl](https://msdn.microsoft.com/library/windows/desktop/aa380220.aspx).

## <a name="vulnerable-code-example---managed"></a>Güvenlik açığı kod örneğinde - yönetilen

Bu yöntem bir tanımlama bilgisi okur ve onu şifresini çözer ve hiçbir veri bütünlüğü denetimi tarafından görülebilir. Bu nedenle, bu yöntem tarafından salt okunur bir tanımlama bilgisinin içeriğinin aldığı kullanıcı tarafından veya şifrelenmiş bir tanımlama bilgisi değeri elde herhangi bir saldırgan tarafından saldırıya.

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

## <a name="example-code-following-recommended-practices---managed"></a>Örnek kod aşağıda yönetilen uygulamalar - önerilen

Aşağıdaki örnek kod bir standart ileti biçimine kullanır

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

Burada `cipher_algorithm_id` ve `hmac_algorithm_id` algoritması tanımlayıcılardır Bu algoritmalar (standart olmayan) gösterimlerini yerel uygulama. Bu tanımlayıcılar diğer bölümlerinde yerine, mevcut Mesajlaşma Protokolü tam bir birleştirilmiş bytestream mantıklı olabilir.

Bu örnek ayrıca bir şifreleme anahtarı ve bir HMAC anahtarı türetin için tek bir ana anahtar kullanır. Bu hem kolaylık ayrı olarak anahtarlı çift anahtarlı bir uygulamaya ve iki anahtar olarak farklı değerler tutma teşvik eden bir uygulama kapatmayı için sağlanır. Daha fazla eşitleme dışı HMAC anahtarı ve şifreleme anahtarı alınamıyor garanti eder.

Bu örnek kabul etmez bir <xref:System.IO.Stream> şifreleme veya şifre çözme için. Geçerli veri biçimi yaptığı bir geçişi zor şifrelemek için `hmac_tag` değeri ciphertext önce gelir. Ancak, tüm sabit boyutlu öğeleri ayrıştırıcı daha basit tutmak için başında tuttuğu için bu biçim seçildi. Bir uygulayan GetHashAndReset çağırın ve TransformFinalBlock çağırmadan önce sonucu doğrulamak için dikkatli olmalıdır ancak bu veri biçimi ile bir geçişi şifre çözme, mümkündür. Akış şifreleme önemliyse, farklı bir AE modu gerekli olabilir.

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
