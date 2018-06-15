---
title: Zamanlama açıklarıyla doldurmayı kullanarak CBC modunda simetrik şifre çözme
description: Algılanmasına ve zamanlama güvenlik açıkları dolgusu kullanılarak Şifre blok zincirleme (CBC) modunu simetrik şifre çözme ile öğrenin.
ms.date: 06/12/2018
author: blowdart
ms.author: mairaw
ms.openlocfilehash: a07acbb943c430f6e26bec44f55a5c84306da513
ms.sourcegitcommit: 73a662360bbe2f43c19aca1fbcc2565025c60cd8
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2018
ms.locfileid: "35327271"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a><span data-ttu-id="31081-103">Zamanlama açıklarıyla doldurmayı kullanarak CBC modunda simetrik şifre çözme</span><span class="sxs-lookup"><span data-stu-id="31081-103">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>

<span data-ttu-id="31081-104">Microsoft, şu anda bilinen şifreleme araştırmaya göre çok özel durumlar dışında artık doğrulanabilen doldurma kaldığında simetrik şifreleme şifre blok zincirleme (CBC) modunu ile şifrelenmiş verilerin şifresini çözmek güvenli, olduğunu düşündüğünü ilk ciphertext bütünlüğünü sağlamaya olmadan uygulanır.</span><span class="sxs-lookup"><span data-stu-id="31081-104">Microsoft, based on currently known cryptographic research, believes that, except for very specific circumstances, it's no longer safe to decrypt data encrypted with the Cipher-Block-Chaining (CBC) mode of symmetric encryption when verifiable padding has been applied without first ensuring the integrity of the ciphertext.</span></span>

## <a name="introduction"></a><span data-ttu-id="31081-105">Giriş</span><span class="sxs-lookup"><span data-stu-id="31081-105">Introduction</span></span>

<span data-ttu-id="31081-106">Doldurma oracle saldırı, saldırganın anahtarı bilmeden veri içeriğinin şifresini çözmek şifrelenmiş veri saldırısı türüdür.</span><span class="sxs-lookup"><span data-stu-id="31081-106">A padding oracle attack is a type of attack against encrypted data that allows the attacker to decrypt the contents of the data, without knowing the key.</span></span>

<span data-ttu-id="31081-107">Bir oracle bir "bilgi" yürütme eylemi doğru olup olmamasına hakkında bir saldırganın bilgi veren ifade eder.</span><span class="sxs-lookup"><span data-stu-id="31081-107">An oracle refers to a "tell" which gives an attacker information about whether the action they're executing is correct or not.</span></span> <span data-ttu-id="31081-108">Bir kart çalma düşünün veya bir çocuk oyun kartı.</span><span class="sxs-lookup"><span data-stu-id="31081-108">Imagine playing a board or card game with a child.</span></span> <span data-ttu-id="31081-109">Ne zaman kendi yüz yanar ile büyük bir gülümseme gönderme aynen aynen taşıdığını düşündüğü çünkü bir oracle olan iyi bir ettirmek üzere.</span><span class="sxs-lookup"><span data-stu-id="31081-109">When her face lights up with a big smile because she thinks she's about to make a good move, that's an oracle.</span></span> <span data-ttu-id="31081-110">Bir sonraki uygun şekilde planlamak için bu oracle rakip kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31081-110">You, as the opponent, can use this oracle to plan your next move appropriately.</span></span>

<span data-ttu-id="31081-111">Doldurma belirli bir şifreleme terimdir.</span><span class="sxs-lookup"><span data-stu-id="31081-111">Padding is a specific cryptographic term.</span></span> <span data-ttu-id="31081-112">Verilerinizi şifrelemek için kullanılan algoritmalar olan bazı şifrelemeleri blokların sabit bir boyuta olduğu veri blokları üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="31081-112">Some ciphers, which are the algorithms used to encrypt your data, work on blocks of data where each block is a fixed size.</span></span> <span data-ttu-id="31081-113">Şifrelemek istediğiniz veri blokları doldurmak için doğru boyutta değilse, bunu yapar kadar verilerinizi sıfır eklenir.</span><span class="sxs-lookup"><span data-stu-id="31081-113">If the data you want to encrypt isn't the right size to fill the blocks, your data is padded until it does.</span></span> <span data-ttu-id="31081-114">Doldurma birçok forms özgün giriş uygun boyutta olsa bile her zaman, bulunması için dolgu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="31081-114">Many forms of padding require that padding to always be present, even if the original input was of the right size.</span></span> <span data-ttu-id="31081-115">Bu her zaman güvenli bir şekilde şifre çözme sırasında kaldırılacak doldurma sağlar.</span><span class="sxs-lookup"><span data-stu-id="31081-115">This allows the padding to always be safely removed upon decryption.</span></span>

<span data-ttu-id="31081-116">İki şey bir araya getirilmesi, doldurma oracle yazılım uygulamasıyla şifresi çözülmüş veriler geçerli doldurma sahip olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="31081-116">Putting the two things together, a software implementation with a padding oracle reveals whether decrypted data has valid padding.</span></span> <span data-ttu-id="31081-117">Oracle "Geçersiz doldurma" belirten bir değer döndürme olarak basit bir şey ya da geçersiz bir blok aksine geçerli bir blok işlemek için sorunlarında farklı bir zaman ayırdığınız gibi daha karmaşık bir şey olabilir.</span><span class="sxs-lookup"><span data-stu-id="31081-117">The oracle could be something as simple as returning a value that says "Invalid padding" or something more complicated like taking a measurably different time to process a valid block as opposed to an invalid block.</span></span>

