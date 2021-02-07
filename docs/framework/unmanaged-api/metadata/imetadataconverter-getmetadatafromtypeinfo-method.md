---
description: ': IMetaDataConverter:: GetMetaDataFromTypeInfo yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 224be07463b19ed9e22bef1a9d454d91a8086304
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753633"
---
# <a name="imetadataconvertergetmetadatafromtypeinfo-method"></a><span data-ttu-id="ae882-103">IMetaDataConverter::GetMetaDataFromTypeInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="ae882-103">IMetaDataConverter::GetMetaDataFromTypeInfo Method</span></span>

<span data-ttu-id="ae882-104">Belirtilen örnek tarafından başvurulan tür kitaplığının meta veri imzasını temsil eden bir [IMetaDataImport](imetadataimport-interface.md) örneğine yönelik bir işaretçi alır `ITypeInfo` .</span><span class="sxs-lookup"><span data-stu-id="ae882-104">Gets a pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature of the type library referenced by the specified `ITypeInfo` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae882-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae882-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeInfo (  
    [in]  ITypeInfo         *pITI,  
    [out] IMetaDataImport   **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae882-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ae882-106">Parameters</span></span>  

 `pITI`  
 <span data-ttu-id="ae882-107">'ndaki `ITypeInfo` Tür kitaplığına başvuran bir nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ae882-107">[in] A pointer to an `ITypeInfo` object that refers to the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="ae882-108">dışı `IMetaDataImport` Meta veri imzasını temsil eden örneğin adresini alan bir konum işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ae882-108">[out] A pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae882-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae882-109">Requirements</span></span>  

 <span data-ttu-id="ae882-110">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae882-110">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae882-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ae882-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ae882-112">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ae882-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ae882-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae882-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae882-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae882-114">See also</span></span>

- [<span data-ttu-id="ae882-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae882-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="ae882-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae882-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
