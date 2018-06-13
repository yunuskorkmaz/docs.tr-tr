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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a489e05435ce160c65e936f448688d69b3a965f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435267"
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="2a129-102">ICLRStrongName::GetHashFromBlob Metodu</span><span class="sxs-lookup"><span data-stu-id="2a129-102">ICLRStrongName::GetHashFromBlob Method</span></span>
<span data-ttu-id="2a129-103">Derleme karmasını belirtilen karma algoritması kullanılarak belirtilen bellek adresinde alır.</span><span class="sxs-lookup"><span data-stu-id="2a129-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a129-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a129-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a129-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2a129-105">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="2a129-106">[in] Karma hale getirilmesi için bellek bloğu adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2a129-106">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="2a129-107">[in] Uzunluğu, bayt cinsinden bellek bloğu.</span><span class="sxs-lookup"><span data-stu-id="2a129-107">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="2a129-108">[içinde out] Karma algoritmasını belirtir sabiti.</span><span class="sxs-lookup"><span data-stu-id="2a129-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="2a129-109">Varsayılan algoritma için sıfır değerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2a129-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="2a129-110">[out] Döndürülen karma arabellek.</span><span class="sxs-lookup"><span data-stu-id="2a129-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="2a129-111">[in] İstenen en büyük boyutunu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="2a129-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="2a129-112">[out] Dönen bayt cinsinden boyutu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="2a129-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2a129-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2a129-113">Return Value</span></span>  
 <span data-ttu-id="2a129-114">`S_OK` Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="2a129-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a129-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a129-115">Requirements</span></span>  
 <span data-ttu-id="2a129-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a129-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a129-117">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="2a129-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2a129-118">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2a129-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2a129-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a129-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a129-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2a129-120">See Also</span></span>  
 [<span data-ttu-id="2a129-121">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a129-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
