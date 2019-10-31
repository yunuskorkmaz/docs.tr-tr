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
ms.openlocfilehash: 553acc178bc5805b5afef5931fefc8ad74cbac39
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135183"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="8ade9-102">ICLRStrongName::GetHashFromFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8ade9-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="8ade9-103">Unicode dizesi tarafından belirtilen dosyanın içeriği üzerinde bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8ade9-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ade9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ade9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="8ade9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8ade9-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="8ade9-106">'ndaki Karma olacak dosyanın Unicode adı.</span><span class="sxs-lookup"><span data-stu-id="8ade9-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="8ade9-107">[in, out] Karma oluşturulurken kullanılacak algoritma.</span><span class="sxs-lookup"><span data-stu-id="8ade9-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="8ade9-108">Geçerli algoritmalar Win32 CryptoAPI tarafından tanımlı olanlardır.</span><span class="sxs-lookup"><span data-stu-id="8ade9-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="8ade9-109">`piHashAlg` 0 olarak ayarlanırsa, varsayılan algoritma CALG_SHA-1 kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8ade9-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="8ade9-110">dışı Oluşturulan karmayı içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="8ade9-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="8ade9-111">'ndaki `pbHash`tarafından işaret edilen arabelleğin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="8ade9-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="8ade9-112">dışı `pbHash`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="8ade9-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ade9-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8ade9-113">Return Value</span></span>  
 <span data-ttu-id="8ade9-114">Yöntem başarıyla tamamlanırsa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](https://go.microsoft.com/fwlink/?LinkId=213878) ).</span><span class="sxs-lookup"><span data-stu-id="8ade9-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ade9-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ade9-115">Remarks</span></span>  
 <span data-ttu-id="8ade9-116">Bu yöntem, [ICLRStrongName:: GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) yöntemiyle aynıdır, ancak dosya adı belirtimi ANSI yerine Unicode olur.</span><span class="sxs-lookup"><span data-stu-id="8ade9-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ade9-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ade9-117">Requirements</span></span>  
 <span data-ttu-id="8ade9-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ade9-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ade9-119">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="8ade9-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8ade9-120">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="8ade9-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ade9-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ade9-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ade9-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ade9-122">See also</span></span>

- [<span data-ttu-id="8ade9-123">GetHashFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8ade9-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="8ade9-124">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8ade9-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
