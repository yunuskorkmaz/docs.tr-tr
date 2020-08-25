---
title: Tanımlayıcı adlandırmayı iyileştirme
description: .NET Framework derlemeler için geleneksel tanımlayıcı ad imzaları sınırlamaları vardır. Gelişmiş tanımlayıcı adlandırma hakkında bilgi edinin.
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
ms.openlocfilehash: f0160f033760582c914a0d64c21415e5e921d907
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811086"
---
# <a name="enhanced-strong-naming"></a><span data-ttu-id="ee156-104">Tanımlayıcı adlandırmayı iyileştirme</span><span class="sxs-lookup"><span data-stu-id="ee156-104">Enhanced strong naming</span></span>
<span data-ttu-id="ee156-105">Tanımlayıcı ad imzası, derlemeleri tanımlamak için .NET Framework bir kimlik mekanizmasıdır.</span><span class="sxs-lookup"><span data-stu-id="ee156-105">A strong name signature is an identity mechanism in the .NET Framework for identifying assemblies.</span></span> <span data-ttu-id="ee156-106">Genellikle bir oluşturana (imzalayan) bir alıcıya (Doğrulayıcı) geçirilen verilerin bütünlüğünü doğrulamak için kullanılan ortak anahtar dijital imzadır.</span><span class="sxs-lookup"><span data-stu-id="ee156-106">It is a public-key digital signature that is typically used to verify the integrity of data being passed from an originator (signer) to a recipient (verifier).</span></span> <span data-ttu-id="ee156-107">Bu imza, bir derleme için benzersiz bir kimlik olarak kullanılır ve derlemeye yapılan başvuruların belirsiz olmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee156-107">This signature is used as a unique identity for an assembly and ensures that references to the assembly are not ambiguous.</span></span> <span data-ttu-id="ee156-108">Derleme, derleme sürecinin bir parçası olarak imzalanır ve sonra yüklendiğinde doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="ee156-108">The assembly is signed as part of the build process and then verified when it is loaded.</span></span>  
  
 <span data-ttu-id="ee156-109">Tanımlayıcı ad imzaları kötü amaçlı tarafların bir bütünleştirilmiş koda müdahale etmelerini önlemeye yardımcı olur ve derlemeyi özgün imzalayan anahtarıyla yeniden imzalamasını önler.</span><span class="sxs-lookup"><span data-stu-id="ee156-109">Strong name signatures help prevent malicious parties from tampering with an assembly and then re-signing the assembly with the original signer’s key.</span></span> <span data-ttu-id="ee156-110">Ancak, tanımlayıcı ad anahtarları yayımcı hakkında güvenilir bilgiler içermez ve bir sertifika hiyerarşisi içermez.</span><span class="sxs-lookup"><span data-stu-id="ee156-110">However, strong name keys don’t contain any reliable information about the publisher, nor do they contain a certificate hierarchy.</span></span> <span data-ttu-id="ee156-111">Tanımlayıcı ad imzası, derlemeyi imzalayan kişinin güvenilirliğini garanti etmez veya bu kişinin, anahtarın meşru sahibi olup olmadığını belirtir; yalnızca anahtarın sahibinin derlemeyi imzaladığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ee156-111">A strong name signature does not guarantee the trustworthiness of the person who signed the assembly or indicate whether that person was a legitimate owner of the key; it indicates only that the owner of the key signed the assembly.</span></span> <span data-ttu-id="ee156-112">Bu nedenle, üçüncü taraf koda güvenmek için bir güvenlik doğrulayıcısı olarak tanımlayıcı ad imzası kullanılması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="ee156-112">Therefore, we do not recommend using a strong name signature as a security validator for trusting third-party code.</span></span> <span data-ttu-id="ee156-113">Microsoft Authenticode, kodun kimliğini doğrulamak için önerilen yoldur.</span><span class="sxs-lookup"><span data-stu-id="ee156-113">Microsoft Authenticode is the recommended way to authenticate code.</span></span>  
  
