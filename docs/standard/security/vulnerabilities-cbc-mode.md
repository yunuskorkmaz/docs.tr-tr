---
title: Zamanlama açıklarıyla doldurmayı kullanarak CBC modunda simetrik şifre çözme
description: Algılama ve doldurmayı kullanarak Şifre blok zincirleme (CBC) modunu simetrik şifre çözme ile zamanlama güvenlik açıklarını azaltmaya öğrenin.
ms.date: 06/12/2018
author: blowdart
ms.author: mairaw
ms.openlocfilehash: 6d16b6849bfd4744f1828cda38a537f842243c1d
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45594880"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a><span data-ttu-id="e8468-103">Zamanlama açıklarıyla doldurmayı kullanarak CBC modunda simetrik şifre çözme</span><span class="sxs-lookup"><span data-stu-id="e8468-103">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>

<span data-ttu-id="e8468-104">Microsoft, artık ilk ciphertext bütünlüğünü dışında sağlamaya gerek kalmadan doğrulanabilir doldurma yapıldıysa simetrik şifreleme şifre blok zincirleme (CBC) modunu ile şifrelenen verilerin şifresini çözmek güvenli olduğunu düşündüğü özgü koşullar.</span><span class="sxs-lookup"><span data-stu-id="e8468-104">Microsoft believes that it's no longer safe to decrypt data encrypted with the Cipher-Block-Chaining (CBC) mode of symmetric encryption when verifiable padding has been applied without first ensuring the integrity of the ciphertext, except for very specific circumstances.</span></span> <span data-ttu-id="e8468-105">Bu judgement üzerinde şu anda bilinen şifreleme araştırmaları temel alır.</span><span class="sxs-lookup"><span data-stu-id="e8468-105">This judgement is based on currently known cryptographic research.</span></span> 

## <a name="introduction"></a><span data-ttu-id="e8468-106">Giriş</span><span class="sxs-lookup"><span data-stu-id="e8468-106">Introduction</span></span>

<span data-ttu-id="e8468-107">Doldurma oracle saldırı sağlar saldırgan anahtarı bilmeden içeriği verilerin şifresini çözmek, şifrelenmiş verilere karşı bir saldırı türüdür.</span><span class="sxs-lookup"><span data-stu-id="e8468-107">A padding oracle attack is a type of attack against encrypted data that allows the attacker to decrypt the contents of the data, without knowing the key.</span></span>

<span data-ttu-id="e8468-108">Bir "bilgi" bunlar yürütüyorsunuz eylem doğru olup olmamasına hakkında bir saldırgan bilgi veren bir oracle başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="e8468-108">An oracle refers to a "tell" which gives an attacker information about whether the action they're executing is correct or not.</span></span> <span data-ttu-id="e8468-109">Bir Pano yürütmeyi Imagine veya bir alt ile oyun kartı.</span><span class="sxs-lookup"><span data-stu-id="e8468-109">Imagine playing a board or card game with a child.</span></span> <span data-ttu-id="e8468-110">Ne zaman kendi yüz yanar büyük gülümseme Filiz Filiz olarak gördüğü için oracle olan iyi bir ettirmek üzere.</span><span class="sxs-lookup"><span data-stu-id="e8468-110">When her face lights up with a big smile because she thinks she's about to make a good move, that's an oracle.</span></span> <span data-ttu-id="e8468-111">Bir sonraki uygun şekilde planlamak için bu oracle rakip kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8468-111">You, as the opponent, can use this oracle to plan your next move appropriately.</span></span>

<span data-ttu-id="e8468-112">Doldurma özel bir şifreleme terimdir.</span><span class="sxs-lookup"><span data-stu-id="e8468-112">Padding is a specific cryptographic term.</span></span> <span data-ttu-id="e8468-113">Verilerinizi şifrelemek için kullanılan algoritmalar olan bazı şifrelemeleri her blok sabit boyutta olduğu veri blokları üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="e8468-113">Some ciphers, which are the algorithms used to encrypt your data, work on blocks of data where each block is a fixed size.</span></span> <span data-ttu-id="e8468-114">Şifrelemek istediğiniz veri blokları doldurmak için doğru boyutta değilse, verilerinizi mevcut kadar sıfır eklenir.</span><span class="sxs-lookup"><span data-stu-id="e8468-114">If the data you want to encrypt isn't the right size to fill the blocks, your data is padded until it does.</span></span> <span data-ttu-id="e8468-115">Doldurma birçok forms uygun boyutta özgün giriş olsa bile her zaman mevcut olacak şekilde bu doldurma gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e8468-115">Many forms of padding require that padding to always be present, even if the original input was of the right size.</span></span> <span data-ttu-id="e8468-116">Bu şifre çözme sırasında her zaman güvenli bir şekilde kaldırılması için doldurma sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8468-116">This allows the padding to always be safely removed upon decryption.</span></span>

<span data-ttu-id="e8468-117">İki şeyi bir araya getirildiğinde, bir yazılım uygulaması doldurma oracle ile şifresi çözülmüş veriler geçerli doldurma olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8468-117">Putting the two things together, a software implementation with a padding oracle reveals whether decrypted data has valid padding.</span></span> <span data-ttu-id="e8468-118">Oracle, "Geçersiz doldurma" ifadesini içeren bir değer döndüren olarak basit bir şey ya da geçersiz bir engel aksine geçerli bloğu işlemek için bir yaşamları farklı zaman ayırdığınız gibi daha karmaşık bir şey olabilir.</span><span class="sxs-lookup"><span data-stu-id="e8468-118">The oracle could be something as simple as returning a value that says "Invalid padding" or something more complicated like taking a measurably different time to process a valid block as opposed to an invalid block.</span></span>

