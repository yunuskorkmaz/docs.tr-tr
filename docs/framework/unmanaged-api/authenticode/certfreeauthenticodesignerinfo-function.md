---
title: "CertFreeAuthenticodeSignerInfo İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CertFreeAuthenticodeSignerInfo
api_location: clr.dll
api_type: DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f922cdba8bcfce6c9ff4543f6aea5bacfdc60ab0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="5e23b-102">CertFreeAuthenticodeSignerInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="5e23b-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="5e23b-103">İçin ayrılan kaynakları serbest bırakır [axl_authentıcode_sıgner_ınfo](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="5e23b-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e23b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e23b-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5e23b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5e23b-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="5e23b-106">[içinde out] Yayımlanacak imzalayan bilgileri.</span><span class="sxs-lookup"><span data-stu-id="5e23b-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="5e23b-107">Bkz: [axl_authentıcode_sıgner_ınfo](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="5e23b-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e23b-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5e23b-108">Return Value</span></span>  
 <span data-ttu-id="5e23b-109">`S_OK`işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="5e23b-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="5e23b-110">Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e23b-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e23b-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5e23b-111">See Also</span></span>  
 [<span data-ttu-id="5e23b-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="5e23b-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
