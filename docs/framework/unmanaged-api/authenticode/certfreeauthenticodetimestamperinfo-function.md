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
ms.openlocfilehash: 27c16cb5d85ddffc1646bee893c5644682812025
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560587"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="587d8-102">CertFreeAuthenticodeTimestamperInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="587d8-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="587d8-103">İçin ayrılan kaynakları serbest bırakan [axl_authentıcode_tımestamper_ınfo](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="587d8-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="587d8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="587d8-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="587d8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="587d8-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="587d8-106">[out içinde] Serbest bırakılacak zamanı stamper bilgiler.</span><span class="sxs-lookup"><span data-stu-id="587d8-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="587d8-107">Bkz: [axl_authentıcode_tımestamper_ınfo](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="587d8-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="587d8-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="587d8-108">Return Value</span></span>  
 <span data-ttu-id="587d8-109">`S_OK` işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="587d8-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="587d8-110">Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="587d8-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="587d8-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="587d8-111">See also</span></span>
- [<span data-ttu-id="587d8-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="587d8-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