<span data-ttu-id="31081-118">Şifre blok tabanlı veri ikinci blok verilerde ilk bloğundaki ilişki belirler, modu adlı başka bir özellik varsa ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="31081-118">Block-based ciphers have another property, called the mode, which determines the relationship of data in the first block to the data in the second block, and so on.</span></span> <span data-ttu-id="31081-119">En yaygın kullanılan modlar CBC biridir.</span><span class="sxs-lookup"><span data-stu-id="31081-119">One of the most commonly used modes is CBC.</span></span> <span data-ttu-id="31081-120">CBC başlatma vektörü (IV olarak), bilinen bir ilk rasgele blok tanıtır ve önceki blok aynı anahtar ile aynı iletiyi şifreleme her zaman aynı şifrelenmiş çıktı oluşturmuyor emin olmak için statik şifreleme sonucu ile birleştirir.</span><span class="sxs-lookup"><span data-stu-id="31081-120">CBC introduces an initial random block, known as the Initialization Vector (IV), and combines the previous block with the result of static encryption to make it such that encrypting the same message with the same key doesn't always produce the same encrypted output.</span></span>

<span data-ttu-id="31081-121">Oracle gösteren kodu için biraz değiştirilmiş iletilerini göndermek ve bunları oracle söyler kadar veri göndermeye devam verilerinin doğru olduğundan, bir saldırganın CBC verileri nasıl yapılandırıldığını ile birlikte bir doldurma oracle kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31081-121">An attacker can use a padding oracle, in combination with how CBC data is structured, to send slightly changed messages to the code that exposes the oracle, and keep sending data until the oracle tells them the data is correct.</span></span> <span data-ttu-id="31081-122">Bu yanıt, saldırganın bayt ileti şifresini çözebilir.</span><span class="sxs-lookup"><span data-stu-id="31081-122">From this response, the attacker can decrypt the message byte by byte.</span></span>

<span data-ttu-id="31081-123">Modern bilgisayar gibi kaliteli bir saldırganın çok küçük (değerinden 0,1 ms) yürütme farklılıkları uzak sistemlerde zaman algılayabilir ağlardır.</span><span class="sxs-lookup"><span data-stu-id="31081-123">Modern computer networks are of such high quality that an attacker can detect very small (less than 0.1 ms) differences in execution time on remote systems.</span></span> <span data-ttu-id="31081-124">Veri değiştirilmiş değildi ederken başarılı bir şifre çözme yalnızca ortaya çıkar varsayılarak uygulamaları başarılı ve başarısız şifre çözme farklılıkları izlemek için tasarlanmış Araçları'ndan saldırıya açık olabilir.</span><span class="sxs-lookup"><span data-stu-id="31081-124">Applications that are assuming that a successful decryption can only happen when the data wasn't tampered with may be vulnerable to attack from tools that are designed to observe differences in successful and unsuccessful decryption.</span></span> <span data-ttu-id="31081-125">Bu zamanlama fark diğerlerinden bazı dil ya da kitaplıkları daha önemli olsa da, bunu şimdi uygulamanın yanıt başarısızlık dikkate alındığında bu tüm diller ve kitaplıkları için kullanışlı bir tehdit olduğu düşünülen.</span><span class="sxs-lookup"><span data-stu-id="31081-125">While this timing difference may be more significant in some languages or libraries than others, it's now believed that this is a practical threat for all languages and libraries when the application's response to failure is taken into account.</span></span>

<span data-ttu-id="31081-126">Bu saldırı şifrelenen verileri değiştirmek ve test sonucu oracle ile özelliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="31081-126">This attack relies on the ability to change the encrypted data and test the result with the oracle.</span></span> <span data-ttu-id="31081-127">Tam olarak saldırının etkisini azaltmak için yalnızca şifrelenmiş veriler üzerindeki değişiklikleri algılar ve herhangi bir eylem gerçekleştirmek Reddet yoludur.</span><span class="sxs-lookup"><span data-stu-id="31081-127">The only way to fully mitigate the attack is to detect changes to the encrypted data and refuse to perform any actions on it.</span></span> <span data-ttu-id="31081-128">Bunu yapmak için standart verileri için imza oluşturma ve tüm işlemler gerçekleştirilir önce o imzayı doğrulamak için yoludur.</span><span class="sxs-lookup"><span data-stu-id="31081-128">The standard way to do this is to create a signature for the data and validate that signature before any operations are performed.</span></span> <span data-ttu-id="31081-129">İmza doğrulanabilen, saldırgan tarafından oluşturulamaz, aksi halde bunlar şifrelenmiş veriler değiştirin, sonra değiştirilen verileri temel alan yeni bir imza işlem.</span><span class="sxs-lookup"><span data-stu-id="31081-129">The signature must be verifiable, it cannot be created by the attacker, otherwise they'd change the encrypted data, then compute a new signature based on the changed data.</span></span> <span data-ttu-id="31081-130">Bir ortak türü uygun imzalı bir anahtarlı karma ileti kimlik doğrulama kodu (HMAC) bilinir.</span><span class="sxs-lookup"><span data-stu-id="31081-130">One common type of appropriate signature is known as a keyed-hash message authentication code (HMAC).</span></span> <span data-ttu-id="31081-131">Bir HMAC gizli bir anahtar yalnızca HMAC oluşturan kişiye ve bunu doğrulama kişiye bilinen sürdüğünü sağlama toplamı farklıdır.</span><span class="sxs-lookup"><span data-stu-id="31081-131">An HMAC differs from a checksum in that it takes a secret key, known only to the person producing the HMAC and to the person validating it.</span></span> <span data-ttu-id="31081-132">Anahtara sahip olan, doğru HMAC üretemiyor.</span><span class="sxs-lookup"><span data-stu-id="31081-132">Without possession of the key, you can't produce a correct HMAC.</span></span> <span data-ttu-id="31081-133">Verilerinizi aldığınızda, şifrelenmiş veri almak, gizli anahtarı kullanarak HMAC ve gönderen paylaşımı sonra bunlar karşı bir gönderdiğiniz HMAC hesaplanan karşılaştırma bağımsız olarak işlem.</span><span class="sxs-lookup"><span data-stu-id="31081-133">When you receive your data, you'd take the encrypted data, independently compute the HMAC using the secret key you and the sender share, then compare the HMAC they sent against the one you computed.</span></span> <span data-ttu-id="31081-134">Bu karşılaştırma sabit zaman olmalıdır, farklı türde bir saldırı sağlayan başka bir algılanabilir oracle, aksi takdirde ekledik.</span><span class="sxs-lookup"><span data-stu-id="31081-134">This comparison must be constant time, otherwise you've added another detectable oracle, allowing a different type of attack.</span></span>

