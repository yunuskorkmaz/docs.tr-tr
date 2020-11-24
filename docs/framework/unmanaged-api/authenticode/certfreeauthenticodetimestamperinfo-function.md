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
ms.openlocfilehash: 1ef71b14faf66c179030dff2a7d953e27463c1f7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674170"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="630af-102">CertFreeAuthenticodeTimestamperInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="630af-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>

<span data-ttu-id="630af-103">[AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) yapısı için ayrılan kaynakları boşaltır.</span><span class="sxs-lookup"><span data-stu-id="630af-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="630af-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="630af-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="630af-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="630af-105">Parameters</span></span>  

 `pTimestamperInfo`  
 <span data-ttu-id="630af-106">[in, out] Yayımlanacak zaman bilgileri.</span><span class="sxs-lookup"><span data-stu-id="630af-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="630af-107">[AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) yapısına bakın.</span><span class="sxs-lookup"><span data-stu-id="630af-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="630af-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="630af-108">Return Value</span></span>  

 <span data-ttu-id="630af-109">`S_OK` işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="630af-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="630af-110">Aksi takdirde, bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="630af-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="630af-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="630af-111">See also</span></span>

- [<span data-ttu-id="630af-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="630af-112">Authenticode</span></span>](index.md)
