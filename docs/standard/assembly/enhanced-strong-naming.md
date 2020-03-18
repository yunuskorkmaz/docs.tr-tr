---
title: Tanımlayıcı adlandırmayı iyileştirme
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
ms.openlocfilehash: 1d582513b10de88e4e5b9b9ef8c338599d6980f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141164"
---
# <a name="enhanced-strong-naming"></a><span data-ttu-id="5ec3d-102">Tanımlayıcı adlandırmayı iyileştirme</span><span class="sxs-lookup"><span data-stu-id="5ec3d-102">Enhanced strong naming</span></span>
<span data-ttu-id="5ec3d-103">Güçlü ad imzası, .NET Framework'de derlemeleri tanımlamak için bir kimlik mekanizmasıdır.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-103">A strong name signature is an identity mechanism in the .NET Framework for identifying assemblies.</span></span> <span data-ttu-id="5ec3d-104">Genellikle bir kaynaktan (imzalayan) alıcıya (doğrulayıcı) geçirilen verilerin bütünlüğünü doğrulamak için kullanılan ortak anahtarlı bir dijital imzadır.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-104">It is a public-key digital signature that is typically used to verify the integrity of data being passed from an originator (signer) to a recipient (verifier).</span></span> <span data-ttu-id="5ec3d-105">Bu imza, derleme için benzersiz bir kimlik olarak kullanılır ve derlemeye yapılan başvuruların belirsiz olmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-105">This signature is used as a unique identity for an assembly and ensures that references to the assembly are not ambiguous.</span></span> <span data-ttu-id="5ec3d-106">Derleme yapı işleminin bir parçası olarak imzalanır ve yüklendiğinde doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-106">The assembly is signed as part of the build process and then verified when it is loaded.</span></span>  
  
 <span data-ttu-id="5ec3d-107">Güçlü ad imzaları, kötü niyetli tarafların bir derlemeyi kurcalamasını ve ardından orijinal imzalayanın anahtarıyla derlemeyi yeniden imzalamasını önlemeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-107">Strong name signatures help prevent malicious parties from tampering with an assembly and then re-signing the assembly with the original signer’s key.</span></span> <span data-ttu-id="5ec3d-108">Ancak, güçlü ad anahtarları yayımcı hakkında güvenilir bir bilgi içermez veya sertifika hiyerarşisi içermez.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-108">However, strong name keys don’t contain any reliable information about the publisher, nor do they contain a certificate hierarchy.</span></span> <span data-ttu-id="5ec3d-109">Güçlü bir ad imzası, montajı imzalayan kişinin güvenilirliğini garanti etmez veya bu kişinin anahtarın yasal sahibi olup olmadığını göstermez; yalnızca anahtarın sahibinin montajı imzaladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-109">A strong name signature does not guarantee the trustworthiness of the person who signed the assembly or indicate whether that person was a legitimate owner of the key; it indicates only that the owner of the key signed the assembly.</span></span> <span data-ttu-id="5ec3d-110">Bu nedenle, üçüncü taraf koduna güvenmek için güvenlik doğrulayıcısı olarak güçlü bir ad imzası kullanmanızı önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-110">Therefore, we do not recommend using a strong name signature as a security validator for trusting third-party code.</span></span> <span data-ttu-id="5ec3d-111">Microsoft Authenticode, kodun kimliğini doğrulamanın önerilen yoludur.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-111">Microsoft Authenticode is the recommended way to authenticate code.</span></span>  
  
## <a name="limitations-of-conventional-strong-names"></a><span data-ttu-id="5ec3d-112">Geleneksel güçlü isimlerin sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="5ec3d-112">Limitations of conventional strong names</span></span>  
 <span data-ttu-id="5ec3d-113">.NET Framework 4.5'ten önceki sürümlerde kullanılan güçlü adlandırma teknolojisiaşağıdaki eksikliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="5ec3d-113">The strong naming technology used in versions before the .NET Framework 4.5 has the following shortcomings:</span></span>  
  
- <span data-ttu-id="5ec3d-114">Anahtarlar sürekli saldırı altındadır ve geliştirilmiş teknikler ve donanım, ortak bir anahtardan özel bir anahtarı çıkarmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-114">Keys are constantly under attack, and improved techniques and hardware make it easier to infer a private key from a public key.</span></span> <span data-ttu-id="5ec3d-115">Saldırılara karşı korumak için daha büyük tuşlar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-115">To guard against attacks, larger keys are necessary.</span></span> <span data-ttu-id="5ec3d-116">.NET Framework 4.5'ten önce .NET Framework sürümleri herhangi bir boyut tuşuyla (varsayılan boyut 1024 bittir) imzalama olanağı sağlar, ancak yeni bir anahtarla bir derlemeimzalama, derlemenin eski kimliğine başvuran tüm ikilileri kırar.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-116">.NET Framework versions before the .NET Framework 4.5 provide the ability to sign with any size key (the default size is 1024 bits), but signing an assembly with a new key breaks all binaries that reference the older identity of the assembly.</span></span> <span data-ttu-id="5ec3d-117">Bu nedenle, uyumluluğu korumak istiyorsanız, bir imzalama anahtarıboyutunu yükseltmek son derece zordur.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-117">Therefore, it is extremely difficult to upgrade the size of a signing key if you want to maintain compatibility.</span></span>  
  
