---
title: IMetaDataConverter::GetTypeLibFromMetaData Metodu
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
ms.openlocfilehash: 9351738e979b49ec23b51a2fa554fc219e163541
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444122"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="4eb68-102">IMetaDataConverter::GetTypeLibFromMetaData Metodu</span><span class="sxs-lookup"><span data-stu-id="4eb68-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="4eb68-103">Bir işaretçi alır bir `ITypeLib` Belirtilen kitaplık ve modül adlara sahip tür kitaplığı temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="4eb68-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4eb68-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4eb68-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,   
    [in]  BSTR     strTlbName,   
    [out] ITypeLib **ppITL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4eb68-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4eb68-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="4eb68-106">[in] Tür kitaplığının modülü adı.</span><span class="sxs-lookup"><span data-stu-id="4eb68-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="4eb68-107">[in] Tür kitaplığı adı.</span><span class="sxs-lookup"><span data-stu-id="4eb68-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="4eb68-108">[out] Bir işaretçi adresini alır bir konuma `ITypeLib` tür kitaplığı temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="4eb68-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4eb68-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4eb68-109">Requirements</span></span>  
 <span data-ttu-id="4eb68-110">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4eb68-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4eb68-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4eb68-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4eb68-112">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="4eb68-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4eb68-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4eb68-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eb68-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4eb68-114">See Also</span></span>  
 [<span data-ttu-id="4eb68-115">IMetaDataConverter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4eb68-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
