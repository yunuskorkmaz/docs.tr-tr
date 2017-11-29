---
title: "Güçlü Adlandırmayı İyileştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 429a54340cef6d608692abd71311c012afe9a3d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="enhanced-strong-naming"></a><span data-ttu-id="414d4-102">Güçlü Adlandırmayı İyileştirme</span><span class="sxs-lookup"><span data-stu-id="414d4-102">Enhanced Strong Naming</span></span>
<span data-ttu-id="414d4-103">Tanımlayıcı ad imzası derlemeleri tanımlamak için bir kimlik .NET Framework'teki mekanizmasıdır.</span><span class="sxs-lookup"><span data-stu-id="414d4-103">A strong name signature is an identity mechanism in the .NET Framework for identifying assemblies.</span></span> <span data-ttu-id="414d4-104">Bu, genellikle bir gönderene (imzalayan) bir alıcı (Doğrulayıcı) geçirilen verilerin bütünlüğünü doğrulamak için kullanılan bir ortak anahtar dijital imza olur.</span><span class="sxs-lookup"><span data-stu-id="414d4-104">It is a public-key digital signature that is typically used to verify the integrity of data being passed from an originator (signer) to a recipient (verifier).</span></span> <span data-ttu-id="414d4-105">Bu imza, bir derleme için benzersiz bir kimliği olarak kullanılan ve derleme başvurularını belirsiz olmadığından sağlar.</span><span class="sxs-lookup"><span data-stu-id="414d4-105">This signature is used as a unique identity for an assembly and ensures that references to the assembly are not ambiguous.</span></span> <span data-ttu-id="414d4-106">Derleme oluşturma işleminin bir parçası olarak imzalanır ve yüklendiğinde sonra doğrulandı.</span><span class="sxs-lookup"><span data-stu-id="414d4-106">The assembly is signed as part of the build process and then verified when it is loaded.</span></span>  
  
 <span data-ttu-id="414d4-107">Güçlü ad imzaları ile bir derlemeyi izinsiz ve derleme özgün imzalayan anahtarla yeniden imzalama amaçlı tarafların önlemeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="414d4-107">Strong name signatures help prevent malicious parties from tampering with an assembly and then re-signing the assembly with the original signer’s key.</span></span> <span data-ttu-id="414d4-108">Ancak, güçlü ad anahtarları yayımcı ilgili herhangi bir güvenilir bilgi içermeyen veya bir sertifika hiyerarşisi içerirler.</span><span class="sxs-lookup"><span data-stu-id="414d4-108">However, strong name keys don’t contain any reliable information about the publisher, nor do they contain a certificate hierarchy.</span></span> <span data-ttu-id="414d4-109">Sağlam ad imzası derleme imzalanmamış kişiye'nın güvenilirliği garanti ya da bu kişi yasal bir anahtarın sahibi olduğunu gösterir; yalnızca anahtarın sahibini derleme imzalanmamış gösterir.</span><span class="sxs-lookup"><span data-stu-id="414d4-109">A strong name signature does not guarantee the trustworthiness of the person who signed the assembly or indicate whether that person was a legitimate owner of the key; it indicates only that the owner of the key signed the assembly.</span></span> <span data-ttu-id="414d4-110">Bu nedenle, bir tanımlayıcı ad imzası güvenen üçüncü taraf kodu için bir güvenlik Doğrulayıcı kullanarak önerilmez.</span><span class="sxs-lookup"><span data-stu-id="414d4-110">Therefore, we do not recommend using a strong name signature as a security validator for trusting third-party code.</span></span> <span data-ttu-id="414d4-111">Microsoft Authenticode kod kimlik doğrulaması için önerilen yoldur.</span><span class="sxs-lookup"><span data-stu-id="414d4-111">Microsoft Authenticode is the recommended way to authenticate code.</span></span>  
  
## <a name="limitations-of-conventional-strong-names"></a><span data-ttu-id="414d4-112">Geleneksel tanımlayıcı adlar sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="414d4-112">Limitations of Conventional Strong Names</span></span>  
 <span data-ttu-id="414d4-113">Önceki sürümler kullanılan güçlü adlandırma teknolojisi [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] aşağıdaki eksiklikleri vardır:</span><span class="sxs-lookup"><span data-stu-id="414d4-113">The strong naming technology used in versions before the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] has the following shortcomings:</span></span>  
  
