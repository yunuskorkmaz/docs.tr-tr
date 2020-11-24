---
title: ICLRStrongName::GetHashFromAssemblyFileW Metodu
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW method [.NET Framework hosting]
- GetHashFromAssemblyFileW method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5d0b44a2-5a14-44a2-9a0e-e8682fd4e106
topic_type:
- apiref
ms.openlocfilehash: e94bfe6151ed42886355423a838f21e13748ec61
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685779"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="d26bb-102">ICLRStrongName::GetHashFromAssemblyFileW Metodu</span><span class="sxs-lookup"><span data-stu-id="d26bb-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>

<span data-ttu-id="d26bb-103">Unicode dizesi tarafından belirtilen dosyanın içeriği üzerinde bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d26bb-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d26bb-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d26bb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d26bb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d26bb-105">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="d26bb-106">'ndaki Karma hale getirilen dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="d26bb-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="d26bb-107">Bu parametre bir Unicode dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d26bb-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="d26bb-108">[in, out] Karma algoritmayı belirten bir sabit.</span><span class="sxs-lookup"><span data-stu-id="d26bb-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="d26bb-109">Varsayılan karma algoritması için sıfır kullanın.</span><span class="sxs-lookup"><span data-stu-id="d26bb-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="d26bb-110">dışı Döndürülen karma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="d26bb-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="d26bb-111">'ndaki İstenen en büyük boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="d26bb-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="d26bb-112">dışı Bayt cinsinden döndürülen boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="d26bb-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d26bb-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d26bb-113">Return Value</span></span>  

 <span data-ttu-id="d26bb-114">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="d26bb-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d26bb-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d26bb-115">Requirements</span></span>  

 <span data-ttu-id="d26bb-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d26bb-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d26bb-117">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="d26bb-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d26bb-118">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d26bb-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d26bb-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d26bb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d26bb-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d26bb-120">See also</span></span>

- [<span data-ttu-id="d26bb-121">GetHashFromAssemblyFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d26bb-121">GetHashFromAssemblyFile Method</span></span>](iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="d26bb-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d26bb-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
