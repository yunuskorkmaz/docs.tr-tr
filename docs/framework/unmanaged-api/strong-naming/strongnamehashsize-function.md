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
ms.openlocfilehash: 8093a702069e4ecd4dad761ad0a431abe81d6141
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780422"
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="c2b76-102">StrongNameHashSize İşlevi</span><span class="sxs-lookup"><span data-stu-id="c2b76-102">StrongNameHashSize Function</span></span>
<span data-ttu-id="c2b76-103">Belirtilen karma algoritması kullanarak bir karma için gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="c2b76-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="c2b76-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="c2b76-104">This function has been deprecated.</span></span> <span data-ttu-id="c2b76-105">Kullanım [Iclrstrongname::strongnamehashsize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="c2b76-105">Use the [ICLRStrongName::StrongNameHashSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2b76-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2b76-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2b76-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c2b76-107">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="c2b76-108">[in] Arabellek boyutunu hesaplamak için kullanılan karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="c2b76-108">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="c2b76-109">[out] Döndürülen arabellek bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="c2b76-109">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2b76-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c2b76-110">Return Value</span></span>  
 <span data-ttu-id="c2b76-111">`true` başarıyla tamamlandığında; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="c2b76-111">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2b76-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c2b76-112">Remarks</span></span>  
 <span data-ttu-id="c2b76-113">Varsa `StrongNameHashSize` işlevi değil başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) oluşturulan son hatayı alması için işlevi.</span><span class="sxs-lookup"><span data-stu-id="c2b76-113">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2b76-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2b76-114">Requirements</span></span>  
 <span data-ttu-id="c2b76-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2b76-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2b76-116">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="c2b76-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c2b76-117">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c2b76-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c2b76-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2b76-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2b76-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2b76-119">See also</span></span>

- [<span data-ttu-id="c2b76-120">StrongNameHashSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2b76-120">StrongNameHashSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)
- [<span data-ttu-id="c2b76-121">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2b76-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
