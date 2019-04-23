---
title: StrongNameHashSize İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameHashSize
helpviewer_keywords:
- StrongNameHashSize function [.NET Framework strong naming]
ms.assetid: 738c98d7-a60c-45fe-a296-220af05e6991
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7e807b502e0905f9ae785203289447c71d25e04
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072151"
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="557bb-102">StrongNameHashSize İşlevi</span><span class="sxs-lookup"><span data-stu-id="557bb-102">StrongNameHashSize Function</span></span>
<span data-ttu-id="557bb-103">Belirtilen karma algoritması kullanarak bir karma için gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="557bb-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="557bb-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="557bb-104">This function has been deprecated.</span></span> <span data-ttu-id="557bb-105">Kullanım [Iclrstrongname::strongnamehashsize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="557bb-105">Use the [ICLRStrongName::StrongNameHashSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="557bb-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="557bb-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="557bb-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="557bb-107">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="557bb-108">[in] Arabellek boyutunu hesaplamak için kullanılan karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="557bb-108">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="557bb-109">[out] Döndürülen arabellek bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="557bb-109">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="557bb-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="557bb-110">Return Value</span></span>  
 <span data-ttu-id="557bb-111">`true` başarıyla tamamlandığında; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="557bb-111">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="557bb-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="557bb-112">Remarks</span></span>  
 <span data-ttu-id="557bb-113">Varsa `StrongNameHashSize` işlevi değil başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) oluşturulan son hatayı alması için işlevi.</span><span class="sxs-lookup"><span data-stu-id="557bb-113">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="557bb-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="557bb-114">Requirements</span></span>  
 <span data-ttu-id="557bb-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="557bb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="557bb-116">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="557bb-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="557bb-117">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="557bb-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="557bb-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="557bb-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="557bb-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="557bb-119">See also</span></span>

- [<span data-ttu-id="557bb-120">StrongNameHashSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="557bb-120">StrongNameHashSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)
- [<span data-ttu-id="557bb-121">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="557bb-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
