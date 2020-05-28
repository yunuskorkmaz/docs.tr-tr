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
ms.openlocfilehash: b6ca7c619d32e69ffac20b80561171d0320db2d4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008384"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="e2ed6-102">IMetaDataConverter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2ed6-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="e2ed6-103">Tür kitaplıklarını meta veri imzalarına eşlemek ve birinden diğerine dönüştürmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2ed6-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e2ed6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e2ed6-104">Methods</span></span>  
  
|<span data-ttu-id="e2ed6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e2ed6-105">Method</span></span>|<span data-ttu-id="e2ed6-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2ed6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e2ed6-107">GetMetaDataFromTypeInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="e2ed6-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="e2ed6-108">Belirtilen örnek tarafından başvurulan tür kitaplığının meta veri imzasını temsil eden bir [IMetaDataImport](imetadataimport-interface.md) örneğine yönelik bir işaretçi alır `ITypeInfo` .</span><span class="sxs-lookup"><span data-stu-id="e2ed6-108">Gets a pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="e2ed6-109">GetMetaDataFromTypeLib Metodu</span><span class="sxs-lookup"><span data-stu-id="e2ed6-109">GetMetaDataFromTypeLib Method</span></span>](imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="e2ed6-110">`IMetaDataImport`Belirtilen örnek tarafından temsil edilen tür kitaplığı için meta veri imzasını temsil eden bir örneğe yönelik bir işaretçi alır `ITypeLib` .</span><span class="sxs-lookup"><span data-stu-id="e2ed6-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="e2ed6-111">GetTypeLibFromMetaData Metodu</span><span class="sxs-lookup"><span data-stu-id="e2ed6-111">GetTypeLibFromMetaData Method</span></span>](imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="e2ed6-112">`ITypeLib`Belirtilen modüle ve kitaplık adlarına sahip tür kitaplığını temsil eden bir örneğe yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="e2ed6-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e2ed6-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2ed6-113">Requirements</span></span>  
 <span data-ttu-id="e2ed6-114">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2ed6-114">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2ed6-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e2ed6-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e2ed6-116">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e2ed6-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e2ed6-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2ed6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2ed6-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2ed6-118">See also</span></span>

- [<span data-ttu-id="e2ed6-119">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e2ed6-119">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="e2ed6-120">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2ed6-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
