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
ms.openlocfilehash: 1f45310bc65bc8614033182a81db451b79bcf97f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714724"
---
# <a name="imetadataconvertergetmetadatafromtypeinfo-method"></a><span data-ttu-id="9b65d-102">IMetaDataConverter::GetMetaDataFromTypeInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="9b65d-102">IMetaDataConverter::GetMetaDataFromTypeInfo Method</span></span>

<span data-ttu-id="9b65d-103">Belirtilen örnek tarafından başvurulan tür kitaplığının meta veri imzasını temsil eden bir [IMetaDataImport](imetadataimport-interface.md) örneğine yönelik bir işaretçi alır `ITypeInfo` .</span><span class="sxs-lookup"><span data-stu-id="9b65d-103">Gets a pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature of the type library referenced by the specified `ITypeInfo` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b65d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9b65d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeInfo (  
    [in]  ITypeInfo         *pITI,  
    [out] IMetaDataImport   **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b65d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9b65d-105">Parameters</span></span>  

 `pITI`  
 <span data-ttu-id="9b65d-106">'ndaki `ITypeInfo` Tür kitaplığına başvuran bir nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="9b65d-106">[in] A pointer to an `ITypeInfo` object that refers to the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="9b65d-107">dışı `IMetaDataImport` Meta veri imzasını temsil eden örneğin adresini alan bir konum işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="9b65d-107">[out] A pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b65d-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b65d-108">Requirements</span></span>  

 <span data-ttu-id="9b65d-109">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b65d-109">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b65d-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9b65d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9b65d-111">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="9b65d-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9b65d-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b65d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b65d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b65d-113">See also</span></span>

- [<span data-ttu-id="9b65d-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b65d-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="9b65d-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b65d-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
