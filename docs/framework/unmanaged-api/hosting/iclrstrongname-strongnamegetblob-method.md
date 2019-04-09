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
ms.openlocfilehash: 38b6785afae75888398f1c0d3d69be2ce21d67bd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160790"
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="467ed-102">ICLRStrongName::StrongNameGetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="467ed-102">ICLRStrongName::StrongNameGetBlob Method</span></span>
<span data-ttu-id="467ed-103">Belirtilen arabellek, yürütülebilir dosyanın belirtilen adreste ikili gösterimini ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="467ed-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="467ed-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="467ed-104">Syntax</span></span>  
  
```  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="467ed-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="467ed-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="467ed-106">[in] Yüklenen yürütülebilir dosyanın geçerli bir yol.</span><span class="sxs-lookup"><span data-stu-id="467ed-106">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="467ed-107">[in] Arabelleğe yürütülebilir dosyayı yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="467ed-107">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="467ed-108">[out içinde] Bayt cinsinden en büyük boyutu, istenen `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="467ed-108">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="467ed-109">İade, bayt cinsinden gerçek boyutu bağlı, `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="467ed-109">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="467ed-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="467ed-110">Return Value</span></span>  
 `S_OK` <span data-ttu-id="467ed-111">yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="467ed-111">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="467ed-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="467ed-112">Requirements</span></span>  
 <span data-ttu-id="467ed-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="467ed-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="467ed-114">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="467ed-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="467ed-115">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="467ed-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="467ed-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="467ed-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="467ed-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="467ed-117">See also</span></span>

- [<span data-ttu-id="467ed-118">StrongNameGetBlobFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="467ed-118">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="467ed-119">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="467ed-119">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
