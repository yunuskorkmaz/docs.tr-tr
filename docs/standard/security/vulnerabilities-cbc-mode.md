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
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a><span data-ttu-id="5468c-103">Doldurmayı kullanarak CBC modunda simetrik şifre çözmedeki zamanlama açıkları</span><span class="sxs-lookup"><span data-stu-id="5468c-103">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>

<span data-ttu-id="5468c-104">Microsoft, çok özel durumlar dışında, doğrulanabilir dolgu uygulandığında, doğrulanabilir dolgu uygulaması uygulandığında, şifreleme-Blok Zincirleme (CBC) modu ile şifrelenmiş verilerin şifresini çözmenin artık güvenli olmadığına inanıyor Koşul -larda.</span><span class="sxs-lookup"><span data-stu-id="5468c-104">Microsoft believes that it's no longer safe to decrypt data encrypted with the Cipher-Block-Chaining (CBC) mode of symmetric encryption when verifiable padding has been applied without first ensuring the integrity of the ciphertext, except for very specific circumstances.</span></span> <span data-ttu-id="5468c-105">Bu yargı şu anda bilinen kriptografik araştırmaya dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5468c-105">This judgement is based on currently known cryptographic research.</span></span>

## <a name="introduction"></a><span data-ttu-id="5468c-106">Giriş</span><span class="sxs-lookup"><span data-stu-id="5468c-106">Introduction</span></span>

<span data-ttu-id="5468c-107">Dolgu oracle saldırısı, saldırganın anahtarı bilmeden verilerin içeriğini çözmesini sağlayan şifrelenmiş verilere karşı bir saldırı türüdür.</span><span class="sxs-lookup"><span data-stu-id="5468c-107">A padding oracle attack is a type of attack against encrypted data that allows the attacker to decrypt the contents of the data, without knowing the key.</span></span>

<span data-ttu-id="5468c-108">Bir kahin, saldırgana yürüttüldettikleri eylemin doğru olup olmadığı hakkında bilgi veren bir "tell" anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5468c-108">An oracle refers to a "tell" which gives an attacker information about whether the action they're executing is correct or not.</span></span> <span data-ttu-id="5468c-109">Bir çocukla tahta veya kart oyunu oynadığınızı düşünün.</span><span class="sxs-lookup"><span data-stu-id="5468c-109">Imagine playing a board or card game with a child.</span></span> <span data-ttu-id="5468c-110">Yüzleri büyük bir gülümsemeyle parlıyorçünkü iyi bir hamle yapmak üzere olduklarını düşündükleri nde, bu bir kahindir.</span><span class="sxs-lookup"><span data-stu-id="5468c-110">When their face lights up with a big smile because they think they're about to make a good move, that's an oracle.</span></span> <span data-ttu-id="5468c-111">Siz, rakip olarak, bir sonraki hamlenizi uygun bir şekilde planlamak için bu kahini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5468c-111">You, as the opponent, can use this oracle to plan your next move appropriately.</span></span>

<span data-ttu-id="5468c-112">Dolgu belirli bir şifreleme terimidir.</span><span class="sxs-lookup"><span data-stu-id="5468c-112">Padding is a specific cryptographic term.</span></span> <span data-ttu-id="5468c-113">Verilerinizi şifrelemek için kullanılan algoritmalar olan bazı şifreler, her bloğun sabit boyutta olduğu veri blokları üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="5468c-113">Some ciphers, which are the algorithms used to encrypt your data, work on blocks of data where each block is a fixed size.</span></span> <span data-ttu-id="5468c-114">Şifrelemek istediğiniz veriler blokları doldurmak için doğru boyutta değilse, verileriniz bunu yapana kadar doldurulur.</span><span class="sxs-lookup"><span data-stu-id="5468c-114">If the data you want to encrypt isn't the right size to fill the blocks, your data is padded until it does.</span></span> <span data-ttu-id="5468c-115">Dolgu birçok formları, orijinal giriş doğru boyutta olsa bile, dolgu her zaman mevcut olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5468c-115">Many forms of padding require that padding to always be present, even if the original input was of the right size.</span></span> <span data-ttu-id="5468c-116">Bu, dolgunun şifre çözme üzerine her zaman güvenli bir şekilde kaldırılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5468c-116">This allows the padding to always be safely removed upon decryption.</span></span>

<span data-ttu-id="5468c-117">İki şeyi bir araya getirerek, bir dolgu kahini ile bir yazılım uygulaması, şifresi çözülmüş verilerin geçerli dolguya sahip olup olmadığını ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="5468c-117">Putting the two things together, a software implementation with a padding oracle reveals whether decrypted data has valid padding.</span></span> <span data-ttu-id="5468c-118">Kahin, geçersiz bir bloğun aksine geçerli bir bloğu işlemek için ölçülebilir derecede farklı bir zaman almak gibi "Geçersiz dolgu" yazan bir değeri döndürmek kadar basit bir şey olabilir.</span><span class="sxs-lookup"><span data-stu-id="5468c-118">The oracle could be something as simple as returning a value that says "Invalid padding" or something more complicated like taking a measurably different time to process a valid block as opposed to an invalid block.</span></span>

<span data-ttu-id="5468c-119">Blok tabanlı şifrelemeler, ilk bloktaki verilerin ikinci bloktaki verilerle ilişkisini belirleyen mod adı verilen başka bir özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5468c-119">Block-based ciphers have another property, called the mode, which determines the relationship of data in the first block to the data in the second block, and so on.</span></span> <span data-ttu-id="5468c-120">En sık kullanılan modlardan biri CBC'dir.</span><span class="sxs-lookup"><span data-stu-id="5468c-120">One of the most commonly used modes is CBC.</span></span> <span data-ttu-id="5468c-121">CBC, Başlangıç Vektörü (IV) olarak bilinen bir başlangıç rasgele bloğu tanıtır ve önceki bloğu statik şifreleme nin sonucuyla birleştirerek aynı iletiyi aynı anahtarla şifrelemenin her zaman aynı şifreli çıktıyı oluşturmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5468c-121">CBC introduces an initial random block, known as the Initialization Vector (IV), and combines the previous block with the result of static encryption to make it such that encrypting the same message with the same key doesn't always produce the same encrypted output.</span></span>

