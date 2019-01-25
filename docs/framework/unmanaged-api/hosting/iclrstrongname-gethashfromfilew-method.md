---
title: ICLRStrongName::GetHashFromFileW Metodu
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromFileW method [.NET Framework hosting]
ms.assetid: c6ff45fc-905d-4c6e-b00c-97c6c7c55d99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2ca00b660a9cbb408fd1175e94a4242dae5f1a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523967"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="dfdc5-102">ICLRStrongName::GetHashFromFileW Metodu</span><span class="sxs-lookup"><span data-stu-id="dfdc5-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="dfdc5-103">Unicode dizesi tarafından belirtilen dosyanın içeriğini üzerinden bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dfdc5-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfdc5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dfdc5-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="dfdc5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dfdc5-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="dfdc5-106">[in] Karma dosyayı Unicode adı.</span><span class="sxs-lookup"><span data-stu-id="dfdc5-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="dfdc5-107">[out içinde] Karma oluşturulurken kullanılacak algoritma.</span><span class="sxs-lookup"><span data-stu-id="dfdc5-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="dfdc5-108">Geçerli algoritmaları Win32 CryptoAPI tarafından tanımlanmış izinlerdir.</span><span class="sxs-lookup"><span data-stu-id="dfdc5-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="dfdc5-109">Varsa `piHashAlg` CALG_SHA 1 kullanılan varsayılan algoritma 0 olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="dfdc5-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="dfdc5-110">[out] Oluşturulan karma içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="dfdc5-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="dfdc5-111">[in] En büyük arabellek boyutunu tarafından işaret edilen `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="dfdc5-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="dfdc5-112">[out] Bayt cinsinden boyutu, `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="dfdc5-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dfdc5-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dfdc5-113">Return Value</span></span>  
 <span data-ttu-id="dfdc5-114">`S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="dfdc5-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfdc5-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dfdc5-115">Remarks</span></span>  
 <span data-ttu-id="dfdc5-116">Bu yöntem ile aynıdır [Iclrstrongname::gethashfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) yöntemi, dosya adı, tek farkı belirtimi yerine ANSI Unicode.</span><span class="sxs-lookup"><span data-stu-id="dfdc5-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfdc5-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dfdc5-117">Requirements</span></span>  
 <span data-ttu-id="dfdc5-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfdc5-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfdc5-119">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="dfdc5-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="dfdc5-120">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="dfdc5-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dfdc5-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfdc5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfdc5-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfdc5-122">See also</span></span>
- [<span data-ttu-id="dfdc5-123">GetHashFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfdc5-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="dfdc5-124">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dfdc5-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
