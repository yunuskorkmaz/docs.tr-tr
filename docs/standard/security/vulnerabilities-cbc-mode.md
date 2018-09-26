---
title: Zamanlama açıklarıyla doldurmayı kullanarak CBC modunda simetrik şifre çözme
description: Algılama ve doldurmayı kullanarak Şifre blok zincirleme (CBC) modunu simetrik şifre çözme ile zamanlama güvenlik açıklarını azaltmaya öğrenin.
ms.date: 06/12/2018
author: blowdart
ms.author: mairaw
ms.openlocfilehash: 6d16b6849bfd4744f1828cda38a537f842243c1d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47109306"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a>Zamanlama açıklarıyla doldurmayı kullanarak CBC modunda simetrik şifre çözme

Microsoft, artık ilk ciphertext bütünlüğünü dışında sağlamaya gerek kalmadan doğrulanabilir doldurma yapıldıysa simetrik şifreleme şifre blok zincirleme (CBC) modunu ile şifrelenen verilerin şifresini çözmek güvenli olduğunu düşündüğü özgü koşullar. Bu judgement üzerinde şu anda bilinen şifreleme araştırmaları temel alır. 

## <a name="introduction"></a>Giriş

Doldurma oracle saldırı sağlar saldırgan anahtarı bilmeden içeriği verilerin şifresini çözmek, şifrelenmiş verilere karşı bir saldırı türüdür.

Bir "bilgi" bunlar yürütüyorsunuz eylem doğru olup olmamasına hakkında bir saldırgan bilgi veren bir oracle başvuruyor. Bir Pano yürütmeyi Imagine veya bir alt ile oyun kartı. Ne zaman kendi yüz yanar büyük gülümseme Filiz Filiz olarak gördüğü için oracle olan iyi bir ettirmek üzere. Bir sonraki uygun şekilde planlamak için bu oracle rakip kullanabilirsiniz.

Doldurma özel bir şifreleme terimdir. Verilerinizi şifrelemek için kullanılan algoritmalar olan bazı şifrelemeleri her blok sabit boyutta olduğu veri blokları üzerinde çalışır. Şifrelemek istediğiniz veri blokları doldurmak için doğru boyutta değilse, verilerinizi mevcut kadar sıfır eklenir. Doldurma birçok forms uygun boyutta özgün giriş olsa bile her zaman mevcut olacak şekilde bu doldurma gerektirir. Bu şifre çözme sırasında her zaman güvenli bir şekilde kaldırılması için doldurma sağlar.

İki şeyi bir araya getirildiğinde, bir yazılım uygulaması doldurma oracle ile şifresi çözülmüş veriler geçerli doldurma olup olmadığını gösterir. Oracle, "Geçersiz doldurma" ifadesini içeren bir değer döndüren olarak basit bir şey ya da geçersiz bir engel aksine geçerli bloğu işlemek için bir yaşamları farklı zaman ayırdığınız gibi daha karmaşık bir şey olabilir.

Blok tabanlı şifrelemeleri ilişki verileri ikinci bloğundaki ilk blokla veri belirleyen modu adlı başka bir özelliğe sahip ve benzeri. En sık kullanılan modları CBC biridir. CBC başlatma vektörü (IV olarak), bilinen bir ilk rastgele bloğunu ortaya çıkarır ve önceki blok aynı anahtarla aynı ileti şifreleme her zaman aynı şifrelenmiş çıktı oluşturmasa şekilde sağlamak için statik şifreleme sonucu ile birleştirir.

Oracle sunan koda biraz değiştirilmiş bir ileti gönderin ve bunları oracle söyler kadar veri göndermeye devam verilerinin doğru olduğundan, bir saldırganın doldurma oracle, CBC verileri nasıl yapılandırıldığını birlikte kullanabilirsiniz. Bu yanıtından, saldırgan iletinin bayt şifresini çözebilir.

