---
description: 'Daha fazla bilgi edinin: GetHashFromFileW Işlevi'
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
ms.openlocfilehash: daebd06de02dfe936f1bdeb8697de4fe6524dce3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736574"
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="c9413-103">GetHashFromFileW İşlevi</span><span class="sxs-lookup"><span data-stu-id="c9413-103">GetHashFromFileW Function</span></span>

<span data-ttu-id="c9413-104">Unicode dizesi tarafından belirtilen dosyanın içeriği üzerinde bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c9413-104">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="c9413-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="c9413-105">This function has been deprecated.</span></span> <span data-ttu-id="c9413-106">Bunun yerine [ICLRStrongName:: GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c9413-106">Use the [ICLRStrongName::GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9413-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9413-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="c9413-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c9413-108">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="c9413-109">'ndaki Karma olacak dosyanın Unicode adı.</span><span class="sxs-lookup"><span data-stu-id="c9413-109">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="c9413-110">[in, out] Karma oluşturulurken kullanılacak algoritma.</span><span class="sxs-lookup"><span data-stu-id="c9413-110">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="c9413-111">Geçerli algoritmalar Win32 CryptoAPI tarafından tanımlı olanlardır.</span><span class="sxs-lookup"><span data-stu-id="c9413-111">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="c9413-112">`piHashAlg`0 olarak ayarlanırsa, CALG_SHA-1 varsayılan algoritma kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c9413-112">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="c9413-113">dışı Oluşturulan karmayı içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="c9413-113">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="c9413-114">'ndaki Tarafından işaret edilen arabelleğin en büyük boyutu `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="c9413-114">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="c9413-115">dışı Bayt cinsinden boyutu `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="c9413-115">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9413-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c9413-116">Remarks</span></span>  

 <span data-ttu-id="c9413-117">Bu işlev, [GetHashFromFile](gethashfromfile-function.md)ile aynıdır, ancak dosya adı belirtimi ANSI yerine Unicode olur.</span><span class="sxs-lookup"><span data-stu-id="c9413-117">This function is the same as [GetHashFromFile](gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9413-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9413-118">Requirements</span></span>  

 <span data-ttu-id="c9413-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9413-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9413-120">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="c9413-120">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c9413-121">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="c9413-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c9413-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9413-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9413-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9413-123">See also</span></span>

- [<span data-ttu-id="c9413-124">GetHashFromFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9413-124">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="c9413-125">GetHashFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9413-125">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="c9413-126">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c9413-126">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
