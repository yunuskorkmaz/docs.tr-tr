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
ms.openlocfilehash: a8ecada29528b065ddad0abc80a850ee0f347f6b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786997"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="2f6be-102">CertFreeAuthenticodeTimestamperInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="2f6be-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="2f6be-103">[AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) yapısı için ayrılan kaynakları boşaltır.</span><span class="sxs-lookup"><span data-stu-id="2f6be-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f6be-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f6be-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f6be-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2f6be-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="2f6be-106">[in, out] Yayımlanacak zaman bilgileri.</span><span class="sxs-lookup"><span data-stu-id="2f6be-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="2f6be-107">Bkz. [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="2f6be-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f6be-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2f6be-108">Return Value</span></span>  
 <span data-ttu-id="2f6be-109">`S_OK`işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="2f6be-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="2f6be-110">Aksi takdirde, bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="2f6be-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f6be-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f6be-111">See also</span></span>

- [<span data-ttu-id="2f6be-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="2f6be-112">Authenticode</span></span>](index.md)