<span data-ttu-id="e8468-119">Blok tabanlı şifrelemeleri ilişki verileri ikinci bloğundaki ilk blokla veri belirleyen modu adlı başka bir özelliğe sahip ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="e8468-119">Block-based ciphers have another property, called the mode, which determines the relationship of data in the first block to the data in the second block, and so on.</span></span> <span data-ttu-id="e8468-120">En sık kullanılan modları CBC biridir.</span><span class="sxs-lookup"><span data-stu-id="e8468-120">One of the most commonly used modes is CBC.</span></span> <span data-ttu-id="e8468-121">CBC başlatma vektörü (IV olarak), bilinen bir ilk rastgele bloğunu ortaya çıkarır ve önceki blok aynı anahtarla aynı ileti şifreleme her zaman aynı şifrelenmiş çıktı oluşturmasa şekilde sağlamak için statik şifreleme sonucu ile birleştirir.</span><span class="sxs-lookup"><span data-stu-id="e8468-121">CBC introduces an initial random block, known as the Initialization Vector (IV), and combines the previous block with the result of static encryption to make it such that encrypting the same message with the same key doesn't always produce the same encrypted output.</span></span>

<span data-ttu-id="e8468-122">Oracle sunan koda biraz değiştirilmiş bir ileti gönderin ve bunları oracle söyler kadar veri göndermeye devam verilerinin doğru olduğundan, bir saldırganın doldurma oracle, CBC verileri nasıl yapılandırıldığını birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8468-122">An attacker can use a padding oracle, in combination with how CBC data is structured, to send slightly changed messages to the code that exposes the oracle, and keep sending data until the oracle tells them the data is correct.</span></span> <span data-ttu-id="e8468-123">Bu yanıtından, saldırgan iletinin bayt şifresini çözebilir.</span><span class="sxs-lookup"><span data-stu-id="e8468-123">From this response, the attacker can decrypt the message byte by byte.</span></span>

