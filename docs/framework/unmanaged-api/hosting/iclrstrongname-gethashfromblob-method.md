---
title: ICLRStrongName::GetHashFromBlob Metodu
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromBlob
helpviewer_keywords:
- ICLRStrongName::GetHashFromBlob method [.NET Framework hosting]
- GetHashFromBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: f91d0f89-f356-49ac-aafb-50fad963c13d
topic_type:
- apiref
ms.openlocfilehash: 6b67aed90585f57d2635bb1a22d3e009edf01159
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714815"
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="f1c0e-102">ICLRStrongName::GetHashFromBlob Metodu</span><span class="sxs-lookup"><span data-stu-id="f1c0e-102">ICLRStrongName::GetHashFromBlob Method</span></span>

<span data-ttu-id="f1c0e-103">Belirtilen karma algoritmasını kullanarak, belirtilen bellek adresindeki derlemenin karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="f1c0e-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1c0e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f1c0e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1c0e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f1c0e-105">Parameters</span></span>  

 `pbBlob`  
 <span data-ttu-id="f1c0e-106">'ndaki Karma hale getirilen bellek bloğunun adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f1c0e-106">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="f1c0e-107">'ndaki Bellek bloğunun bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="f1c0e-107">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="f1c0e-108">[in, out] Karma algoritmayı belirten bir sabit.</span><span class="sxs-lookup"><span data-stu-id="f1c0e-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="f1c0e-109">Varsayılan algoritma için sıfır kullanın.</span><span class="sxs-lookup"><span data-stu-id="f1c0e-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="f1c0e-110">dışı Döndürülen karma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="f1c0e-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="f1c0e-111">'ndaki İstenen en büyük boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="f1c0e-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="f1c0e-112">dışı Döndürülen bayt cinsinden boyutu `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="f1c0e-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1c0e-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f1c0e-113">Return Value</span></span>  

 <span data-ttu-id="f1c0e-114">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="f1c0e-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1c0e-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1c0e-115">Requirements</span></span>  

 <span data-ttu-id="f1c0e-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1c0e-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1c0e-117">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="f1c0e-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f1c0e-118">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f1c0e-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1c0e-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1c0e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1c0e-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1c0e-120">See also</span></span>

- [<span data-ttu-id="f1c0e-121">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f1c0e-121">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
