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
ms.openlocfilehash: cbed2ece8b10c6385341c0af44a81dfa16b6f60c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497489"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="cd56d-102">CertFreeAuthenticodeSignerInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="cd56d-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="cd56d-103">İçin ayrılan kaynakları serbest bırakan [axl_authentıcode_sıgner_ınfo](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="cd56d-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd56d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd56d-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd56d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cd56d-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="cd56d-106">[out içinde] Yayımlanacak imzalayan bilgileri.</span><span class="sxs-lookup"><span data-stu-id="cd56d-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="cd56d-107">Bkz: [axl_authentıcode_sıgner_ınfo](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="cd56d-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd56d-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cd56d-108">Return Value</span></span>  
 <span data-ttu-id="cd56d-109">`S_OK` işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="cd56d-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="cd56d-110">Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="cd56d-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd56d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd56d-111">See also</span></span>
- [<span data-ttu-id="cd56d-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="cd56d-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
