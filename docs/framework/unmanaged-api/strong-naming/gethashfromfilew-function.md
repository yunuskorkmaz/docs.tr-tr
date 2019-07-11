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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77b164cdec0dd224042e4de3265d14a4991d60ba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771894"
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="f1d8d-102">GetHashFromFileW İşlevi</span><span class="sxs-lookup"><span data-stu-id="f1d8d-102">GetHashFromFileW Function</span></span>
<span data-ttu-id="f1d8d-103">Unicode dizesi tarafından belirtilen dosyanın içeriğini üzerinden bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f1d8d-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="f1d8d-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="f1d8d-104">This function has been deprecated.</span></span> <span data-ttu-id="f1d8d-105">Kullanım [Iclrstrongname::gethashfromfilew](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="f1d8d-105">Use the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1d8d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1d8d-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="f1d8d-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f1d8d-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="f1d8d-108">[in] Karma dosyayı Unicode adı.</span><span class="sxs-lookup"><span data-stu-id="f1d8d-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="f1d8d-109">[out içinde] Karma oluşturulurken kullanılacak algoritma.</span><span class="sxs-lookup"><span data-stu-id="f1d8d-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="f1d8d-110">Geçerli algoritmaları Win32 CryptoAPI tarafından tanımlanmış izinlerdir.</span><span class="sxs-lookup"><span data-stu-id="f1d8d-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="f1d8d-111">Varsa `piHashAlg` CALG_SHA 1 kullanılan varsayılan algoritma 0 olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f1d8d-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="f1d8d-112">[out] Oluşturulan karma içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="f1d8d-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="f1d8d-113">[in] En büyük arabellek boyutunu tarafından işaret edilen `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="f1d8d-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="f1d8d-114">[out] Bayt cinsinden boyutu, `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="f1d8d-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1d8d-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1d8d-115">Remarks</span></span>  
 <span data-ttu-id="f1d8d-116">Bu işlev aynı şekilde, [GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md), dosya adı belirtimi yerine ANSI Unicode olması dışında.</span><span class="sxs-lookup"><span data-stu-id="f1d8d-116">This function is the same as [GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1d8d-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1d8d-117">Requirements</span></span>  
 <span data-ttu-id="f1d8d-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1d8d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1d8d-119">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="f1d8d-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f1d8d-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f1d8d-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f1d8d-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1d8d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1d8d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1d8d-122">See also</span></span>

- [<span data-ttu-id="f1d8d-123">GetHashFromFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f1d8d-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="f1d8d-124">GetHashFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f1d8d-124">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="f1d8d-125">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f1d8d-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
