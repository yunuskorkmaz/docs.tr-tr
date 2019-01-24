---
title: Güçlü Adlandırmayı İyileştirme
ms.date: 03/30/2017
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a0b63e27a3eceb80d42d43eea321b0dc757ad69
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688876"
---
# <a name="enhanced-strong-naming"></a><span data-ttu-id="3e0a2-102">Güçlü Adlandırmayı İyileştirme</span><span class="sxs-lookup"><span data-stu-id="3e0a2-102">Enhanced Strong Naming</span></span>
<span data-ttu-id="3e0a2-103">Tanımlayıcı ad imzası derlemeleri tanımlamak için bir kimlik .NET Framework mekanizmasıdır.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-103">A strong name signature is an identity mechanism in the .NET Framework for identifying assemblies.</span></span> <span data-ttu-id="3e0a2-104">Buna genellikle bir oluşturucu (imzalayan) alıcıya (doğrulama) geçirilen verilerin bütünlüğünü doğrulamak için kullanılan ortak anahtar dijital imzası var.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-104">It is a public-key digital signature that is typically used to verify the integrity of data being passed from an originator (signer) to a recipient (verifier).</span></span> <span data-ttu-id="3e0a2-105">Bu imza, bir derleme için benzersiz bir kimlik kullanılır ve derlemeye yapılan başvuruların belirsiz olmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-105">This signature is used as a unique identity for an assembly and ensures that references to the assembly are not ambiguous.</span></span> <span data-ttu-id="3e0a2-106">Derleme oluşturma işleminin bir parçası imzalanır ve sonra yüklendiğinde doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-106">The assembly is signed as part of the build process and then verified when it is loaded.</span></span>  
  
 <span data-ttu-id="3e0a2-107">Tanımlayıcı ad imzaları, kötü amaçlı taraflar bir derlemeye müdahale etmesine ve derlemeyi özgün İmzalayanın anahtarıyla yeniden imzalama engelleyin.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-107">Strong name signatures help prevent malicious parties from tampering with an assembly and then re-signing the assembly with the original signer’s key.</span></span> <span data-ttu-id="3e0a2-108">Ancak kesin ad anahtarları yayıncı hakkında herhangi bir güvenilir bilgi içermeyen ya da bunlar bir sertifika hiyerarşisi içermez.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-108">However, strong name keys don’t contain any reliable information about the publisher, nor do they contain a certificate hierarchy.</span></span> <span data-ttu-id="3e0a2-109">Tanımlayıcı ad imzası derlemeyi imzalayan kişinin güvenilirliğini garanti vermez veya söz konusu kişinin anahtarın yasal sahibi olup olmadığını göstermez; yalnızca anahtar sahibinin derlemeyi imzaladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-109">A strong name signature does not guarantee the trustworthiness of the person who signed the assembly or indicate whether that person was a legitimate owner of the key; it indicates only that the owner of the key signed the assembly.</span></span> <span data-ttu-id="3e0a2-110">Bu nedenle, tanımlayıcı ad imzası, güvenen üçüncü taraf kodu için güvenlik Doğrulayıcısı olarak kullanılması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-110">Therefore, we do not recommend using a strong name signature as a security validator for trusting third-party code.</span></span> <span data-ttu-id="3e0a2-111">Microsoft Authenticode, kod kimlik doğrulaması için önerilen yoldur.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-111">Microsoft Authenticode is the recommended way to authenticate code.</span></span>  
  
## <a name="limitations-of-conventional-strong-names"></a><span data-ttu-id="3e0a2-112">Geleneksel tanımlayıcı adlar kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="3e0a2-112">Limitations of Conventional Strong Names</span></span>  
 <span data-ttu-id="3e0a2-113">Önceki sürümlerde kullanılan tanımlayıcı adlandırma teknolojisinin [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] aşağıdaki eksiklikleri vardır:</span><span class="sxs-lookup"><span data-stu-id="3e0a2-113">The strong naming technology used in versions before the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] has the following shortcomings:</span></span>  
  
-   <span data-ttu-id="3e0a2-114">Anahtarlar sürekli saldırı altında olan ve gelişmiş teknikler ve donanım bir özel anahtarı bir ortak anahtar Infer kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-114">Keys are constantly under attack, and improved techniques and hardware make it easier to infer a private key from a public key.</span></span> <span data-ttu-id="3e0a2-115">Saldırılara karşı korunmak için büyük anahtarlar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-115">To guard against attacks, larger keys are necessary.</span></span> <span data-ttu-id="3e0a2-116">.NET framework sürümlerini önce [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] herhangi boyutta anahtarla (varsayılan boyut 1024 bit olan) olanağı sağlar, ancak yeni anahtarla bir derlemeyi imzalamak, derlemenin daha eski kimliği başvuran tüm ikili dosyaları keser.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-116">.NET Framework versions before the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] provide the ability to sign with any size key (the default size is 1024 bits), but signing an assembly with a new key breaks all binaries that reference the older identity of the assembly.</span></span> <span data-ttu-id="3e0a2-117">Bu nedenle, uyumluluğu korumak istiyorsanız, bir imzalama anahtarı boyutunu yükseltmek son derece zordur.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-117">Therefore, it is extremely difficult to upgrade the size of a signing key if you want to maintain compatibility.</span></span>  
  
