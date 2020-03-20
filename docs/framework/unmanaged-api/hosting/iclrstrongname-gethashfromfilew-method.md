---
title: ICLRStrongName::GetHashFromFileW Yöntemi
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
ms.openlocfilehash: 8f2d74531233f2ba423c39126ddc43e499cbb5d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176376"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="c265f-102">ICLRStrongName::GetHashFromFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c265f-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="c265f-103">Unicode dizesi tarafından belirtilen dosyanın içeriği üzerinde karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c265f-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c265f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c265f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="c265f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c265f-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="c265f-106">[içinde] Karma dosyanın Unicode adı.</span><span class="sxs-lookup"><span data-stu-id="c265f-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="c265f-107">[içinde, dışarı] Karma oluştururken kullanılacak algoritma.</span><span class="sxs-lookup"><span data-stu-id="c265f-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="c265f-108">Geçerli algoritmalar Win32 CryptoAPI tarafından tanımlanan algoritmalardır.</span><span class="sxs-lookup"><span data-stu-id="c265f-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="c265f-109">0 `piHashAlg` olarak ayarlanırsa, varsayılan algoritma CALG_SHA-1 kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c265f-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="c265f-110">[çıkış] Oluşturulan karma içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="c265f-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="c265f-111">[içinde] Tarafından işaret edilen arabelleğe `pbHash`işaret edilen maksimum boyutu.</span><span class="sxs-lookup"><span data-stu-id="c265f-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="c265f-112">[çıkış] Boyutu, bayt, ve. `pbHash`</span><span class="sxs-lookup"><span data-stu-id="c265f-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c265f-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c265f-113">Return Value</span></span>  
 <span data-ttu-id="c265f-114">`S_OK`yöntem başarıyla tamamlanırsa; aksi takdirde, başarısızlığı gösteren bir HRESULT değeri (liste için [Ortak HRESULT Değerleri'ne](/windows/win32/seccrypto/common-hresult-values) bakın).</span><span class="sxs-lookup"><span data-stu-id="c265f-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c265f-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c265f-115">Remarks</span></span>  
 <span data-ttu-id="c265f-116">Bu yöntem, dosya adı belirtimi NINAnSI yerine Unicode [dışında, ICLRStrongName aynıdır::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c265f-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c265f-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c265f-117">Requirements</span></span>  
 <span data-ttu-id="c265f-118">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c265f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c265f-119">**Üstbilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="c265f-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c265f-120">**Kütüphane:** MSCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="c265f-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c265f-121">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c265f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c265f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c265f-122">See also</span></span>

- [<span data-ttu-id="c265f-123">GetHashFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c265f-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="c265f-124">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c265f-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
