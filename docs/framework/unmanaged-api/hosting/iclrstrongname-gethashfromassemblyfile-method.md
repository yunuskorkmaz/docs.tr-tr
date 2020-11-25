---
title: ICLRStrongName::GetHashFromAssemblyFile Metodu
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFile method [.NET Framework hosting]
- GetHashFromAssemblyFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 0b67ea03-d474-4605-acaa-57455790250c
topic_type:
- apiref
ms.openlocfilehash: 0a15a4d237f63da54615ee1801e6cd39620e8274
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727867"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="e1c9a-102">ICLRStrongName::GetHashFromAssemblyFile Metodu</span><span class="sxs-lookup"><span data-stu-id="e1c9a-102">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>

<span data-ttu-id="e1c9a-103">Belirtilen karma algoritmasını kullanarak belirtilen derleme dosyasının karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1c9a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e1c9a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1c9a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e1c9a-105">Parameters</span></span>  

 `szFilePath`  
 <span data-ttu-id="e1c9a-106">'ndaki Karma hale getirilen dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-106">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="e1c9a-107">[in, out] Karma algoritmayı belirten bir sabit.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="e1c9a-108">Varsayılan karma algoritması için sıfır kullanın.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-108">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="e1c9a-109">dışı Döndürülen karma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="e1c9a-110">'ndaki İstenen en büyük boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="e1c9a-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="e1c9a-111">dışı Bayt cinsinden döndürülen boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="e1c9a-111">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1c9a-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e1c9a-112">Return Value</span></span>  

 <span data-ttu-id="e1c9a-113">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="e1c9a-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1c9a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1c9a-114">Requirements</span></span>  

 <span data-ttu-id="e1c9a-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1c9a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1c9a-116">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="e1c9a-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e1c9a-117">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e1c9a-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e1c9a-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1c9a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1c9a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-119">See also</span></span>

- [<span data-ttu-id="e1c9a-120">GetHashFromAssemblyFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1c9a-120">GetHashFromAssemblyFileW Method</span></span>](iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="e1c9a-121">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1c9a-121">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
