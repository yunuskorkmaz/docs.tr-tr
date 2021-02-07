---
description: 'Daha fazla bilgi edinin: Fusion arabirimleri'
title: Fusion Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework fusion]
- fusion interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], fusion
ms.assetid: e2cf98b7-40c1-4f74-86c7-8a76dd9da677
ms.openlocfilehash: 3b6ca64b40ebc1a7b38129d897059ca628d3914c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761071"
---
# <a name="fusion-interfaces"></a><span data-ttu-id="ee60f-103">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ee60f-103">Fusion Interfaces</span></span>

<span data-ttu-id="ee60f-104">Bu bölümde, Fusion API 'sinin bir uygulama kaynaklarının özelliklerine erişmek ve uygulama için bu kaynakların doğru sürümlerini bulmak için kullandığı yönetilmeyen arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ee60f-104">This section describes the unmanaged interfaces that the fusion API uses to access the properties of an application's resources and to locate the correct versions of those resources for the application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ee60f-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ee60f-105">In This Section</span></span>  

 [<span data-ttu-id="ee60f-106">IAppIdAuthority Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee60f-106">IAppIdAuthority Interface</span></span>](iappidauthority-interface.md)  
 <span data-ttu-id="ee60f-107">Uygulama kimlikleri ve başvuruları için anahtarlar oluşturan ve karşılaştıran yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee60f-107">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="ee60f-108">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee60f-108">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)  
 <span data-ttu-id="ee60f-109">Genel derleme önbelleğinin gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee60f-109">Provides a representation of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="ee60f-110">IAssemblyCacheItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee60f-110">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)  
 <span data-ttu-id="ee60f-111">Genel derleme önbelleğindeki tek bir derlemeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ee60f-111">Represents a single assembly in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="ee60f-112">IAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee60f-112">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)  
 <span data-ttu-id="ee60f-113">Bir nesne dizisi için bir numaralandırıcısı temsil eder `IAssemblyName` .</span><span class="sxs-lookup"><span data-stu-id="ee60f-113">Represents an enumerator for an array of `IAssemblyName` objects.</span></span>  
  
 [<span data-ttu-id="ee60f-114">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee60f-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)  
 <span data-ttu-id="ee60f-115">Bir derlemenin benzersiz kimliğini tanımlamak ve bunlarla çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee60f-115">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
 [<span data-ttu-id="ee60f-116">IDefinitionAppId Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee60f-116">IDefinitionAppId Interface</span></span>](idefinitionappid-interface.md)  
 <span data-ttu-id="ee60f-117">Geçerli kapsamda uygulamayı tanımlayan kod için benzersiz tanımlayıcıyı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ee60f-117">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="ee60f-118">IDefinitionIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee60f-118">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)  
 <span data-ttu-id="ee60f-119">Geçerli kapsamdaki uygulamayı tanımlayan kodun benzersiz imzasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ee60f-119">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="ee60f-120">IEnumDefinitionIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee60f-120">IEnumDefinitionIdentity Interface</span></span>](ienumdefinitionidentity-interface.md)  
 <span data-ttu-id="ee60f-121">Bir nesne koleksiyonu için numaralandırıcı görevi görür `IDefinitionIdentity` .</span><span class="sxs-lookup"><span data-stu-id="ee60f-121">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
 [<span data-ttu-id="ee60f-122">IEnumIDENTITY_ATTRIBUTE Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee60f-122">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)  
 <span data-ttu-id="ee60f-123">Geçerli kapsamdaki kod nesnesinin öznitelikleri için bir Numaralandırıcı işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="ee60f-123">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
 [<span data-ttu-id="ee60f-124">IEnumReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee60f-124">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)  
 <span data-ttu-id="ee60f-125">Bir nesne koleksiyonu için bir Numaralandırıcı görevi görür `IReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="ee60f-125">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
 [<span data-ttu-id="ee60f-126">IIdentityAuthority Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee60f-126">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)  
 <span data-ttu-id="ee60f-127">Kod nesneleri için kimlik anahtarlarını yönetir.</span><span class="sxs-lookup"><span data-stu-id="ee60f-127">Manages identity keys for code objects.</span></span>  
  
 [<span data-ttu-id="ee60f-128">IInstallReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee60f-128">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)  
 <span data-ttu-id="ee60f-129">Genel derleme önbelleğinde yüklü olan başvurulan derlemeler için bir Numaralandırıcı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ee60f-129">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="ee60f-130">IInstallReferenceItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee60f-130">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)  
 <span data-ttu-id="ee60f-131">Genel derleme önbelleğinde yüklü olan bir öğeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ee60f-131">Represents an item installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="ee60f-132">IReferenceAppId Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee60f-132">IReferenceAppId Interface</span></span>](ireferenceappid-interface.md)  
 <span data-ttu-id="ee60f-133">Geçerli kapsamdaki uygulamanın benzersiz tanımlayıcısına yönelik bir başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ee60f-133">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
 [<span data-ttu-id="ee60f-134">IReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee60f-134">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)  
 <span data-ttu-id="ee60f-135">Bir kod nesnesinin benzersiz imzasına bir başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ee60f-135">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ee60f-136">Başvuru</span><span class="sxs-lookup"><span data-stu-id="ee60f-136">Reference</span></span>  

 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a><span data-ttu-id="ee60f-137">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="ee60f-137">Related Sections</span></span>  

 [<span data-ttu-id="ee60f-138">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="ee60f-138">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)  
  
 [<span data-ttu-id="ee60f-139">Fusion Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="ee60f-139">Fusion Enumerations</span></span>](fusion-enumerations.md)  
  
 [<span data-ttu-id="ee60f-140">Fusion Yapıları</span><span class="sxs-lookup"><span data-stu-id="ee60f-140">Fusion Structures</span></span>](fusion-structures.md)