## <a name="limitations-of-conventional-strong-names"></a><span data-ttu-id="ee156-114">Geleneksel tanımlayıcı adların sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="ee156-114">Limitations of conventional strong names</span></span>  
 <span data-ttu-id="ee156-115">.NET Framework 4,5 ' den önceki sürümlerde kullanılan tanımlayıcı adlandırma teknolojisinin aşağıdaki eksiklikleri vardır:</span><span class="sxs-lookup"><span data-stu-id="ee156-115">The strong naming technology used in versions before the .NET Framework 4.5 has the following shortcomings:</span></span>  
  
- <span data-ttu-id="ee156-116">Anahtarlar sürekli saldırı aşamasındadır ve geliştirilmiş teknikler ve donanımlar, ortak anahtardan özel bir anahtar çıkarmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="ee156-116">Keys are constantly under attack, and improved techniques and hardware make it easier to infer a private key from a public key.</span></span> <span data-ttu-id="ee156-117">Saldırılara karşı koruma sağlamak için daha büyük anahtarlar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ee156-117">To guard against attacks, larger keys are necessary.</span></span> <span data-ttu-id="ee156-118">.NET Framework 4,5 ' den önceki sürümlerde .NET Framework, herhangi bir boyut anahtarıyla (varsayılan boyut 1024 bit) oturum açabilme olanağı sağlar, ancak yeni bir anahtarla bir derlemeyi imzalamak, derlemenin eski kimliğine başvuran tüm ikili dosyaları keser.</span><span class="sxs-lookup"><span data-stu-id="ee156-118">.NET Framework versions before the .NET Framework 4.5 provide the ability to sign with any size key (the default size is 1024 bits), but signing an assembly with a new key breaks all binaries that reference the older identity of the assembly.</span></span> <span data-ttu-id="ee156-119">Bu nedenle, uyumluluk sağlamak istiyorsanız İmzalama anahtarının boyutunu yükseltmek son derece zordur.</span><span class="sxs-lookup"><span data-stu-id="ee156-119">Therefore, it is extremely difficult to upgrade the size of a signing key if you want to maintain compatibility.</span></span>  
  
- <span data-ttu-id="ee156-120">Tanımlayıcı ad imzalama yalnızca SHA-1 algoritmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="ee156-120">Strong name signing supports only the SHA-1 algorithm.</span></span> <span data-ttu-id="ee156-121">SHA-1 ' in yakın zamanda güvenli karma uygulamalar için yetersiz olduğu belirlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="ee156-121">SHA-1 has recently been found to be inadequate for secure hashing applications.</span></span> <span data-ttu-id="ee156-122">Bu nedenle, daha güçlü bir algoritma (SHA-256 veya üzeri) gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ee156-122">Therefore, a stronger algorithm (SHA-256 or greater) is necessary.</span></span> <span data-ttu-id="ee156-123">SHA-1 ' i, FIPS ile uyumlu olan ve yalnızca FIPS uyumlu yazılım ve algoritmaları kullanmayı seçen sorunlar sunacak şekilde kaybedecektir.</span><span class="sxs-lookup"><span data-stu-id="ee156-123">It is possible that SHA-1 will lose its FIPS-compliant standing, which would present problems for those who choose to use only FIPS-compliant software and algorithms.</span></span>  
  
## <a name="advantages-of-enhanced-strong-names"></a><span data-ttu-id="ee156-124">Gelişmiş tanımlayıcı adların avantajları</span><span class="sxs-lookup"><span data-stu-id="ee156-124">Advantages of enhanced strong names</span></span>  
 <span data-ttu-id="ee156-125">Gelişmiş tanımlayıcı adların başlıca avantajları, önceden var olan kesin adlarla ve bir kimliğin diğerine eşdeğer bir şekilde talep etme özelliği ile uyumludur:</span><span class="sxs-lookup"><span data-stu-id="ee156-125">The main advantages of enhanced strong names are compatibility with pre-existing strong names and the ability to claim that one identity is equivalent to another:</span></span>  
  
