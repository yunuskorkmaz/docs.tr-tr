---
title: IMetaDataImport::GetUserString Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetUserString
helpviewer_keywords:
- IMetaDataImport::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0fd3bb47-58b5-4083-b241-b9719df7a285
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 944d7e6413f35ad56af38dee90dc90f881c1d4cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="dbe2c-102">IMetaDataImport::GetUserString Metodu</span><span class="sxs-lookup"><span data-stu-id="dbe2c-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="dbe2c-103">Belirtilen meta veri simgesi tarafından temsil edilen sabit değerli bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="dbe2c-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbe2c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dbe2c-104">Syntax</span></span>  
  
```  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dbe2c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dbe2c-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="dbe2c-106">[in] İlişkili dizesi döndürülecek dize belirteci.</span><span class="sxs-lookup"><span data-stu-id="dbe2c-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="dbe2c-107">[out] İstenen dize bir kopyası.</span><span class="sxs-lookup"><span data-stu-id="dbe2c-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="dbe2c-108">[in] Geniş karakterler istenen en büyük boyutu `szString`.</span><span class="sxs-lookup"><span data-stu-id="dbe2c-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="dbe2c-109">[out] Geniş karakterler dönen boyutu `szString`.</span><span class="sxs-lookup"><span data-stu-id="dbe2c-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbe2c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dbe2c-110">Requirements</span></span>  
 <span data-ttu-id="dbe2c-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbe2c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbe2c-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dbe2c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dbe2c-113">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="dbe2c-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dbe2c-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbe2c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbe2c-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dbe2c-115">See Also</span></span>  
 [<span data-ttu-id="dbe2c-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dbe2c-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="dbe2c-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dbe2c-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
