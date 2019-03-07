---
title: IMetaDataConverter::GetMetaDataFromTypeInfo Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeInfo
helpviewer_keywords:
- GetMetaDataFromTypeInfo method [.NET Framework metadata]
- IMetaDataConverter::GetMetaDataFromTypeInfo method [.NET Framework metadata]
ms.assetid: d44484bb-23a3-49c3-9e46-69d0d9ab4f0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8619bf0e62752513b1ae03fa01d22be40f65e58e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468864"
---
# <a name="imetadataconvertergetmetadatafromtypeinfo-method"></a><span data-ttu-id="ff4b0-102">IMetaDataConverter::GetMetaDataFromTypeInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="ff4b0-102">IMetaDataConverter::GetMetaDataFromTypeInfo Method</span></span>
<span data-ttu-id="ff4b0-103">Bir işaretçi alır bir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) belirtilen tarafından başvurulan tür kitaplığının meta veri imzası temsil eden örneği `ITypeInfo` örneği.</span><span class="sxs-lookup"><span data-stu-id="ff4b0-103">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library referenced by the specified `ITypeInfo` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff4b0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff4b0-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataFromTypeInfo (  
    [in]  ITypeInfo         *pITI,  
    [out] IMetaDataImport   **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff4b0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ff4b0-105">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="ff4b0-106">[in] Bir işaretçi bir `ITypeInfo` tür kitaplığına başvuran nesne.</span><span class="sxs-lookup"><span data-stu-id="ff4b0-106">[in] A pointer to an `ITypeInfo` object that refers to the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="ff4b0-107">[out] Bir işaretçi adresini alan bir konuma `IMetaDataImport` meta veri imzası temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="ff4b0-107">[out] A pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff4b0-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff4b0-108">Requirements</span></span>  
 <span data-ttu-id="ff4b0-109">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff4b0-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff4b0-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="ff4b0-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ff4b0-111">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="ff4b0-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ff4b0-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff4b0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff4b0-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff4b0-113">See also</span></span>
- [<span data-ttu-id="ff4b0-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff4b0-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ff4b0-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff4b0-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
