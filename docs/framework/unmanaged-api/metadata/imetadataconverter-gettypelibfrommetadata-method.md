---
title: IMetaDataConverter::GetTypeLibFromMetaData Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetTypeLibFromMetaData
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetTypeLibFromMetaData
helpviewer_keywords:
- GetTypeLibFromMetaData method [.NET Framework metadata]
- IMetaDataConverter::GetTypeLibFromMetaData method [.NET Framework metadata]
ms.assetid: 90eab7b3-1fae-4af4-8bce-f7bc0e188a99
topic_type:
- apiref
ms.openlocfilehash: 9da4e34fa948db2fc73cbde813bac9b3430605ca
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436255"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="16737-102">IMetaDataConverter::GetTypeLibFromMetaData Yöntemi</span><span class="sxs-lookup"><span data-stu-id="16737-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="16737-103">Belirtilen kitaplık ve modül adlarına sahip tür kitaplığını temsil eden bir `ITypeLib` örneğine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="16737-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16737-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16737-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,   
    [in]  BSTR     strTlbName,   
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16737-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="16737-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="16737-106">'ndaki Tür kitaplığının modülünün adı.</span><span class="sxs-lookup"><span data-stu-id="16737-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="16737-107">'ndaki Tür kitaplığının adı.</span><span class="sxs-lookup"><span data-stu-id="16737-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="16737-108">dışı Tür kitaplığını temsil eden `ITypeLib` örneğinin adresini alan bir konum işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="16737-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16737-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16737-109">Requirements</span></span>  
 <span data-ttu-id="16737-110">**Platform:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16737-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16737-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="16737-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="16737-112">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="16737-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="16737-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16737-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16737-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16737-114">See also</span></span>

- [<span data-ttu-id="16737-115">IMetaDataConverter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="16737-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
