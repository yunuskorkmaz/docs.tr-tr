---
title: CertFreeAuthenticodeTimestamperInfo İşlevi
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeTimestamperInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 3eb14c49-68c2-4516-ac89-e5bd7473831c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 082ed24eb65de12f337ab4a379b088da0f6eea5a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497385"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="bed9a-102">CertFreeAuthenticodeTimestamperInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="bed9a-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="bed9a-103">İçin ayrılan kaynakları serbest bırakan [axl_authentıcode_tımestamper_ınfo](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="bed9a-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bed9a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bed9a-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bed9a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bed9a-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="bed9a-106">[out içinde] Serbest bırakılacak zamanı stamper bilgiler.</span><span class="sxs-lookup"><span data-stu-id="bed9a-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="bed9a-107">Bkz: [axl_authentıcode_tımestamper_ınfo](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="bed9a-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bed9a-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bed9a-108">Return Value</span></span>  
 <span data-ttu-id="bed9a-109">`S_OK` işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="bed9a-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="bed9a-110">Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="bed9a-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bed9a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bed9a-111">See also</span></span>
- [<span data-ttu-id="bed9a-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="bed9a-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
