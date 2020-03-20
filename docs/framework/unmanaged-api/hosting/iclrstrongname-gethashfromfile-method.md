---
title: ICLRStrongName::GetHashFromFile Yöntemi
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
ms.openlocfilehash: ed735c3d7830551581df35793f3f6fdc4953dc8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178069"
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="c61de-102">ICLRStrongName::GetHashFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c61de-102">ICLRStrongName::GetHashFromFile Method</span></span>
<span data-ttu-id="c61de-103">Belirtilen dosyanın içeriği üzerinde karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c61de-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c61de-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c61de-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c61de-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c61de-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="c61de-106">[içinde] Karma dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="c61de-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="c61de-107">[içinde, dışarı] Karma oluştururken kullanılacak algoritma.</span><span class="sxs-lookup"><span data-stu-id="c61de-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="c61de-108">Geçerli algoritmalar Win32 CryptoAPI tarafından tanımlanan algoritmalardır.</span><span class="sxs-lookup"><span data-stu-id="c61de-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="c61de-109">0 `piHashAlg` olarak ayarlanırsa, varsayılan algoritma CALG_SHA-1 kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c61de-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="c61de-110">[çıkış] Oluşturulan karma içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="c61de-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="c61de-111">[içinde] Tamponun işaret eden `pbHash` maksimum boyutu.</span><span class="sxs-lookup"><span data-stu-id="c61de-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="c61de-112">[çıkış] Döndürülen baytların `pbHash`boyutu.</span><span class="sxs-lookup"><span data-stu-id="c61de-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c61de-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c61de-113">Return Value</span></span>  
 <span data-ttu-id="c61de-114">`S_OK`yöntem başarıyla tamamlanırsa; aksi takdirde, başarısızlığı gösteren bir HRESULT değeri (liste için [Ortak HRESULT Değerleri'ne](/windows/win32/seccrypto/common-hresult-values) bakın).</span><span class="sxs-lookup"><span data-stu-id="c61de-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c61de-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c61de-115">Remarks</span></span>  
 <span data-ttu-id="c61de-116">Bu yöntem, Dosya adı belirtimi Unicode yerine ANSI [dışında, ICLRStrongName aynıdır::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c61de-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c61de-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c61de-117">Requirements</span></span>  
 <span data-ttu-id="c61de-118">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c61de-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c61de-119">**Üstbilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="c61de-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c61de-120">**Kütüphane:** MSCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="c61de-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c61de-121">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c61de-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c61de-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c61de-122">See also</span></span>

- [<span data-ttu-id="c61de-123">GetHashFromFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c61de-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="c61de-124">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c61de-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