<span data-ttu-id="e8468-124">Modern bir bilgisayar gibi yüksek kaliteli bir saldırganın çok küçük (0,1 MS'den kısa) yürütme farklılıkları uzak sistemlere zaman algılayabilir ağlardır.</span><span class="sxs-lookup"><span data-stu-id="e8468-124">Modern computer networks are of such high quality that an attacker can detect very small (less than 0.1 ms) differences in execution time on remote systems.</span></span> <span data-ttu-id="e8468-125">Başarılı bir şifre çözme veri üzerinde oynama değildi, yalnızca oluşabilir varsayılarak uygulamaları araçlarından başarılı ve başarısız şifre çözme farklılıkları gözlemlemek için tasarlanmış saldırılara karşı savunmasız olabilir.</span><span class="sxs-lookup"><span data-stu-id="e8468-125">Applications that are assuming that a successful decryption can only happen when the data wasn't tampered with may be vulnerable to attack from tools that are designed to observe differences in successful and unsuccessful decryption.</span></span> <span data-ttu-id="e8468-126">Bu zamanlama fark diğerlerinden bazı diller ya da kitaplıkları daha önemli olabilir, ancak bunu şimdi uygulamanın yanıt hata olarak dikkate alındığında bu tüm dillerde ve kitaplıklarda için pratik bir tehdit olarak yorumlanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e8468-126">While this timing difference may be more significant in some languages or libraries than others, it's now believed that this is a practical threat for all languages and libraries when the application's response to failure is taken into account.</span></span>

<span data-ttu-id="e8468-127">Bu saldırı şifrelenmiş verileri değiştirin ve test sonucu oracle ile olanağı kullanır.</span><span class="sxs-lookup"><span data-stu-id="e8468-127">This attack relies on the ability to change the encrypted data and test the result with the oracle.</span></span> <span data-ttu-id="e8468-128">Tam olarak saldırının etkilerini hafifletmek için tek yolu, şifrelenmiş verilere değişiklikleri algılar ve herhangi bir eylem gerçekleştirmek Reddet sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="e8468-128">The only way to fully mitigate the attack is to detect changes to the encrypted data and refuse to perform any actions on it.</span></span> <span data-ttu-id="e8468-129">Bunu yapmak için standart verileri için imza oluşturma ve tüm işlemler gerçekleştirilir önce bu imzayı doğrulamak için yoludur.</span><span class="sxs-lookup"><span data-stu-id="e8468-129">The standard way to do this is to create a signature for the data and validate that signature before any operations are performed.</span></span> <span data-ttu-id="e8468-130">İmza doğrulanabilir, saldırgan tarafından oluşturulamıyor, aksi takdirde bunlar şifrelenmiş veriler değiştirin, sonra değiştirilen verileri temel alan yeni bir imza işlem.</span><span class="sxs-lookup"><span data-stu-id="e8468-130">The signature must be verifiable, it cannot be created by the attacker, otherwise they'd change the encrypted data, then compute a new signature based on the changed data.</span></span> <span data-ttu-id="e8468-131">Bir ortak tür uygun imzaya anahtarlı karma ileti kimlik doğrulama kodu (HMAC) bilinir.</span><span class="sxs-lookup"><span data-stu-id="e8468-131">One common type of appropriate signature is known as a keyed-hash message authentication code (HMAC).</span></span> <span data-ttu-id="e8468-132">Gizli bir anahtar yalnızca HMAC oluşturan kişi ve doğrulamadan kişi bilinen alır, bir HMAC bir sağlama toplamı farklıdır.</span><span class="sxs-lookup"><span data-stu-id="e8468-132">An HMAC differs from a checksum in that it takes a secret key, known only to the person producing the HMAC and to the person validating it.</span></span> <span data-ttu-id="e8468-133">Elinde anahtarının doğru HMAC üretemiyor.</span><span class="sxs-lookup"><span data-stu-id="e8468-133">Without possession of the key, you can't produce a correct HMAC.</span></span> <span data-ttu-id="e8468-134">Verilerinizi almak, şifrelenmiş verilerin, gizli bir anahtar kullanarak HMAC ve gönderen paylaşımı, daha sonra karşı bir gönderildiği HMAC hesaplanan karşılaştırma bağımsız olarak işlem.</span><span class="sxs-lookup"><span data-stu-id="e8468-134">When you receive your data, you'd take the encrypted data, independently compute the HMAC using the secret key you and the sender share, then compare the HMAC they sent against the one you computed.</span></span> <span data-ttu-id="e8468-135">Bu karşılaştırma sabit zaman olmalıdır, farklı türde bir saldırı sağlayan başka bir algılanabilir oracle, aksi takdirde ekledik.</span><span class="sxs-lookup"><span data-stu-id="e8468-135">This comparison must be constant time, otherwise you've added another detectable oracle, allowing a different type of attack.</span></span>

<span data-ttu-id="e8468-136">Özet olarak, sıfır güvenli bir şekilde CBC blok şifreleme özelliklerinden kullanmak için bunları bir HMAC (veya başka bir veri bütünlük denetimi ile) kullanarak verilerin şifresini çözmek için bir sabit zaman karşılaştırma denemeden önce doğrulayan birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8468-136">In summary, to use padded CBC block ciphers safely, you must combine them with an HMAC (or another data integrity check) that you validate using a constant time comparison before trying to decrypt the data.</span></span> <span data-ttu-id="e8468-137">Tüm değiştirilmiş bir yanıt oluşturması için aynı süre iletilerin olduğundan, saldırı engellenir.</span><span class="sxs-lookup"><span data-stu-id="e8468-137">Since all altered messages take the same amount time to produce a response, the attack is prevented.</span></span>

## <a name="who-is-vulnerable"></a><span data-ttu-id="e8468-138">Güvenlik Açığı kimdir</span><span class="sxs-lookup"><span data-stu-id="e8468-138">Who is vulnerable</span></span>

<span data-ttu-id="e8468-139">Bu güvenlik açığını kendi şifreleme ve şifre çözme işlemi hem yönetilen hem de yerel uygulamalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e8468-139">This vulnerability applies to both managed and native applications that are performing their own encryption and decryption.</span></span> <span data-ttu-id="e8468-140">Bu, örneğin içerir:</span><span class="sxs-lookup"><span data-stu-id="e8468-140">This includes, for example:</span></span>

- <span data-ttu-id="e8468-141">Sunucuda sonraki şifre çözme için bir tanımlama bilgisi şifreler uygulama.</span><span class="sxs-lookup"><span data-stu-id="e8468-141">An application that encrypts a cookie for later decryption on the server.</span></span>
- <span data-ttu-id="e8468-142">Sütunları kullanıcıların bir tabloya veri ekleme yeteneği sağlayan bir veritabanı uygulaması daha sonra şifresi.</span><span class="sxs-lookup"><span data-stu-id="e8468-142">A database application that provides the ability for users to insert data into a table whose columns are later decrypted.</span></span>
- <span data-ttu-id="e8468-143">Şifreleme Aktarımdaki verileri korumak için paylaşılan bir anahtar kullanarak dayalı bir veri aktarımı uygulama.</span><span class="sxs-lookup"><span data-stu-id="e8468-143">A data transfer application that relies on encryption using a shared key to protect the data in transit.</span></span>
- <span data-ttu-id="e8468-144">Bir uygulama, uygulama şifreleyen ve iletilerin "içinde" TLS tünelinin şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="e8468-144">An application that encrypts and decrypts messages "inside" the TLS tunnel.</span></span>

<span data-ttu-id="e8468-145">Tek başına TLS kullanarak, bu senaryolarda koruma sağlamaz olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e8468-145">Note that using TLS alone may not protect you in these scenarios.</span></span>

<span data-ttu-id="e8468-146">Bir güvenlik açığına sahip uygulama:</span><span class="sxs-lookup"><span data-stu-id="e8468-146">A vulnerable application:</span></span>

- <span data-ttu-id="e8468-147">PKCS #7 ya da ANSI X.923 gibi doğrulanabilir doldurma moduyla CBC şifreleme modu kullanarak verilerin şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="e8468-147">Decrypts data using the CBC cipher mode with a verifiable padding mode, such as PKCS#7 or ANSI X.923.</span></span>
- <span data-ttu-id="e8468-148">Şifre çözme veri bütünleştirme denetimi (MAC ya da asimetrik bir dijital imza) aracılığıyla gerçekleştirilen olmadan gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e8468-148">Performs the decryption without having performed a data integrity check (via a MAC or an asymmetric digital signature).</span></span>

<span data-ttu-id="e8468-149">Bu soyutlama üzerinde şu temel elemanlar şifreli ileti söz dizimi (PKCS #7/CMS) EnvelopedData yapısı gibi üst üzerinden oluşturulan uygulamalar için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e8468-149">This also applies to applications built on top of abstractions over top of these primitives, such as the Cryptographic Message Syntax (PKCS#7/CMS) EnvelopedData structure.</span></span>

## <a name="related-areas-of-concern"></a><span data-ttu-id="e8468-150">İlgili sorunlu alanları</span><span class="sxs-lookup"><span data-stu-id="e8468-150">Related areas of concern</span></span>

<span data-ttu-id="e8468-151">Araştırma ISO 10126 ileti iyi bilinen veya öngörülebilir alt yapısına sahip olduğunda doldurma eşdeğeri ile doldurulan CBC iletileri hakkında daha fazla endişe Microsoft'a açmıştır.</span><span class="sxs-lookup"><span data-stu-id="e8468-151">Research has led Microsoft to be further concerned about CBC messages that are padded with ISO 10126-equivalent padding when the message has a well-known or predictable footer structure.</span></span> <span data-ttu-id="e8468-152">Örneğin, öneri (xmlenc EncryptedXml) işleme ve W3C XML şifreleme sözdizimi kurallarına altında hazırlanmış içeriği.</span><span class="sxs-lookup"><span data-stu-id="e8468-152">For example, content prepared under the rules of the W3C XML Encryption Syntax and Processing Recommendation (xmlenc, EncryptedXml).</span></span> <span data-ttu-id="e8468-153">İletiyi imzalamak sonra şifrelemek için W3C kılavuzunu zaman uygun kabul ederken Microsoft artık her zaman şifreleyin-then-oturum yapılması önerir.</span><span class="sxs-lookup"><span data-stu-id="e8468-153">While the W3C guidance to sign the message then encrypt was considered appropriate at the time, Microsoft now recommends always doing encrypt-then-sign.</span></span>

<span data-ttu-id="e8468-154">Asimetrik anahtar ile rastgele bir ileti arasındaki devralınan güven ilişkisi olduğundan uygulama geliştiricilerinin her zaman bir asimetrik imza anahtarı uygulanabilirliğini doğrulama dikkatli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e8468-154">Application developers should always be mindful of verifying the applicability of an asymmetric signature key, as there's no inherent trust relationship between an asymmetric key and an arbitrary message.</span></span>

## <a name="details"></a><span data-ttu-id="e8468-155">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e8468-155">Details</span></span>

<span data-ttu-id="e8468-156">Tarihsel olarak, hem şifreleme hem de HMAC veya RSA imzaları gibi bir araç kullanarak önemli verileri doğrulamak önemli olan bir fikir birliğine varılmış olmuştur.</span><span class="sxs-lookup"><span data-stu-id="e8468-156">Historically, there has been consensus that it's important to both encrypt and authenticate important data, using means such as HMAC or RSA signatures.</span></span> <span data-ttu-id="e8468-157">Ancak, how to sequence şifreleme ve kimlik doğrulama işlemleri için daha az kılavuzluk olmuştur.</span><span class="sxs-lookup"><span data-stu-id="e8468-157">However, there has been less clear guidance as to how to sequence the encryption and authentication operations.</span></span> <span data-ttu-id="e8468-158">Bu makalede ayrıntılı güvenlik açığı nedeniyle, Microsoft'un Kılavuzu artık her zaman "şifrelemek-then-sign" paradigma kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="e8468-158">Due to the vulnerability detailed in this article, Microsoft's guidance is now to always use the "encrypt-then-sign" paradigm.</span></span> <span data-ttu-id="e8468-159">Diğer bir deyişle, ilk simetrik anahtar kullanarak verileri şifreleme ve ardından MAC ya da asimetrik imza ciphertext (şifrelenmiş veri) üzerinde işlem.</span><span class="sxs-lookup"><span data-stu-id="e8468-159">That is, first encrypt data using a symmetric key, then compute a MAC or asymmetric signature over the ciphertext (encrypted data).</span></span> <span data-ttu-id="e8468-160">Verilerin şifresini çözme, ters gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="e8468-160">When decrypting data, perform the reverse.</span></span> <span data-ttu-id="e8468-161">İlk olarak, MAC veya imza şifreler onayladıktan sonra şifreyi.</span><span class="sxs-lookup"><span data-stu-id="e8468-161">First, confirm the MAC or signature of the ciphertext, then decrypt it.</span></span>

<span data-ttu-id="e8468-162">"Oracle saldırıları doldurma" 10 yılı aşkın süredir mevcut bilinmektedir olarak bilinen güvenlik açıklarının sınıf.</span><span class="sxs-lookup"><span data-stu-id="e8468-162">A class of vulnerabilities known as "padding oracle attacks" have been known to exist for over 10 years.</span></span> <span data-ttu-id="e8468-163">Bu güvenlik açıklarına veri bloğu başına en fazla 4096 deneme kullanarak AES ve 3DES ' gibi blok simetrik algoritmaları ile şifrelenen verilerin şifresini çözmek bir saldırganın.</span><span class="sxs-lookup"><span data-stu-id="e8468-163">These vulnerabilities allow an attacker to decrypt data encrypted by symmetric block algorithms, such as AES and 3DES, using no more than 4096 attempts per block of data.</span></span> <span data-ttu-id="e8468-164">Bu güvenlik açıklarına olun şifrelemeleri block olgu kullanımını sonunda doğrulanabilir doldurma verilerle en sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e8468-164">These vulnerabilities make use of the fact that block ciphers are most frequently used with verifiable padding data at the end.</span></span> <span data-ttu-id="e8468-165">Bir saldırganın ile ciphertext değiştirmesine ve olup kurcalama hata en sonda doldurma biçimde neden olduğunu bulmak, saldırgan verilerin şifresini çözebilen bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="e8468-165">It was found that if an attacker can tamper with ciphertext and find out whether the tampering caused an error in the format of the padding at the end, the attacker can decrypt the data.</span></span>

<span data-ttu-id="e8468-166">Başlangıçta, pratik saldırıları doldurma gibi ASP.NET güvenlik açığı geçerli olup üzerinde farklı hata kodları döndürecekti Hizmetleri bağlı [MS10-070](https://technet.microsoft.com/library/security/ms10-070.aspx).</span><span class="sxs-lookup"><span data-stu-id="e8468-166">Initially, practical attacks were based on services that would return different error codes based on whether padding was valid, such as the ASP.NET vulnerability [MS10-070](https://technet.microsoft.com/library/security/ms10-070.aspx).</span></span> <span data-ttu-id="e8468-167">Ancak, Microsoft artık yalnızca zamanlama geçerli ve geçersiz doldurma işlem arasındaki farklılıkları kullanarak benzer saldırıları yürütmek pratik olduğunu düşündüğü.</span><span class="sxs-lookup"><span data-stu-id="e8468-167">However, Microsoft now believes that it's practical to conduct similar attacks using only the differences in timing between processing valid and invalid padding.</span></span>

<span data-ttu-id="e8468-168">İmza şifreleme şeması kullanır ve imza doğrulaması (içeriği) bağımsız olarak veri belirli bir süre için sabit bir çalışma zamanı ile gerçekleştirilen şartıyla, veri bütünlüğünü herhangi bir bilgi yayma olmadan doğrulanabilir bir Saldırgan aracılığıyla bir [yan kanal](https://en.wikipedia.org/wiki/Side-channel_attack).</span><span class="sxs-lookup"><span data-stu-id="e8468-168">Provided that the encryption scheme employs a signature and that the signature verification is performed with a fixed runtime for a given length of data (irrespective of the contents), the data integrity can be verified without emitting any information to an attacker via a [side channel](https://en.wikipedia.org/wiki/Side-channel_attack).</span></span> <span data-ttu-id="e8468-169">Bütünlük denetimi değiştirilen tüm iletileri reddeder beri doldurma oracle tehdit azalır.</span><span class="sxs-lookup"><span data-stu-id="e8468-169">Since the integrity check rejects any tampered messages, the padding oracle threat is mitigated.</span></span>

## <a name="guidance"></a><span data-ttu-id="e8468-170">Kılavuz</span><span class="sxs-lookup"><span data-stu-id="e8468-170">Guidance</span></span>

<span data-ttu-id="e8468-171">İlk ve, Microsoft gizlilik sahip herhangi bir veri üzerinden Aktarım Katmanı Güvenliği (TLS), Güvenli Yuva Katmanı (SSL) için ardıl iletilmesi önerir.</span><span class="sxs-lookup"><span data-stu-id="e8468-171">First and foremost, Microsoft recommends that any data that has confidentiality needs be transmitted over Transport Layer Security (TLS), the successor to Secure Sockets Layer (SSL).</span></span>

<span data-ttu-id="e8468-172">Ardından, uygulamanızı çözümleyin:</span><span class="sxs-lookup"><span data-stu-id="e8468-172">Next, analyze your application to:</span></span>

- <span data-ttu-id="e8468-173">Tam olarak hangi şifreleme gerçekleştirmekte anlayın ve hangi şifreleme platformlar ve API'ler kullanmakta olduğunuz tarafından sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e8468-173">Understand precisely what encryption you're performing and what encryption is being provided by the platforms and APIs you're using.</span></span>
- <span data-ttu-id="e8468-174">Belirli bir simetrik, her katmanda her kullanım olun [blok şifreleme algoritması](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers)gibi gizli Anahtarlanan veri bütünleştirme denetimi kullanımını AES ve CBC modunda 3DES birleştirmek (asimetrik bir imza, bir HMAC veya şifreleme modunu değiştirmek için bir [kimliği doğrulanmış şifreleme](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE) modunu GCM veya CCM gibi).</span><span class="sxs-lookup"><span data-stu-id="e8468-174">Be certain that each usage at each layer of a symmetric [block cipher algorithm](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), such as AES and 3DES, in CBC mode incorporate the use of a secret-keyed data integrity check (an asymmetric signature, an HMAC, or to change the cipher mode to an [authenticated encryption](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE) mode such as GCM or CCM).</span></span>

<span data-ttu-id="e8468-175">Güncel bir araştırmaya göre bunu genellikle kimlik doğrulama ve şifreleme adımları birbirinden bağımsız olarak şifreleme AE olmayan modları için gerçekleştirildiğinde, şifreli kimlik doğrulaması (şifreleme-then-oturum) genel en iyi seçenek olduğunu azalttığı kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="e8468-175">Based on the current research, it's generally believed that when the authentication and encryption steps are performed independently for non-AE modes of encryption, authenticating the ciphertext (encrypt-then-sign) is the best general option.</span></span> <span data-ttu-id="e8468-176">Ancak, şifreleme BT'ye bir doğru yanıt yok ve bu Genelleştirme profesyonel cryptographer kadar iyi yönlendirilmiş önerileri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e8468-176">However, there's no one-size-fits-all correct answer to cryptography and this generalization isn't as good as directed advice from a professional cryptographer.</span></span>

<span data-ttu-id="e8468-177">Kendi ileti biçimi değiştirebilirsiniz ancak kimlik doğrulamasız CBC şifre çözme gerçekleştirmek mümkün olan uygulamaların risk azaltma işlemleri gibi birleştirmek için önerilir:</span><span class="sxs-lookup"><span data-stu-id="e8468-177">Applications that are unable to change their messaging format but perform unauthenticated CBC decryption are encouraged to try to incorporate mitigations such as:</span></span>

- <span data-ttu-id="e8468-178">Doğrulayın veya doldurmayı kaldırmak şifre çözücü vermeden şifre çözme:</span><span class="sxs-lookup"><span data-stu-id="e8468-178">Decrypt without allowing the decryptor to verify or remove padding:</span></span>
  - <span data-ttu-id="e8468-179">Uygulanmış olan tüm doldurma hala göz ardı veya kaldırılmasına izin gerekir, uygulamanıza yük taşıma.</span><span class="sxs-lookup"><span data-stu-id="e8468-179">Any padding that was applied still needs to be removed or ignored, you're moving the burden into your application.</span></span>
  - <span data-ttu-id="e8468-180">Diğer uygulama veri doğrulama mantığı eklemenize doldurma doğrulama ve temizleme birleştirilebilir avantajdır.</span><span class="sxs-lookup"><span data-stu-id="e8468-180">The benefit is that the padding verification and removal can be incorporated into other application data verification logic.</span></span> <span data-ttu-id="e8468-181">Verileri doğrulama ve doldurma doğrulama Sabit sürede yapılabilir, tehdit azaltılır.</span><span class="sxs-lookup"><span data-stu-id="e8468-181">If the padding verification and data verification can be done in constant time, the threat is reduced.</span></span>
  - <span data-ttu-id="e8468-182">Algılanan ileti uzunluğu doldurmayı yorumunu değişiklikleri olduğundan, yine de bu yaklaşımı yayılan zamanlama bilgi olabilir.</span><span class="sxs-lookup"><span data-stu-id="e8468-182">Since the interpretation of the padding changes the perceived message length, there may still be timing information emitted from this approach.</span></span>
- <span data-ttu-id="e8468-183">Şifre çözme doldurma modu için ISO10126 değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e8468-183">Change the decryption padding mode to ISO10126:</span></span>
  - <span data-ttu-id="e8468-184">ISO10126 şifre çözme doldurma PKCS7 şifreleme doldurma ve ANSIX923 şifreleme doldurma ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="e8468-184">ISO10126 decryption padding is compatible with both PKCS7 encryption padding and ANSIX923 encryption padding.</span></span>
  - <span data-ttu-id="e8468-185">Modunu değiştirme doldurma oracle bilgi tüm bloğu yerine 1 bayt azaltır.</span><span class="sxs-lookup"><span data-stu-id="e8468-185">Changing the mode reduces the padding oracle knowledge to 1 byte instead of the entire block.</span></span> <span data-ttu-id="e8468-186">Ancak, içerik XML öğesi, bir kapatma gibi iyi bilinen bir alt bilgi varsa ilgili saldırıları ileti geri kalanını saldırılara karşı devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8468-186">However, if the content has a well-known footer, such as a closing XML element, related attacks can continue to attack the rest of the message.</span></span>
  - <span data-ttu-id="e8468-187">Ayrıca, burada saldırganın birden çok kez farklı ileti uzaklığı ile şifrelenmiş aynı düz metin zorlayacak durumlarda düz metin kurtarma da engellemez.</span><span class="sxs-lookup"><span data-stu-id="e8468-187">This also doesn't prevent plaintext recovery in situations where the attacker can coerce the same plaintext to be encrypted multiple times with a different message offset.</span></span>
- <span data-ttu-id="e8468-188">Şifre çözme çağrısı zamanlama sinyal Donuklaştır değerlendirmesi kapısı:</span><span class="sxs-lookup"><span data-stu-id="e8468-188">Gate the evaluation of a decryption call to dampen the timing signal:</span></span>
  - <span data-ttu-id="e8468-189">Durma süresini hesaplama şifre çözme işlemi doldurma içeren veri segmenti için gereken en uzun süreyi aşan en az olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e8468-189">The computation of hold time must have a minimum in excess of the maximum amount of time the decryption operation would take for any data segment that contains padding.</span></span>
  - <span data-ttu-id="e8468-190">Saat hesaplamaları kılavuzunda göre yapılmalıdır [yüksek çözünürlüklü zaman damgaları alınırken](https://msdn.microsoft.com/library/windows/desktop/dn55340.aspx), kullanarak değil <xref:System.Environment.TickCount?displayProperty=nameWithType> (tabi Top-üzerinden/taşma) veya iki sistem zaman damgaları (tabi NTP ayarlama çıkararak hatalar).</span><span class="sxs-lookup"><span data-stu-id="e8468-190">Time computations should be done according to the guidance in [Acquiring high-resolution time stamps](https://msdn.microsoft.com/library/windows/desktop/dn55340.aspx), not by using <xref:System.Environment.TickCount?displayProperty=nameWithType> (subject to roll-over/overflow) or subtracting two system timestamps (subject to NTP adjustment errors).</span></span>
  - <span data-ttu-id="e8468-191">Saat hesaplamaları tüm potansiyel özel durumlar dahil olmak üzere şifre çözme işlemi tamamlanmıyorsa yönetilmelidir veya C++ uygulamaları, yalnızca sona sıfır.</span><span class="sxs-lookup"><span data-stu-id="e8468-191">Time computations must be inclusive of the decryption operation including all potential exceptions in managed or C++ applications, not just padded onto the end.</span></span>
  - <span data-ttu-id="e8468-192">Başarı veya başarısızlık henüz belirlendiyse, zamanlama kapısı süresi dolduğunda, hata döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8468-192">If success or failure has been determined yet, the timing gate needs to return failure when it expires.</span></span>
- <span data-ttu-id="e8468-193">Kimliği doğrulanmamış şifre çözme işlemi Hizmetleri "geçersiz" iletileri hakkında güncelleştirmekte gelen olduğunu algılamak için bir izleme olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8468-193">Services that are performing unauthenticated decryption should have monitoring in place to detect that a flood of "invalid" messages has come through.</span></span>
  - <span data-ttu-id="e8468-194">Bu sinyal hatalı pozitif sonuçları (duyup duymayacağını bozuk veri) hem de false negatif (saldırı algılama atlatabilir yeterince uzun bir zaman aşımına yayılmasını) taşıyan aklınızda size aittir.</span><span class="sxs-lookup"><span data-stu-id="e8468-194">Bear in mind that this signal carries both false positives (legitimately corrupted data) and false negatives (spreading out the attack over a sufficiently long time to evade detection).</span></span>

## <a name="finding-vulnerable-code---native-applications"></a><span data-ttu-id="e8468-195">Güvenlik Açığı kodu - yerel uygulamaları bulma</span><span class="sxs-lookup"><span data-stu-id="e8468-195">Finding vulnerable code - native applications</span></span>

<span data-ttu-id="e8468-196">Windows şifreleme karşı yerleşik programları için: yeni nesil (CNG) kitaplığı:</span><span class="sxs-lookup"><span data-stu-id="e8468-196">For programs built against the Windows Cryptography: Next Generation (CNG) library:</span></span>

- <span data-ttu-id="e8468-197">Şifre çözme çağrıdır [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt), belirten `BCRYPT_BLOCK_PADDING` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="e8468-197">The decryption call is to [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt), specifying the `BCRYPT_BLOCK_PADDING` flag.</span></span>
- <span data-ttu-id="e8468-198">Anahtar tanıtıcısı çağırarak başlatılmış [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) ile [BCRYPT_CHAINING_MODE](https://msdn.microsoft.com/library/windows/desktop/aa376211.aspx#BCRYPT_CHAINING_MODE) kümesine `BCRYPT_CHAIN_MODE_CBC`.</span><span class="sxs-lookup"><span data-stu-id="e8468-198">The key handle has been initialized by calling [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) with [BCRYPT_CHAINING_MODE](https://msdn.microsoft.com/library/windows/desktop/aa376211.aspx#BCRYPT_CHAINING_MODE) set to `BCRYPT_CHAIN_MODE_CBC`.</span></span>
  - <span data-ttu-id="e8468-199">Bu yana `BCRYPT_CHAIN_MODE_CBC` etkilenen varsayılan kod değil atamış herhangi bir değer `BCRYPT_CHAINING_MODE`.</span><span class="sxs-lookup"><span data-stu-id="e8468-199">Since `BCRYPT_CHAIN_MODE_CBC` is the default, affected code may not have assigned any value for `BCRYPT_CHAINING_MODE`.</span></span>

<span data-ttu-id="e8468-200">Eski Windows şifreleme API üzerinde derlenmiş programlar için:</span><span class="sxs-lookup"><span data-stu-id="e8468-200">For programs built against the older Windows Cryptographic API:</span></span>

- <span data-ttu-id="e8468-201">Şifre çözme çağrıdır [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) ile `Final=TRUE`.</span><span class="sxs-lookup"><span data-stu-id="e8468-201">The decryption call is to [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) with `Final=TRUE`.</span></span>
- <span data-ttu-id="e8468-202">Anahtar tanıtıcısı çağırarak başlatılmış [CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) ile [KP_MODE](https://msdn.microsoft.com/library/windows/desktop/aa379949.aspx#KP_MODE) kümesine `CRYPT_MODE_CBC`.</span><span class="sxs-lookup"><span data-stu-id="e8468-202">The key handle has been initialized by calling [CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) with [KP_MODE](https://msdn.microsoft.com/library/windows/desktop/aa379949.aspx#KP_MODE) set to `CRYPT_MODE_CBC`.</span></span>
  - <span data-ttu-id="e8468-203">Bu yana `CRYPT_MODE_CBC` etkilenen varsayılan kod değil atamış herhangi bir değer `KP_MODE`.</span><span class="sxs-lookup"><span data-stu-id="e8468-203">Since `CRYPT_MODE_CBC` is the default, affected code may not have assigned any value for `KP_MODE`.</span></span>

## <a name="finding-vulnerable-code---managed-applications"></a><span data-ttu-id="e8468-204">Güvenlik Açığı kodu bulma - yönetilen uygulamalar</span><span class="sxs-lookup"><span data-stu-id="e8468-204">Finding vulnerable code - managed applications</span></span>

- <span data-ttu-id="e8468-205">Şifre çözme çağrıdır <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> veya <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> yöntemlerde <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e8468-205">The decryption call is to the <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> or <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> methods on <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="e8468-206">.NET içinde aşağıdaki türetilmiş türlerini içerir, ancak ayrıca üçüncü taraf türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e8468-206">This includes the following derived types within the .NET, but may also include third-party types:</span></span>
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
- <span data-ttu-id="e8468-207"><xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> Özelliğinin ayarlandığı <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, veya <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e8468-207">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, or <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="e8468-208">Bu yana <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> etkilenen varsayılan kod hiçbir zaman atamış <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e8468-208">Since <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property.</span></span>
- <span data-ttu-id="e8468-209"><xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> Özelliği ayarlanmıştır <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e8468-209">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span></span>
  - <span data-ttu-id="e8468-210">Bu yana <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> etkilenen varsayılan kod hiçbir zaman atamış <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e8468-210">Since <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property.</span></span>

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a><span data-ttu-id="e8468-211">Şifreli ileti söz dizimi - savunmasız kod bulma</span><span class="sxs-lookup"><span data-stu-id="e8468-211">Finding vulnerable code - cryptographic message syntax</span></span>

<span data-ttu-id="e8468-212">Kimliği doğrulanmamış bir CMS EnvelopedData ileti şifreli içerikleri CBC modunda AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES kullanır (1.2.840.113549.3.7) veya RC2 (1.2.840.113549.3.2) olan açıktan de olarak diğer bir blok şifreleme algoritmaları kullanarak CBC modunda iletileri.</span><span class="sxs-lookup"><span data-stu-id="e8468-212">An unauthenticated CMS EnvelopedData message whose encrypted content uses the CBC mode of AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) or RC2 (1.2.840.113549.3.2) is vulnerable, as well as messages using any other block cipher algorithms in CBC mode.</span></span>

<span data-ttu-id="e8468-213">Akış şifrelemeleri belirli bu güvenlik açığını maruz değildir, ancak her zaman veri ContentEncryptionAlgorithm değeri inceleyerek üzerinden kimlik doğrulaması yapan Microsoft önerir.</span><span class="sxs-lookup"><span data-stu-id="e8468-213">While stream ciphers aren't susceptible to this particular vulnerability, Microsoft recommends always authenticating the data over inspecting the ContentEncryptionAlgorithm value.</span></span>

<span data-ttu-id="e8468-214">Yönetilen uygulamalar için blob olabilir bir CMS EnvelopedData geçirilir olarak herhangi bir değer algılandı. <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="e8468-214">For managed applications, a CMS EnvelopedData blob can be detected as any value that is passed to <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.</span></span>

<span data-ttu-id="e8468-215">Yerel uygulamalar için bir CMS EnvelopedData blob bir CMS tanıtıcı sağlanan herhangi bir değer olarak algılanabilir [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) olan kaynaklanan [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) olduğu `CMSG_ENVELOPED` ve/veya CMS tanıtıcısı Daha sonra gönderilen bir `CMSG_CTRL_DECRYPT` yönerge aracılığıyla [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol).</span><span class="sxs-lookup"><span data-stu-id="e8468-215">For native applications, a CMS EnvelopedData blob can be detected as any value provided to a CMS handle via [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) whose resulting [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) is `CMSG_ENVELOPED` and/or the CMS handle is later sent a `CMSG_CTRL_DECRYPT` instruction via [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol).</span></span>

## <a name="vulnerable-code-example---managed"></a><span data-ttu-id="e8468-216">Güvenlik açığı kod örneği - yönetilen</span><span class="sxs-lookup"><span data-stu-id="e8468-216">Vulnerable code example - managed</span></span>

<span data-ttu-id="e8468-217">Bu yöntem bir tanımlama bilgisi okur ve bunun şifresini çözer ve hiçbir veri bütünlüğü denetimi tarafından görülebilir.</span><span class="sxs-lookup"><span data-stu-id="e8468-217">This method reads a cookie and decrypts it and no data integrity check is visible.</span></span> <span data-ttu-id="e8468-218">Bu nedenle, bu yöntem tarafından okunan bir tanımlama bilgisinin içeriğinin aldığı kullanıcı tarafından veya şifrelenmiş bir tanımlama bilgisi değeri elde herhangi bir saldırgan tarafından saldırıya.</span><span class="sxs-lookup"><span data-stu-id="e8468-218">Therefore, the contents of a cookie that is read by this method can be attacked by the user who received it, or by any attacker who has obtained the encrypted cookie value.</span></span>

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

## <a name="example-code-following-recommended-practices---managed"></a><span data-ttu-id="e8468-219">Önerilen uygulamalar - yönetilen örnek kodu aşağıdaki</span><span class="sxs-lookup"><span data-stu-id="e8468-219">Example code following recommended practices - managed</span></span>

<span data-ttu-id="e8468-220">Aşağıdaki örnek kod bir standart ileti biçimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e8468-220">The following sample code uses a non-standard message format of</span></span>

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

<span data-ttu-id="e8468-221">Burada `cipher_algorithm_id` ve `hmac_algorithm_id` algoritması tanımlayıcılardır yerel uygulama (standart) bu algoritmaları temsillerini.</span><span class="sxs-lookup"><span data-stu-id="e8468-221">where the `cipher_algorithm_id` and `hmac_algorithm_id` algorithm identifiers are application-local (non-standard) representations of those algorithms.</span></span> <span data-ttu-id="e8468-222">Bu tanımlayıcılar, var olan bir Mesajlaşma Protokolü yerine diğer bölümlerinde çıplak bir birleştirilmiş bytestream mantıklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e8468-222">These identifiers may make sense in other parts of your existing messaging protocol instead of as a bare concatenated bytestream.</span></span>

<span data-ttu-id="e8468-223">Bu örnek, tek bir ana anahtarı hem bir şifreleme anahtarı hem de bir HMAC anahtarı türetmek için de kullanır.</span><span class="sxs-lookup"><span data-stu-id="e8468-223">This example also uses a single master key to derive both an encryption key and an HMAC key.</span></span> <span data-ttu-id="e8468-224">Bu kolaylık her ikisi de tek Anahtarlanan çift Anahtarlanan bir uygulamaya ve iki anahtar olarak farklı değerler tutma teşvik etmek için bir uygulamayı kapatmak için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e8468-224">This is provided both as a convenience for turning a singly-keyed application into a dual-keyed application, and to encourage keeping the two keys as different values.</span></span> <span data-ttu-id="e8468-225">Daha fazla eşitleme dışı şifreleme anahtarını ve HMAC anahtarı alınamıyor garanti eder.</span><span class="sxs-lookup"><span data-stu-id="e8468-225">It further guarantees that the HMAC key and encryption key can't get out of synchronization.</span></span>

<span data-ttu-id="e8468-226">Bu örnek kabul etmeyen bir <xref:System.IO.Stream> şifreleme veya şifre çözme.</span><span class="sxs-lookup"><span data-stu-id="e8468-226">This sample doesn't accept a <xref:System.IO.Stream> for either encryption or decryption.</span></span> <span data-ttu-id="e8468-227">Geçerli veri biçimi yaptığı bir geçişli zor şifrelemek için `hmac_tag` değeri önündeki şifreler.</span><span class="sxs-lookup"><span data-stu-id="e8468-227">The current data format makes one-pass encrypt difficult because the `hmac_tag` value precedes the ciphertext.</span></span> <span data-ttu-id="e8468-228">Ancak, ayrıştırıcının daha basit tutmaya başında tuttuğundan, tüm sabit boyutlu öğeleri bu biçim seçildi.</span><span class="sxs-lookup"><span data-stu-id="e8468-228">However, this format was chosen because it keeps all of the fixed-size elements at the beginning to keep the parser simpler.</span></span> <span data-ttu-id="e8468-229">Bir uygulayan GetHashAndReset arayın ve sonuç TransformFinalBlock çağırmadan önce doğrulamak için dikkatli olmalıdır ancak bu veri biçimiyle bir geçişli şifresini çözme mümkündür.</span><span class="sxs-lookup"><span data-stu-id="e8468-229">With this data format, one-pass decrypt is possible, though an implementer is cautioned to call GetHashAndReset and verify the result before calling TransformFinalBlock.</span></span> <span data-ttu-id="e8468-230">Akış şifreleme önemliyse, farklı bir AE modu gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="e8468-230">If streaming encryption is important, then a different AE mode may be required.</span></span>

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
