---
title: ICLRStrongName::GetHashFromFile Metodu
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 33aab5ee23a1f0d30d1f9f3079856ca30d46d2ec
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46519204"
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="4d943-102">ICLRStrongName::GetHashFromFile Metodu</span><span class="sxs-lookup"><span data-stu-id="4d943-102">ICLRStrongName::GetHashFromFile Method</span></span>
<span data-ttu-id="4d943-103">Belirtilen dosyanın içeriğini bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4d943-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d943-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d943-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d943-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4d943-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="4d943-106">[in] Karma değeri dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="4d943-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="4d943-107">[out içinde] Karma oluşturulurken kullanılacak algoritma.</span><span class="sxs-lookup"><span data-stu-id="4d943-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="4d943-108">Geçerli algoritmaları Win32 CryptoAPI tarafından tanımlanmış izinlerdir.</span><span class="sxs-lookup"><span data-stu-id="4d943-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="4d943-109">Varsa `piHashAlg` CALG_SHA 1 kullanılan varsayılan algoritma 0 olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="4d943-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="4d943-110">[out] Oluşturulan karma içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="4d943-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="4d943-111">[in] En büyük arabellek boyutunu, `pbHash` işaret eder.</span><span class="sxs-lookup"><span data-stu-id="4d943-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="4d943-112">[out] Döndürülen bayt cinsinden boyutu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="4d943-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d943-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4d943-113">Return Value</span></span>  
 <span data-ttu-id="4d943-114">`S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="4d943-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d943-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4d943-115">Remarks</span></span>  
 <span data-ttu-id="4d943-116">Bu yöntem ile aynıdır [Iclrstrongname::gethashfromfilew](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) yöntemi, dosya adı, tek farkı belirtimi Unicode yerine ANSI.</span><span class="sxs-lookup"><span data-stu-id="4d943-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d943-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4d943-117">Requirements</span></span>  
 <span data-ttu-id="4d943-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d943-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d943-119">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="4d943-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4d943-120">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4d943-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4d943-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d943-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d943-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4d943-122">See Also</span></span>  
 [<span data-ttu-id="4d943-123">GetHashFromFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d943-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [<span data-ttu-id="4d943-124">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d943-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
