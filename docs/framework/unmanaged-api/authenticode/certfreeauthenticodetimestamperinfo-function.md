---
title: "CertFreeAuthenticodeTimestamperInfo İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CertFreeAuthenticodeTimestamperInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 3eb14c49-68c2-4516-ac89-e5bd7473831c
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 353bba880cfa8a5ecf9ed826fbb529e31f790a12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="92578-102">CertFreeAuthenticodeTimestamperInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="92578-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="92578-103">İçin ayrılan kaynakları serbest bırakır [axl_authentıcode_tımestamper_ınfo](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="92578-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92578-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92578-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92578-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="92578-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="92578-106">[içinde out] Yayımlanacak zaman stamper bilgileri.</span><span class="sxs-lookup"><span data-stu-id="92578-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="92578-107">Bkz: [axl_authentıcode_tımestamper_ınfo](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="92578-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92578-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="92578-108">Return Value</span></span>  
 <span data-ttu-id="92578-109">`S_OK`işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="92578-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="92578-110">Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="92578-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92578-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="92578-111">See Also</span></span>  
 [<span data-ttu-id="92578-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="92578-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