<span data-ttu-id="31081-135">Özet olarak, doldurulan güvenle CBC blok şifrelemeler kullanmak için bunları bir HMAC (veya başka bir veri bütünlüğü denetimi ile) kullanarak verileri şifrelemek için bir sabit zaman karşılaştırma denemeden önce doğrulayan birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31081-135">In summary, to use padded CBC block ciphers safely, you must combine them with an HMAC (or another data integrity check) that you validate using a constant time comparison before trying to decrypt the data.</span></span> <span data-ttu-id="31081-136">Tüm değiştirilmiş iletileri bir yanıtı oluşturan aynı tutar zaman beri saldırı engellenir.</span><span class="sxs-lookup"><span data-stu-id="31081-136">Since all altered messages take the same amount time to produce a response, the attack is prevented.</span></span>

## <a name="who-is-vulnerable"></a><span data-ttu-id="31081-137">Güvenlik Açığı kim</span><span class="sxs-lookup"><span data-stu-id="31081-137">Who is vulnerable</span></span>

<span data-ttu-id="31081-138">Bu güvenlik açığından kendi şifreleme ve şifre çözme gerçekleştirme yönetilen ve yerel uygulamalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="31081-138">This vulnerability applies to both managed and native applications that are performing their own encryption and decryption.</span></span> <span data-ttu-id="31081-139">Bu, örneğin içerir:</span><span class="sxs-lookup"><span data-stu-id="31081-139">This includes, for example:</span></span>

- <span data-ttu-id="31081-140">Tanımlama bilgisi sunucuda sonraki şifre çözme için şifreler bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="31081-140">An application that encrypts a cookie for later decryption on the server.</span></span>
- <span data-ttu-id="31081-141">Kullanıcılara bir tabloya veri eklemek sütunları sağlayan bir veritabanı uygulaması daha sonra şifresi.</span><span class="sxs-lookup"><span data-stu-id="31081-141">A database application that provides the ability for users to insert data into a table whose columns are later decrypted.</span></span>
- <span data-ttu-id="31081-142">Aktarımdaki verileri korumak için paylaşılan bir anahtar kullanarak şifreleme dayanan bir veri aktarımı uygulaması.</span><span class="sxs-lookup"><span data-stu-id="31081-142">A data transfer application that relies on encryption using a shared key to protect the data in transit.</span></span>
- <span data-ttu-id="31081-143">Şifreler ve şifresini çözer "içindeki" TLS tüneli iletileri bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="31081-143">An application that encrypts and decrypts messages "inside" the TLS tunnel.</span></span>

<span data-ttu-id="31081-144">Tek başına TLS kullanarak, bu senaryolarda koruma sağlamaz olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="31081-144">Note that using TLS alone may not protect you in these scenarios.</span></span>

<span data-ttu-id="31081-145">Bir güvenlik açığı uygulama:</span><span class="sxs-lookup"><span data-stu-id="31081-145">A vulnerable application:</span></span>

- <span data-ttu-id="31081-146">PKCS #7 veya ANSI X.923 gibi bir doğrulanabilen doldurma modu CBC şifreleme modu kullanarak verilerin şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="31081-146">Decrypts data using the CBC cipher mode with a verifiable padding mode, such as PKCS#7 or ANSI X.923.</span></span>
- <span data-ttu-id="31081-147">Şifre çözme veri bütünleştirme denetimi (MAC veya asimetrik bir dijital imza) üzerinden gerçekleştirilen olmadan gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="31081-147">Performs the decryption without having performed a data integrity check (via a MAC or an asymmetric digital signature).</span></span>

