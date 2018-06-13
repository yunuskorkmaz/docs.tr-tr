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
ms.openlocfilehash: 87600781c90fe5e6e049af74a68859955153f3b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433347"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="21e69-102">ICLRStrongName::GetHashFromFileW Metodu</span><span class="sxs-lookup"><span data-stu-id="21e69-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="21e69-103">Bir UNICODE dizesi tarafından belirtilen dosyanın içeriğini üzerinden bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="21e69-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21e69-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21e69-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="21e69-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21e69-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="21e69-106">[in] Karma dosyasına Unicode adı.</span><span class="sxs-lookup"><span data-stu-id="21e69-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="21e69-107">[içinde out] Karma oluşturulurken kullanılacak algoritması.</span><span class="sxs-lookup"><span data-stu-id="21e69-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="21e69-108">Geçerli algoritmaları Win32 CryptoAPI tarafından tanımlanmış izinlerdir.</span><span class="sxs-lookup"><span data-stu-id="21e69-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="21e69-109">Varsa `piHashAlg` CALG_SHA-1 kullanılan varsayılan algoritma 0 olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="21e69-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="21e69-110">[out] Üretilen karma içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="21e69-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="21e69-111">[in] Tarafından için en büyük arabellek boyutunu işaret `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="21e69-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="21e69-112">[out] Bayt olarak boyutu, `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="21e69-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21e69-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="21e69-113">Return Value</span></span>  
 <span data-ttu-id="21e69-114">`S_OK` Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="21e69-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21e69-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21e69-115">Remarks</span></span>  
 <span data-ttu-id="21e69-116">Bu yöntem ile aynıdır [Iclrstrongname::gethashfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) yöntemi, dosya adı belirtimi olmasıdır ANSI yerine Unicode.</span><span class="sxs-lookup"><span data-stu-id="21e69-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21e69-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21e69-117">Requirements</span></span>  
 <span data-ttu-id="21e69-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21e69-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21e69-119">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="21e69-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="21e69-120">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="21e69-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21e69-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21e69-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e69-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="21e69-122">See Also</span></span>  
 [<span data-ttu-id="21e69-123">GetHashFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21e69-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [<span data-ttu-id="21e69-124">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21e69-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
