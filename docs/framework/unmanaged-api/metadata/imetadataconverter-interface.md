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
ms.openlocfilehash: fc1f813cac237642fdaab653cd47552ab7472ab0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732934"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="7434e-102">IMetaDataConverter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7434e-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="7434e-103">Tür kitaplıkları, meta verileri imza eşlemek için ve biri diğerine dönüştürmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7434e-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7434e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7434e-104">Methods</span></span>  
  
|<span data-ttu-id="7434e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7434e-105">Method</span></span>|<span data-ttu-id="7434e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7434e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7434e-107">GetMetaDataFromTypeInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7434e-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="7434e-108">Bir işaretçi alır bir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) belirtilen tarafından başvurulan tür kitaplığının meta veri imzası temsil eden örneği `ITypeInfo` örneği.</span><span class="sxs-lookup"><span data-stu-id="7434e-108">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="7434e-109">GetMetaDataFromTypeLib Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7434e-109">GetMetaDataFromTypeLib Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="7434e-110">Bir işaretçi alır bir `IMetaDataImport` belirtilen tarafından temsil edilen tür kitaplığı için meta verileri imza temsil eden örneği `ITypeLib` örneği.</span><span class="sxs-lookup"><span data-stu-id="7434e-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="7434e-111">GetTypeLibFromMetaData Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7434e-111">GetTypeLibFromMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="7434e-112">Bir işaretçi alır bir `ITypeLib` Belirtilen modül ve kitaplık adlara sahip bir tür kitaplığı temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="7434e-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7434e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7434e-113">Requirements</span></span>  
 <span data-ttu-id="7434e-114">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7434e-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7434e-115">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7434e-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7434e-116">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="7434e-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7434e-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7434e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7434e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7434e-118">See also</span></span>
- [<span data-ttu-id="7434e-119">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7434e-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="7434e-120">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7434e-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