-   <span data-ttu-id="414d4-114">Anahtarları sürekli Saldırıya uğramış olan ve geliştirilmiş teknikleri ve donanım ortak anahtarı bir özel anahtar Infer kolaylaştırmak.</span><span class="sxs-lookup"><span data-stu-id="414d4-114">Keys are constantly under attack, and improved techniques and hardware make it easier to infer a private key from a public key.</span></span> <span data-ttu-id="414d4-115">Saldırılara karşı koruma sağlamak için daha büyük anahtarları gereklidir.</span><span class="sxs-lookup"><span data-stu-id="414d4-115">To guard against attacks, larger keys are necessary.</span></span> <span data-ttu-id="414d4-116">.NET framework sürümleri önce [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] (varsayılan büyüklüğü, 1024 bit) tüm boyutu anahtar ile oturum açma olanağı sağlar, ancak yeni bir anahtar ile bir derlemeyi imzalamak derleme eski kimliğini başvuru tüm ikili dosyaları keser.</span><span class="sxs-lookup"><span data-stu-id="414d4-116">.NET Framework versions before the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] provide the ability to sign with any size key (the default size is 1024 bits), but signing an assembly with a new key breaks all binaries that reference the older identity of the assembly.</span></span> <span data-ttu-id="414d4-117">Bu nedenle, uyumluluğu korumak istiyorsanız, imzalama anahtarı boyutunu yükseltmek son derece zordur.</span><span class="sxs-lookup"><span data-stu-id="414d4-117">Therefore, it is extremely difficult to upgrade the size of a signing key if you want to maintain compatibility.</span></span>  
  
-   <span data-ttu-id="414d4-118">Tanımlayıcı ad imzası yalnızca SHA-1 algoritmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="414d4-118">Strong name signing supports only the SHA-1 algorithm.</span></span> <span data-ttu-id="414d4-119">SHA-1, güvenli karma uygulamalar için yetersiz olması için en son bulunmadı.</span><span class="sxs-lookup"><span data-stu-id="414d4-119">SHA-1 has recently been found to be inadequate for secure hashing applications.</span></span> <span data-ttu-id="414d4-120">Bu nedenle, daha güçlü bir algoritma (SHA-256 veya daha büyük) gereklidir.</span><span class="sxs-lookup"><span data-stu-id="414d4-120">Therefore, a stronger algorithm (SHA-256 or greater) is necessary.</span></span> <span data-ttu-id="414d4-121">SHA-1 sorunları yalnızca FIPS uyumlu yazılım ve algoritmaları kullanmayı tercih olanlar için sunmak, FIPS uyumlu durumu kaybedersiniz mümkündür.</span><span class="sxs-lookup"><span data-stu-id="414d4-121">It is possible that SHA-1 will lose its FIPS-compliant standing, which would present problems for those who choose to use only FIPS-compliant software and algorithms.</span></span>  
  
## <a name="advantages-of-enhanced-strong-names"></a><span data-ttu-id="414d4-122">Gelişmiş tanımlayıcı adlar avantajları</span><span class="sxs-lookup"><span data-stu-id="414d4-122">Advantages of Enhanced Strong Names</span></span>  
 <span data-ttu-id="414d4-123">Önceden varolan tanımlayıcı adlar ile uyumluluk ve bir kimlik başka eşdeğer olduğunu talep yeteneği Gelişmiş tanımlayıcı adlar ana avantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="414d4-123">The main advantages of enhanced strong names are compatibility with pre-existing strong names and the ability to claim that one identity is equivalent to another:</span></span>  
  
-   <span data-ttu-id="414d4-124">Önceden varolan imzalı derlemeler sahip geliştiriciler, SHA-2 algoritmaları eski kimlikleri başvuru derlemeleri uyumluluğunu korurken kimliklerini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="414d4-124">Developers who have pre-existing signed assemblies can migrate their identities to the SHA-2 algorithms while maintaining compatibility with assemblies that reference the old identities.</span></span>  
  
-   <span data-ttu-id="414d4-125">Yeni derlemeleri oluşturma ve güçlü ad imzaları önceden var olan bir kaygınız geliştiriciler daha güvenli SHA-2 algoritmaları ve her zamanki gibi derlemeler oturum kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="414d4-125">Developers who create new assemblies and are not concerned with pre-existing strong name signatures can use the more secure SHA-2 algorithms and sign the assemblies as they always have.</span></span>  
  
## <a name="using-enhanced-strong-names"></a><span data-ttu-id="414d4-126">Gelişmiş güçlü adlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="414d4-126">Using Enhanced Strong Names</span></span>  
 <span data-ttu-id="414d4-127">Güçlü ad anahtarları bir imza anahtarı ve bir kimlik anahtarı oluşur.</span><span class="sxs-lookup"><span data-stu-id="414d4-127">Strong name keys consist of a signature key and an identity key.</span></span> <span data-ttu-id="414d4-128">Derleme imza anahtarı ile imzalanmış ve kimlik anahtar tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="414d4-128">The assembly is signed with the signature key and is identified by the identity key.</span></span> <span data-ttu-id="414d4-129">Öncesinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], bu iki anahtarlar aynı.</span><span class="sxs-lookup"><span data-stu-id="414d4-129">Prior to the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], these two keys were identical.</span></span> <span data-ttu-id="414d4-130">İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]kimlik anahtarı önceki .NET Framework sürümlerinde olduğu gibi aynı kalır, ancak imza anahtarı daha güçlü bir karma algoritması ile geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="414d4-130">Starting with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], the identity key remains the same as in earlier .NET Framework versions, but the signature key is enhanced with a stronger hash algorithm.</span></span> <span data-ttu-id="414d4-131">Ayrıca, imza anahtarı karşı imza oluşturmak için kimlik anahtarla imzalanmıştır.</span><span class="sxs-lookup"><span data-stu-id="414d4-131">In addition, the signature key is signed with the identity key to create a counter-signature.</span></span>  
  
 <span data-ttu-id="414d4-132"><xref:System.Reflection.AssemblySignatureKeyAttribute> Özniteliği önceden var olan ortak anahtar çalışmaya devam etmek eski derleme başvurularını sağlayan derleme kimlik için kullanılacak derleme meta verilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="414d4-132">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute enables the assembly metadata to use the pre-existing public key for assembly identity, which allows old assembly references to continue to work.</span></span>  <span data-ttu-id="414d4-133"><xref:System.Reflection.AssemblySignatureKeyAttribute> Özniteliğini yeni imza anahtarı sahibi eski kimlik anahtarı sahibi olduğundan emin olmak için tamamlayıcı imza kullanır.</span><span class="sxs-lookup"><span data-stu-id="414d4-133">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute uses the counter-signature to ensure that the owner of the new signature key is also the owner of the old identity key.</span></span>  
  
