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
ms.openlocfilehash: 4f0806e0273b111e3398fb8f2884231b96cf1116
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099765"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="a4b6a-102">CertFreeAuthenticodeTimestamperInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="a4b6a-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="a4b6a-103">[AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) yapısı için ayrılan kaynakları boşaltır.</span><span class="sxs-lookup"><span data-stu-id="a4b6a-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4b6a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4b6a-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4b6a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a4b6a-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="a4b6a-106">[in, out] Yayımlanacak zaman bilgileri.</span><span class="sxs-lookup"><span data-stu-id="a4b6a-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="a4b6a-107">Bkz. [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="a4b6a-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4b6a-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a4b6a-108">Return Value</span></span>  
 <span data-ttu-id="a4b6a-109">işlev başarılı olursa `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="a4b6a-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="a4b6a-110">Aksi takdirde, bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="a4b6a-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4b6a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4b6a-111">See also</span></span>

- [<span data-ttu-id="a4b6a-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="a4b6a-112">Authenticode</span></span>](index.md)