- <span data-ttu-id="ee156-126">Önceden varolan imzalı derlemeler içeren geliştiriciler, eski kimliklere başvuran Derlemelerle uyumluluğu sürdürirken kimliklerini SHA-2 algoritmalarına geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="ee156-126">Developers who have pre-existing signed assemblies can migrate their identities to the SHA-2 algorithms while maintaining compatibility with assemblies that reference the old identities.</span></span>  
  
- <span data-ttu-id="ee156-127">Yeni derlemeler oluşturan ve önceden var olan güçlü ad imzalarıyla ilgilenme yapan geliştiriciler, daha güvenli SHA-2 algoritmalarını kullanabilir ve derlemeleri her zaman sahip oldukları şekilde imzalayabilirler.</span><span class="sxs-lookup"><span data-stu-id="ee156-127">Developers who create new assemblies and are not concerned with pre-existing strong name signatures can use the more secure SHA-2 algorithms and sign the assemblies as they always have.</span></span>  
  
## <a name="use-enhanced-strong-names"></a><span data-ttu-id="ee156-128">Gelişmiş tanımlayıcı adlar kullanın</span><span class="sxs-lookup"><span data-stu-id="ee156-128">Use enhanced strong names</span></span>  
 <span data-ttu-id="ee156-129">Tanımlayıcı ad anahtarları bir imza anahtarından ve bir kimlik anahtarından oluşur.</span><span class="sxs-lookup"><span data-stu-id="ee156-129">Strong name keys consist of a signature key and an identity key.</span></span> <span data-ttu-id="ee156-130">Derleme imza anahtarıyla imzalanır ve kimlik anahtarı tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="ee156-130">The assembly is signed with the signature key and is identified by the identity key.</span></span> <span data-ttu-id="ee156-131">.NET Framework 4,5 ' den önce bu iki anahtar birbirinin aynısıdır.</span><span class="sxs-lookup"><span data-stu-id="ee156-131">Prior to the .NET Framework 4.5, these two keys were identical.</span></span> <span data-ttu-id="ee156-132">.NET Framework 4,5 ' den başlayarak, kimlik anahtarı önceki .NET Framework sürümlerle aynı kalır, ancak imza anahtarı daha güçlü bir karma algoritmayla geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ee156-132">Starting with the .NET Framework 4.5, the identity key remains the same as in earlier .NET Framework versions, but the signature key is enhanced with a stronger hash algorithm.</span></span> <span data-ttu-id="ee156-133">Ayrıca, imza anahtarı kimlik anahtarıyla imzalanır ve bir sayaç imzası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ee156-133">In addition, the signature key is signed with the identity key to create a counter-signature.</span></span>  
  
 <span data-ttu-id="ee156-134"><xref:System.Reflection.AssemblySignatureKeyAttribute>Özniteliği, derleme meta verilerinin derleme kimliği için önceden mevcut ortak anahtarı kullanmasını sağlar, bu da eski derleme başvurularının çalışmaya devam etmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ee156-134">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute enables the assembly metadata to use the pre-existing public key for assembly identity, which allows old assembly references to continue to work.</span></span>  <span data-ttu-id="ee156-135"><xref:System.Reflection.AssemblySignatureKeyAttribute>Özniteliği, yeni imza anahtarı sahibinin de eski kimlik anahtarının sahibi olduğundan emin olmak için sayaç imzasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="ee156-135">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute uses the counter-signature to ensure that the owner of the new signature key is also the owner of the old identity key.</span></span>  
  
### <a name="sign-with-sha-2-without-key-migration"></a><span data-ttu-id="ee156-136">Anahtar Geçişi olmadan SHA-2 ile imzala</span><span class="sxs-lookup"><span data-stu-id="ee156-136">Sign with SHA-2, without key migration</span></span>  
 <span data-ttu-id="ee156-137">Bir derlemeyi tanımlayıcı ad imzasına geçirmeden imzalamak için komut isteminden aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="ee156-137">Run the following commands from a command prompt to sign an assembly without migrating a strong name signature:</span></span>  
  
