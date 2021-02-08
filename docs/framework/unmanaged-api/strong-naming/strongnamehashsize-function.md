---
description: 'Daha fazla bilgi edinin: StrongNameHashSize Işlevi'
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
ms.openlocfilehash: 3e6700bfce3ba480814f3837011c5f8f7107bbd5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781252"
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="a1f28-103">StrongNameHashSize İşlevi</span><span class="sxs-lookup"><span data-stu-id="a1f28-103">StrongNameHashSize Function</span></span>

<span data-ttu-id="a1f28-104">Belirtilen karma algoritmasını kullanarak bir karma için gereken arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="a1f28-104">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="a1f28-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="a1f28-105">This function has been deprecated.</span></span> <span data-ttu-id="a1f28-106">Bunun yerine [ICLRStrongName:: StrongNameHashSize](../hosting/iclrstrongname-strongnamehashsize-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="a1f28-106">Use the [ICLRStrongName::StrongNameHashSize](../hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1f28-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a1f28-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1f28-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a1f28-108">Parameters</span></span>  

 `ulHashAlg`  
 <span data-ttu-id="a1f28-109">'ndaki Arabellek boyutunu hesaplamak için kullanılan karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="a1f28-109">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="a1f28-110">dışı Bayt cinsinden döndürülen arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="a1f28-110">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1f28-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a1f28-111">Return Value</span></span>  

 <span data-ttu-id="a1f28-112">`true` başarıyla tamamlandığında; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="a1f28-112">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1f28-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1f28-113">Remarks</span></span>  

 <span data-ttu-id="a1f28-114">`StrongNameHashSize`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="a1f28-114">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1f28-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a1f28-115">Requirements</span></span>  

 <span data-ttu-id="a1f28-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1f28-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1f28-117">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="a1f28-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a1f28-118">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a1f28-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a1f28-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1f28-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1f28-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1f28-120">See also</span></span>

- [<span data-ttu-id="a1f28-121">StrongNameHashSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1f28-121">StrongNameHashSize Method</span></span>](../hosting/iclrstrongname-strongnamehashsize-method.md)
- [<span data-ttu-id="a1f28-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1f28-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
