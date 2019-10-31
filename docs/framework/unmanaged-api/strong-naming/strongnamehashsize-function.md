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
ms.openlocfilehash: c656f73748faf8be7124be65f3ed455f2d5fd07a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73105184"
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="b1dfb-102">StrongNameHashSize İşlevi</span><span class="sxs-lookup"><span data-stu-id="b1dfb-102">StrongNameHashSize Function</span></span>
<span data-ttu-id="b1dfb-103">Belirtilen karma algoritmasını kullanarak bir karma için gereken arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="b1dfb-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="b1dfb-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="b1dfb-104">This function has been deprecated.</span></span> <span data-ttu-id="b1dfb-105">Bunun yerine [ICLRStrongName:: StrongNameHashSize](../hosting/iclrstrongname-strongnamehashsize-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="b1dfb-105">Use the [ICLRStrongName::StrongNameHashSize](../hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1dfb-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1dfb-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1dfb-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b1dfb-107">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="b1dfb-108">'ndaki Arabellek boyutunu hesaplamak için kullanılan karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="b1dfb-108">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="b1dfb-109">dışı Bayt cinsinden döndürülen arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="b1dfb-109">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1dfb-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b1dfb-110">Return Value</span></span>  
 <span data-ttu-id="b1dfb-111">başarılı tamamlamada `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="b1dfb-111">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1dfb-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1dfb-112">Remarks</span></span>  
 <span data-ttu-id="b1dfb-113">`StrongNameHashSize` işlevi başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="b1dfb-113">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1dfb-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1dfb-114">Requirements</span></span>  
 <span data-ttu-id="b1dfb-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1dfb-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1dfb-116">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="b1dfb-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="b1dfb-117">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="b1dfb-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b1dfb-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1dfb-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1dfb-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1dfb-119">See also</span></span>

- [<span data-ttu-id="b1dfb-120">StrongNameHashSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1dfb-120">StrongNameHashSize Method</span></span>](../hosting/iclrstrongname-strongnamehashsize-method.md)
- [<span data-ttu-id="b1dfb-121">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1dfb-121">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
