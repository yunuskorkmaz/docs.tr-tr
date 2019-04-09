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
ms.openlocfilehash: f84d50579feade09df1b42a8e2f0c6b3e6a94fac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157770"
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="b5bc1-102">ICLRStrongName::GetHashFromBlob Metodu</span><span class="sxs-lookup"><span data-stu-id="b5bc1-102">ICLRStrongName::GetHashFromBlob Method</span></span>
<span data-ttu-id="b5bc1-103">Derleme karması belirtilen karma algoritması kullanılarak belirtilen bellek adresinde alır.</span><span class="sxs-lookup"><span data-stu-id="b5bc1-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5bc1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b5bc1-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b5bc1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b5bc1-105">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="b5bc1-106">[in] Adres karma hale getirilecek bellek bloğu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b5bc1-106">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="b5bc1-107">[in] Uzunluğu, bayt cinsinden bellek bloğu.</span><span class="sxs-lookup"><span data-stu-id="b5bc1-107">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="b5bc1-108">[out içinde] Sabit karma algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5bc1-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="b5bc1-109">Sıfır varsayılan algoritma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5bc1-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="b5bc1-110">[out] Döndürülen karma arabellek.</span><span class="sxs-lookup"><span data-stu-id="b5bc1-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="b5bc1-111">[in] İstenen en büyük boyutunu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="b5bc1-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="b5bc1-112">[out] Döndürülen bayt cinsinden boyutu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="b5bc1-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5bc1-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b5bc1-113">Return Value</span></span>  
 `S_OK` <span data-ttu-id="b5bc1-114">yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="b5bc1-114">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5bc1-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b5bc1-115">Requirements</span></span>  
 <span data-ttu-id="b5bc1-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5bc1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5bc1-117">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b5bc1-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b5bc1-118">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b5bc1-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b5bc1-119">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="b5bc1-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b5bc1-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5bc1-120">See also</span></span>

- [<span data-ttu-id="b5bc1-121">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b5bc1-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
