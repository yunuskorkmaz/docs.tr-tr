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
ms.openlocfilehash: 9ab1d39ddb53e08e6fd36016f544162e2b11edb0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472076"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="51039-102">IMetaDataConverter::GetTypeLibFromMetaData Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51039-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="51039-103">Bir işaretçi alır bir `ITypeLib` Belirtilen kitaplık ve modül adlarını içeren bir tür kitaplığı temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="51039-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51039-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="51039-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,   
    [in]  BSTR     strTlbName,   
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51039-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="51039-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="51039-106">[in] Tür kitaplığının modülünün adı.</span><span class="sxs-lookup"><span data-stu-id="51039-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="51039-107">[in] Tür kitaplığının adı.</span><span class="sxs-lookup"><span data-stu-id="51039-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="51039-108">[out] Bir işaretçi adresini alan bir konuma `ITypeLib` tür kitaplığı temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="51039-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51039-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51039-109">Requirements</span></span>  
 <span data-ttu-id="51039-110">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51039-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51039-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="51039-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="51039-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="51039-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="51039-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51039-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51039-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51039-114">See also</span></span>
- [<span data-ttu-id="51039-115">IMetaDataConverter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51039-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
