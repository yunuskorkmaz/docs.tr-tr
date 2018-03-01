---
title: IMetaDataConverter Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataConverter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter
helpviewer_keywords:
- IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 758ea4261b859773c600ca91d52e3a9053776136
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="078f6-102">IMetaDataConverter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="078f6-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="078f6-103">Tür kitaplıkları kendi meta verileri imzalar için eşleme ve diğerine dönüştürmek için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="078f6-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="078f6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="078f6-104">Methods</span></span>  
  
|<span data-ttu-id="078f6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="078f6-105">Method</span></span>|<span data-ttu-id="078f6-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="078f6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="078f6-107">GetMetaDataFromTypeInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="078f6-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="078f6-108">Bir işaretçi alır bir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) belirtilen tarafından başvurulan tür kitaplığı için meta veri imzası temsil eden örneği `ITypeInfo` örneği.</span><span class="sxs-lookup"><span data-stu-id="078f6-108">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="078f6-109">GetMetaDataFromTypeLib Yöntemi</span><span class="sxs-lookup"><span data-stu-id="078f6-109">GetMetaDataFromTypeLib Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="078f6-110">Bir işaretçi alır bir `IMetaDataImport` belirtilen tarafından temsil edilen tür kitaplığı için meta veri imzası temsil eden örneği `ITypeLib` örneği.</span><span class="sxs-lookup"><span data-stu-id="078f6-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="078f6-111">GetTypeLibFromMetaData Yöntemi</span><span class="sxs-lookup"><span data-stu-id="078f6-111">GetTypeLibFromMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="078f6-112">Bir işaretçi alır bir `ITypeLib` belirtilen modülü ve kitaplık adlara sahip tür kitaplığı temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="078f6-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="078f6-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="078f6-113">Requirements</span></span>  
 <span data-ttu-id="078f6-114">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="078f6-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="078f6-115">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="078f6-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="078f6-116">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="078f6-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="078f6-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="078f6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="078f6-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="078f6-118">See Also</span></span>  
 [<span data-ttu-id="078f6-119">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="078f6-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="078f6-120">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="078f6-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
