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
ms.openlocfilehash: 5774b7cdcfedfc407b626ab5052f5b4a77461e9b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155915"
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="2e872-102">GetHashFromFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="2e872-102">GetHashFromFile Function</span></span>
<span data-ttu-id="2e872-103">Belirtilen dosyanın içeriğini bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2e872-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="2e872-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="2e872-104">This function has been deprecated.</span></span> <span data-ttu-id="2e872-105">Kullanım [Iclrstrongname::gethashfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="2e872-105">Use the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e872-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e872-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e872-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2e872-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="2e872-108">[in] Karma değeri dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="2e872-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="2e872-109">[out içinde] Karma oluşturulurken kullanılacak algoritma.</span><span class="sxs-lookup"><span data-stu-id="2e872-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="2e872-110">Geçerli algoritmaları Win32 CryptoAPI tarafından tanımlanmış izinlerdir.</span><span class="sxs-lookup"><span data-stu-id="2e872-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="2e872-111">Varsa `piHashAlg` CALG_SHA 1 kullanılan varsayılan algoritma 0 olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="2e872-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="2e872-112">[out] Oluşturulan karma içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="2e872-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="2e872-113">[in] En büyük arabellek boyutunu, `pbHash` işaret eder.</span><span class="sxs-lookup"><span data-stu-id="2e872-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="2e872-114">[out] Döndürülen bayt cinsinden boyutu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="2e872-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e872-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2e872-115">Remarks</span></span>  
 <span data-ttu-id="2e872-116">Bu işlev aynı şekilde, [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), dosya adı belirtimi Unicode yerine ANSI hariç aynıdırlar.</span><span class="sxs-lookup"><span data-stu-id="2e872-116">This function is the same as [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e872-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e872-117">Requirements</span></span>  
 <span data-ttu-id="2e872-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e872-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e872-119">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="2e872-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="2e872-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2e872-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="2e872-121">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="2e872-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2e872-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e872-122">See also</span></span>

- [<span data-ttu-id="2e872-123">GetHashFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e872-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="2e872-124">GetHashFromFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e872-124">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="2e872-125">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e872-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
