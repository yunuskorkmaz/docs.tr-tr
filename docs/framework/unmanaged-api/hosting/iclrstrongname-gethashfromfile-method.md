---
title: ICLRStrongName::GetHashFromFile Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.GetHashFromFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 480113148e039ff1be3e438b4af2e24fdeacba14
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="0a605-102">ICLRStrongName::GetHashFromFile Metodu</span><span class="sxs-lookup"><span data-stu-id="0a605-102">ICLRStrongName::GetHashFromFile Method</span></span>
<span data-ttu-id="0a605-103">Belirtilen dosyanın içeriğini bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0a605-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a605-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a605-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0a605-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0a605-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="0a605-106">[in] Karma değerini dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="0a605-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="0a605-107">[içinde out] Karma oluşturulurken kullanılacak algoritması.</span><span class="sxs-lookup"><span data-stu-id="0a605-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="0a605-108">Geçerli algoritmaları Win32 CryptoAPI tarafından tanımlanmış izinlerdir.</span><span class="sxs-lookup"><span data-stu-id="0a605-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="0a605-109">Varsa `piHashAlg` CALG_SHA-1 kullanılan varsayılan algoritma 0 olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0a605-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="0a605-110">[out] Üretilen karma içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="0a605-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="0a605-111">[in] Arabelleğin en büyük boyutu, `pbHash` işaret eder.</span><span class="sxs-lookup"><span data-stu-id="0a605-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="0a605-112">[out] Dönen bayt cinsinden boyutu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="0a605-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a605-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0a605-113">Return Value</span></span>  
 <span data-ttu-id="0a605-114">`S_OK`Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="0a605-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a605-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0a605-115">Remarks</span></span>  
 <span data-ttu-id="0a605-116">Bu yöntem ile aynıdır [Iclrstrongname::gethashfromfilew](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) yöntemi, dosya adı belirtimi olmasıdır Unicode yerine ANSI.</span><span class="sxs-lookup"><span data-stu-id="0a605-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a605-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a605-117">Requirements</span></span>  
 <span data-ttu-id="0a605-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a605-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a605-119">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="0a605-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0a605-120">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0a605-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a605-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a605-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a605-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0a605-122">See Also</span></span>  
 [<span data-ttu-id="0a605-123">GetHashFromFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a605-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [<span data-ttu-id="0a605-124">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a605-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
