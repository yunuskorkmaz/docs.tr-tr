---
title: "StrongNameFreeBuffer İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameFreeBuffer
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: StrongNameFreeBuffer
helpviewer_keywords: StrongNameFreeBuffer function [.NET Framework strong naming]
ms.assetid: eda21ecf-4734-4f92-aaba-9f34884385db
topic_type: apiref
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ef48c79cc7dc0fb7d881e0cced29741431044551
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="9feb4-102">StrongNameFreeBuffer İşlevi</span><span class="sxs-lookup"><span data-stu-id="9feb4-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="9feb4-103">Önceki bir güçlü ad işlevi çağrısı ile ayrıldı bellek boşaltır [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), veya [StrongNameSignatureGeneration ](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="9feb4-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="9feb4-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="9feb4-104">This function has been deprecated.</span></span> <span data-ttu-id="9feb4-105">Kullanım [Iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="9feb4-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9feb4-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9feb4-106">Syntax</span></span>  
  
```  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9feb4-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9feb4-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="9feb4-108">[in] Bellek boşaltmak için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9feb4-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9feb4-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9feb4-109">Requirements</span></span>  
 <span data-ttu-id="9feb4-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9feb4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9feb4-111">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="9feb4-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="9feb4-112">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9feb4-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9feb4-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9feb4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9feb4-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9feb4-114">See Also</span></span>  
 [<span data-ttu-id="9feb4-115">StrongNameFreeBuffer yöntemi</span><span class="sxs-lookup"><span data-stu-id="9feb4-115">StrongNameFreeBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)  
 [<span data-ttu-id="9feb4-116">Iclrstrongname arabirimi</span><span class="sxs-lookup"><span data-stu-id="9feb4-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
