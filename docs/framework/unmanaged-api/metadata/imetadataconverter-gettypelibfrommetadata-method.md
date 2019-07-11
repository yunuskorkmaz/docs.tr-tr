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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 208dd5ff2ba9eb450cac5a9807f0cd09852d5cf3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777826"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="350d3-102">IMetaDataConverter::GetTypeLibFromMetaData Yöntemi</span><span class="sxs-lookup"><span data-stu-id="350d3-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="350d3-103">Bir işaretçi alır bir `ITypeLib` Belirtilen kitaplık ve modül adlarını içeren bir tür kitaplığı temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="350d3-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="350d3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="350d3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,   
    [in]  BSTR     strTlbName,   
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="350d3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="350d3-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="350d3-106">[in] Tür kitaplığının modülünün adı.</span><span class="sxs-lookup"><span data-stu-id="350d3-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="350d3-107">[in] Tür kitaplığının adı.</span><span class="sxs-lookup"><span data-stu-id="350d3-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="350d3-108">[out] Bir işaretçi adresini alan bir konuma `ITypeLib` tür kitaplığı temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="350d3-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="350d3-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="350d3-109">Requirements</span></span>  
 <span data-ttu-id="350d3-110">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="350d3-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="350d3-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="350d3-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="350d3-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="350d3-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="350d3-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="350d3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="350d3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="350d3-114">See also</span></span>

- [<span data-ttu-id="350d3-115">IMetaDataConverter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="350d3-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
