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
ms.openlocfilehash: 355e6c7b1cd77936d5ccfa5ccff7312c8e35ac63
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220411"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="3559b-102">CertFreeAuthenticodeTimestamperInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="3559b-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="3559b-103">İçin ayrılan kaynakları serbest bırakan [axl_authentıcode_tımestamper_ınfo](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="3559b-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3559b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3559b-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3559b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3559b-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="3559b-106">[out içinde] Serbest bırakılacak zamanı stamper bilgiler.</span><span class="sxs-lookup"><span data-stu-id="3559b-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="3559b-107">Bkz: [axl_authentıcode_tımestamper_ınfo](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="3559b-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3559b-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3559b-108">Return Value</span></span>  
 `S_OK` <span data-ttu-id="3559b-109">işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="3559b-109">if the function succeeds.</span></span> <span data-ttu-id="3559b-110">Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="3559b-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3559b-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3559b-111">See also</span></span>

- [<span data-ttu-id="3559b-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="3559b-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
