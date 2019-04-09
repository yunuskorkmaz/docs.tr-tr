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
ms.openlocfilehash: bdb764417b757cd7388c49d7e5cac9a960074820
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142408"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="de754-102">CertFreeAuthenticodeSignerInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="de754-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="de754-103">İçin ayrılan kaynakları serbest bırakan [axl_authentıcode_sıgner_ınfo](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="de754-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de754-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de754-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de754-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="de754-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="de754-106">[out içinde] Yayımlanacak imzalayan bilgileri.</span><span class="sxs-lookup"><span data-stu-id="de754-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="de754-107">Bkz: [axl_authentıcode_sıgner_ınfo](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="de754-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de754-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="de754-108">Return Value</span></span>  
 `S_OK` <span data-ttu-id="de754-109">işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="de754-109">if the function succeeds.</span></span> <span data-ttu-id="de754-110">Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="de754-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de754-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de754-111">See also</span></span>

- [<span data-ttu-id="de754-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="de754-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
