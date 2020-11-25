---
title: GetHashFromFileW İşlevi
ms.date: 03/30/2017
api_name:
- GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type:
- apiref
ms.openlocfilehash: 8038d0abc93e058e6bde897bbf2261d8f1df885a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732332"
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="f2b4f-102">GetHashFromFileW İşlevi</span><span class="sxs-lookup"><span data-stu-id="f2b4f-102">GetHashFromFileW Function</span></span>

<span data-ttu-id="f2b4f-103">Unicode dizesi tarafından belirtilen dosyanın içeriği üzerinde bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f2b4f-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="f2b4f-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="f2b4f-104">This function has been deprecated.</span></span> <span data-ttu-id="f2b4f-105">Bunun yerine [ICLRStrongName:: GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f2b4f-105">Use the [ICLRStrongName::GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2b4f-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f2b4f-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="f2b4f-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2b4f-107">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="f2b4f-108">'ndaki Karma olacak dosyanın Unicode adı.</span><span class="sxs-lookup"><span data-stu-id="f2b4f-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="f2b4f-109">[in, out] Karma oluşturulurken kullanılacak algoritma.</span><span class="sxs-lookup"><span data-stu-id="f2b4f-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="f2b4f-110">Geçerli algoritmalar Win32 CryptoAPI tarafından tanımlı olanlardır.</span><span class="sxs-lookup"><span data-stu-id="f2b4f-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="f2b4f-111">`piHashAlg`0 olarak ayarlanırsa, CALG_SHA-1 varsayılan algoritma kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f2b4f-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="f2b4f-112">dışı Oluşturulan karmayı içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="f2b4f-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="f2b4f-113">'ndaki Tarafından işaret edilen arabelleğin en büyük boyutu `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="f2b4f-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="f2b4f-114">dışı Bayt cinsinden boyutu `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="f2b4f-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2b4f-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2b4f-115">Remarks</span></span>  

 <span data-ttu-id="f2b4f-116">Bu işlev, [GetHashFromFile](gethashfromfile-function.md)ile aynıdır, ancak dosya adı belirtimi ANSI yerine Unicode olur.</span><span class="sxs-lookup"><span data-stu-id="f2b4f-116">This function is the same as [GetHashFromFile](gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2b4f-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2b4f-117">Requirements</span></span>  

 <span data-ttu-id="f2b4f-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2b4f-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2b4f-119">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="f2b4f-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f2b4f-120">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f2b4f-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f2b4f-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2b4f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2b4f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2b4f-122">See also</span></span>

- [<span data-ttu-id="f2b4f-123">GetHashFromFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2b4f-123">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="f2b4f-124">GetHashFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2b4f-124">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="f2b4f-125">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2b4f-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