-   <span data-ttu-id="3e0a2-118">Tanımlayıcı ad imzası yalnızca SHA-1 algoritmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-118">Strong name signing supports only the SHA-1 algorithm.</span></span> <span data-ttu-id="3e0a2-119">SHA-1, güvenli karma uygulamalar için yetersiz olduğu yakın zamanda bulundu.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-119">SHA-1 has recently been found to be inadequate for secure hashing applications.</span></span> <span data-ttu-id="3e0a2-120">Bu nedenle, daha güçlü bir algoritma (SHA-256 veya daha büyük) gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-120">Therefore, a stronger algorithm (SHA-256 or greater) is necessary.</span></span> <span data-ttu-id="3e0a2-121">SHA-1 yalnızca FIPS uyumlu yazılım ve algoritmaları kullanmayı tercih edenler için sorunlara neden olabilir, FIPS uyumlu ayakta kaybedersiniz mümkündür.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-121">It is possible that SHA-1 will lose its FIPS-compliant standing, which would present problems for those who choose to use only FIPS-compliant software and algorithms.</span></span>  
  
## <a name="advantages-of-enhanced-strong-names"></a><span data-ttu-id="3e0a2-122">Gelişmiş tanımlayıcı adların avantajları</span><span class="sxs-lookup"><span data-stu-id="3e0a2-122">Advantages of Enhanced Strong Names</span></span>  
 <span data-ttu-id="3e0a2-123">Önceden varolan tanımlayıcı adlarla uyumluluk ve tek bir kimlik diğerine eşdeğer olduğunu iddia edebilme yeteneğidir geliştirilmiş tanımlayıcı adların başlıca avantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3e0a2-123">The main advantages of enhanced strong names are compatibility with pre-existing strong names and the ability to claim that one identity is equivalent to another:</span></span>  
  
-   <span data-ttu-id="3e0a2-124">Önceden mevcut olan imzalı derlemelere sahip geliştiriciler eski kimliklere başvuran derlemeler ile uyumluluğu korurken kendi kimliklerini SHA-2 algoritmalarına geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-124">Developers who have pre-existing signed assemblies can migrate their identities to the SHA-2 algorithms while maintaining compatibility with assemblies that reference the old identities.</span></span>  
  
-   <span data-ttu-id="3e0a2-125">Yeni derlemeler oluşturan ve tanımlayıcı ad imzaları önceden mevcut olan ilgisi olmayan geliştiriciler daha güvenli SHA-2 algoritmalarını kullanabilir ve her zaman olduğu gibi derlemelerini imzalayabilirler.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-125">Developers who create new assemblies and are not concerned with pre-existing strong name signatures can use the more secure SHA-2 algorithms and sign the assemblies as they always have.</span></span>  
  
## <a name="using-enhanced-strong-names"></a><span data-ttu-id="3e0a2-126">Geliştirilmiş katı adları kullanma</span><span class="sxs-lookup"><span data-stu-id="3e0a2-126">Using Enhanced Strong Names</span></span>  
 <span data-ttu-id="3e0a2-127">Tanımlayıcı ad anahtarı bir imza anahtarı ve bir kimlik anahtarından oluşur.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-127">Strong name keys consist of a signature key and an identity key.</span></span> <span data-ttu-id="3e0a2-128">Derleme imza anahtarıyla imzalanır ve kimlik anahtarı tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-128">The assembly is signed with the signature key and is identified by the identity key.</span></span> <span data-ttu-id="3e0a2-129">Öncesinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], bu iki tuş aynıydı.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-129">Prior to the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], these two keys were identical.</span></span> <span data-ttu-id="3e0a2-130">İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]kimlik anahtarı önceki .NET Framework sürümlerinde olduğu gibi aynı kalır, ancak imza anahtarı daha güçlü bir karma algoritması ile geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-130">Starting with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], the identity key remains the same as in earlier .NET Framework versions, but the signature key is enhanced with a stronger hash algorithm.</span></span> <span data-ttu-id="3e0a2-131">Ayrıca, imza anahtarı kimlik anahtarı ile bir karşı imza oluşturmak için imzalanır.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-131">In addition, the signature key is signed with the identity key to create a counter-signature.</span></span>  
  
 <span data-ttu-id="3e0a2-132"><xref:System.Reflection.AssemblySignatureKeyAttribute> Özniteliği derleme meta verileri, eski derleme başvurularının çalışmaya devam etmeyi sağlayan derleme kimliği için önceden varolan genel anahtarı kullanmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-132">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute enables the assembly metadata to use the pre-existing public key for assembly identity, which allows old assembly references to continue to work.</span></span>  <span data-ttu-id="3e0a2-133"><xref:System.Reflection.AssemblySignatureKeyAttribute> Özniteliği, yeni imza anahtarı sahibinin eski kimlik anahtarının sahibi olduğundan emin olmak için olması için karşı imzayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-133">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute uses the counter-signature to ensure that the owner of the new signature key is also the owner of the old identity key.</span></span>  
  
