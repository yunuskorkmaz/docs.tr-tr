---
title: IMetaDataAssemblyEmit Arabirimi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit
helpviewer_keywords:
- IMetaDataAssemblyEmit interface [.NET Framework metadata]
ms.assetid: 34fb03cc-2285-4a45-ac48-ad993b7a921a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 02d52c5281662b8374869cf9424a6df9ee51e262
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550740"
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="30944-102">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30944-102">IMetaDataAssemblyEmit Interface</span></span>
<span data-ttu-id="30944-103">Çözmek ve kaynakları kullanmak için ortak dil çalışma zamanı tarafından kullanılan kendi kendine açıklama modelini desteklemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="30944-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="30944-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="30944-104">Methods</span></span>  
  
|<span data-ttu-id="30944-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="30944-105">Method</span></span>|<span data-ttu-id="30944-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30944-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="30944-107">DefineAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30944-107">DefineAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="30944-108">Belirtilen derleme için meta verileri içeren bir derleme veri yapısı oluşturur ve ilişkili meta veri belirteci döndürür.</span><span class="sxs-lookup"><span data-stu-id="30944-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="30944-109">DefineAssemblyRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30944-109">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="30944-110">Oluşturur bir `AssemblyRef` yapısı bu derlemeye başvuran bir derleme için meta verileri içeren ve ilişkili meta veri belirteci döndürür.</span><span class="sxs-lookup"><span data-stu-id="30944-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="30944-111">DefineExportedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30944-111">DefineExportedType Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="30944-112">Oluşturur bir `ExportedType` yapısı meta verilerini içeren, belirtilen dışarı türü ve ilişkili meta veri belirteci döndürür.</span><span class="sxs-lookup"><span data-stu-id="30944-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="30944-113">DefineFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30944-113">DefineFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="30944-114">Oluşturur bir `File` derleme bu derlemesi tarafından başvurulan ve ilişkili meta veri belirteci döndürür meta verilerini içeren meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="30944-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="30944-115">DefineManifestResource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30944-115">DefineManifestResource Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="30944-116">Oluşturur bir `ManifestResource` belirtilen bildirim kaynağı için meta veriler içeren yapı ve ilişkili meta veri belirteci döndürür.</span><span class="sxs-lookup"><span data-stu-id="30944-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="30944-117">SetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30944-117">SetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="30944-118">Belirtilen değiştirir `Assembly` meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="30944-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="30944-119">SetAssemblyRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30944-119">SetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="30944-120">Belirtilen değiştirir `AssemblyRef` meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="30944-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="30944-121">SetExportedTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30944-121">SetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="30944-122">Belirtilen değiştirir `ExportedType` meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="30944-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="30944-123">SetFileProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30944-123">SetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="30944-124">Belirtilen değiştirir `File` meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="30944-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="30944-125">SetManifestResourceProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30944-125">SetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="30944-126">Belirtilen değiştirir `ManifestResource` meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="30944-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30944-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30944-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30944-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30944-128">Requirements</span></span>  
 <span data-ttu-id="30944-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30944-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30944-130">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="30944-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="30944-131">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="30944-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="30944-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30944-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30944-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30944-133">See also</span></span>
- [<span data-ttu-id="30944-134">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="30944-134">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="30944-135">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30944-135">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