- <span data-ttu-id="5ec3d-118">Güçlü ad imzalama yalnızca SHA-1 algoritmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-118">Strong name signing supports only the SHA-1 algorithm.</span></span> <span data-ttu-id="5ec3d-119">SHA-1 son zamanlarda güvenli karma uygulamalar için yetersiz olduğu tespit edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-119">SHA-1 has recently been found to be inadequate for secure hashing applications.</span></span> <span data-ttu-id="5ec3d-120">Bu nedenle, daha güçlü bir algoritma (SHA-256 veya daha büyük) gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-120">Therefore, a stronger algorithm (SHA-256 or greater) is necessary.</span></span> <span data-ttu-id="5ec3d-121">SHA-1'in FIPS uyumlu duruşunu kaybetmesi mümkündür, bu da yalnızca FIPS uyumlu yazılım ve algoritmaları kullanmayı seçenler için sorun teşkil eder.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-121">It is possible that SHA-1 will lose its FIPS-compliant standing, which would present problems for those who choose to use only FIPS-compliant software and algorithms.</span></span>  
  
## <a name="advantages-of-enhanced-strong-names"></a><span data-ttu-id="5ec3d-122">Gelişmiş güçlü isimlerin avantajları</span><span class="sxs-lookup"><span data-stu-id="5ec3d-122">Advantages of enhanced strong names</span></span>  
 <span data-ttu-id="5ec3d-123">Gelişmiş güçlü adların başlıca avantajları, önceden varolan güçlü adlarla uyumluluk ve bir kimliğin diğerine eşdeğer olduğunu iddia edebilme yeteneğidir:</span><span class="sxs-lookup"><span data-stu-id="5ec3d-123">The main advantages of enhanced strong names are compatibility with pre-existing strong names and the ability to claim that one identity is equivalent to another:</span></span>  
  
- <span data-ttu-id="5ec3d-124">Önceden varolan imzalı derlemelere sahip geliştiriciler, eski kimliklere başvuran derlemelerle uyumluluğu korurken kimliklerini SHA-2 algoritmalarına geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-124">Developers who have pre-existing signed assemblies can migrate their identities to the SHA-2 algorithms while maintaining compatibility with assemblies that reference the old identities.</span></span>  
  
- <span data-ttu-id="5ec3d-125">Yeni derlemeler oluşturan ve önceden varolan güçlü ad imzalarıyla ilgilenmeyen geliştiriciler, daha güvenli SHA-2 algoritmalarını kullanabilir ve derlemeleri her zaman olduğu gibi imzalayabilir.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-125">Developers who create new assemblies and are not concerned with pre-existing strong name signatures can use the more secure SHA-2 algorithms and sign the assemblies as they always have.</span></span>  
  
## <a name="use-enhanced-strong-names"></a><span data-ttu-id="5ec3d-126">Gelişmiş güçlü adlar kullanma</span><span class="sxs-lookup"><span data-stu-id="5ec3d-126">Use enhanced strong names</span></span>  
 <span data-ttu-id="5ec3d-127">Güçlü ad anahtarları imza anahtarı ve kimlik anahtarından oluşur.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-127">Strong name keys consist of a signature key and an identity key.</span></span> <span data-ttu-id="5ec3d-128">Derleme imza anahtarı ile imzalanır ve kimlik anahtarı ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-128">The assembly is signed with the signature key and is identified by the identity key.</span></span> <span data-ttu-id="5ec3d-129">.NET Framework 4.5'ten önce bu iki anahtar aynıydı.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-129">Prior to the .NET Framework 4.5, these two keys were identical.</span></span> <span data-ttu-id="5ec3d-130">.NET Framework 4.5 ile başlayarak, kimlik anahtarı önceki .NET Framework sürümlerinde olduğu gibi kalır, ancak imza anahtarı daha güçlü bir karma algoritması ile geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-130">Starting with the .NET Framework 4.5, the identity key remains the same as in earlier .NET Framework versions, but the signature key is enhanced with a stronger hash algorithm.</span></span> <span data-ttu-id="5ec3d-131">Buna ek olarak, imza anahtarı bir karşı imza oluşturmak için kimlik anahtarı ile imzalanır.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-131">In addition, the signature key is signed with the identity key to create a counter-signature.</span></span>  
  
 <span data-ttu-id="5ec3d-132">Öznitelik, <xref:System.Reflection.AssemblySignatureKeyAttribute> derleme meta verilerinin derleme kimliği için önceden varolan ortak anahtarı kullanmasına olanak tanır ve bu da eski derleme başvurularının çalışmaya devam etmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-132">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute enables the assembly metadata to use the pre-existing public key for assembly identity, which allows old assembly references to continue to work.</span></span>  <span data-ttu-id="5ec3d-133">Öznitelik, <xref:System.Reflection.AssemblySignatureKeyAttribute> yeni imza anahtarının sahibinin aynı zamanda eski kimlik anahtarının sahibi olduğundan emin olmak için karşı imzayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-133">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute uses the counter-signature to ensure that the owner of the new signature key is also the owner of the old identity key.</span></span>  
  
