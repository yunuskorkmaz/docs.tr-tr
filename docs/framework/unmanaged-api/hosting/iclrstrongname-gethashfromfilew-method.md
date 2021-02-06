---
description: ': ICLRStrongName:: GetHashFromFileW yöntemi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 6145a044f490ef3827de6db8d84d16222306642d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636981"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="fdc7a-103">ICLRStrongName::GetHashFromFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fdc7a-103">ICLRStrongName::GetHashFromFileW Method</span></span>

<span data-ttu-id="fdc7a-104">Unicode dizesi tarafından belirtilen dosyanın içeriği üzerinde bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fdc7a-104">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdc7a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fdc7a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="fdc7a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fdc7a-106">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="fdc7a-107">'ndaki Karma olacak dosyanın Unicode adı.</span><span class="sxs-lookup"><span data-stu-id="fdc7a-107">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="fdc7a-108">[in, out] Karma oluşturulurken kullanılacak algoritma.</span><span class="sxs-lookup"><span data-stu-id="fdc7a-108">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="fdc7a-109">Geçerli algoritmalar Win32 CryptoAPI tarafından tanımlı olanlardır.</span><span class="sxs-lookup"><span data-stu-id="fdc7a-109">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="fdc7a-110">`piHashAlg`0 olarak ayarlanırsa, CALG_SHA-1 varsayılan algoritma kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fdc7a-110">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="fdc7a-111">dışı Oluşturulan karmayı içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="fdc7a-111">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="fdc7a-112">'ndaki Tarafından işaret edilen arabelleğin en büyük boyutu `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="fdc7a-112">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="fdc7a-113">dışı Bayt cinsinden boyutu `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="fdc7a-113">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fdc7a-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fdc7a-114">Return Value</span></span>  

 <span data-ttu-id="fdc7a-115">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="fdc7a-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fdc7a-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fdc7a-116">Remarks</span></span>  

 <span data-ttu-id="fdc7a-117">Bu yöntem, [ICLRStrongName:: GetHashFromFile](iclrstrongname-gethashfromfile-method.md) yöntemiyle aynıdır, ancak dosya adı belirtimi ANSI yerine Unicode olur.</span><span class="sxs-lookup"><span data-stu-id="fdc7a-117">This method is the same as the [ICLRStrongName::GetHashFromFile](iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdc7a-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fdc7a-118">Requirements</span></span>  

 <span data-ttu-id="fdc7a-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdc7a-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdc7a-120">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="fdc7a-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="fdc7a-121">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="fdc7a-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fdc7a-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdc7a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdc7a-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdc7a-123">See also</span></span>

- [<span data-ttu-id="fdc7a-124">GetHashFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fdc7a-124">GetHashFromFile Method</span></span>](iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="fdc7a-125">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fdc7a-125">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
