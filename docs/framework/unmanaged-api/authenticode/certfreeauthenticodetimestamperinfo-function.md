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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941654"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="1378a-102">CertFreeAuthenticodeTimestamperInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="1378a-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="1378a-103">İçin ayrılan kaynakları serbest bırakan [axl_authentıcode_tımestamper_ınfo](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="1378a-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1378a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1378a-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1378a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1378a-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="1378a-106">[out içinde] Serbest bırakılacak zamanı stamper bilgiler.</span><span class="sxs-lookup"><span data-stu-id="1378a-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="1378a-107">Bkz: [axl_authentıcode_tımestamper_ınfo](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="1378a-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1378a-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1378a-108">Return Value</span></span>  
 <span data-ttu-id="1378a-109">`S_OK` işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="1378a-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="1378a-110">Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="1378a-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1378a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1378a-111">See also</span></span>

- [<span data-ttu-id="1378a-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="1378a-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
