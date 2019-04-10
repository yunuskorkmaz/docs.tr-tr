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
ms.openlocfilehash: c0943971dc4858e2dce4d977f6f906b26f8ad51e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231021"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="06de8-102">IMetaDataConverter::GetTypeLibFromMetaData Yöntemi</span><span class="sxs-lookup"><span data-stu-id="06de8-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="06de8-103">Bir işaretçi alır bir `ITypeLib` Belirtilen kitaplık ve modül adlarını içeren bir tür kitaplığı temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="06de8-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06de8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06de8-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,   
    [in]  BSTR     strTlbName,   
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06de8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="06de8-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="06de8-106">[in] Tür kitaplığının modülünün adı.</span><span class="sxs-lookup"><span data-stu-id="06de8-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="06de8-107">[in] Tür kitaplığının adı.</span><span class="sxs-lookup"><span data-stu-id="06de8-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="06de8-108">[out] Bir işaretçi adresini alan bir konuma `ITypeLib` tür kitaplığı temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="06de8-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06de8-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06de8-109">Requirements</span></span>  
 <span data-ttu-id="06de8-110">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06de8-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06de8-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="06de8-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="06de8-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="06de8-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="06de8-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="06de8-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="06de8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06de8-114">See also</span></span>

- [<span data-ttu-id="06de8-115">IMetaDataConverter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="06de8-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
