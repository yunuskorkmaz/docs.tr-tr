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
ms.openlocfilehash: 357a2ca0ffc733adb14a21624cbe28fb754c8240
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776734"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="81bdd-102">CertFreeAuthenticodeSignerInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="81bdd-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="81bdd-103">[AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) yapısı için ayrılan kaynakları boşaltır.</span><span class="sxs-lookup"><span data-stu-id="81bdd-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81bdd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81bdd-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81bdd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="81bdd-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="81bdd-106">[in, out] Yayımlanacak imzalayan bilgileri.</span><span class="sxs-lookup"><span data-stu-id="81bdd-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="81bdd-107">Bkz. [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="81bdd-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81bdd-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="81bdd-108">Return Value</span></span>  
 <span data-ttu-id="81bdd-109">`S_OK`işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="81bdd-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="81bdd-110">Aksi takdirde, bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="81bdd-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81bdd-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81bdd-111">See also</span></span>

- [<span data-ttu-id="81bdd-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="81bdd-112">Authenticode</span></span>](index.md)