### <a name="signing-with-sha-2-without-key-migration"></a><span data-ttu-id="3e0a2-134">SHA-2, anahtar geçişi olmadan imzalama</span><span class="sxs-lookup"><span data-stu-id="3e0a2-134">Signing with SHA-2, Without Key Migration</span></span>  
 <span data-ttu-id="3e0a2-135">Bir derlemeyi bir güçlü ad geçirmeden imzalamak için bir komut istemi penceresinden aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="3e0a2-135">Run the following commands from a Command Prompt window to sign an assembly without migrating a strong name signature:</span></span>  
  
1.  <span data-ttu-id="3e0a2-136">Yeni bir kimlik anahtarı (gerekiyorsa) üretin.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-136">Generate the new identity key (if necessary).</span></span>  
  
    ```  
    sn -k IdentityKey.snk  
    ```  
  
2.  <span data-ttu-id="3e0a2-137">Kimlik genel anahtarını ayıklayın ve bu anahtar ile imzalarken bir SHA-2 algoritmasının kullanılacağını belirtin.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-137">Extract the identity public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3.  <span data-ttu-id="3e0a2-138">Derlemeyi kimlik genel anahtar dosyasıyla Gecikmeli imzalayın.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-138">Delay-sign the assembly with the identity public key file.</span></span>  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4.  <span data-ttu-id="3e0a2-139">Derlemeyi tam kimlik anahtar çifti ile yeniden imzalayın.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-139">Re-sign the assembly with the full identity key pair.</span></span>  
  
    ```  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="signing-with-sha-2-with-key-migration"></a><span data-ttu-id="3e0a2-140">SHA-2 ile anahtar geçişi ile imzalama</span><span class="sxs-lookup"><span data-stu-id="3e0a2-140">Signing with SHA-2, with Key Migration</span></span>  
 <span data-ttu-id="3e0a2-141">Bir derlemeyi geçirilen kesin ad imzalı imzalamak için bir komut istemi penceresinden aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-141">Run the following commands from a Command Prompt window to sign an assembly with a migrated strong name signature.</span></span>  
  
1.  <span data-ttu-id="3e0a2-142">Bir kimlik ve imza anahtar çifti (gerekiyorsa) üretin.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-142">Generate an identity and signature key pair (if necessary).</span></span>  
  
    ```  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2.  <span data-ttu-id="3e0a2-143">İmza genel anahtarını ayıklayın ve bu anahtar ile imzalarken bir SHA-2 algoritmasının kullanılacağını belirtin.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-143">Extract the signature public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3.  <span data-ttu-id="3e0a2-144">Bir karşı imza üreten karma algoritmayı belirleyen kimlik genel anahtarını ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-144">Extract the identity public key, which determines the hash algorithm that generates a counter-signature.</span></span>  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4.  <span data-ttu-id="3e0a2-145">İçin parametreler üretin bir <xref:System.Reflection.AssemblySignatureKeyAttribute> özniteliği ve özniteliği derlemeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-145">Generate the parameters for a <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute, and attach the attribute to the assembly.</span></span>  
  
    ```  
    sn -a IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  

    <span data-ttu-id="3e0a2-146">Bu, aşağıdakine benzer bir çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-146">This produces output similar to the following.</span></span>

    ```
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

    <span data-ttu-id="3e0a2-147">Bu çıkış ardından dönüştürülmüş bir AssemblySignatureKeyAttribute.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-147">This output can then be transformed into an AssemblySignatureKeyAttribute.</span></span>

    ```
    [assembly:System.Reflection.AssemblySignatureKeyAttribute(
    "002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b43893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a34d153cdd",
    "e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91ebe1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3ae5fec2c682e57b7442738"
    )]
    ```
  
5.  <span data-ttu-id="3e0a2-148">Derlemeyi kimlik genel anahtarıyla Gecikmeli imzalayın.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-148">Delay-sign the assembly with the identity public key.</span></span>  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6.  <span data-ttu-id="3e0a2-149">Derlemeyi imza kimlik anahtar çifti ile tam olarak imzalayın.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-149">Fully sign the assembly with the signature key pair.</span></span>  
  
    ```  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3e0a2-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e0a2-150">See also</span></span>
- [<span data-ttu-id="3e0a2-151">Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="3e0a2-151">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
