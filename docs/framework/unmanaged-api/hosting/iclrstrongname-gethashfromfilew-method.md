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
ms.openlocfilehash: 6dbb3360132186c38c007fb5fa12a3724ca145aa
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762103"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="36368-102">ICLRStrongName::GetHashFromFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="36368-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="36368-103">Unicode dizesi tarafından belirtilen dosyanın içeriği üzerinde bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="36368-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36368-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="36368-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="36368-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="36368-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="36368-106">'ndaki Karma olacak dosyanın Unicode adı.</span><span class="sxs-lookup"><span data-stu-id="36368-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="36368-107">[in, out] Karma oluşturulurken kullanılacak algoritma.</span><span class="sxs-lookup"><span data-stu-id="36368-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="36368-108">Geçerli algoritmalar Win32 CryptoAPI tarafından tanımlı olanlardır.</span><span class="sxs-lookup"><span data-stu-id="36368-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="36368-109">`piHashAlg`0 olarak ayarlanırsa, CALG_SHA-1 varsayılan algoritma kullanılır.</span><span class="sxs-lookup"><span data-stu-id="36368-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="36368-110">dışı Oluşturulan karmayı içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="36368-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="36368-111">'ndaki Tarafından işaret edilen arabelleğin en büyük boyutu `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="36368-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="36368-112">dışı Bayt cinsinden boyutu `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="36368-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36368-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="36368-113">Return Value</span></span>  
 <span data-ttu-id="36368-114">`S_OK`Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="36368-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36368-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36368-115">Remarks</span></span>  
 <span data-ttu-id="36368-116">Bu yöntem, [ICLRStrongName:: GetHashFromFile](iclrstrongname-gethashfromfile-method.md) yöntemiyle aynıdır, ancak dosya adı belirtimi ANSI yerine Unicode olur.</span><span class="sxs-lookup"><span data-stu-id="36368-116">This method is the same as the [ICLRStrongName::GetHashFromFile](iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36368-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="36368-117">Requirements</span></span>  
 <span data-ttu-id="36368-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36368-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36368-119">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="36368-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="36368-120">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="36368-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="36368-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36368-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36368-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36368-122">See also</span></span>

- [<span data-ttu-id="36368-123">GetHashFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="36368-123">GetHashFromFile Method</span></span>](iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="36368-124">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="36368-124">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
