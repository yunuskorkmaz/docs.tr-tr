---
description: ': IMetaDataConverter:: GetMetaDataFromTypeLib Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: d1ed5feb9f42ea0f8dc802c4dad527be5d2ed25f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789287"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="048ec-103">IMetaDataConverter::GetMetaDataFromTypeLib Yöntemi</span><span class="sxs-lookup"><span data-stu-id="048ec-103">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>

<span data-ttu-id="048ec-104">Belirtilen örnek tarafından temsil edilen tür kitaplığının meta veri imzasını temsil eden bir [IMetaDataImport](imetadataimport-interface.md) örneğine yönelik bir arabirim işaretçisi alır `ITypeLib` .</span><span class="sxs-lookup"><span data-stu-id="048ec-104">Gets an interface pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="048ec-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="048ec-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="048ec-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="048ec-106">Parameters</span></span>  

 `pITL`  
 <span data-ttu-id="048ec-107">'ndaki `ITypeLib` Tür kitaplığını temsil eden bir nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="048ec-107">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="048ec-108">dışı `IMetaDataImport` Meta veri imzasını temsil eden örneğin adresini alan bir konum işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="048ec-108">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="048ec-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="048ec-109">Requirements</span></span>  

 <span data-ttu-id="048ec-110">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="048ec-110">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="048ec-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="048ec-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="048ec-112">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="048ec-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="048ec-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="048ec-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="048ec-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="048ec-114">See also</span></span>

- [<span data-ttu-id="048ec-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="048ec-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="048ec-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="048ec-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
