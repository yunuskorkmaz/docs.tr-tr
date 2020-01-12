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
ms.openlocfilehash: b42079d138e754996470e07b884d49c1ebb625c3
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901163"
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="7d2ab-102">ICLRStrongName::GetHashFromBlob Metodu</span><span class="sxs-lookup"><span data-stu-id="7d2ab-102">ICLRStrongName::GetHashFromBlob Method</span></span>
<span data-ttu-id="7d2ab-103">Belirtilen karma algoritmasını kullanarak, belirtilen bellek adresindeki derlemenin karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="7d2ab-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d2ab-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d2ab-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="7d2ab-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7d2ab-105">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="7d2ab-106">'ndaki Karma hale getirilen bellek bloğunun adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7d2ab-106">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="7d2ab-107">'ndaki Bellek bloğunun bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="7d2ab-107">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="7d2ab-108">[in, out] Karma algoritmayı belirten bir sabit.</span><span class="sxs-lookup"><span data-stu-id="7d2ab-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="7d2ab-109">Varsayılan algoritma için sıfır kullanın.</span><span class="sxs-lookup"><span data-stu-id="7d2ab-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="7d2ab-110">dışı Döndürülen karma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="7d2ab-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="7d2ab-111">'ndaki İstenen en büyük boyut `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="7d2ab-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="7d2ab-112">dışı Döndürülen `pbHash`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="7d2ab-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d2ab-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7d2ab-113">Return Value</span></span>  
 <span data-ttu-id="7d2ab-114">Yöntem başarıyla tamamlanırsa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="7d2ab-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d2ab-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d2ab-115">Requirements</span></span>  
 <span data-ttu-id="7d2ab-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d2ab-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d2ab-117">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="7d2ab-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7d2ab-118">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="7d2ab-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d2ab-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d2ab-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d2ab-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d2ab-120">See also</span></span>

- [<span data-ttu-id="7d2ab-121">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d2ab-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
