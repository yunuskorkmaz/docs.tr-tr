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
ms.openlocfilehash: 42f5685a9a976be7a3a73badf286f77216e43106
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741235"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="291a7-102">CertFreeAuthenticodeSignerInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="291a7-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="291a7-103">İçin ayrılan kaynakları serbest bırakan [axl_authentıcode_sıgner_ınfo](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="291a7-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="291a7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="291a7-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="291a7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="291a7-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="291a7-106">[out içinde] Yayımlanacak imzalayan bilgileri.</span><span class="sxs-lookup"><span data-stu-id="291a7-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="291a7-107">Bkz: [axl_authentıcode_sıgner_ınfo](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="291a7-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="291a7-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="291a7-108">Return Value</span></span>  
 <span data-ttu-id="291a7-109">`S_OK` işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="291a7-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="291a7-110">Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="291a7-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="291a7-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="291a7-111">See also</span></span>

- [<span data-ttu-id="291a7-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="291a7-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
