---
title: "İntranet Uygulamalarını Tam Güvende Çalıştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full trust, running intranet applications in
- intranet applications, running in full trust
- running intranet applications in full trust
ms.assetid: ee13c0a8-ab02-49f7-b8fb-9eab16c6c4f0
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 58eeda82c66ecda6ffd714e808b006634ccba804
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="running-intranet-applications-in-full-trust"></a><span data-ttu-id="aad1a-102">İntranet Uygulamalarını Tam Güvende Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="aad1a-102">Running Intranet Applications in Full Trust</span></span>
<span data-ttu-id="aad1a-103">.NET Framework sürüm 3.5 ile başlayan Service Pack 1 (SP1), uygulamaları ve bunların kitaplık derlemeleri tam güven derlemeleri olarak bir ağ paylaşımından çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="aad1a-103">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), applications and their library assemblies can be run as full-trust assemblies from a network share.</span></span> <span data-ttu-id="aad1a-104"><xref:System.Security.SecurityZone.MyComputer>Bölge kanıt, intranet üzerindeki paylaşımdan yüklenen derlemeler otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="aad1a-104"><xref:System.Security.SecurityZone.MyComputer> zone evidence is automatically added to assemblies that are loaded from a share on the intranet.</span></span> <span data-ttu-id="aad1a-105">Bu bulgu aynı bilgisayarda bulunabilir derlemeleri olarak (genellikle tam güven olduğu) kümesini vermek bu derlemeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="aad1a-105">This evidence gives those assemblies the same grant set (which is typically full trust) as the assemblies that reside on the computer.</span></span> <span data-ttu-id="aad1a-106">Bu işlev ClickOnce uygulamaları veya bir ana bilgisayarda çalıştırmak için tasarlanmış uygulamalar için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="aad1a-106">This functionality does not apply to ClickOnce applications or to applications that are designed to run on a host.</span></span>  
  
## <a name="rules-for-library-assemblies"></a><span data-ttu-id="aad1a-107">Kitaplık derlemeleri için kurallar</span><span class="sxs-lookup"><span data-stu-id="aad1a-107">Rules for Library Assemblies</span></span>  
 <span data-ttu-id="aad1a-108">Bir ağ paylaşımına çalıştırılabilir tarafından yüklenen derlemeler için aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="aad1a-108">The following rules apply to assemblies that are loaded by an executable on a network share:</span></span>  
  
-   <span data-ttu-id="aad1a-109">Kitaplık derlemeleri yürütülebilir derleme ile aynı klasörde bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aad1a-109">Library assemblies must reside in the same folder as the executable assembly.</span></span> <span data-ttu-id="aad1a-110">Bir alt klasöründe bulunan veya farklı bir yolda başvurulan derlemeleri tam güven verme kümesi verilmedi.</span><span class="sxs-lookup"><span data-stu-id="aad1a-110">Assemblies that reside in a subfolder or are referenced on a different path are not given the full-trust grant set.</span></span>  
  
-   <span data-ttu-id="aad1a-111">Yürütülebilir dosya gecikme-bir derleme yüklerini gerekiyorsa, yürütülebilir dosya başlatmak için kullanılan aynı yol kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="aad1a-111">If the executable delay-loads an assembly, it must use the same path that was used to start the executable.</span></span> <span data-ttu-id="aad1a-112">Örneğin, varsa Paylaşım \\ \\ *ağ bilgisayar*\\*paylaşmak* bir sürücü harfine eşlenmez ve yürütülebilir yüklenen derlemeler bu yolundan çalıştırın Ağ yolu kullanarak yürütülebilir olarak tam güven verilecektir değil.</span><span class="sxs-lookup"><span data-stu-id="aad1a-112">For example, if the share \\\\*network-computer*\\*share* is mapped to a drive letter and the executable is run from that path, assemblies that are loaded by the executable by using the network path will not be granted full trust.</span></span> <span data-ttu-id="aad1a-113">Gecikme yükü bir derlemede için <xref:System.Security.SecurityZone.MyComputer> bölgesi, yürütülebilir dosya sürücü harfi yolu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="aad1a-113">To delay-load an assembly in the <xref:System.Security.SecurityZone.MyComputer> zone, the executable must use the drive letter path.</span></span>  
  
## <a name="restoring-the-former-intranet-policy"></a><span data-ttu-id="aad1a-114">Eski Intranet İlkesi geri yükleniyor</span><span class="sxs-lookup"><span data-stu-id="aad1a-114">Restoring the Former Intranet Policy</span></span>  
 <span data-ttu-id="aad1a-115">.NET Framework önceki sürümlerinde, paylaşılan derlemeler verilmiş <xref:System.Security.SecurityZone.Intranet> bölge kanıtlar.</span><span class="sxs-lookup"><span data-stu-id="aad1a-115">In earlier versions of the .NET Framework, shared assemblies were granted <xref:System.Security.SecurityZone.Intranet> zone evidence.</span></span> <span data-ttu-id="aad1a-116">Bir derlemeyi paylaşımında tam güven vermek için kod erişimi güvenlik ilkesi belirtin gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="aad1a-116">You had to specify code access security policy to grant full trust to an assembly on a share.</span></span>  
  
 <span data-ttu-id="aad1a-117">Bu yeni davranış intranet derlemeler için varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="aad1a-117">This new behavior is the default for intranet assemblies.</span></span> <span data-ttu-id="aad1a-118">Sağlama önceki davranış döndürebilir <xref:System.Security.SecurityZone.Intranet> bilgisayardaki tüm uygulamalar için geçerli bir kayıt defteri anahtarını ayarlayarak kanıtlar.</span><span class="sxs-lookup"><span data-stu-id="aad1a-118">You can return to the earlier behavior of providing <xref:System.Security.SecurityZone.Intranet> evidence by setting a registry key that applies to all applications on the computer.</span></span> <span data-ttu-id="aad1a-119">Bu işlem, 32 bit ve 64-bit bilgisayarlar için farklıdır:</span><span class="sxs-lookup"><span data-stu-id="aad1a-119">This process is different for 32-bit and 64-bit computers:</span></span>  
  
-   <span data-ttu-id="aad1a-120">32-bit bilgisayarlarda HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft altında bir alt anahtar oluşturma\\. Sistem kayıt defteri anahtarında NETFramework.</span><span class="sxs-lookup"><span data-stu-id="aad1a-120">On 32-bit computers, create a subkey under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key in the system registry.</span></span> <span data-ttu-id="aad1a-121">Anahtar adı LegacyMyComputerZone DWORD değeri 1 ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="aad1a-121">Use the key name LegacyMyComputerZone with a DWORD value of 1.</span></span>  
  
-   <span data-ttu-id="aad1a-122">64-bit bilgisayarlarda HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft altında bir alt anahtar oluşturma\\. Sistem kayıt defteri anahtarında NETFramework.</span><span class="sxs-lookup"><span data-stu-id="aad1a-122">On 64-bit computers, create a subkey under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key in the system registry.</span></span> <span data-ttu-id="aad1a-123">Anahtar adı LegacyMyComputerZone DWORD değeri 1 ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="aad1a-123">Use the key name LegacyMyComputerZone with a DWORD value of 1.</span></span> <span data-ttu-id="aad1a-124">HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft altında aynı alt anahtarını oluşturmak\\. NETFramework anahtarı.</span><span class="sxs-lookup"><span data-stu-id="aad1a-124">Create the same subkey under the HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aad1a-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aad1a-125">See Also</span></span>  
 [<span data-ttu-id="aad1a-126">Derlemelerle programlama</span><span class="sxs-lookup"><span data-stu-id="aad1a-126">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
