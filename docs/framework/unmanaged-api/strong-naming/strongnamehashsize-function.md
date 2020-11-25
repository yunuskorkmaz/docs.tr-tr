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
ms.openlocfilehash: 1116fcde754f966a783f4fdca85df8bd3ca1b0ba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724448"
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="8339a-102">StrongNameHashSize İşlevi</span><span class="sxs-lookup"><span data-stu-id="8339a-102">StrongNameHashSize Function</span></span>

<span data-ttu-id="8339a-103">Belirtilen karma algoritmasını kullanarak bir karma için gereken arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="8339a-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="8339a-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="8339a-104">This function has been deprecated.</span></span> <span data-ttu-id="8339a-105">Bunun yerine [ICLRStrongName:: StrongNameHashSize](../hosting/iclrstrongname-strongnamehashsize-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="8339a-105">Use the [ICLRStrongName::StrongNameHashSize](../hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8339a-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8339a-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8339a-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8339a-107">Parameters</span></span>  

 `ulHashAlg`  
 <span data-ttu-id="8339a-108">'ndaki Arabellek boyutunu hesaplamak için kullanılan karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="8339a-108">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="8339a-109">dışı Bayt cinsinden döndürülen arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="8339a-109">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8339a-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8339a-110">Return Value</span></span>  

 <span data-ttu-id="8339a-111">`true` başarıyla tamamlandığında; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="8339a-111">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8339a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8339a-112">Remarks</span></span>  

 <span data-ttu-id="8339a-113">`StrongNameHashSize`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="8339a-113">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8339a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8339a-114">Requirements</span></span>  

 <span data-ttu-id="8339a-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8339a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8339a-116">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="8339a-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="8339a-117">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="8339a-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8339a-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8339a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8339a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8339a-119">See also</span></span>

- [<span data-ttu-id="8339a-120">StrongNameHashSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8339a-120">StrongNameHashSize Method</span></span>](../hosting/iclrstrongname-strongnamehashsize-method.md)
- [<span data-ttu-id="8339a-121">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8339a-121">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
