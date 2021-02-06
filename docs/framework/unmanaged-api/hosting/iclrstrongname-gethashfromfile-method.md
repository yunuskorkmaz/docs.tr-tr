---
description: ': ICLRStrongName:: GetHashFromFile Yöntemi hakkında daha fazla bilgi'
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
ms.openlocfilehash: e930f1c21e5b0be441fe44ad352b2ef2f43d0f67
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637059"
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="8a7c2-103">ICLRStrongName::GetHashFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a7c2-103">ICLRStrongName::GetHashFromFile Method</span></span>

<span data-ttu-id="8a7c2-104">Belirtilen dosyanın içeriği üzerinde bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8a7c2-104">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a7c2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8a7c2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a7c2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8a7c2-106">Parameters</span></span>  

 `szFilePath`  
 <span data-ttu-id="8a7c2-107">'ndaki Karma yapılacak dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="8a7c2-107">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="8a7c2-108">[in, out] Karma oluşturulurken kullanılacak algoritma.</span><span class="sxs-lookup"><span data-stu-id="8a7c2-108">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="8a7c2-109">Geçerli algoritmalar Win32 CryptoAPI tarafından tanımlı olanlardır.</span><span class="sxs-lookup"><span data-stu-id="8a7c2-109">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="8a7c2-110">`piHashAlg`0 olarak ayarlanırsa, CALG_SHA-1 varsayılan algoritma kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8a7c2-110">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="8a7c2-111">dışı Oluşturulan karmayı içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="8a7c2-111">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="8a7c2-112">'ndaki İşaret eden arabelleğin en büyük boyutu `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="8a7c2-112">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="8a7c2-113">dışı Döndürülen bayt cinsinden boyutu `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="8a7c2-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a7c2-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8a7c2-114">Return Value</span></span>  

 <span data-ttu-id="8a7c2-115">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="8a7c2-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a7c2-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a7c2-116">Remarks</span></span>  

 <span data-ttu-id="8a7c2-117">Bu yöntem, [ICLRStrongName:: GetHashFromFileW](iclrstrongname-gethashfromfilew-method.md) yöntemiyle aynıdır, ancak dosya adı belirtimi UNICODE yerine ANSI olur.</span><span class="sxs-lookup"><span data-stu-id="8a7c2-117">This method is the same as the [ICLRStrongName::GetHashFromFileW](iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a7c2-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8a7c2-118">Requirements</span></span>  

 <span data-ttu-id="8a7c2-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a7c2-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a7c2-120">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="8a7c2-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8a7c2-121">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="8a7c2-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8a7c2-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a7c2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a7c2-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a7c2-123">See also</span></span>

- [<span data-ttu-id="8a7c2-124">GetHashFromFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a7c2-124">GetHashFromFileW Method</span></span>](iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="8a7c2-125">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a7c2-125">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
