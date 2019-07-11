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
ms.openlocfilehash: 680d9c959c57620ff38f8e785c670b451e5805b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741224"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="684ce-102">CertFreeAuthenticodeTimestamperInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="684ce-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="684ce-103">İçin ayrılan kaynakları serbest bırakan [axl_authentıcode_tımestamper_ınfo](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="684ce-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="684ce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="684ce-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="684ce-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="684ce-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="684ce-106">[out içinde] Serbest bırakılacak zamanı stamper bilgiler.</span><span class="sxs-lookup"><span data-stu-id="684ce-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="684ce-107">Bkz: [axl_authentıcode_tımestamper_ınfo](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="684ce-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="684ce-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="684ce-108">Return Value</span></span>  
 <span data-ttu-id="684ce-109">`S_OK` işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="684ce-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="684ce-110">Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="684ce-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="684ce-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="684ce-111">See also</span></span>

- [<span data-ttu-id="684ce-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="684ce-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
