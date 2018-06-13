---
title: CertFreeAuthenticodeSignerInfo İşlevi
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeSignerInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84f15dc49d14e781f69d0f9da8f314eb71d8c034
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401622"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="e38c7-102">CertFreeAuthenticodeSignerInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="e38c7-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="e38c7-103">İçin ayrılan kaynakları serbest bırakır [axl_authentıcode_sıgner_ınfo](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="e38c7-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e38c7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e38c7-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e38c7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e38c7-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="e38c7-106">[içinde out] Yayımlanacak imzalayan bilgileri.</span><span class="sxs-lookup"><span data-stu-id="e38c7-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="e38c7-107">Bkz: [axl_authentıcode_sıgner_ınfo](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="e38c7-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e38c7-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e38c7-108">Return Value</span></span>  
 <span data-ttu-id="e38c7-109">`S_OK` işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="e38c7-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="e38c7-110">Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="e38c7-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e38c7-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e38c7-111">See Also</span></span>  
 [<span data-ttu-id="e38c7-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="e38c7-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