<span data-ttu-id="31081-148">Bu üst şifreleme iletisi söz dizimi (PKCS #7/CMS) EnvelopedData yapısı gibi bu elemanlar üzerinden soyutlamalar en üstünde oluşturulan uygulamalar için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="31081-148">This also applies to applications built on top of abstractions over top of these primitives, such as the Cryptographic Message Syntax (PKCS#7/CMS) EnvelopedData structure.</span></span>

## <a name="related-areas-of-concern"></a><span data-ttu-id="31081-149">Sorun ilgili alanlarını</span><span class="sxs-lookup"><span data-stu-id="31081-149">Related areas of concern</span></span>

<span data-ttu-id="31081-150">Araştırma ISO 10126-ileti iyi bilinen veya tahmin edilebilir altbilgi yapısı olduğunda doldurma eşdeğerleriyle doldurulan CBC iletileri hakkında daha fazla endişe Microsoft'a açmıştır.</span><span class="sxs-lookup"><span data-stu-id="31081-150">Research has led Microsoft to be further concerned about CBC messages that are padded with ISO 10126-equivalent padding when the message has a well-known or predictable footer structure.</span></span> <span data-ttu-id="31081-151">Örneğin, işleme öneri (xmlenc, EncryptedXml) ve W3C XML şifreleme sözdizimi kurallarına altında hazırlanan içeriği.</span><span class="sxs-lookup"><span data-stu-id="31081-151">For example, content prepared under the rules of the W3C XML Encryption Syntax and Processing Recommendation (xmlenc, EncryptedXml).</span></span> <span data-ttu-id="31081-152">İletiyi şifrelemek için W3C Kılavuzu zaman uygun olarak kabul edildiği sırada Microsoft şimdi her zaman şifrelemek-ardından-oturum yapılması önerir.</span><span class="sxs-lookup"><span data-stu-id="31081-152">While the W3C guidance to sign the message then encrypt was considered appropriate at the time, Microsoft now recommends always doing encrypt-then-sign.</span></span>

<span data-ttu-id="31081-153">Asimetrik anahtar ve rasgele bir ileti arasında bir devralınan güven ilişkisi olduğundan uygulama geliştiricileri her zaman bir asimetrik imza anahtarı uygulanabilirliğini doğrulanıyor dikkatli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="31081-153">Application developers should always be mindful of verifying the applicability of an asymmetric signature key, as there's no inherent trust relationship between an asymmetric key and an arbitrary message.</span></span>

## <a name="details"></a><span data-ttu-id="31081-154">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="31081-154">Details</span></span>

<span data-ttu-id="31081-155">Geçmişte, şifrelemek ve HMAC veya RSA İmza gibi yollarla kullanarak önemli verileri kimlik doğrulaması önemlidir anlaşma açıldı.</span><span class="sxs-lookup"><span data-stu-id="31081-155">Historically, there has been consensus that it's important to both encrypt and authenticate important data, using means such as HMAC or RSA signatures.</span></span> <span data-ttu-id="31081-156">Ancak, şifreleme ve kimlik doğrulama işlemleri sıralamak nasıl aldığını daha az Temizle Kılavuzu açıldı.</span><span class="sxs-lookup"><span data-stu-id="31081-156">However, there has been less clear guidance as to how to sequence the encryption and authentication operations.</span></span> <span data-ttu-id="31081-157">Bu makalede ayrıntılı güvenlik açığı nedeniyle, Microsoft'un Kılavuzu şimdi her zaman "şifrelemek-ardından-oturum" kip kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="31081-157">Due to the vulnerability detailed in this article, Microsoft's guidance is now to always use the "encrypt-then-sign" paradigm.</span></span> <span data-ttu-id="31081-158">Diğer bir deyişle, ilk simetrik anahtar kullanarak verileri şifrelemek ve sonra MAC ya da asimetrik imza (şifrelenmiş veriler) ciphertext işlem.</span><span class="sxs-lookup"><span data-stu-id="31081-158">That is, first encrypt data using a symmetric key, then compute a MAC or asymmetric signature over the ciphertext (encrypted data).</span></span> <span data-ttu-id="31081-159">Verilerin şifresini çözmek, ters gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="31081-159">When decrypting data, perform the reverse.</span></span> <span data-ttu-id="31081-160">İlk olarak, MAC veya ciphertext imzası onaylayın, sonra şifresini.</span><span class="sxs-lookup"><span data-stu-id="31081-160">First, confirm the MAC or signature of the ciphertext, then decrypt it.</span></span>

<span data-ttu-id="31081-161">Bir sınıf "oracle saldırıları doldurma" 10 yılı aşkın mevcut bilinmektedir olarak bilinen güvenlik açıklarının.</span><span class="sxs-lookup"><span data-stu-id="31081-161">A class of vulnerabilities known as "padding oracle attacks" have been known to exist for over 10 years.</span></span> <span data-ttu-id="31081-162">Bu güvenlik açıkları, bir veri bloğunun başına en fazla 4096 denemeleri kullanarak AES ve 3DES ' gibi blok simetrik algoritmaları tarafından şifrelenmiş verilerin şifresini çözmek bir saldırganın.</span><span class="sxs-lookup"><span data-stu-id="31081-162">These vulnerabilities allow an attacker to decrypt data encrypted by symmetric block algorithms, such as AES and 3DES, using no more than 4096 attempts per block of data.</span></span> <span data-ttu-id="31081-163">Bu güvenlik açıklarından olun şifrelemeleri engelleme olgu kullanımını sonunda doğrulanabilen doldurma verilerle en sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="31081-163">These vulnerabilities make use of the fact that block ciphers are most frequently used with verifiable padding data at the end.</span></span> <span data-ttu-id="31081-164">Bir saldırgan, ciphertext ile değiştirmesine ve olup kurcalama hata sonunda dolgunun biçiminde neden olduğunu bulmak, saldırganın verilerin şifresini çözebilen bulundu.</span><span class="sxs-lookup"><span data-stu-id="31081-164">It was found that if an attacker can tamper with ciphertext and find out whether the tampering caused an error in the format of the padding at the end, the attacker can decrypt the data.</span></span>

<span data-ttu-id="31081-165">Başlangıçta, pratik doldurma gibi ASP.NET güvenlik açığı geçerli olup üzerinde farklı hata kodları döndürecektir Hizmetleri tabanlı saldırıları [MS10-070](https://technet.microsoft.com/library/security/ms10-070.aspx).</span><span class="sxs-lookup"><span data-stu-id="31081-165">Initially, practical attacks were based on services that would return different error codes based on whether padding was valid, such as the ASP.NET vulnerability [MS10-070](https://technet.microsoft.com/library/security/ms10-070.aspx).</span></span> <span data-ttu-id="31081-166">Ancak, Microsoft artık yalnızca zamanlama geçersiz ve geçerli doldurma işleme arasındaki farklılıkları kullanan benzer saldırısı yapmanın pratik olduğunu düşünür.</span><span class="sxs-lookup"><span data-stu-id="31081-166">However, Microsoft now believes that it's practical to conduct similar attacks using only the differences in timing between processing valid and invalid padding.</span></span>

<span data-ttu-id="31081-167">İmza şifreleme şeması kullanır ve imza doğrulaması (yedeklemiş içeriği) veri belirli bir süre için sabit bir çalışma zamanı ile gerçekleştirilen koşuluyla, veri bütünlüğünü herhangi bir bilgi yayma olmadan doğrulanabilir bir Saldırgan aracılığıyla bir [yan kanal](https://en.wikipedia.org/wiki/Side-channel_attack).</span><span class="sxs-lookup"><span data-stu-id="31081-167">Provided that the encryption scheme employs a signature and that the signature verification is performed with a fixed runtime for a given length of data (irrespective of the contents), the data integrity can be verified without emitting any information to an attacker via a [side channel](https://en.wikipedia.org/wiki/Side-channel_attack).</span></span> <span data-ttu-id="31081-168">Değiştirilen herhangi bir ileti bütünlük denetimi reddeder beri doldurma oracle tehdit azalır.</span><span class="sxs-lookup"><span data-stu-id="31081-168">Since the integrity check rejects any tampered messages, the padding oracle threat is mitigated.</span></span>

## <a name="guidance"></a><span data-ttu-id="31081-169">Kılavuz</span><span class="sxs-lookup"><span data-stu-id="31081-169">Guidance</span></span>

<span data-ttu-id="31081-170">Öncelikle, Microsoft gizliliği sahip herhangi bir veriyi üzerinden Aktarım Katmanı Güvenliği (TLS), Güvenli Yuva Katmanı (SSL) için ardıl iletilmesi önerir.</span><span class="sxs-lookup"><span data-stu-id="31081-170">First and foremost, Microsoft recommends that any data that has confidentiality needs be transmitted over Transport Layer Security (TLS), the successor to Secure Sockets Layer (SSL).</span></span>

<span data-ttu-id="31081-171">Ardından, uygulamanıza çözümleyin:</span><span class="sxs-lookup"><span data-stu-id="31081-171">Next, analyze your application to:</span></span>

- <span data-ttu-id="31081-172">Gerçekleştirmekte olarak tam olarak hangi şifreleme anlayın ve hangi şifreleme platformlar ve API'ler, kullanmakta olduğunuz tarafından sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31081-172">Understand precisely what encryption you're performing and what encryption is being provided by the platforms and APIs you're using.</span></span>
- <span data-ttu-id="31081-173">Belirli bir simetrik, her katmanda her kullanım olun [blok şifreleme algoritması](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), AES ve CBC modunda 3DES gizli anahtarlı veri bütünlüğü denetimi kullanımını birleştirmek gibi (bir HMAC asimetrik bir imza veya şifreleme modu değiştirmek için bir [şifreleme kimlik doğrulaması](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE) mod GCM veya CCM gibi).</span><span class="sxs-lookup"><span data-stu-id="31081-173">Be certain that each usage at each layer of a symmetric [block cipher algorithm](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), such as AES and 3DES, in CBC mode incorporate the use of a secret-keyed data integrity check (an asymmetric signature, an HMAC, or to change the cipher mode to an [authenticated encryption](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE) mode such as GCM or CCM).</span></span>

<span data-ttu-id="31081-174">Geçerli araştırmaya dayanarak, bu genellikle kimlik doğrulama ve şifreleme adımları bağımsız olarak şifreleme AE olmayan modları için gerçekleştirildiğinde, şifreli kimlik doğrulaması (şifrelemek-ardından-oturum) en iyi genel seçenek olduğunu düşünülen.</span><span class="sxs-lookup"><span data-stu-id="31081-174">Based on the current research, it's generally believed that when the authentication and encryption steps are performed independently for non-AE modes of encryption, authenticating the ciphertext (encrypt-then-sign) is the best general option.</span></span> <span data-ttu-id="31081-175">Ancak, şifreleme için BT'ye bir doğru yanıt yok ve bu Genelleştirme profesyonel cryptographer kadar iyi yönlendirilmiş önerileri değil.</span><span class="sxs-lookup"><span data-stu-id="31081-175">However, there's no one-size-fits-all correct answer to cryptography and this generalization isn't as good as directed advice from a professional cryptographer.</span></span>

<span data-ttu-id="31081-176">Kendi ileti biçimi değiştirebilirsiniz ancak kimlik doğrulamasız CBC şifre çözme gerçekleştirmek mümkün olan uygulamalar gibi Azaltıcı Etkenler içerecek şekilde denemek için önerilir:</span><span class="sxs-lookup"><span data-stu-id="31081-176">Applications that are unable to change their messaging format but perform unauthenticated CBC decryption are encouraged to try to incorporate mitigations such as:</span></span>

- <span data-ttu-id="31081-177">Doğrulamak veya doldurma kaldırmak şifre çözücü vermeden şifre çözme:</span><span class="sxs-lookup"><span data-stu-id="31081-177">Decrypt without allowing the decryptor to verify or remove padding:</span></span>
  - <span data-ttu-id="31081-178">Uygulanan doldurma halen göz ardı veya kaldırılması gereken, uygulamanıza yükünü taşıma.</span><span class="sxs-lookup"><span data-stu-id="31081-178">Any padding that was applied still needs to be removed or ignored, you're moving the burden into your application.</span></span>
  - <span data-ttu-id="31081-179">Avantajı, kaldırma ve doldurma doğrulama diğer uygulama veri doğrulama mantığı birleştirilebilir ' dir.</span><span class="sxs-lookup"><span data-stu-id="31081-179">The benefit is that the padding verification and removal can be incorporated into other application data verification logic.</span></span> <span data-ttu-id="31081-180">Doldurma doğrulaması ve veri doğrulaması sabit zamanında yapılabilir, tehdit azalır.</span><span class="sxs-lookup"><span data-stu-id="31081-180">If the padding verification and data verification can be done in constant time, the threat is reduced.</span></span>
  - <span data-ttu-id="31081-181">Algılanan ileti uzunluğu doldurma yorumu değişiklikleri olduğundan, hala bu yaklaşımı yayılan zamanlama bilgi olabilir.</span><span class="sxs-lookup"><span data-stu-id="31081-181">Since the interpretation of the padding changes the perceived message length, there may still be timing information emitted from this approach.</span></span>
- <span data-ttu-id="31081-182">Şifre çözme doldurma modu için ISO10126 değiştirin:</span><span class="sxs-lookup"><span data-stu-id="31081-182">Change the decryption padding mode to ISO10126:</span></span>
  - <span data-ttu-id="31081-183">ISO10126 şifre çözme doldurma PKCS7 şifreleme doldurma ve ANSIX923 şifreleme doldurma ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="31081-183">ISO10126 decryption padding is compatible with both PKCS7 encryption padding and ANSIX923 encryption padding.</span></span>
  - <span data-ttu-id="31081-184">Modunu değiştirme doldurma oracle bilgi tüm blok yerine 1 bayt azaltır.</span><span class="sxs-lookup"><span data-stu-id="31081-184">Changing the mode reduces the padding oracle knowledge to 1 byte instead of the entire block.</span></span> <span data-ttu-id="31081-185">Ancak, içerik XML öğesi, kapatma gibi iyi bilinen bir altbilgi varsa ilgili saldırıları iletinin kalan kısmını saldırmak devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31081-185">However, if the content has a well-known footer, such as a closing XML element, related attacks can continue to attack the rest of the message.</span></span>
  - <span data-ttu-id="31081-186">Bu da saldırganın birden çok kez farklı ileti uzaklık ile şifrelenmesi için aynı düz metin burada zorlayacak durumlarda düz metin kurtarma engellemez.</span><span class="sxs-lookup"><span data-stu-id="31081-186">This also doesn't prevent plaintext recovery in situations where the attacker can coerce the same plaintext to be encrypted multiple times with a different message offset.</span></span>
- <span data-ttu-id="31081-187">Ağ geçidi zamanlama sinyal Donuklaştır için bir şifre çözme çağrısı değerlendirmesi:</span><span class="sxs-lookup"><span data-stu-id="31081-187">Gate the evaluation of a decryption call to dampen the timing signal:</span></span>
  - <span data-ttu-id="31081-188">Tutma süresi hesaplama şifre çözme işlemi doldurma içeren veri kesimi için harcanacak en uzun süreyi aşan en az olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="31081-188">The computation of hold time must have a minimum in excess of the maximum amount of time the decryption operation would take for any data segment that contains padding.</span></span>
  - <span data-ttu-id="31081-189">Saat hesaplamaları kılavuzunda göre yapılması [yüksek çözünürlüklü zaman damgaları alınırken](https://msdn.microsoft.com/library/windows/desktop/dn55340.aspx), kullanarak değil <xref:System.Environment.TickCount?displayProperty=nameWithType> (tabi Top-üzerinden/taşma) veya (tabi NTP ayarlama iki sistem zaman damgaları çıkarma hatalar).</span><span class="sxs-lookup"><span data-stu-id="31081-189">Time computations should be done according to the guidance in [Acquiring high-resolution time stamps](https://msdn.microsoft.com/library/windows/desktop/dn55340.aspx), not by using <xref:System.Environment.TickCount?displayProperty=nameWithType> (subject to roll-over/overflow) or subtracting two system timestamps (subject to NTP adjustment errors).</span></span>
  - <span data-ttu-id="31081-190">Saat hesaplamaları tüm olası durumlar da dahil olmak üzere şifre çözme işlemi planlayacak yönetilmelidir ya da yalnızca bitiş doldurulan C++ uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="31081-190">Time computations must be inclusive of the decryption operation including all potential exceptions in managed or C++ applications, not just padded onto the end.</span></span>
  - <span data-ttu-id="31081-191">Başarı veya başarısızlık henüz belirlendiyse, zamanlama kapısı süresi dolduğunda, hata döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="31081-191">If success or failure has been determined yet, the timing gate needs to return failure when it expires.</span></span>
- <span data-ttu-id="31081-192">Kimliği doğrulanmamış şifre çözme işlemi Hizmetleri "geçersiz" iletilerinin sel geldiğini algılamak yerinde izleme olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="31081-192">Services that are performing unauthenticated decryption should have monitoring in place to detect that a flood of "invalid" messages has come through.</span></span>
  - <span data-ttu-id="31081-193">Bu sinyal hatalı pozitif sonuç (yasal bozuk veri) ve (saldırı algılama alınmadan kurtulması için yeterince uzun bir süre içinde çıkış yayılmak) false negatif taşıyan aklınızda size aittir.</span><span class="sxs-lookup"><span data-stu-id="31081-193">Bear in mind that this signal carries both false positives (legitimately corrupted data) and false negatives (spreading out the attack over a sufficiently long time to evade detection).</span></span>

## <a name="finding-vulnerable-code---native-applications"></a><span data-ttu-id="31081-194">Güvenlik açığı kod - yerel uygulamalar bulma</span><span class="sxs-lookup"><span data-stu-id="31081-194">Finding vulnerable code - native applications</span></span>

<span data-ttu-id="31081-195">Windows şifrelemesi karşı yerleşik programlar için: yeni nesil (CNG) kitaplığı:</span><span class="sxs-lookup"><span data-stu-id="31081-195">For programs built against the Windows Cryptography: Next Generation (CNG) library:</span></span>

- <span data-ttu-id="31081-196">Şifre çözme çağrıdır [BCryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa375391.aspx), belirten `BCRYPT_BLOCK_PADDING` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="31081-196">The decryption call is to [BCryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa375391.aspx), specifying the `BCRYPT_BLOCK_PADDING` flag.</span></span>
- <span data-ttu-id="31081-197">Anahtar tanıtıcısı çağırarak başlatıldı [BCryptSetProperty](https://msdn.microsoft.com/library/windows/desktop/aa375504.aspx) ile [BCRYPT_CHAINING_MODE](https://msdn.microsoft.com/library/windows/desktop/aa376211.aspx#BCRYPT_CHAINING_MODE) kümesine `BCRYPT_CHAIN_MODE_CBC`.</span><span class="sxs-lookup"><span data-stu-id="31081-197">The key handle has been initialized by calling [BCryptSetProperty](https://msdn.microsoft.com/library/windows/desktop/aa375504.aspx) with [BCRYPT_CHAINING_MODE](https://msdn.microsoft.com/library/windows/desktop/aa376211.aspx#BCRYPT_CHAINING_MODE) set to `BCRYPT_CHAIN_MODE_CBC`.</span></span>
  - <span data-ttu-id="31081-198">Bu yana `BCRYPT_CHAIN_MODE_CBC` etkilenen varsayılan kod atanmamıştır için herhangi bir değer `BCRYPT_CHAINING_MODE`.</span><span class="sxs-lookup"><span data-stu-id="31081-198">Since `BCRYPT_CHAIN_MODE_CBC` is the default, affected code may not have assigned any value for `BCRYPT_CHAINING_MODE`.</span></span>

<span data-ttu-id="31081-199">Eski Windows şifreleme API'si karşı yerleşik programlar için:</span><span class="sxs-lookup"><span data-stu-id="31081-199">For programs built against the older Windows Cryptographic API:</span></span>

- <span data-ttu-id="31081-200">Şifre çözme çağrıdır [CryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa379913.aspx) ile `Final=TRUE`.</span><span class="sxs-lookup"><span data-stu-id="31081-200">The decryption call is to [CryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa379913.aspx) with `Final=TRUE`.</span></span>
- <span data-ttu-id="31081-201">Anahtar tanıtıcısı çağırarak başlatıldı [CryptSetKeyParam](https://msdn.microsoft.com/library/windows/desktop/aa380272.aspx) ile [KP_MODE](https://msdn.microsoft.com/library/windows/desktop/aa379949.aspx#KP_MODE) kümesine `CRYPT_MODE_CBC`.</span><span class="sxs-lookup"><span data-stu-id="31081-201">The key handle has been initialized by calling [CryptSetKeyParam](https://msdn.microsoft.com/library/windows/desktop/aa380272.aspx) with [KP_MODE](https://msdn.microsoft.com/library/windows/desktop/aa379949.aspx#KP_MODE) set to `CRYPT_MODE_CBC`.</span></span>
  - <span data-ttu-id="31081-202">Bu yana `CRYPT_MODE_CBC` etkilenen varsayılan kod atanmamıştır için herhangi bir değer `KP_MODE`.</span><span class="sxs-lookup"><span data-stu-id="31081-202">Since `CRYPT_MODE_CBC` is the default, affected code may not have assigned any value for `KP_MODE`.</span></span>

## <a name="finding-vulnerable-code---managed-applications"></a><span data-ttu-id="31081-203">Bulma savunmasız kod - yönetilen uygulamalar</span><span class="sxs-lookup"><span data-stu-id="31081-203">Finding vulnerable code - managed applications</span></span>

- <span data-ttu-id="31081-204">Şifre çözme çağrıdır <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> veya <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> yöntemlere <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="31081-204">The decryption call is to the <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> or <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> methods on <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="31081-205">Bu, .NET içinde aşağıdaki türetilmiş türler içerir, ancak ayrıca üçüncü taraf türleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="31081-205">This includes the following derived types within the .NET, but may also include third-party types:</span></span>
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
- <span data-ttu-id="31081-206"><xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> Özelliği ayarlandığı <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, veya <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="31081-206">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, or <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="31081-207">Bu yana <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> etkilenen varsayılan kod hiçbir zaman atamış <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="31081-207">Since <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property.</span></span>
- <span data-ttu-id="31081-208"><xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> Özelliği ayarlandığı <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="31081-208">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span></span>
  - <span data-ttu-id="31081-209">Bu yana <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> etkilenen varsayılan kod hiçbir zaman atamış <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="31081-209">Since <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property.</span></span>

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a><span data-ttu-id="31081-210">Şifreleme iletisi söz dizimi savunmasız kod - bulma</span><span class="sxs-lookup"><span data-stu-id="31081-210">Finding vulnerable code - cryptographic message syntax</span></span>

<span data-ttu-id="31081-211">Kimliği doğrulanmamış bir CMS EnvelopedData ileti şifrelenmiş içerikleri CBC modunda AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES kullanır (1.2.840.113549.3.7) veya RC2'yi (1.2.840.113549.3.2) değil güvenlik açığı, de gibi başka bir blok şifreleme algoritmaları CBC modunda iletileri.</span><span class="sxs-lookup"><span data-stu-id="31081-211">An unauthenticated CMS EnvelopedData message whose encrypted content uses the CBC mode of AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) or RC2 (1.2.840.113549.3.2) is vulnerable, as well as messages using any other block cipher algorithms in CBC mode.</span></span>

<span data-ttu-id="31081-212">Akış şifrelemeleri bu belirli açığı uygulanmadıkça değil, ancak Microsoft, her zaman veri ContentEncryptionAlgorithm değerini inceleyerek üzerinden kimlik doğrulaması yapan önerir.</span><span class="sxs-lookup"><span data-stu-id="31081-212">While stream ciphers aren't susceptible to this particular vulnerability, Microsoft recommends always authenticating the data over inspecting the ContentEncryptionAlgorithm value.</span></span>

<span data-ttu-id="31081-213">Yönetilen uygulamalar için blob olabilir bir CMS EnvelopedData geçirilir olarak herhangi bir değer algılanan <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="31081-213">For managed applications, a CMS EnvelopedData blob can be detected as any value that is passed to <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.</span></span>

<span data-ttu-id="31081-214">Yerel uygulamalar için bir CMS tanıtıcı sağlanan herhangi bir değer olarak bir CMS EnvelopedData blob algılanabilir [CryptMsgUpdate](https://msdn.microsoft.com/library/windows/desktop/aa380231.aspx) , elde edilen [CMSG_TYPE_PARAM](https://msdn.microsoft.com/library/windows/desktop/aa380227.aspx) olan `CMSG_ENVELOPED` ve/veya CMS tanıtıcısı Daha sonra gönderilen bir `CMSG_CTRL_DECRYPT` aracılığıyla yönerge [CryptMsgControl](https://msdn.microsoft.com/library/windows/desktop/aa380220.aspx).</span><span class="sxs-lookup"><span data-stu-id="31081-214">For native applications, a CMS EnvelopedData blob can be detected as any value provided to a CMS handle via [CryptMsgUpdate](https://msdn.microsoft.com/library/windows/desktop/aa380231.aspx) whose resulting [CMSG_TYPE_PARAM](https://msdn.microsoft.com/library/windows/desktop/aa380227.aspx) is `CMSG_ENVELOPED` and/or the CMS handle is later sent a `CMSG_CTRL_DECRYPT` instruction via [CryptMsgControl](https://msdn.microsoft.com/library/windows/desktop/aa380220.aspx).</span></span>

## <a name="vulnerable-code-example---managed"></a><span data-ttu-id="31081-215">Güvenlik açığı kod örneğinde - yönetilen</span><span class="sxs-lookup"><span data-stu-id="31081-215">Vulnerable code example - managed</span></span>

<span data-ttu-id="31081-216">Bu yöntem bir tanımlama bilgisi okur ve onu şifresini çözer ve hiçbir veri bütünlüğü denetimi tarafından görülebilir.</span><span class="sxs-lookup"><span data-stu-id="31081-216">This method reads a cookie and decrypts it and no data integrity check is visible.</span></span> <span data-ttu-id="31081-217">Bu nedenle, bu yöntem tarafından salt okunur bir tanımlama bilgisinin içeriğinin aldığı kullanıcı tarafından veya şifrelenmiş bir tanımlama bilgisi değeri elde herhangi bir saldırgan tarafından saldırıya.</span><span class="sxs-lookup"><span data-stu-id="31081-217">Therefore, the contents of a cookie that is read by this method can be attacked by the user who received it, or by any attacker who has obtained the encrypted cookie value.</span></span>

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

## <a name="example-code-following-recommended-practices---managed"></a><span data-ttu-id="31081-218">Örnek kod aşağıda yönetilen uygulamalar - önerilen</span><span class="sxs-lookup"><span data-stu-id="31081-218">Example code following recommended practices - managed</span></span>

<span data-ttu-id="31081-219">Aşağıdaki örnek kod bir standart ileti biçimine kullanır</span><span class="sxs-lookup"><span data-stu-id="31081-219">The following sample code uses a non-standard message format of</span></span>

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

<span data-ttu-id="31081-220">Burada `cipher_algorithm_id` ve `hmac_algorithm_id` algoritması tanımlayıcılardır Bu algoritmalar (standart olmayan) gösterimlerini yerel uygulama.</span><span class="sxs-lookup"><span data-stu-id="31081-220">where the `cipher_algorithm_id` and `hmac_algorithm_id` algorithm identifiers are application-local (non-standard) representations of those algorithms.</span></span> <span data-ttu-id="31081-221">Bu tanımlayıcılar diğer bölümlerinde yerine, mevcut Mesajlaşma Protokolü tam bir birleştirilmiş bytestream mantıklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="31081-221">These identifiers may make sense in other parts of your existing messaging protocol instead of as a bare concatenated bytestream.</span></span>

<span data-ttu-id="31081-222">Bu örnek ayrıca bir şifreleme anahtarı ve bir HMAC anahtarı türetin için tek bir ana anahtar kullanır.</span><span class="sxs-lookup"><span data-stu-id="31081-222">This example also uses a single master key to derive both an encryption key and an HMAC key.</span></span> <span data-ttu-id="31081-223">Bu hem kolaylık ayrı olarak anahtarlı çift anahtarlı bir uygulamaya ve iki anahtar olarak farklı değerler tutma teşvik eden bir uygulama kapatmayı için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="31081-223">This is provided both as a convenience for turning a singly-keyed application into a dual-keyed application, and to encourage keeping the two keys as different values.</span></span> <span data-ttu-id="31081-224">Daha fazla eşitleme dışı HMAC anahtarı ve şifreleme anahtarı alınamıyor garanti eder.</span><span class="sxs-lookup"><span data-stu-id="31081-224">It further guarantees that the HMAC key and encryption key can't get out of synchronization.</span></span>

<span data-ttu-id="31081-225">Bu örnek kabul etmez bir <xref:System.IO.Stream> şifreleme veya şifre çözme için.</span><span class="sxs-lookup"><span data-stu-id="31081-225">This sample doesn't accept a <xref:System.IO.Stream> for either encryption or decryption.</span></span> <span data-ttu-id="31081-226">Geçerli veri biçimi yaptığı bir geçişi zor şifrelemek için `hmac_tag` değeri ciphertext önce gelir.</span><span class="sxs-lookup"><span data-stu-id="31081-226">The current data format makes one-pass encrypt difficult because the `hmac_tag` value precedes the ciphertext.</span></span> <span data-ttu-id="31081-227">Ancak, tüm sabit boyutlu öğeleri ayrıştırıcı daha basit tutmak için başında tuttuğu için bu biçim seçildi.</span><span class="sxs-lookup"><span data-stu-id="31081-227">However, this format was chosen because it keeps all of the fixed-size elements at the beginning to keep the parser simpler.</span></span> <span data-ttu-id="31081-228">Bir uygulayan GetHashAndReset çağırın ve TransformFinalBlock çağırmadan önce sonucu doğrulamak için dikkatli olmalıdır ancak bu veri biçimi ile bir geçişi şifre çözme, mümkündür.</span><span class="sxs-lookup"><span data-stu-id="31081-228">With this data format, one-pass decrypt is possible, though an implementer is cautioned to call GetHashAndReset and verify the result before calling TransformFinalBlock.</span></span> <span data-ttu-id="31081-229">Akış şifreleme önemliyse, farklı bir AE modu gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="31081-229">If streaming encryption is important, then a different AE mode may be required.</span></span>

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
