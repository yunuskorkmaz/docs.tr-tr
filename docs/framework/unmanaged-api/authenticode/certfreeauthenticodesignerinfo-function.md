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
ms.openlocfilehash: dc6bb5a137a50ec07f89f292e5d9beac4349c3c7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674183"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="1bdac-102">CertFreeAuthenticodeSignerInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="1bdac-102">CertFreeAuthenticodeSignerInfo Function</span></span>

<span data-ttu-id="1bdac-103">[AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) yapısı için ayrılan kaynakları boşaltır.</span><span class="sxs-lookup"><span data-stu-id="1bdac-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bdac-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1bdac-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bdac-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1bdac-105">Parameters</span></span>  

 `pSignerInfo`  
 <span data-ttu-id="1bdac-106">[in, out] Yayımlanacak imzalayan bilgileri.</span><span class="sxs-lookup"><span data-stu-id="1bdac-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="1bdac-107">[AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) yapısına bakın.</span><span class="sxs-lookup"><span data-stu-id="1bdac-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1bdac-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1bdac-108">Return Value</span></span>  

 <span data-ttu-id="1bdac-109">`S_OK` işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="1bdac-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="1bdac-110">Aksi takdirde, bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="1bdac-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bdac-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bdac-111">See also</span></span>

- [<span data-ttu-id="1bdac-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="1bdac-112">Authenticode</span></span>](index.md)
