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
ms.openlocfilehash: 798bb0585bfe4cc29afba2fbefae818301704613
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135189"
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="42de8-102">ICLRStrongName::GetHashFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="42de8-102">ICLRStrongName::GetHashFromFile Method</span></span>
<span data-ttu-id="42de8-103">Belirtilen dosyanın içeriği üzerinde bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="42de8-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42de8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="42de8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42de8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="42de8-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="42de8-106">'ndaki Karma yapılacak dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="42de8-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="42de8-107">[in, out] Karma oluşturulurken kullanılacak algoritma.</span><span class="sxs-lookup"><span data-stu-id="42de8-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="42de8-108">Geçerli algoritmalar Win32 CryptoAPI tarafından tanımlı olanlardır.</span><span class="sxs-lookup"><span data-stu-id="42de8-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="42de8-109">`piHashAlg` 0 olarak ayarlanırsa, varsayılan algoritma CALG_SHA-1 kullanılır.</span><span class="sxs-lookup"><span data-stu-id="42de8-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="42de8-110">dışı Oluşturulan karmayı içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="42de8-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="42de8-111">'ndaki `pbHash` arabelleğin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="42de8-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="42de8-112">dışı Döndürülen `pbHash`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="42de8-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42de8-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="42de8-113">Return Value</span></span>  
 <span data-ttu-id="42de8-114">Yöntem başarıyla tamamlanırsa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](https://go.microsoft.com/fwlink/?LinkId=213878) ).</span><span class="sxs-lookup"><span data-stu-id="42de8-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42de8-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42de8-115">Remarks</span></span>  
 <span data-ttu-id="42de8-116">Bu yöntem, [ICLRStrongName:: GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) yöntemiyle aynıdır, ancak dosya adı belirtimi UNICODE yerine ANSI olur.</span><span class="sxs-lookup"><span data-stu-id="42de8-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42de8-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="42de8-117">Requirements</span></span>  
 <span data-ttu-id="42de8-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42de8-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42de8-119">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="42de8-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="42de8-120">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="42de8-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42de8-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42de8-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42de8-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42de8-122">See also</span></span>

- [<span data-ttu-id="42de8-123">GetHashFromFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="42de8-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="42de8-124">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="42de8-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
