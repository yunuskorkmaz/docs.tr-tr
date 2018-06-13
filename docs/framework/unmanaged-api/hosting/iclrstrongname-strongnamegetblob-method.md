---
title: ICLRStrongName::StrongNameGetBlob Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlob
- ICLRStrongName.StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlob
helpviewer_keywords:
- ICLRStrongName::StrongNameGetBlob method [.NET Framework hosting]
- StrongNameGetBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: a24218f8-7196-44be-b7a2-ee9cdd7a85c4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81e2c59a538bd436606c226855c002cecd501e33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433672"
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="04288-102">ICLRStrongName::StrongNameGetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04288-102">ICLRStrongName::StrongNameGetBlob Method</span></span>
<span data-ttu-id="04288-103">Belirtilen arabellek yürütülebilir dosyanın belirtilen adresteki ikili gösterimidir doldurur.</span><span class="sxs-lookup"><span data-stu-id="04288-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04288-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04288-104">Syntax</span></span>  
  
```  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04288-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="04288-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="04288-106">[in] Yüklenecek yürütülebilir dosyanın geçerli bir yol.</span><span class="sxs-lookup"><span data-stu-id="04288-106">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="04288-107">[in] Arabelleğe hangi yürütülebilir dosyası yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="04288-107">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="04288-108">[içinde out] Bayt cinsinden en büyük boyutu, istenen `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="04288-108">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="04288-109">Return, bayt cinsinden gerçek boyutu bağlı, `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="04288-109">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04288-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="04288-110">Return Value</span></span>  
 <span data-ttu-id="04288-111">`S_OK` Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="04288-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04288-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04288-112">Requirements</span></span>  
 <span data-ttu-id="04288-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04288-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04288-114">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="04288-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="04288-115">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="04288-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04288-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04288-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04288-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="04288-117">See Also</span></span>  
 [<span data-ttu-id="04288-118">StrongNameGetBlobFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04288-118">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="04288-119">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04288-119">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
