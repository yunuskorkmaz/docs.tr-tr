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
ms.openlocfilehash: e5821abed4d6c7f7595bad3240ab86d5a128d794
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901158"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="d5b8c-102">ICLRStrongName::GetHashFromFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5b8c-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="d5b8c-103">Unicode dizesi tarafından belirtilen dosyanın içeriği üzerinde bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d5b8c-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5b8c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5b8c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="d5b8c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d5b8c-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="d5b8c-106">'ndaki Karma olacak dosyanın Unicode adı.</span><span class="sxs-lookup"><span data-stu-id="d5b8c-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="d5b8c-107">[in, out] Karma oluşturulurken kullanılacak algoritma.</span><span class="sxs-lookup"><span data-stu-id="d5b8c-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="d5b8c-108">Geçerli algoritmalar Win32 CryptoAPI tarafından tanımlı olanlardır.</span><span class="sxs-lookup"><span data-stu-id="d5b8c-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="d5b8c-109">`piHashAlg` 0 olarak ayarlanırsa, varsayılan algoritma CALG_SHA-1 kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d5b8c-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="d5b8c-110">dışı Oluşturulan karmayı içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="d5b8c-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="d5b8c-111">'ndaki `pbHash`tarafından işaret edilen arabelleğin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="d5b8c-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="d5b8c-112">dışı `pbHash`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="d5b8c-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5b8c-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d5b8c-113">Return Value</span></span>  
 <span data-ttu-id="d5b8c-114">Yöntem başarıyla tamamlanırsa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="d5b8c-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5b8c-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5b8c-115">Remarks</span></span>  
 <span data-ttu-id="d5b8c-116">Bu yöntem, [ICLRStrongName:: GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) yöntemiyle aynıdır, ancak dosya adı belirtimi ANSI yerine Unicode olur.</span><span class="sxs-lookup"><span data-stu-id="d5b8c-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5b8c-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5b8c-117">Requirements</span></span>  
 <span data-ttu-id="d5b8c-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5b8c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5b8c-119">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="d5b8c-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d5b8c-120">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="d5b8c-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5b8c-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5b8c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5b8c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5b8c-122">See also</span></span>

- [<span data-ttu-id="d5b8c-123">GetHashFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5b8c-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="d5b8c-124">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5b8c-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
