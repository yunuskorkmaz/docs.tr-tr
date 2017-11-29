---
title: IMetaDataConverter::GetTypeLibFromMetaData Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataConverter.GetTypeLibFromMetaData
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataConverter::GetTypeLibFromMetaData
helpviewer_keywords:
- GetTypeLibFromMetaData method [.NET Framework metadata]
- IMetaDataConverter::GetTypeLibFromMetaData method [.NET Framework metadata]
ms.assetid: 90eab7b3-1fae-4af4-8bce-f7bc0e188a99
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b2b12c5f3ecb0d30fad3bfb5c96e0e66fd9ee7bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="55365-102">IMetaDataConverter::GetTypeLibFromMetaData Metodu</span><span class="sxs-lookup"><span data-stu-id="55365-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="55365-103">Bir işaretçi alır bir `ITypeLib` Belirtilen kitaplık ve modül adlara sahip tür kitaplığı temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="55365-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55365-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55365-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,   
    [in]  BSTR     strTlbName,   
    [out] ITypeLib **ppITL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="55365-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="55365-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="55365-106">[in] Tür kitaplığının modülü adı.</span><span class="sxs-lookup"><span data-stu-id="55365-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="55365-107">[in] Tür kitaplığı adı.</span><span class="sxs-lookup"><span data-stu-id="55365-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="55365-108">[out] Bir işaretçi adresini alır bir konuma `ITypeLib` tür kitaplığı temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="55365-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55365-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="55365-109">Requirements</span></span>  
 <span data-ttu-id="55365-110">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55365-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55365-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="55365-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="55365-112">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="55365-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="55365-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55365-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55365-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55365-114">See Also</span></span>  
 [<span data-ttu-id="55365-115">Imetadataconverter arabirimi</span><span class="sxs-lookup"><span data-stu-id="55365-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
