---
description: ': ICLRStrongName:: GetHashFromBlob yöntemi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 20d03184f57e77741e656575038e426ee37968f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637072"
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="4eb20-103">ICLRStrongName::GetHashFromBlob Metodu</span><span class="sxs-lookup"><span data-stu-id="4eb20-103">ICLRStrongName::GetHashFromBlob Method</span></span>

<span data-ttu-id="4eb20-104">Belirtilen karma algoritmasını kullanarak, belirtilen bellek adresindeki derlemenin karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="4eb20-104">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4eb20-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4eb20-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4eb20-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4eb20-106">Parameters</span></span>  

 `pbBlob`  
 <span data-ttu-id="4eb20-107">'ndaki Karma hale getirilen bellek bloğunun adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4eb20-107">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="4eb20-108">'ndaki Bellek bloğunun bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="4eb20-108">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="4eb20-109">[in, out] Karma algoritmayı belirten bir sabit.</span><span class="sxs-lookup"><span data-stu-id="4eb20-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="4eb20-110">Varsayılan algoritma için sıfır kullanın.</span><span class="sxs-lookup"><span data-stu-id="4eb20-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="4eb20-111">dışı Döndürülen karma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="4eb20-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="4eb20-112">'ndaki İstenen en büyük boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="4eb20-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="4eb20-113">dışı Döndürülen bayt cinsinden boyutu `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="4eb20-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4eb20-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4eb20-114">Return Value</span></span>  

 <span data-ttu-id="4eb20-115">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="4eb20-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4eb20-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4eb20-116">Requirements</span></span>  

 <span data-ttu-id="4eb20-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4eb20-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4eb20-118">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="4eb20-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4eb20-119">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="4eb20-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4eb20-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4eb20-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eb20-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4eb20-121">See also</span></span>

- [<span data-ttu-id="4eb20-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4eb20-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