Modern bir bilgisayar gibi yüksek kaliteli bir saldırganın çok küçük (0,1 MS'den kısa) yürütme farklılıkları uzak sistemlere zaman algılayabilir ağlardır. Başarılı bir şifre çözme veri üzerinde oynama değildi, yalnızca oluşabilir varsayılarak uygulamaları araçlarından başarılı ve başarısız şifre çözme farklılıkları gözlemlemek için tasarlanmış saldırılara karşı savunmasız olabilir. Bu zamanlama fark diğerlerinden bazı diller ya da kitaplıkları daha önemli olabilir, ancak bunu şimdi uygulamanın yanıt hata olarak dikkate alındığında bu tüm dillerde ve kitaplıklarda için pratik bir tehdit olarak yorumlanmamalıdır.

Bu saldırı şifrelenmiş verileri değiştirin ve test sonucu oracle ile olanağı kullanır. Tam olarak saldırının etkilerini hafifletmek için tek yolu, şifrelenmiş verilere değişiklikleri algılar ve herhangi bir eylem gerçekleştirmek Reddet sağlamaktır. Bunu yapmak için standart verileri için imza oluşturma ve tüm işlemler gerçekleştirilir önce bu imzayı doğrulamak için yoludur. İmza doğrulanabilir, saldırgan tarafından oluşturulamıyor, aksi takdirde bunlar şifrelenmiş veriler değiştirin, sonra değiştirilen verileri temel alan yeni bir imza işlem. Bir ortak tür uygun imzaya anahtarlı karma ileti kimlik doğrulama kodu (HMAC) bilinir. Gizli bir anahtar yalnızca HMAC oluşturan kişi ve doğrulamadan kişi bilinen alır, bir HMAC bir sağlama toplamı farklıdır. Elinde anahtarının doğru HMAC üretemiyor. Verilerinizi almak, şifrelenmiş verilerin, gizli bir anahtar kullanarak HMAC ve gönderen paylaşımı, daha sonra karşı bir gönderildiği HMAC hesaplanan karşılaştırma bağımsız olarak işlem. Bu karşılaştırma sabit zaman olmalıdır, farklı türde bir saldırı sağlayan başka bir algılanabilir oracle, aksi takdirde ekledik.

Özet olarak, sıfır güvenli bir şekilde CBC blok şifreleme özelliklerinden kullanmak için bunları bir HMAC (veya başka bir veri bütünlük denetimi ile) kullanarak verilerin şifresini çözmek için bir sabit zaman karşılaştırma denemeden önce doğrulayan birleştirebilirsiniz. Tüm değiştirilmiş bir yanıt oluşturması için aynı süre iletilerin olduğundan, saldırı engellenir.

## <a name="who-is-vulnerable"></a>Güvenlik Açığı kimdir

Bu güvenlik açığını kendi şifreleme ve şifre çözme işlemi hem yönetilen hem de yerel uygulamalar için geçerlidir. Bu, örneğin içerir:

- Sunucuda sonraki şifre çözme için bir tanımlama bilgisi şifreler uygulama.
- Sütunları kullanıcıların bir tabloya veri ekleme yeteneği sağlayan bir veritabanı uygulaması daha sonra şifresi.
- Şifreleme Aktarımdaki verileri korumak için paylaşılan bir anahtar kullanarak dayalı bir veri aktarımı uygulama.
- Bir uygulama, uygulama şifreleyen ve iletilerin "içinde" TLS tünelinin şifresini çözer.

Tek başına TLS kullanarak, bu senaryolarda koruma sağlamaz olduğunu unutmayın.

Bir güvenlik açığına sahip uygulama:

- PKCS #7 ya da ANSI X.923 gibi doğrulanabilir doldurma moduyla CBC şifreleme modu kullanarak verilerin şifresini çözer.
- Şifre çözme veri bütünleştirme denetimi (MAC ya da asimetrik bir dijital imza) aracılığıyla gerçekleştirilen olmadan gerçekleştirir.

Bu soyutlama üzerinde şu temel elemanlar şifreli ileti söz dizimi (PKCS #7/CMS) EnvelopedData yapısı gibi üst üzerinden oluşturulan uygulamalar için de geçerlidir.

## <a name="related-areas-of-concern"></a>İlgili sorunlu alanları

Araştırma ISO 10126 ileti iyi bilinen veya öngörülebilir alt yapısına sahip olduğunda doldurma eşdeğeri ile doldurulan CBC iletileri hakkında daha fazla endişe Microsoft'a açmıştır. Örneğin, öneri (xmlenc EncryptedXml) işleme ve W3C XML şifreleme sözdizimi kurallarına altında hazırlanmış içeriği. İletiyi imzalamak sonra şifrelemek için W3C kılavuzunu zaman uygun kabul ederken Microsoft artık her zaman şifreleyin-then-oturum yapılması önerir.

Asimetrik anahtar ile rastgele bir ileti arasındaki devralınan güven ilişkisi olduğundan uygulama geliştiricilerinin her zaman bir asimetrik imza anahtarı uygulanabilirliğini doğrulama dikkatli olmalıdır.

## <a name="details"></a>Ayrıntılar

Tarihsel olarak, hem şifreleme hem de HMAC veya RSA imzaları gibi bir araç kullanarak önemli verileri doğrulamak önemli olan bir fikir birliğine varılmış olmuştur. Ancak, how to sequence şifreleme ve kimlik doğrulama işlemleri için daha az kılavuzluk olmuştur. Bu makalede ayrıntılı güvenlik açığı nedeniyle, Microsoft'un Kılavuzu artık her zaman "şifrelemek-then-sign" paradigma kullanmaktır. Diğer bir deyişle, ilk simetrik anahtar kullanarak verileri şifreleme ve ardından MAC ya da asimetrik imza ciphertext (şifrelenmiş veri) üzerinde işlem. Verilerin şifresini çözme, ters gerçekleştirin. İlk olarak, MAC veya imza şifreler onayladıktan sonra şifreyi.

"Oracle saldırıları doldurma" 10 yılı aşkın süredir mevcut bilinmektedir olarak bilinen güvenlik açıklarının sınıf. Bu güvenlik açıklarına veri bloğu başına en fazla 4096 deneme kullanarak AES ve 3DES ' gibi blok simetrik algoritmaları ile şifrelenen verilerin şifresini çözmek bir saldırganın. Bu güvenlik açıklarına olun şifrelemeleri block olgu kullanımını sonunda doğrulanabilir doldurma verilerle en sık kullanılır. Bir saldırganın ile ciphertext değiştirmesine ve olup kurcalama hata en sonda doldurma biçimde neden olduğunu bulmak, saldırgan verilerin şifresini çözebilen bulunamadı.

Başlangıçta, pratik saldırıları doldurma gibi ASP.NET güvenlik açığı geçerli olup üzerinde farklı hata kodları döndürecekti Hizmetleri bağlı [MS10-070](https://technet.microsoft.com/library/security/ms10-070.aspx). Ancak, Microsoft artık yalnızca zamanlama geçerli ve geçersiz doldurma işlem arasındaki farklılıkları kullanarak benzer saldırıları yürütmek pratik olduğunu düşündüğü.

İmza şifreleme şeması kullanır ve imza doğrulaması (içeriği) bağımsız olarak veri belirli bir süre için sabit bir çalışma zamanı ile gerçekleştirilen şartıyla, veri bütünlüğünü herhangi bir bilgi yayma olmadan doğrulanabilir bir Saldırgan aracılığıyla bir [yan kanal](https://en.wikipedia.org/wiki/Side-channel_attack). Bütünlük denetimi değiştirilen tüm iletileri reddeder beri doldurma oracle tehdit azalır.

## <a name="guidance"></a>Kılavuz

İlk ve, Microsoft gizlilik sahip herhangi bir veri üzerinden Aktarım Katmanı Güvenliği (TLS), Güvenli Yuva Katmanı (SSL) için ardıl iletilmesi önerir.

Ardından, uygulamanızı çözümleyin:

- Tam olarak hangi şifreleme gerçekleştirmekte anlayın ve hangi şifreleme platformlar ve API'ler kullanmakta olduğunuz tarafından sağlanmaktadır.
- Belirli bir simetrik, her katmanda her kullanım olun [blok şifreleme algoritması](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers)gibi gizli Anahtarlanan veri bütünleştirme denetimi kullanımını AES ve CBC modunda 3DES birleştirmek (asimetrik bir imza, bir HMAC veya şifreleme modunu değiştirmek için bir [kimliği doğrulanmış şifreleme](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE) modunu GCM veya CCM gibi).

Güncel bir araştırmaya göre bunu genellikle kimlik doğrulama ve şifreleme adımları birbirinden bağımsız olarak şifreleme AE olmayan modları için gerçekleştirildiğinde, şifreli kimlik doğrulaması (şifreleme-then-oturum) genel en iyi seçenek olduğunu azalttığı kabul edilir. Ancak, şifreleme BT'ye bir doğru yanıt yok ve bu Genelleştirme profesyonel cryptographer kadar iyi yönlendirilmiş önerileri desteklenmez.

Kendi ileti biçimi değiştirebilirsiniz ancak kimlik doğrulamasız CBC şifre çözme gerçekleştirmek mümkün olan uygulamaların risk azaltma işlemleri gibi birleştirmek için önerilir:

- Doğrulayın veya doldurmayı kaldırmak şifre çözücü vermeden şifre çözme:
  - Uygulanmış olan tüm doldurma hala göz ardı veya kaldırılmasına izin gerekir, uygulamanıza yük taşıma.
  - Diğer uygulama veri doğrulama mantığı eklemenize doldurma doğrulama ve temizleme birleştirilebilir avantajdır. Verileri doğrulama ve doldurma doğrulama Sabit sürede yapılabilir, tehdit azaltılır.
  - Algılanan ileti uzunluğu doldurmayı yorumunu değişiklikleri olduğundan, yine de bu yaklaşımı yayılan zamanlama bilgi olabilir.
- Şifre çözme doldurma modu için ISO10126 değiştirin:
  - ISO10126 şifre çözme doldurma PKCS7 şifreleme doldurma ve ANSIX923 şifreleme doldurma ile uyumludur.
  - Modunu değiştirme doldurma oracle bilgi tüm bloğu yerine 1 bayt azaltır. Ancak, içerik XML öğesi, bir kapatma gibi iyi bilinen bir alt bilgi varsa ilgili saldırıları ileti geri kalanını saldırılara karşı devam edebilirsiniz.
  - Ayrıca, burada saldırganın birden çok kez farklı ileti uzaklığı ile şifrelenmiş aynı düz metin zorlayacak durumlarda düz metin kurtarma da engellemez.
- Şifre çözme çağrısı zamanlama sinyal Donuklaştır değerlendirmesi kapısı:
  - Durma süresini hesaplama şifre çözme işlemi doldurma içeren veri segmenti için gereken en uzun süreyi aşan en az olmalıdır.
  - Saat hesaplamaları kılavuzunda göre yapılmalıdır [yüksek çözünürlüklü zaman damgaları alınırken](https://msdn.microsoft.com/library/windows/desktop/dn55340.aspx), kullanarak değil <xref:System.Environment.TickCount?displayProperty=nameWithType> (tabi Top-üzerinden/taşma) veya iki sistem zaman damgaları (tabi NTP ayarlama çıkararak hatalar).
  - Saat hesaplamaları tüm potansiyel özel durumlar dahil olmak üzere şifre çözme işlemi tamamlanmıyorsa yönetilmelidir veya C++ uygulamaları, yalnızca sona sıfır.
  - Başarı veya başarısızlık henüz belirlendiyse, zamanlama kapısı süresi dolduğunda, hata döndürmesi gerekir.
- Kimliği doğrulanmamış şifre çözme işlemi Hizmetleri "geçersiz" iletileri hakkında güncelleştirmekte gelen olduğunu algılamak için bir izleme olması gerekir.
  - Bu sinyal hatalı pozitif sonuçları (duyup duymayacağını bozuk veri) hem de false negatif (saldırı algılama atlatabilir yeterince uzun bir zaman aşımına yayılmasını) taşıyan aklınızda size aittir.

## <a name="finding-vulnerable-code---native-applications"></a>Güvenlik Açığı kodu - yerel uygulamaları bulma

Windows şifreleme karşı yerleşik programları için: yeni nesil (CNG) kitaplığı:

- Şifre çözme çağrıdır [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt), belirten `BCRYPT_BLOCK_PADDING` bayrağı.
- Anahtar tanıtıcısı çağırarak başlatılmış [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) ile [BCRYPT_CHAINING_MODE](https://msdn.microsoft.com/library/windows/desktop/aa376211.aspx#BCRYPT_CHAINING_MODE) kümesine `BCRYPT_CHAIN_MODE_CBC`.
  - Bu yana `BCRYPT_CHAIN_MODE_CBC` etkilenen varsayılan kod değil atamış herhangi bir değer `BCRYPT_CHAINING_MODE`.

Eski Windows şifreleme API üzerinde derlenmiş programlar için:

- Şifre çözme çağrıdır [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) ile `Final=TRUE`.
- Anahtar tanıtıcısı çağırarak başlatılmış [CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) ile [KP_MODE](https://msdn.microsoft.com/library/windows/desktop/aa379949.aspx#KP_MODE) kümesine `CRYPT_MODE_CBC`.
  - Bu yana `CRYPT_MODE_CBC` etkilenen varsayılan kod değil atamış herhangi bir değer `KP_MODE`.

## <a name="finding-vulnerable-code---managed-applications"></a>Güvenlik Açığı kodu bulma - yönetilen uygulamalar

- Şifre çözme çağrıdır <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> veya <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> yöntemlerde <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.
  - .NET içinde aşağıdaki türetilmiş türlerini içerir, ancak ayrıca üçüncü taraf türleri şunlardır:
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
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> Özelliğinin ayarlandığı <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, veya <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.
  - Bu yana <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> etkilenen varsayılan kod hiçbir zaman atamış <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> özelliği.
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> Özelliği ayarlanmıştır <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>
  - Bu yana <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> etkilenen varsayılan kod hiçbir zaman atamış <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> özelliği.

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a>Şifreli ileti söz dizimi - savunmasız kod bulma

Kimliği doğrulanmamış bir CMS EnvelopedData ileti şifreli içerikleri CBC modunda AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES kullanır (1.2.840.113549.3.7) veya RC2 (1.2.840.113549.3.2) olan açıktan de olarak diğer bir blok şifreleme algoritmaları kullanarak CBC modunda iletileri.

Akış şifrelemeleri belirli bu güvenlik açığını maruz değildir, ancak her zaman veri ContentEncryptionAlgorithm değeri inceleyerek üzerinden kimlik doğrulaması yapan Microsoft önerir.

Yönetilen uygulamalar için blob olabilir bir CMS EnvelopedData geçirilir olarak herhangi bir değer algılandı. <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.

Yerel uygulamalar için bir CMS EnvelopedData blob bir CMS tanıtıcı sağlanan herhangi bir değer olarak algılanabilir [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) olan kaynaklanan [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) olduğu `CMSG_ENVELOPED` ve/veya CMS tanıtıcısı Daha sonra gönderilen bir `CMSG_CTRL_DECRYPT` yönerge aracılığıyla [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol).

## <a name="vulnerable-code-example---managed"></a>Güvenlik açığı kod örneği - yönetilen

Bu yöntem bir tanımlama bilgisi okur ve bunun şifresini çözer ve hiçbir veri bütünlüğü denetimi tarafından görülebilir. Bu nedenle, bu yöntem tarafından okunan bir tanımlama bilgisinin içeriğinin aldığı kullanıcı tarafından veya şifrelenmiş bir tanımlama bilgisi değeri elde herhangi bir saldırgan tarafından saldırıya.

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

## <a name="example-code-following-recommended-practices---managed"></a>Önerilen uygulamalar - yönetilen örnek kodu aşağıdaki

Aşağıdaki örnek kod bir standart ileti biçimini kullanır.

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

Burada `cipher_algorithm_id` ve `hmac_algorithm_id` algoritması tanımlayıcılardır yerel uygulama (standart) bu algoritmaları temsillerini. Bu tanımlayıcılar, var olan bir Mesajlaşma Protokolü yerine diğer bölümlerinde çıplak bir birleştirilmiş bytestream mantıklı olabilir.

Bu örnek, tek bir ana anahtarı hem bir şifreleme anahtarı hem de bir HMAC anahtarı türetmek için de kullanır. Bu kolaylık her ikisi de tek Anahtarlanan çift Anahtarlanan bir uygulamaya ve iki anahtar olarak farklı değerler tutma teşvik etmek için bir uygulamayı kapatmak için sağlanır. Daha fazla eşitleme dışı şifreleme anahtarını ve HMAC anahtarı alınamıyor garanti eder.

Bu örnek kabul etmeyen bir <xref:System.IO.Stream> şifreleme veya şifre çözme. Geçerli veri biçimi yaptığı bir geçişli zor şifrelemek için `hmac_tag` değeri önündeki şifreler. Ancak, ayrıştırıcının daha basit tutmaya başında tuttuğundan, tüm sabit boyutlu öğeleri bu biçim seçildi. Bir uygulayan GetHashAndReset arayın ve sonuç TransformFinalBlock çağırmadan önce doğrulamak için dikkatli olmalıdır ancak bu veri biçimiyle bir geçişli şifresini çözme mümkündür. Akış şifreleme önemliyse, farklı bir AE modu gerekli olabilir.

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