### <a name="sign-with-sha-2-without-key-migration"></a><span data-ttu-id="5ec3d-134">Anahtar geçişi olmadan SHA-2 ile imzalayın</span><span class="sxs-lookup"><span data-stu-id="5ec3d-134">Sign with SHA-2, without key migration</span></span>  
 <span data-ttu-id="5ec3d-135">Güçlü bir ad imzası geçirmeden bir derlemeyi imzalamak için komut isteminden aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="5ec3d-135">Run the following commands from a command prompt to sign an assembly without migrating a strong name signature:</span></span>  
  
1. <span data-ttu-id="5ec3d-136">Yeni kimlik anahtarını oluşturun (gerekirse).</span><span class="sxs-lookup"><span data-stu-id="5ec3d-136">Generate the new identity key (if necessary).</span></span>  
  
    ```console  
    sn -k IdentityKey.snk  
    ```  
  
2. <span data-ttu-id="5ec3d-137">Kimlik ortak anahtarını ayıklayın ve bu anahtarla imzalarken SHA-2 algoritmasının kullanılması gerektiğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-137">Extract the identity public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3. <span data-ttu-id="5ec3d-138">Kimlik ortak anahtar dosyasıyla montajı geciktirme işareti.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-138">Delay-sign the assembly with the identity public key file.</span></span>  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4. <span data-ttu-id="5ec3d-139">Tam kimlik anahtar çifti ile montajı yeniden imzalayın.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-139">Re-sign the assembly with the full identity key pair.</span></span>  
  
    ```console  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="sign-with-sha-2-with-key-migration"></a><span data-ttu-id="5ec3d-140">ANAHTAR geçişi ile SHA-2 ile imzalayın</span><span class="sxs-lookup"><span data-stu-id="5ec3d-140">Sign with SHA-2, with key migration</span></span>  
 <span data-ttu-id="5ec3d-141">Geçirilen güçlü ad imzası olan bir derlemeyi imzalamak için komut isteminden aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-141">Run the following commands from a command prompt to sign an assembly with a migrated strong name signature.</span></span>  
  
1. <span data-ttu-id="5ec3d-142">Kimlik ve imza anahtar çifti (gerekirse) oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-142">Generate an identity and signature key pair (if necessary).</span></span>  
  
    ```console  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2. <span data-ttu-id="5ec3d-143">İmza ortak anahtarını ayıklayın ve bu anahtarla imzalanırken SHA-2 algoritmasının kullanılması gerektiğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-143">Extract the signature public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```console  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3. <span data-ttu-id="5ec3d-144">Karşı imza oluşturan karma algoritmasını belirleyen kimlik ortak anahtarını ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-144">Extract the identity public key, which determines the hash algorithm that generates a counter-signature.</span></span>  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4. <span data-ttu-id="5ec3d-145">Bir <xref:System.Reflection.AssemblySignatureKeyAttribute> öznitelik için parametreleri oluşturun ve özniteliği derlemeye takın.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-145">Generate the parameters for a <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute, and attach the attribute to the assembly.</span></span>  
  
    ```console  
    sn -a IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  

    <span data-ttu-id="5ec3d-146">Bu, aşağıdakine benzer çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-146">This produces output similar to the following.</span></span>

    ```output
    Information for key migration attribute.
    (System.Reflection.AssemblySignatureKeyAttribute):
    publicKey=
    002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519
    d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936
    e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b4
    3893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a3
    4d153cdd

    counterSignature=
    e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91eb
    e1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8
    ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3
    ae5fec2c682e57b7442738
    ```

    <span data-ttu-id="5ec3d-147">Bu çıktı daha sonra bir AssemblySignatureKeyAttribute dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-147">This output can then be transformed into an AssemblySignatureKeyAttribute.</span></span>

    ```
    [assembly:System.Reflection.AssemblySignatureKeyAttribute(
    "002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b43893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a34d153cdd",
    "e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91ebe1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3ae5fec2c682e57b7442738"
    )]
    ```
  
5. <span data-ttu-id="5ec3d-148">Kimlik ortak anahtarıyla montajı geciktirme işareti.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-148">Delay-sign the assembly with the identity public key.</span></span>  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6. <span data-ttu-id="5ec3d-149">Tam imza anahtar çifti ile montaj imzalayın.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-149">Fully sign the assembly with the signature key pair.</span></span>  
  
    ```console  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5ec3d-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ec3d-150">See also</span></span>

- [<span data-ttu-id="5ec3d-151">Tanımlayıcı adlı derlemeler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="5ec3d-151">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
