---
title: "GetHashFromFileW İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromFileW
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromFileW
helpviewer_keywords: GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d7d62526a6ac9bb06a7de8287c9687933402bfb8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="40e5a-102">GetHashFromFileW İşlevi</span><span class="sxs-lookup"><span data-stu-id="40e5a-102">GetHashFromFileW Function</span></span>
<span data-ttu-id="40e5a-103">Bir UNICODE dizesi tarafından belirtilen dosyanın içeriğini üzerinden bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="40e5a-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="40e5a-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="40e5a-104">This function has been deprecated.</span></span> <span data-ttu-id="40e5a-105">Kullanım [Iclrstrongname::gethashfromfilew](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="40e5a-105">Use the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40e5a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40e5a-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="40e5a-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="40e5a-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="40e5a-108">[in] Karma dosyasına Unicode adı.</span><span class="sxs-lookup"><span data-stu-id="40e5a-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="40e5a-109">[içinde out] Karma oluşturulurken kullanılacak algoritması.</span><span class="sxs-lookup"><span data-stu-id="40e5a-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="40e5a-110">Geçerli algoritmaları Win32 CryptoAPI tarafından tanımlanmış izinlerdir.</span><span class="sxs-lookup"><span data-stu-id="40e5a-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="40e5a-111">Varsa `piHashAlg` CALG_SHA-1 kullanılan varsayılan algoritma 0 olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="40e5a-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="40e5a-112">[out] Üretilen karma içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="40e5a-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="40e5a-113">[in] Tarafından için en büyük arabellek boyutunu işaret `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="40e5a-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="40e5a-114">[out] Bayt olarak boyutu, `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="40e5a-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40e5a-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40e5a-115">Remarks</span></span>  
 <span data-ttu-id="40e5a-116">Bu işlev aynıdır [GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md), dosya adı belirtimine ANSI yerine Unicode olması dışında.</span><span class="sxs-lookup"><span data-stu-id="40e5a-116">This function is the same as [GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40e5a-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40e5a-117">Requirements</span></span>  
 <span data-ttu-id="40e5a-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40e5a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40e5a-119">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="40e5a-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="40e5a-120">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="40e5a-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="40e5a-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40e5a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40e5a-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="40e5a-122">See Also</span></span>  
 [<span data-ttu-id="40e5a-123">GetHashFromFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40e5a-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [<span data-ttu-id="40e5a-124">GetHashFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40e5a-124">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [<span data-ttu-id="40e5a-125">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40e5a-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