### <a name="signing-with-sha-2-without-key-migration"></a><span data-ttu-id="414d4-134">SHA-2, anahtar geçişi olmadan ile imzalama</span><span class="sxs-lookup"><span data-stu-id="414d4-134">Signing with SHA-2, Without Key Migration</span></span>  
 <span data-ttu-id="414d4-135">Tanımlayıcı ad imzası geçirmeden derlemeyi imzalamak için bir komut istemi penceresinden aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="414d4-135">Run the following commands from a Command Prompt window to sign an assembly without migrating a strong name signature:</span></span>  
  
1.  <span data-ttu-id="414d4-136">Yeni kimlik anahtarı (gerekirse) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="414d4-136">Generate the new identity key (if necessary).</span></span>  
  
    ```  
    sn -k IdentityKey.snk  
    ```  
  
2.  <span data-ttu-id="414d4-137">Kimlik ortak anahtarı ayıklayın ve SHA-2 algoritmasını bu anahtarla imzalarken kullanılacağını belirtin.</span><span class="sxs-lookup"><span data-stu-id="414d4-137">Extract the identity public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3.  <span data-ttu-id="414d4-138">Gecikme-oturum kimliğini ortak anahtar dosyası derleme.</span><span class="sxs-lookup"><span data-stu-id="414d4-138">Delay-sign the assembly with the identity public key file.</span></span>  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4.  <span data-ttu-id="414d4-139">Derleme tam kimlik anahtar çifti ile yeniden oturum açın.</span><span class="sxs-lookup"><span data-stu-id="414d4-139">Re-sign the assembly with the full identity key pair.</span></span>  
  
    ```  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="signing-with-sha-2-with-key-migration"></a><span data-ttu-id="414d4-140">SHA-2, anahtar geçişi ile birlikte imzalama</span><span class="sxs-lookup"><span data-stu-id="414d4-140">Signing with SHA-2, with Key Migration</span></span>  
 <span data-ttu-id="414d4-141">Geçirilen sağlam ad imzası ile bir derlemeyi imzalamak için bir komut istemi penceresinden aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="414d4-141">Run the following commands from a Command Prompt window to sign an assembly with a migrated strong name signature.</span></span>  
  
1.  <span data-ttu-id="414d4-142">Bir kimlik ve imza anahtar çifti (gerekirse) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="414d4-142">Generate an identity and signature key pair (if necessary).</span></span>  
  
    ```  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2.  <span data-ttu-id="414d4-143">İmza ortak anahtarı ayıklayın ve SHA-2 algoritmasını bu anahtarla imzalarken kullanılacağını belirtin.</span><span class="sxs-lookup"><span data-stu-id="414d4-143">Extract the signature public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3.  <span data-ttu-id="414d4-144">Tamamlayıcı imza oluşturur karma algoritmasını belirler kimlik ortak anahtarı ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="414d4-144">Extract the identity public key, which determines the hash algorithm that generates a counter-signature.</span></span>  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4.  <span data-ttu-id="414d4-145">Parametrelerini oluşturmak bir <xref:System.Reflection.AssemblySignatureKeyAttribute> özniteliği ve derlemeye öznitelik ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="414d4-145">Generate the parameters for a <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute, and attach the attribute to the assembly.</span></span>  
  
    ```  
    sn -ac IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  
  
5.  <span data-ttu-id="414d4-146">Gecikme-oturum kimliğini ortak anahtarla derleme.</span><span class="sxs-lookup"><span data-stu-id="414d4-146">Delay-sign the assembly with the identity public key.</span></span>  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6.  <span data-ttu-id="414d4-147">Derleme imza anahtar çifti ile tam olarak oturum açın.</span><span class="sxs-lookup"><span data-stu-id="414d4-147">Fully sign the assembly with the signature key pair.</span></span>  
  
    ```  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="414d4-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="414d4-148">See Also</span></span>  
 [<span data-ttu-id="414d4-149">Oluşturma ve tanımlayıcı adlı derlemeler kullanma</span><span class="sxs-lookup"><span data-stu-id="414d4-149">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
