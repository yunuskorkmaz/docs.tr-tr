---
title: Fusion Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework fusion]
- fusion interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], fusion
ms.assetid: e2cf98b7-40c1-4f74-86c7-8a76dd9da677
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec2fd3b309820f2bfb7f6091cc3db720db497408
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434899"
---
# <a name="fusion-interfaces"></a><span data-ttu-id="74fa0-102">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="74fa0-102">Fusion Interfaces</span></span>
<span data-ttu-id="74fa0-103">Bu bölümde API fusion uygulamanın kaynakların özelliklerini erişmek ve bu kaynakları uygulama için doğru sürümlerini bulmak için kullandığı yönetilmeyen arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="74fa0-103">This section describes the unmanaged interfaces that the fusion API uses to access the properties of an application's resources and to locate the correct versions of those resources for the application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="74fa0-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="74fa0-104">In This Section</span></span>  
 [<span data-ttu-id="74fa0-105">IAppIdAuthority Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74fa0-105">IAppIdAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)  
 <span data-ttu-id="74fa0-106">Oluşturma ve uygulama kimlikleri ve başvurular tuşları karşılaştırmak yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="74fa0-106">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="74fa0-107">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74fa0-107">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 <span data-ttu-id="74fa0-108">Genel Derleme Önbelleği gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="74fa0-108">Provides a representation of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="74fa0-109">IAssemblyCacheItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74fa0-109">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)  
 <span data-ttu-id="74fa0-110">Tek bir derleme genel derleme önbelleğinde temsil eder.</span><span class="sxs-lookup"><span data-stu-id="74fa0-110">Represents a single assembly in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="74fa0-111">IAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74fa0-111">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)  
 <span data-ttu-id="74fa0-112">Bir dizi için bir numaralandırıcı temsil eden `IAssemblyName` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="74fa0-112">Represents an enumerator for an array of `IAssemblyName` objects.</span></span>  
  
 [<span data-ttu-id="74fa0-113">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74fa0-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 <span data-ttu-id="74fa0-114">Açıklayan ve bir derlemenin benzersiz kimliği ile çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="74fa0-114">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
 [<span data-ttu-id="74fa0-115">IDefinitionAppId Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74fa0-115">IDefinitionAppId Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md)  
 <span data-ttu-id="74fa0-116">Uygulama geçerli kapsamda tanımlar kodu için benzersiz bir tanımlayıcıyı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="74fa0-116">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="74fa0-117">IDefinitionIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74fa0-117">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 <span data-ttu-id="74fa0-118">Uygulama geçerli kapsamda tanımlar kodunun benzersiz imza temsil eder.</span><span class="sxs-lookup"><span data-stu-id="74fa0-118">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="74fa0-119">IEnumDefinitionIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74fa0-119">IEnumDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md)  
 <span data-ttu-id="74fa0-120">Koleksiyonu için Numaralandırıcı görevi gören `IDefinitionIdentity` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="74fa0-120">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
 [<span data-ttu-id="74fa0-121">IEnumIDENTITY_ATTRIBUTE Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74fa0-121">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)  
 <span data-ttu-id="74fa0-122">Geçerli kapsamdaki kod nesnesinin öznitelikleri için bir numaralandırıcı olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="74fa0-122">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
 [<span data-ttu-id="74fa0-123">IEnumReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74fa0-123">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 <span data-ttu-id="74fa0-124">Bir koleksiyonu için bir numaralandırıcı görevi gören `IReferenceIdentity` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="74fa0-124">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
 [<span data-ttu-id="74fa0-125">IIdentityAuthority Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74fa0-125">IIdentityAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)  
 <span data-ttu-id="74fa0-126">Kod nesneleri kimlik tuşları yönetir.</span><span class="sxs-lookup"><span data-stu-id="74fa0-126">Manages identity keys for code objects.</span></span>  
  
 [<span data-ttu-id="74fa0-127">IInstallReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74fa0-127">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)  
 <span data-ttu-id="74fa0-128">Genel derleme önbelleğinde yüklü başvurulan derlemeler için bir numaralandırıcı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="74fa0-128">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="74fa0-129">IInstallReferenceItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74fa0-129">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 <span data-ttu-id="74fa0-130">Genel derleme önbelleğinde yüklü bir öğeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="74fa0-130">Represents an item installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="74fa0-131">IReferenceAppId Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74fa0-131">IReferenceAppId Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md)  
 <span data-ttu-id="74fa0-132">Geçerli kapsamdaki uygulama için benzersiz tanımlayıcı başvuru temsil eder.</span><span class="sxs-lookup"><span data-stu-id="74fa0-132">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
 [<span data-ttu-id="74fa0-133">IReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74fa0-133">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)  
 <span data-ttu-id="74fa0-134">Bir kod nesnesinin benzersiz imza başvuru temsil eder.</span><span class="sxs-lookup"><span data-stu-id="74fa0-134">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="74fa0-135">Başvuru</span><span class="sxs-lookup"><span data-stu-id="74fa0-135">Reference</span></span>  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a><span data-ttu-id="74fa0-136">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="74fa0-136">Related Sections</span></span>  
 [<span data-ttu-id="74fa0-137">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="74fa0-137">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
  
 [<span data-ttu-id="74fa0-138">Fusion Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="74fa0-138">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [<span data-ttu-id="74fa0-139">Fusion Yapıları</span><span class="sxs-lookup"><span data-stu-id="74fa0-139">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
