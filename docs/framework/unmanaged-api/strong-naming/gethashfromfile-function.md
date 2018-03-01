---
title: "GetHashFromFile İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: be7979eb0f7d32e02257cc0b3cb400263350f0bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="6eb7b-102">GetHashFromFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="6eb7b-102">GetHashFromFile Function</span></span>
<span data-ttu-id="6eb7b-103">Belirtilen dosyanın içeriğini bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6eb7b-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="6eb7b-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="6eb7b-104">This function has been deprecated.</span></span> <span data-ttu-id="6eb7b-105">Kullanım [Iclrstrongname::gethashfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="6eb7b-105">Use the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eb7b-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6eb7b-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6eb7b-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6eb7b-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="6eb7b-108">[in] Karma değerini dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="6eb7b-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="6eb7b-109">[içinde out] Karma oluşturulurken kullanılacak algoritması.</span><span class="sxs-lookup"><span data-stu-id="6eb7b-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="6eb7b-110">Geçerli algoritmaları Win32 CryptoAPI tarafından tanımlanmış izinlerdir.</span><span class="sxs-lookup"><span data-stu-id="6eb7b-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="6eb7b-111">Varsa `piHashAlg` CALG_SHA-1 kullanılan varsayılan algoritma 0 olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="6eb7b-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="6eb7b-112">[out] Üretilen karma içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="6eb7b-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="6eb7b-113">[in] Arabelleğin en büyük boyutu, `pbHash` işaret eder.</span><span class="sxs-lookup"><span data-stu-id="6eb7b-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="6eb7b-114">[out] Dönen bayt cinsinden boyutu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="6eb7b-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6eb7b-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6eb7b-115">Remarks</span></span>  
 <span data-ttu-id="6eb7b-116">Bu işlev aynıdır [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), dosya adı belirtimine Unicode yerine ANSI olması dışında.</span><span class="sxs-lookup"><span data-stu-id="6eb7b-116">This function is the same as [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6eb7b-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6eb7b-117">Requirements</span></span>  
 <span data-ttu-id="6eb7b-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6eb7b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6eb7b-119">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="6eb7b-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="6eb7b-120">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6eb7b-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6eb7b-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6eb7b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eb7b-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6eb7b-122">See Also</span></span>  
 [<span data-ttu-id="6eb7b-123">GetHashFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6eb7b-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [<span data-ttu-id="6eb7b-124">GetHashFromFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6eb7b-124">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [<span data-ttu-id="6eb7b-125">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6eb7b-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
