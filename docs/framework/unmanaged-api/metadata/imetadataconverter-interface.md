---
title: IMetaDataConverter Arabirimi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d3377617ddd6b82ad88d22f6ffda04b1d6ae837
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904756"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="720f3-102">IMetaDataConverter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="720f3-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="720f3-103">Tür kitaplıkları, meta verileri imza eşlemek için ve biri diğerine dönüştürmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="720f3-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="720f3-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="720f3-104">Methods</span></span>  
  
|<span data-ttu-id="720f3-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="720f3-105">Method</span></span>|<span data-ttu-id="720f3-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="720f3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="720f3-107">GetMetaDataFromTypeInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="720f3-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="720f3-108">Bir işaretçi alır bir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) belirtilen tarafından başvurulan tür kitaplığının meta veri imzası temsil eden örneği `ITypeInfo` örneği.</span><span class="sxs-lookup"><span data-stu-id="720f3-108">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="720f3-109">GetMetaDataFromTypeLib Yöntemi</span><span class="sxs-lookup"><span data-stu-id="720f3-109">GetMetaDataFromTypeLib Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="720f3-110">Bir işaretçi alır bir `IMetaDataImport` belirtilen tarafından temsil edilen tür kitaplığı için meta verileri imza temsil eden örneği `ITypeLib` örneği.</span><span class="sxs-lookup"><span data-stu-id="720f3-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="720f3-111">GetTypeLibFromMetaData Yöntemi</span><span class="sxs-lookup"><span data-stu-id="720f3-111">GetTypeLibFromMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="720f3-112">Bir işaretçi alır bir `ITypeLib` Belirtilen modül ve kitaplık adlara sahip bir tür kitaplığı temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="720f3-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="720f3-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="720f3-113">Requirements</span></span>  
 <span data-ttu-id="720f3-114">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="720f3-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="720f3-115">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="720f3-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="720f3-116">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="720f3-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="720f3-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="720f3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="720f3-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="720f3-118">See also</span></span>

- [<span data-ttu-id="720f3-119">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="720f3-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="720f3-120">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="720f3-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
