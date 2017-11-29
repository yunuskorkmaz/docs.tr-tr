---
title: "StrongNameHashSize İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameHashSize
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameHashSize
helpviewer_keywords: StrongNameHashSize function [.NET Framework strong naming]
ms.assetid: 738c98d7-a60c-45fe-a296-220af05e6991
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: baf9c9b2219ff3fb784972b1f54a2b50dcd8657d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="3d822-102">StrongNameHashSize İşlevi</span><span class="sxs-lookup"><span data-stu-id="3d822-102">StrongNameHashSize Function</span></span>
<span data-ttu-id="3d822-103">Belirtilen karma algoritması kullanan bir karma için gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="3d822-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="3d822-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="3d822-104">This function has been deprecated.</span></span> <span data-ttu-id="3d822-105">Kullanım [Iclrstrongname::strongnamehashsize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="3d822-105">Use the [ICLRStrongName::StrongNameHashSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d822-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d822-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d822-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3d822-107">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="3d822-108">[in] Arabellek boyutu hesaplamak için kullanılan karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="3d822-108">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="3d822-109">[out] Bayt cinsinden döndürülen arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="3d822-109">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d822-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3d822-110">Return Value</span></span>  
 <span data-ttu-id="3d822-111">`true`başarılı tamamlanma; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="3d822-111">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d822-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d822-112">Remarks</span></span>  
 <span data-ttu-id="3d822-113">Varsa `StrongNameHashSize` işlevi yok başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) son oluşturulan hata alınacak işlev.</span><span class="sxs-lookup"><span data-stu-id="3d822-113">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d822-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d822-114">Requirements</span></span>  
 <span data-ttu-id="3d822-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d822-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d822-116">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="3d822-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="3d822-117">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3d822-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3d822-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d822-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d822-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3d822-119">See Also</span></span>  
 [<span data-ttu-id="3d822-120">StrongNameHashSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="3d822-120">StrongNameHashSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)  
 [<span data-ttu-id="3d822-121">Iclrstrongname arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d822-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