<span data-ttu-id="5468c-122">Bir saldırgan, CBC verilerinin nasıl yapılandırıldığıyla birlikte, oracle'ı ortaya çıkaran koda biraz değiştirilmiş iletiler göndermek ve oracle verilerin doğru olduğunu söyleyene kadar veri göndermeye devam etmek için bir dolgu kahini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="5468c-122">An attacker can use a padding oracle, in combination with how CBC data is structured, to send slightly changed messages to the code that exposes the oracle, and keep sending data until the oracle tells them the data is correct.</span></span> <span data-ttu-id="5468c-123">Bu yanıttan, saldırgan ileti bayt byşifresini çözebilir.</span><span class="sxs-lookup"><span data-stu-id="5468c-123">From this response, the attacker can decrypt the message byte by byte.</span></span>

<span data-ttu-id="5468c-124">Modern bilgisayar ağları, bir saldırganın uzak sistemlerde yürütme süresi nde çok küçük (0,1 ms'den az) farklılıkları algılayabileceği kadar yüksek kalitededir.</span><span class="sxs-lookup"><span data-stu-id="5468c-124">Modern computer networks are of such high quality that an attacker can detect very small (less than 0.1 ms) differences in execution time on remote systems.</span></span><span data-ttu-id="5468c-125">Başarılı bir şifre çözmenin ancak verilerle değiştirilmediği zaman gerçekleşebileceğini varsayan uygulamalar, başarılı ve başarısız şifre çözme farklılıklarını gözlemlemek üzere tasarlanmış araçlardan gelen saldırılara karşı savunmasız olabilir.</span><span class="sxs-lookup"><span data-stu-id="5468c-125"> Applications that are assuming that a successful decryption can only happen when the data wasn't tampered with may be vulnerable to attack from tools that are designed to observe differences in successful and unsuccessful decryption.</span></span> <span data-ttu-id="5468c-126">Bu zamanlama farkı bazı dillerde veya kütüphanelerde diğerlerinden daha önemli olsa da, uygulamanın hataya yanıtı dikkate alındığında bunun tüm diller ve kitaplıklar için pratik bir tehdit olduğuna inanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5468c-126">While this timing difference may be more significant in some languages or libraries than others, it's now believed that this is a practical threat for all languages and libraries when the application's response to failure is taken into account.</span></span>

<span data-ttu-id="5468c-127">Bu saldırı, şifrelenmiş verileri değiştirme ve sonucu kahinle test etme yeteneğine dayanır.</span><span class="sxs-lookup"><span data-stu-id="5468c-127">This attack relies on the ability to change the encrypted data and test the result with the oracle.</span></span> <span data-ttu-id="5468c-128">Saldırıyı tamamen azaltmanın tek yolu, şifrelenmiş verilerdeki değişiklikleri algılamak ve saldırı yla ilgili herhangi bir eylemde bulunmaktan reddetmektir.</span><span class="sxs-lookup"><span data-stu-id="5468c-128">The only way to fully mitigate the attack is to detect changes to the encrypted data and refuse to perform any actions on it.</span></span> <span data-ttu-id="5468c-129">Bunu yapmanın standart yolu, veriler için bir imza oluşturmak ve herhangi bir işlem gerçekleştirilmeden önce bu imzayı doğrulamaktır.</span><span class="sxs-lookup"><span data-stu-id="5468c-129">The standard way to do this is to create a signature for the data and validate that signature before any operations are performed.</span></span> <span data-ttu-id="5468c-130">İmza doğrulanabilir olmalıdır, saldırgan tarafından oluşturulamaz, aksi takdirde şifrelenmiş verileri değiştirir, sonra değiştirilen verilere dayalı yeni bir imza hesaplar.</span><span class="sxs-lookup"><span data-stu-id="5468c-130">The signature must be verifiable, it cannot be created by the attacker, otherwise they'd change the encrypted data, then compute a new signature based on the changed data.</span></span> <span data-ttu-id="5468c-131">Sık kullanılan bir tür uygun imza, anahtarlı karma ileti kimlik doğrulama kodu (HMAC) olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="5468c-131">One common type of appropriate signature is known as a keyed-hash message authentication code (HMAC).</span></span> <span data-ttu-id="5468c-132">Bir HMAC, yalnızca HMAC'yi üreten kişi ve onu doğrulayan kişi tarafından bilinen gizli bir anahtar alması açısından bir kontrolumdan farklıdır.</span><span class="sxs-lookup"><span data-stu-id="5468c-132">An HMAC differs from a checksum in that it takes a secret key, known only to the person producing the HMAC and to the person validating it.</span></span> <span data-ttu-id="5468c-133">Anahtara sahip olmadan doğru bir HMAC üretemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="5468c-133">Without possession of the key, you can't produce a correct HMAC.</span></span> <span data-ttu-id="5468c-134">Verilerinizi aldığınızda, şifrelenmiş verileri alır, sizin ve gönderenin paylaştığı gizli anahtarı kullanarak HMAC'yi bağımsız olarak hesaplar, ardından gönderdikleri HMAC'yi hesapladığınız verilerle karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="5468c-134">When you receive your data, you'd take the encrypted data, independently compute the HMAC using the secret key you and the sender share, then compare the HMAC they sent against the one you computed.</span></span> <span data-ttu-id="5468c-135">Bu karşılaştırma sabit bir zaman olmalıdır, aksi takdirde farklı bir saldırı türüne izin veren başka bir algılanabilir kahin eklediniz.</span><span class="sxs-lookup"><span data-stu-id="5468c-135">This comparison must be constant time, otherwise you've added another detectable oracle, allowing a different type of attack.</span></span>

<span data-ttu-id="5468c-136">Özetle, yastıklı CBC blok şifrelerini güvenli bir şekilde kullanmak için, verilerin şifresini çözmeye çalışmadan önce sabit bir zaman karşılaştırması kullanarak doğruladığınız bir HMAC (veya başka bir veri bütünlüğü denetimi) ile birleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5468c-136">In summary, to use padded CBC block ciphers safely, you must combine them with an HMAC (or another data integrity check) that you validate using a constant time comparison before trying to decrypt the data.</span></span> <span data-ttu-id="5468c-137">Değiştirilen tüm iletilerin yanıt vermek için aynı miktarda zaman aldığı için, saldırı önlenir.</span><span class="sxs-lookup"><span data-stu-id="5468c-137">Since all altered messages take the same amount time to produce a response, the attack is prevented.</span></span>

## <a name="who-is-vulnerable"></a><span data-ttu-id="5468c-138">Kimler savunmasız</span><span class="sxs-lookup"><span data-stu-id="5468c-138">Who is vulnerable</span></span>

<span data-ttu-id="5468c-139">Bu güvenlik açığı, kendi şifreleme ve şifre çözme gerçekleştiren hem yönetilen hem de yerel uygulamalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5468c-139">This vulnerability applies to both managed and native applications that are performing their own encryption and decryption.</span></span> <span data-ttu-id="5468c-140">Bu, örneğin içerir:</span><span class="sxs-lookup"><span data-stu-id="5468c-140">This includes, for example:</span></span>

- <span data-ttu-id="5468c-141">Sunucuda daha sonra şifre çözme için bir çerez şifreleyen bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="5468c-141">An application that encrypts a cookie for later decryption on the server.</span></span>
- <span data-ttu-id="5468c-142">Kullanıcıların, sütunları daha sonra şifresi çözülmüş bir tabloya veri ekleme olanağı sağlayan bir veritabanı uygulaması.</span><span class="sxs-lookup"><span data-stu-id="5468c-142">A database application that provides the ability for users to insert data into a table whose columns are later decrypted.</span></span>
- <span data-ttu-id="5468c-143">Aktarım sırasındaverileri korumak için paylaşılan bir anahtar kullanarak şifrelemeye dayanan bir veri aktarım uygulaması.</span><span class="sxs-lookup"><span data-stu-id="5468c-143">A data transfer application that relies on encryption using a shared key to protect the data in transit.</span></span>
- <span data-ttu-id="5468c-144">TLS tünelinde iletileri "içinde" şifreleyen ve şifresini çözen bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="5468c-144">An application that encrypts and decrypts messages "inside" the TLS tunnel.</span></span>

<span data-ttu-id="5468c-145">TLS'yi tek başına kullanmanın bu senaryolarda sizi koruyamayabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5468c-145">Note that using TLS alone may not protect you in these scenarios.</span></span>

<span data-ttu-id="5468c-146">Savunmasız bir uygulama:</span><span class="sxs-lookup"><span data-stu-id="5468c-146">A vulnerable application:</span></span>

- <span data-ttu-id="5468c-147">PKCS#7 veya ANSI X.923 gibi doğrulanabilir bir doldurma moduyla CBC şifreleme modunu kullanarak verilerin şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="5468c-147">Decrypts data using the CBC cipher mode with a verifiable padding mode, such as PKCS#7 or ANSI X.923.</span></span>
- <span data-ttu-id="5468c-148">Şifre çözmeyi veri bütünlüğü denetimi gerçekleştirmeden (MAC veya asimetrik dijital imza yoluyla) gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="5468c-148">Performs the decryption without having performed a data integrity check (via a MAC or an asymmetric digital signature).</span></span>

<span data-ttu-id="5468c-149">Bu, Şifreleme İleti Sözdizimi (PKCS#7/CMS) EnvelopedData yapısı gibi bu ilkel lerin üzerine soyutlamaların üzerine inşa edilmiş uygulamalar için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5468c-149">This also applies to applications built on top of abstractions over top of these primitives, such as the Cryptographic Message Syntax (PKCS#7/CMS) EnvelopedData structure.</span></span>

## <a name="related-areas-of-concern"></a><span data-ttu-id="5468c-150">İlgili ilgi alanları</span><span class="sxs-lookup"><span data-stu-id="5468c-150">Related areas of concern</span></span>

<span data-ttu-id="5468c-151">Araştırmalar, Microsoft'un, ileti iyi bilinen veya öngörülebilir altbilgi yapısına sahip olduğunda ISO 10126 eşdeğeri dolgu ile eklenen CBC iletileri konusunda daha fazla endişe duymasına yol açmıştır.</span><span class="sxs-lookup"><span data-stu-id="5468c-151">Research has led Microsoft to be further concerned about CBC messages that are padded with ISO 10126-equivalent padding when the message has a well-known or predictable footer structure.</span></span> <span data-ttu-id="5468c-152">Örneğin, W3C XML Şifreleme Sözdizimi ve İşleme Önerisi (xmlenc, EncryptedXml) kuralları altında hazırlanan içerik.</span><span class="sxs-lookup"><span data-stu-id="5468c-152">For example, content prepared under the rules of the W3C XML Encryption Syntax and Processing Recommendation (xmlenc, EncryptedXml).</span></span> <span data-ttu-id="5468c-153">İletiyi imzalamak için W3C kılavuzu sonra şifreleme kıvranmak o anda uygun kabul edilirken, Microsoft şimdi her zaman şifre-sonra-imza yapma önerir.</span><span class="sxs-lookup"><span data-stu-id="5468c-153">While the W3C guidance to sign the message then encrypt was considered appropriate at the time, Microsoft now recommends always doing encrypt-then-sign.</span></span>

<span data-ttu-id="5468c-154">Uygulama geliştiricileri, asimetrik bir anahtar la rasgele bir ileti arasında doğal bir güven ilişkisi olmadığından, asimetrik imza anahtarının uygulanabilirliğini doğrulamakonusunda her zaman dikkatli olmalıdırlar.</span><span class="sxs-lookup"><span data-stu-id="5468c-154">Application developers should always be mindful of verifying the applicability of an asymmetric signature key, as there's no inherent trust relationship between an asymmetric key and an arbitrary message.</span></span>

## <a name="details"></a><span data-ttu-id="5468c-155">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5468c-155">Details</span></span>

<span data-ttu-id="5468c-156">Tarihsel olarak, HMAC veya RSA imzaları gibi araçları kullanarak önemli verileri şifrelemenin ve doğrulamanın önemli olduğu konusunda fikir birliği vardır.</span><span class="sxs-lookup"><span data-stu-id="5468c-156">Historically, there has been consensus that it's important to both encrypt and authenticate important data, using means such as HMAC or RSA signatures.</span></span> <span data-ttu-id="5468c-157">Ancak, şifreleme ve kimlik doğrulama işlemlerinin nasıl sıralandığıkonusunda daha az net kılavuz lar olmuştur.</span><span class="sxs-lookup"><span data-stu-id="5468c-157">However, there has been less clear guidance as to how to sequence the encryption and authentication operations.</span></span> <span data-ttu-id="5468c-158">Bu makalede ayrıntılı güvenlik açığı nedeniyle, Microsoft'un kılavuzu artık her zaman "şifrele-sonra-işareti" paradigmasını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="5468c-158">Due to the vulnerability detailed in this article, Microsoft's guidance is now to always use the "encrypt-then-sign" paradigm.</span></span> <span data-ttu-id="5468c-159">Diğer bir şey, önce verileri simetrik bir anahtar kullanarak şifreleyin, ardından şifre metni (şifrelenmiş veriler) üzerinde bir MAC veya asimetrik imza hesaplayın.</span><span class="sxs-lookup"><span data-stu-id="5468c-159">That is, first encrypt data using a symmetric key, then compute a MAC or asymmetric signature over the ciphertext (encrypted data).</span></span> <span data-ttu-id="5468c-160">Verilerin şifresini çözerken, ters icra edin.</span><span class="sxs-lookup"><span data-stu-id="5468c-160">When decrypting data, perform the reverse.</span></span> <span data-ttu-id="5468c-161">Önce, MAC'i veya şifreleme metninin imzasını onaylayın, ardından şifresini çözün.</span><span class="sxs-lookup"><span data-stu-id="5468c-161">First, confirm the MAC or signature of the ciphertext, then decrypt it.</span></span>

<span data-ttu-id="5468c-162">"Dolgu oracle saldırıları" olarak bilinen güvenlik açıkları sınıfının 10 yılı aşkın bir süredir var olduğu bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="5468c-162">A class of vulnerabilities known as "padding oracle attacks" have been known to exist for over 10 years.</span></span> <span data-ttu-id="5468c-163">Bu güvenlik açıkları, bir saldırganın veri bloğu başına en fazla 4096 deneme kullanarak AES ve 3DES gibi simetrik blok algoritmaları tarafından şifrelenmiş verilerin şifresini çözmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5468c-163">These vulnerabilities allow an attacker to decrypt data encrypted by symmetric block algorithms, such as AES and 3DES, using no more than 4096 attempts per block of data.</span></span> <span data-ttu-id="5468c-164">Bu güvenlik açıkları, blok şifrelerinin en sık sonunda doğrulanabilir dolgu verileriyle kullanıldığı gerçeğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5468c-164">These vulnerabilities make use of the fact that block ciphers are most frequently used with verifiable padding data at the end.</span></span> <span data-ttu-id="5468c-165">Bir saldırganın şifreleme metnini kurcalayıp, kurcalamanın sonundaki dolgu biçiminde bir hataya neden olup olmadığını öğrenebildiği tespit edildi, saldırgan verilerin şifresini çözebilir.</span><span class="sxs-lookup"><span data-stu-id="5468c-165">It was found that if an attacker can tamper with ciphertext and find out whether the tampering caused an error in the format of the padding at the end, the attacker can decrypt the data.</span></span>

<span data-ttu-id="5468c-166">Başlangıçta, pratik saldırılar, ASP.NET güvenlik açığı [MS10-070](/security-updates/SecurityBulletins/2010/ms10-070)gibi dolgunun geçerli olup olmadığına bağlı olarak farklı hata kodları döndürecek hizmetlere dayanıyordu.</span><span class="sxs-lookup"><span data-stu-id="5468c-166">Initially, practical attacks were based on services that would return different error codes based on whether padding was valid, such as the ASP.NET vulnerability [MS10-070](/security-updates/SecurityBulletins/2010/ms10-070).</span></span> <span data-ttu-id="5468c-167">Ancak Microsoft, geçerli ve geçersiz dolgu işleme arasındaki zamanlama farklılıklarını kullanarak benzer saldırılar gerçekleştirmenin pratik olduğuna inanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5468c-167">However, Microsoft now believes that it's practical to conduct similar attacks using only the differences in timing between processing valid and invalid padding.</span></span>

<span data-ttu-id="5468c-168">Şifreleme düzeninde bir imza istihdam edilmesi ve imza doğrulamasının belirli bir veri uzunluğu için sabit bir çalışma süresiyle gerçekleştirilmesi koşuluyla (içerikten bağımsız olarak), veri bütünlüğü bir [yan kanal](https://en.wikipedia.org/wiki/Side-channel_attack)üzerinden saldırgana herhangi bir bilgi yayan olmadan doğrulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5468c-168">Provided that the encryption scheme employs a signature and that the signature verification is performed with a fixed runtime for a given length of data (irrespective of the contents), the data integrity can be verified without emitting any information to an attacker via a [side channel](https://en.wikipedia.org/wiki/Side-channel_attack).</span></span> <span data-ttu-id="5468c-169">Bütünlük denetimi değiştirilmiş iletileri reddettiğinden, dolgu oracle tehdidi azaltılır.</span><span class="sxs-lookup"><span data-stu-id="5468c-169">Since the integrity check rejects any tampered messages, the padding oracle threat is mitigated.</span></span>

## <a name="guidance"></a><span data-ttu-id="5468c-170">Rehber</span><span class="sxs-lookup"><span data-stu-id="5468c-170">Guidance</span></span>

<span data-ttu-id="5468c-171">Her şeyden önce Microsoft, gizlilik gerektiren tüm verilerin Secure Sockets Layer (SSL) yerine geçen Transport Layer Security (TLS) üzerinden iletilmesini önerir.</span><span class="sxs-lookup"><span data-stu-id="5468c-171">First and foremost, Microsoft recommends that any data that has confidentiality needs be transmitted over Transport Layer Security (TLS), the successor to Secure Sockets Layer (SSL).</span></span>

<span data-ttu-id="5468c-172">Ardından, uygulamanızı şu şekilde analiz edin:</span><span class="sxs-lookup"><span data-stu-id="5468c-172">Next, analyze your application to:</span></span>

- <span data-ttu-id="5468c-173">Kullandığınız şifrelemeyi tam olarak ve kullandığınız platformlar ve API'ler tarafından hangi şifrelemenin sağlandığını anlayın.</span><span class="sxs-lookup"><span data-stu-id="5468c-173">Understand precisely what encryption you're performing and what encryption is being provided by the platforms and APIs you're using.</span></span>
- <span data-ttu-id="5468c-174">CBC modunda, AES ve 3DES gibi simetrik [blok şifreleme algoritmasının](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers)her katmanındaki her kullanımda gizli anahtarlı veri bütünlüğü denetimi (asimetrik imza, HMAC veya şifreleme modunu GCM veya CCM gibi [kimlik doğrulamalı](https://en.wikipedia.org/wiki/Authenticated_encryption) şifreleme (AE) moduna değiştirmek için bir dizi kullanım da dahil olun.</span><span class="sxs-lookup"><span data-stu-id="5468c-174">Be certain that each usage at each layer of a symmetric [block cipher algorithm](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), such as AES and 3DES, in CBC mode incorporate the use of a secret-keyed data integrity check (an asymmetric signature, an HMAC, or to change the cipher mode to an [authenticated encryption](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE) mode such as GCM or CCM).</span></span>

<span data-ttu-id="5468c-175">Geçerli araştırmaya dayanarak, kimlik doğrulama ve şifreleme adımları AE olmayan şifreleme modları için bağımsız olarak gerçekleştirildiğinde, şifreleme metninin (şifreleme-sonra işareti) doğrulanmasının en iyi genel seçenek olduğuna inanılır.</span><span class="sxs-lookup"><span data-stu-id="5468c-175">Based on the current research, it's generally believed that when the authentication and encryption steps are performed independently for non-AE modes of encryption, authenticating the ciphertext (encrypt-then-sign) is the best general option.</span></span> <span data-ttu-id="5468c-176">Ancak, şifrelemeye tek boyutlu uygun doğru bir cevap yoktur ve bu genelleme profesyonel bir kriptografın tavsiyeettiği kadar iyi değildir.</span><span class="sxs-lookup"><span data-stu-id="5468c-176">However, there's no one-size-fits-all correct answer to cryptography and this generalization isn't as good as directed advice from a professional cryptographer.</span></span>

<span data-ttu-id="5468c-177">İleti biçimini değiştiremeyen ancak kimlik doğrulamalı CBC şifresini çözemeyen uygulamaların aşağıdakiler gibi azaltıcı etkenler dahil etmeye çalışması teşvik edilir:</span><span class="sxs-lookup"><span data-stu-id="5468c-177">Applications that are unable to change their messaging format but perform unauthenticated CBC decryption are encouraged to try to incorporate mitigations such as:</span></span>

- <span data-ttu-id="5468c-178">Şifre çözücünün dolguyu doğrulamasına veya kaldırmasına izin vermeden şifreyi çöz:</span><span class="sxs-lookup"><span data-stu-id="5468c-178">Decrypt without allowing the decryptor to verify or remove padding:</span></span>
  - <span data-ttu-id="5468c-179">Uygulanan herhangi bir dolgu hala kaldırılması veya göz ardı edilmesi gerekir, uygulamanıza yük taşıyorsanız.</span><span class="sxs-lookup"><span data-stu-id="5468c-179">Any padding that was applied still needs to be removed or ignored, you're moving the burden into your application.</span></span>
  - <span data-ttu-id="5468c-180">Bunun yararı, dolgu doğrulama ve kaldırma diğer uygulama veri doğrulama mantığına dahil edilebilir olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="5468c-180">The benefit is that the padding verification and removal can be incorporated into other application data verification logic.</span></span> <span data-ttu-id="5468c-181">Dolgu doğrulaması ve veri doğrulaması sürekli olarak yapılabiliyorsa, tehdit azalır.</span><span class="sxs-lookup"><span data-stu-id="5468c-181">If the padding verification and data verification can be done in constant time, the threat is reduced.</span></span>
  - <span data-ttu-id="5468c-182">Dolgu nun yorumlanması algılanan ileti uzunluğunu değiştirdiğinden, bu yaklaşımdan yayılan zamanlama bilgileri hala olabilir.</span><span class="sxs-lookup"><span data-stu-id="5468c-182">Since the interpretation of the padding changes the perceived message length, there may still be timing information emitted from this approach.</span></span>
- <span data-ttu-id="5468c-183">Şifre çözme doldurma modunu ISO10126 olarak değiştirin:</span><span class="sxs-lookup"><span data-stu-id="5468c-183">Change the decryption padding mode to ISO10126:</span></span>
  - <span data-ttu-id="5468c-184">ISO10126 şifre çözme dolgusu hem PKCS7 şifreleme dolgusu hem de ANSIX923 şifreleme dolgusu ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="5468c-184">ISO10126 decryption padding is compatible with both PKCS7 encryption padding and ANSIX923 encryption padding.</span></span>
  - <span data-ttu-id="5468c-185">Modu değiştirmek, dolgu oracle bilgisini tüm blok yerine 1 bayt'a düşürür.</span><span class="sxs-lookup"><span data-stu-id="5468c-185">Changing the mode reduces the padding oracle knowledge to 1 byte instead of the entire block.</span></span> <span data-ttu-id="5468c-186">Ancak, içeriğin kapanış XML öğesi gibi iyi bilinen bir altbilgi varsa, ilgili saldırılar iletinin geri kalanına saldırmaya devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="5468c-186">However, if the content has a well-known footer, such as a closing XML element, related attacks can continue to attack the rest of the message.</span></span>
  - <span data-ttu-id="5468c-187">Bu, saldırganın aynı düz metni farklı bir ileti dışofmemiyle birden çok kez şifrelenmesi için zorladığı durumlarda düz metin kurtarmayı da engellemez.</span><span class="sxs-lookup"><span data-stu-id="5468c-187">This also doesn't prevent plaintext recovery in situations where the attacker can coerce the same plaintext to be encrypted multiple times with a different message offset.</span></span>
- <span data-ttu-id="5468c-188">Zamanlama sinyalini azaltmak için şifre çözme çağrısının değerlendirmesini geçitle:</span><span class="sxs-lookup"><span data-stu-id="5468c-188">Gate the evaluation of a decryption call to dampen the timing signal:</span></span>
  - <span data-ttu-id="5468c-189">Bekleme süresinin hesaplanması, deşifre işleminin dolgu içeren herhangi bir veri kesimi için alacağı maksimum süreyi en az aşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5468c-189">The computation of hold time must have a minimum in excess of the maximum amount of time the decryption operation would take for any data segment that contains padding.</span></span>
  - <span data-ttu-id="5468c-190">Zaman [hesaplamaları, yüksek çözünürlüklü zaman damgaları edinme](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps)kılavuzuna göre,(roll-over/taşma ya da iki sistem zaman damgası (NTP ayarlama hatalarına tabi) çıkarılarak değil, <xref:System.Environment.TickCount?displayProperty=nameWithType> yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5468c-190">Time computations should be done according to the guidance in [Acquiring high-resolution time stamps](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps), not by using <xref:System.Environment.TickCount?displayProperty=nameWithType> (subject to roll-over/overflow) or subtracting two system timestamps (subject to NTP adjustment errors).</span></span>
  - <span data-ttu-id="5468c-191">Zaman hesaplamaları, yönetilen veya C++ uygulamalarındaki tüm olası özel durumlar da dahil olmak üzere şifre çözme işlemini de kapsamalıdır, sadece sonuna kadar yastıklanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5468c-191">Time computations must be inclusive of the decryption operation including all potential exceptions in managed or C++ applications, not just padded onto the end.</span></span>
  - <span data-ttu-id="5468c-192">Başarı veya başarısızlık henüz belirlenmişse, zamanlama kapısının süresi dolduğunda hatadöndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5468c-192">If success or failure has been determined yet, the timing gate needs to return failure when it expires.</span></span>
- <span data-ttu-id="5468c-193">Kimlik doğrulamamış şifre çözme gerçekleştiren hizmetlerin, "geçersiz" iletiler selini niçin geldiğini algılamak için yerinde izleme leri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5468c-193">Services that are performing unauthenticated decryption should have monitoring in place to detect that a flood of "invalid" messages has come through.</span></span>
  - <span data-ttu-id="5468c-194">Bu sinyalin hem yanlış pozitifleri (meşru olarak bozulmuş veriler) hem de yanlış negatifleri (saldırıyı tespitten kaçınmak için yeterince uzun bir süre boyunca yaydığını) taşıdığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5468c-194">Bear in mind that this signal carries both false positives (legitimately corrupted data) and false negatives (spreading out the attack over a sufficiently long time to evade detection).</span></span>

## <a name="finding-vulnerable-code---native-applications"></a><span data-ttu-id="5468c-195">Güvenlik açığı olan kodu bulma - yerel uygulamalar</span><span class="sxs-lookup"><span data-stu-id="5468c-195">Finding vulnerable code - native applications</span></span>

<span data-ttu-id="5468c-196">Windows Şifreleme: Yeni Nesil (CNG) kitaplığına karşı oluşturulmuş programlar için:</span><span class="sxs-lookup"><span data-stu-id="5468c-196">For programs built against the Windows Cryptography: Next Generation (CNG) library:</span></span>

- <span data-ttu-id="5468c-197">Şifre çözme çağrısı [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt)için , `BCRYPT_BLOCK_PADDING` bayrak belirterek.</span><span class="sxs-lookup"><span data-stu-id="5468c-197">The decryption call is to [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt), specifying the `BCRYPT_BLOCK_PADDING` flag.</span></span>
- <span data-ttu-id="5468c-198">Anahtar kolu [BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE) ayarlanmış [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) arayarak başlatılması `BCRYPT_CHAIN_MODE_CBC`olmuştur.</span><span class="sxs-lookup"><span data-stu-id="5468c-198">The key handle has been initialized by calling [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) with [BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE) set to `BCRYPT_CHAIN_MODE_CBC`.</span></span>
  - <span data-ttu-id="5468c-199">Varsayılan `BCRYPT_CHAIN_MODE_CBC` olduğu için, etkilenen kod `BCRYPT_CHAINING_MODE`için herhangi bir değer atamış olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="5468c-199">Since `BCRYPT_CHAIN_MODE_CBC` is the default, affected code may not have assigned any value for `BCRYPT_CHAINING_MODE`.</span></span>

<span data-ttu-id="5468c-200">Eski Windows Şifreleme API'sına karşı oluşturulmuş programlar için:</span><span class="sxs-lookup"><span data-stu-id="5468c-200">For programs built against the older Windows Cryptographic API:</span></span>

- <span data-ttu-id="5468c-201">Şifre çözme çağrısı ile [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) `Final=TRUE`için.</span><span class="sxs-lookup"><span data-stu-id="5468c-201">The decryption call is to [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) with `Final=TRUE`.</span></span>
- <span data-ttu-id="5468c-202">Anahtar kolu [cryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) KP_MODE [olarak](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam) ayarlanmış arayarak `CRYPT_MODE_CBC`başlatılması olmuştur.</span><span class="sxs-lookup"><span data-stu-id="5468c-202">The key handle has been initialized by calling [CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) with [KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam) set to `CRYPT_MODE_CBC`.</span></span>
  - <span data-ttu-id="5468c-203">Varsayılan `CRYPT_MODE_CBC` olduğu için, etkilenen kod `KP_MODE`için herhangi bir değer atamış olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="5468c-203">Since `CRYPT_MODE_CBC` is the default, affected code may not have assigned any value for `KP_MODE`.</span></span>

## <a name="finding-vulnerable-code---managed-applications"></a><span data-ttu-id="5468c-204">Güvenlik açığı kodu bulma - yönetilen uygulamalar</span><span class="sxs-lookup"><span data-stu-id="5468c-204">Finding vulnerable code - managed applications</span></span>

- <span data-ttu-id="5468c-205">Şifre çözme çağrısı <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> veya <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> üzerinde <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>yöntemler.</span><span class="sxs-lookup"><span data-stu-id="5468c-205">The decryption call is to the <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> or <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> methods on <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="5468c-206">Bu, .NET içinde aşağıdaki türetilmiş türleri içerir, ancak üçüncü taraf türleri de içerebilir:</span><span class="sxs-lookup"><span data-stu-id="5468c-206">This includes the following derived types within the .NET, but may also include third-party types:</span></span>
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
- <span data-ttu-id="5468c-207">Özellik <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>veya <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5468c-207">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, or <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="5468c-208">Varsayılan <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> olduğundan, etkilenen kod <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> özelliği hiç atamış olabilir.</span><span class="sxs-lookup"><span data-stu-id="5468c-208">Since <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property.</span></span>
- <span data-ttu-id="5468c-209">Özellik <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> ayarlandı<xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5468c-209">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span></span>
  - <span data-ttu-id="5468c-210">Varsayılan <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> olduğundan, etkilenen kod <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> özelliği hiç atamış olabilir.</span><span class="sxs-lookup"><span data-stu-id="5468c-210">Since <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property.</span></span>

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a><span data-ttu-id="5468c-211">Güvenlik açığı kodu bulma - şifreleme iletisözdizimi</span><span class="sxs-lookup"><span data-stu-id="5468c-211">Finding vulnerable code - cryptographic message syntax</span></span>

<span data-ttu-id="5468c-212">Şifreli içeriği AES'nin CBC modunu kullanan kimliği doğrulanmamış cms zarflı veri iletisi (2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) veya RC2 (1.2.840.113549.3.2) yanı sıra CBC modunda başka bir blok şifreleme algoritmaları kullanarak iletileri savunmasız.</span><span class="sxs-lookup"><span data-stu-id="5468c-212">An unauthenticated CMS EnvelopedData message whose encrypted content uses the CBC mode of AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) or RC2 (1.2.840.113549.3.2) is vulnerable, as well as messages using any other block cipher algorithms in CBC mode.</span></span>

<span data-ttu-id="5468c-213">Akış şifrelemeleri bu özel güvenlik açığına duyarlı olmasa da, Microsoft ContentEncryptionAlgorithm değerini inceleyerek verileri her zaman doğrulamasını önerir.</span><span class="sxs-lookup"><span data-stu-id="5468c-213">While stream ciphers aren't susceptible to this particular vulnerability, Microsoft recommends always authenticating the data over inspecting the ContentEncryptionAlgorithm value.</span></span>

<span data-ttu-id="5468c-214">Yönetilen uygulamalar için, cms envelopedData blob'a <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>geçirilen herhangi bir değer olarak algılanabilir.</span><span class="sxs-lookup"><span data-stu-id="5468c-214">For managed applications, a CMS EnvelopedData blob can be detected as any value that is passed to <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.</span></span>

<span data-ttu-id="5468c-215">Yerel uygulamalar için, bir CMS EnvelopedData blob, ortaya çıkan [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) `CMSG_ENVELOPED` ve/veya CMS kolu daha sonra [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol)üzerinden `CMSG_CTRL_DECRYPT` bir talimat gönderilir [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) üzerinden CMS koluna sağlanan herhangi bir değer olarak algılanabilir.</span><span class="sxs-lookup"><span data-stu-id="5468c-215">For native applications, a CMS EnvelopedData blob can be detected as any value provided to a CMS handle via [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) whose resulting [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) is `CMSG_ENVELOPED` and/or the CMS handle is later sent a `CMSG_CTRL_DECRYPT` instruction via [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol).</span></span>

## <a name="vulnerable-code-example---managed"></a><span data-ttu-id="5468c-216">Savunmasız kod örneği - yönetilen</span><span class="sxs-lookup"><span data-stu-id="5468c-216">Vulnerable code example - managed</span></span>

<span data-ttu-id="5468c-217">Bu yöntem bir çerez okur ve şifresini çözer ve hiçbir veri bütünlüğü denetimi görünür.</span><span class="sxs-lookup"><span data-stu-id="5468c-217">This method reads a cookie and decrypts it and no data integrity check is visible.</span></span> <span data-ttu-id="5468c-218">Bu nedenle, bu yöntemle okunan bir çerezin içeriği, bu çerezi alan kullanıcı veya şifrelenmiş çerez değerini elde eden herhangi bir saldırgan tarafından saldırıya uğrayabilir.</span><span class="sxs-lookup"><span data-stu-id="5468c-218">Therefore, the contents of a cookie that is read by this method can be attacked by the user who received it, or by any attacker who has obtained the encrypted cookie value.</span></span>

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

## <a name="example-code-following-recommended-practices---managed"></a><span data-ttu-id="5468c-219">Önerilen uygulamaları takip eden örnek kod - yönetilen</span><span class="sxs-lookup"><span data-stu-id="5468c-219">Example code following recommended practices - managed</span></span>

<span data-ttu-id="5468c-220">Aşağıdaki örnek kod, standart olmayan bir ileti biçimi kullanır</span><span class="sxs-lookup"><span data-stu-id="5468c-220">The following sample code uses a non-standard message format of</span></span>

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

<span data-ttu-id="5468c-221">`cipher_algorithm_id` ve `hmac_algorithm_id` algoritma tanımlayıcılarının bu algoritmaların uygulama yerel (standart olmayan) gösterimleri olduğu yer.</span><span class="sxs-lookup"><span data-stu-id="5468c-221">where the `cipher_algorithm_id` and `hmac_algorithm_id` algorithm identifiers are application-local (non-standard) representations of those algorithms.</span></span> <span data-ttu-id="5468c-222">Bu tanımlayıcılar, mevcut ileti iletişim günümüzde ki ileti nizaminin diğer bölümlerinde, çıplak bir şekilde bir bytestream olarak değil, anlamlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5468c-222">These identifiers may make sense in other parts of your existing messaging protocol instead of as a bare concatenated bytestream.</span></span>

<span data-ttu-id="5468c-223">Bu örnekte, hem şifreleme anahtarı hem de HMAC anahtarı elde etmek için tek bir ana anahtar da kullanır.</span><span class="sxs-lookup"><span data-stu-id="5468c-223">This example also uses a single master key to derive both an encryption key and an HMAC key.</span></span> <span data-ttu-id="5468c-224">Bu, hem tek tuşlu bir uygulamayı çift tuşlu bir uygulamaya dönüştürmek hem de iki anahtarı farklı değerler olarak tutmayı teşvik etmek için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="5468c-224">This is provided both as a convenience for turning a singly-keyed application into a dual-keyed application, and to encourage keeping the two keys as different values.</span></span> <span data-ttu-id="5468c-225">Ayrıca HMAC anahtarı ve şifreleme anahtarının senkronizasyondan çıkamalarını garanti eder.</span><span class="sxs-lookup"><span data-stu-id="5468c-225">It further guarantees that the HMAC key and encryption key can't get out of synchronization.</span></span>

<span data-ttu-id="5468c-226">Bu örnek şifreleme veya <xref:System.IO.Stream> şifre çözme için kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="5468c-226">This sample doesn't accept a <xref:System.IO.Stream> for either encryption or decryption.</span></span> <span data-ttu-id="5468c-227">Geçerli veri biçimi, tek geçişli `hmac_tag` şifrelemeyi zorlaştırır, çünkü değer şifreleme metninden önce gelir.</span><span class="sxs-lookup"><span data-stu-id="5468c-227">The current data format makes one-pass encrypt difficult because the `hmac_tag` value precedes the ciphertext.</span></span> <span data-ttu-id="5468c-228">Ancak, bu biçim, başlangıçta ki tüm sabit boyutlu öğeleri parser'ı daha basit tutmak için tuttuğundan seçildi.</span><span class="sxs-lookup"><span data-stu-id="5468c-228">However, this format was chosen because it keeps all of the fixed-size elements at the beginning to keep the parser simpler.</span></span> <span data-ttu-id="5468c-229">Bu veri biçimi yle, tek geçişli şifre çözme mümkündür, ancak bir uygulayıcı GetHashAndReset'i aramak ve TransformFinalBlock'u aramadan önce sonucu doğrulamak için uyarılır.</span><span class="sxs-lookup"><span data-stu-id="5468c-229">With this data format, one-pass decrypt is possible, though an implementer is cautioned to call GetHashAndReset and verify the result before calling TransformFinalBlock.</span></span> <span data-ttu-id="5468c-230">Akış şifrelemesi önemliyse, farklı bir AE modu gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="5468c-230">If streaming encryption is important, then a different AE mode may be required.</span></span>

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
