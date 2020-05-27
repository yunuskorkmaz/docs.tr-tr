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
ms.openlocfilehash: 8f8c0c2cb8dea8ad2b9c0040654122ef5942aca0
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008397"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="7721c-102">IMetaDataConverter::GetMetaDataFromTypeLib Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7721c-102">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>
<span data-ttu-id="7721c-103">Belirtilen örnek tarafından temsil edilen tür kitaplığının meta veri imzasını temsil eden bir [IMetaDataImport](imetadataimport-interface.md) örneğine yönelik bir arabirim işaretçisi alır `ITypeLib` .</span><span class="sxs-lookup"><span data-stu-id="7721c-103">Gets an interface pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7721c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7721c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7721c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7721c-105">Parameters</span></span>  
 `pITL`  
 <span data-ttu-id="7721c-106">'ndaki `ITypeLib`Tür kitaplığını temsil eden bir nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7721c-106">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="7721c-107">dışı `IMetaDataImport`Meta veri imzasını temsil eden örneğin adresini alan bir konum işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7721c-107">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7721c-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7721c-108">Requirements</span></span>  
 <span data-ttu-id="7721c-109">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7721c-109">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7721c-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7721c-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7721c-111">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="7721c-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7721c-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7721c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7721c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7721c-113">See also</span></span>

- [<span data-ttu-id="7721c-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7721c-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="7721c-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7721c-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