1. <span data-ttu-id="ee156-138">Yeni kimlik anahtarını (gerekliyse) oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ee156-138">Generate the new identity key (if necessary).</span></span>  
  
    ```console  
    sn -k IdentityKey.snk  
    ```  
  
2. <span data-ttu-id="ee156-139">Kimlik ortak anahtarını ayıklayın ve bu anahtarla imzalarken bir SHA-2 algoritmasının kullanılması gerektiğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="ee156-139">Extract the identity public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3. <span data-ttu-id="ee156-140">Derlemeyi kimlik ortak anahtar dosyası ile gecikmeli imzalayın.</span><span class="sxs-lookup"><span data-stu-id="ee156-140">Delay-sign the assembly with the identity public key file.</span></span>  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4. <span data-ttu-id="ee156-141">Derlemeyi tam kimlik anahtar çifti ile yeniden imzalayın.</span><span class="sxs-lookup"><span data-stu-id="ee156-141">Re-sign the assembly with the full identity key pair.</span></span>  
  
    ```console  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="sign-with-sha-2-with-key-migration"></a><span data-ttu-id="ee156-142">Anahtar geçişi ile SHA-2 ile oturum açma</span><span class="sxs-lookup"><span data-stu-id="ee156-142">Sign with SHA-2, with key migration</span></span>  
 <span data-ttu-id="ee156-143">Bir derlemeyi geçirilmiş bir tanımlayıcı ad imzasıyla imzalamak için komut isteminden aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ee156-143">Run the following commands from a command prompt to sign an assembly with a migrated strong name signature.</span></span>  
  
1. <span data-ttu-id="ee156-144">Bir kimlik ve imza anahtarı çifti oluşturun (gerekirse).</span><span class="sxs-lookup"><span data-stu-id="ee156-144">Generate an identity and signature key pair (if necessary).</span></span>  
  
    ```console  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2. <span data-ttu-id="ee156-145">İmza ortak anahtarını ayıklayın ve bu anahtarla imzalarken bir SHA-2 algoritmasının kullanılması gerektiğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="ee156-145">Extract the signature public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```console  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3. <span data-ttu-id="ee156-146">Bir sayaç imzası üreten karma algoritmayı belirleyen kimlik ortak anahtarını ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="ee156-146">Extract the identity public key, which determines the hash algorithm that generates a counter-signature.</span></span>  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4. <span data-ttu-id="ee156-147">Bir öznitelik için parametreler oluşturun <xref:System.Reflection.AssemblySignatureKeyAttribute> ve özniteliği derlemeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ee156-147">Generate the parameters for a <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute, and attach the attribute to the assembly.</span></span>  
  
    ```console  
    sn -a IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  

    <span data-ttu-id="ee156-148">Bu, aşağıdakine benzer bir çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="ee156-148">This produces output similar to the following.</span></span>

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

    <span data-ttu-id="ee156-149">Bu çıkış daha sonra AssemblySignatureKeyAttribute içine dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="ee156-149">This output can then be transformed into an AssemblySignatureKeyAttribute.</span></span>

    ```csharp
    [assembly:System.Reflection.AssemblySignatureKeyAttribute(
    "002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b43893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a34d153cdd",
    "e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91ebe1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3ae5fec2c682e57b7442738"
    )]
    ```
  
5. <span data-ttu-id="ee156-150">Derlemeyi kimlik ortak anahtarı ile gecikmeli imzalayın.</span><span class="sxs-lookup"><span data-stu-id="ee156-150">Delay-sign the assembly with the identity public key.</span></span>  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6. <span data-ttu-id="ee156-151">Derlemeyi imza anahtar çiftiyle tamamen imzalayın.</span><span class="sxs-lookup"><span data-stu-id="ee156-151">Fully sign the assembly with the signature key pair.</span></span>  
  
    ```console  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ee156-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee156-152">See also</span></span>

- [<span data-ttu-id="ee156-153">Tanımlayıcı adlı derlemeler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="ee156-153">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
