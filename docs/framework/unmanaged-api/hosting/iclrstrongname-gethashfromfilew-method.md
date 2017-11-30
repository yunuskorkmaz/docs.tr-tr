---
title: ICLRStrongName::GetHashFromFileW Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.GetHashFromFileW
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromFileW method [.NET Framework hosting]
ms.assetid: c6ff45fc-905d-4c6e-b00c-97c6c7c55d99
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc7589e2a977502a3e75a95b8a065f45b8805072
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="b507e-102">ICLRStrongName::GetHashFromFileW Metodu</span><span class="sxs-lookup"><span data-stu-id="b507e-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="b507e-103">Bir UNICODE dizesi tarafından belirtilen dosyanın içeriğini üzerinden bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b507e-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b507e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b507e-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="b507e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b507e-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="b507e-106">[in] Karma dosyasına Unicode adı.</span><span class="sxs-lookup"><span data-stu-id="b507e-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="b507e-107">[içinde out] Karma oluşturulurken kullanılacak algoritması.</span><span class="sxs-lookup"><span data-stu-id="b507e-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="b507e-108">Geçerli algoritmaları Win32 CryptoAPI tarafından tanımlanmış izinlerdir.</span><span class="sxs-lookup"><span data-stu-id="b507e-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="b507e-109">Varsa `piHashAlg` CALG_SHA-1 kullanılan varsayılan algoritma 0 olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b507e-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="b507e-110">[out] Üretilen karma içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="b507e-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="b507e-111">[in] Tarafından için en büyük arabellek boyutunu işaret `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="b507e-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="b507e-112">[out] Bayt olarak boyutu, `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="b507e-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b507e-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b507e-113">Return Value</span></span>  
 <span data-ttu-id="b507e-114">`S_OK`Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="b507e-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b507e-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b507e-115">Remarks</span></span>  
 <span data-ttu-id="b507e-116">Bu yöntem ile aynıdır [Iclrstrongname::gethashfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) yöntemi, dosya adı belirtimi olmasıdır ANSI yerine Unicode.</span><span class="sxs-lookup"><span data-stu-id="b507e-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b507e-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b507e-117">Requirements</span></span>  
 <span data-ttu-id="b507e-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b507e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b507e-119">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b507e-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b507e-120">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b507e-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b507e-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b507e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b507e-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b507e-122">See Also</span></span>  
 [<span data-ttu-id="b507e-123">GetHashFromFile yöntemi</span><span class="sxs-lookup"><span data-stu-id="b507e-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [<span data-ttu-id="b507e-124">Iclrstrongname arabirimi</span><span class="sxs-lookup"><span data-stu-id="b507e-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
