---
title: IMetaDataConverter::GetMetaDataFromTypeLib Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeLib
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib
helpviewer_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib method [.NET Framework metadata]
- GetMetaDataFromTypeLib method [.NET Framework metadata]
ms.assetid: 97dc3a56-adfa-431f-889e-06a35ac84d51
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cdc1b0de9795a000ee680df880c73acc4f711db2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62044375"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="be094-102">IMetaDataConverter::GetMetaDataFromTypeLib Yöntemi</span><span class="sxs-lookup"><span data-stu-id="be094-102">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>
<span data-ttu-id="be094-103">Bir arabirim işaretçisi alır bir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) belirtilen tarafından temsil edilen tür kitaplığını meta veri imzası temsil eden örneği `ITypeLib` örneği.</span><span class="sxs-lookup"><span data-stu-id="be094-103">Gets an interface pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be094-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be094-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,   
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be094-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="be094-105">Parameters</span></span>  
 `pITL`  
 <span data-ttu-id="be094-106">[in] İşaretçi bir `ITypeLib` tür kitaplığı temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="be094-106">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="be094-107">[out] İşaretçi adresini alan bir konuma `IMetaDataImport` meta veri imzası temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="be094-107">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be094-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be094-108">Requirements</span></span>  
 <span data-ttu-id="be094-109">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be094-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be094-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="be094-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="be094-111">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="be094-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="be094-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be094-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be094-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be094-113">See also</span></span>

- [<span data-ttu-id="be094-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be094-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="be094-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be094-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
