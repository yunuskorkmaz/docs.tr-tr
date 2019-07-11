---
title: GetHashFromFile İşlevi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38c663bc2db780c89ca666702534a75525ae189b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771964"
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="32d14-102">GetHashFromFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="32d14-102">GetHashFromFile Function</span></span>
<span data-ttu-id="32d14-103">Belirtilen dosyanın içeriğini bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="32d14-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="32d14-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="32d14-104">This function has been deprecated.</span></span> <span data-ttu-id="32d14-105">Kullanım [Iclrstrongname::gethashfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="32d14-105">Use the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32d14-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32d14-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32d14-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="32d14-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="32d14-108">[in] Karma değeri dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="32d14-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="32d14-109">[out içinde] Karma oluşturulurken kullanılacak algoritma.</span><span class="sxs-lookup"><span data-stu-id="32d14-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="32d14-110">Geçerli algoritmaları Win32 CryptoAPI tarafından tanımlanmış izinlerdir.</span><span class="sxs-lookup"><span data-stu-id="32d14-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="32d14-111">Varsa `piHashAlg` CALG_SHA 1 kullanılan varsayılan algoritma 0 olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="32d14-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="32d14-112">[out] Oluşturulan karma içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="32d14-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="32d14-113">[in] En büyük arabellek boyutunu, `pbHash` işaret eder.</span><span class="sxs-lookup"><span data-stu-id="32d14-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="32d14-114">[out] Döndürülen bayt cinsinden boyutu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="32d14-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32d14-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32d14-115">Remarks</span></span>  
 <span data-ttu-id="32d14-116">Bu işlev aynı şekilde, [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), dosya adı belirtimi Unicode yerine ANSI hariç aynıdırlar.</span><span class="sxs-lookup"><span data-stu-id="32d14-116">This function is the same as [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32d14-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32d14-117">Requirements</span></span>  
 <span data-ttu-id="32d14-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32d14-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32d14-119">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="32d14-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="32d14-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="32d14-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="32d14-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32d14-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32d14-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32d14-122">See also</span></span>

- [<span data-ttu-id="32d14-123">GetHashFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="32d14-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="32d14-124">GetHashFromFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="32d14-124">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="32d14-125">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="32d14-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
