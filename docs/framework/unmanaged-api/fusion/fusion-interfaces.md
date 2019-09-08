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
ms.openlocfilehash: 1605605f8510f7ccf5f0bbf2f3f6b09050a16025
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795310"
---
# <a name="fusion-interfaces"></a><span data-ttu-id="d448e-102">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d448e-102">Fusion Interfaces</span></span>
<span data-ttu-id="d448e-103">Bu bölümde, Fusion API 'sinin bir uygulama kaynaklarının özelliklerine erişmek ve uygulama için bu kaynakların doğru sürümlerini bulmak için kullandığı yönetilmeyen arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d448e-103">This section describes the unmanaged interfaces that the fusion API uses to access the properties of an application's resources and to locate the correct versions of those resources for the application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d448e-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d448e-104">In This Section</span></span>  
 [<span data-ttu-id="d448e-105">IAppIdAuthority Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d448e-105">IAppIdAuthority Interface</span></span>](iappidauthority-interface.md)  
 <span data-ttu-id="d448e-106">Uygulama kimlikleri ve başvuruları için anahtarlar oluşturan ve karşılaştıran yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d448e-106">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="d448e-107">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d448e-107">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)  
 <span data-ttu-id="d448e-108">Genel derleme önbelleğinin gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d448e-108">Provides a representation of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="d448e-109">IAssemblyCacheItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d448e-109">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)  
 <span data-ttu-id="d448e-110">Genel derleme önbelleğindeki tek bir derlemeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d448e-110">Represents a single assembly in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="d448e-111">IAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d448e-111">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)  
 <span data-ttu-id="d448e-112">Bir `IAssemblyName` nesne dizisi için bir numaralandırıcısı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d448e-112">Represents an enumerator for an array of `IAssemblyName` objects.</span></span>  
  
 [<span data-ttu-id="d448e-113">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d448e-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)  
 <span data-ttu-id="d448e-114">Bir derlemenin benzersiz kimliğini tanımlamak ve bunlarla çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d448e-114">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
 [<span data-ttu-id="d448e-115">IDefinitionAppId Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d448e-115">IDefinitionAppId Interface</span></span>](idefinitionappid-interface.md)  
 <span data-ttu-id="d448e-116">Geçerli kapsamda uygulamayı tanımlayan kod için benzersiz tanımlayıcıyı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d448e-116">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="d448e-117">IDefinitionIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d448e-117">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)  
 <span data-ttu-id="d448e-118">Geçerli kapsamdaki uygulamayı tanımlayan kodun benzersiz imzasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d448e-118">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="d448e-119">IEnumDefinitionIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d448e-119">IEnumDefinitionIdentity Interface</span></span>](ienumdefinitionidentity-interface.md)  
 <span data-ttu-id="d448e-120">Bir `IDefinitionIdentity` nesne koleksiyonu için numaralandırıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="d448e-120">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
 [<span data-ttu-id="d448e-121">IEnumIDENTITY_ATTRIBUTE Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d448e-121">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)  
 <span data-ttu-id="d448e-122">Geçerli kapsamdaki kod nesnesinin öznitelikleri için bir Numaralandırıcı işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="d448e-122">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
 [<span data-ttu-id="d448e-123">IEnumReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d448e-123">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)  
 <span data-ttu-id="d448e-124">Bir `IReferenceIdentity` nesne koleksiyonu için bir Numaralandırıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="d448e-124">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
 [<span data-ttu-id="d448e-125">IIdentityAuthority Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d448e-125">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)  
 <span data-ttu-id="d448e-126">Kod nesneleri için kimlik anahtarlarını yönetir.</span><span class="sxs-lookup"><span data-stu-id="d448e-126">Manages identity keys for code objects.</span></span>  
  
 [<span data-ttu-id="d448e-127">IInstallReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d448e-127">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)  
 <span data-ttu-id="d448e-128">Genel derleme önbelleğinde yüklü olan başvurulan derlemeler için bir Numaralandırıcı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d448e-128">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="d448e-129">IInstallReferenceItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d448e-129">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)  
 <span data-ttu-id="d448e-130">Genel derleme önbelleğinde yüklü olan bir öğeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d448e-130">Represents an item installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="d448e-131">IReferenceAppId Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d448e-131">IReferenceAppId Interface</span></span>](ireferenceappid-interface.md)  
 <span data-ttu-id="d448e-132">Geçerli kapsamdaki uygulamanın benzersiz tanımlayıcısına yönelik bir başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d448e-132">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
 [<span data-ttu-id="d448e-133">IReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d448e-133">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)  
 <span data-ttu-id="d448e-134">Bir kod nesnesinin benzersiz imzasına bir başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d448e-134">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d448e-135">Başvuru</span><span class="sxs-lookup"><span data-stu-id="d448e-135">Reference</span></span>  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a><span data-ttu-id="d448e-136">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="d448e-136">Related Sections</span></span>  
 [<span data-ttu-id="d448e-137">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d448e-137">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)  
  
 [<span data-ttu-id="d448e-138">Fusion Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d448e-138">Fusion Enumerations</span></span>](fusion-enumerations.md)  
  
 [<span data-ttu-id="d448e-139">Fusion Yapıları</span><span class="sxs-lookup"><span data-stu-id="d448e-139">Fusion Structures</span></span>](fusion-structures.md)
