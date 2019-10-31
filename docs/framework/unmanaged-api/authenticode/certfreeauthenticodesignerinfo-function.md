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
ms.openlocfilehash: a233e0b8d17b9ee61b1991086f794c9fb20f89e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099831"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="73e65-102">CertFreeAuthenticodeSignerInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="73e65-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="73e65-103">[AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) yapısı için ayrılan kaynakları boşaltır.</span><span class="sxs-lookup"><span data-stu-id="73e65-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73e65-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73e65-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73e65-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="73e65-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="73e65-106">[in, out] Yayımlanacak imzalayan bilgileri.</span><span class="sxs-lookup"><span data-stu-id="73e65-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="73e65-107">Bkz. [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="73e65-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73e65-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="73e65-108">Return Value</span></span>  
 <span data-ttu-id="73e65-109">işlev başarılı olursa `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="73e65-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="73e65-110">Aksi takdirde, bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="73e65-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73e65-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73e65-111">See also</span></span>

- [<span data-ttu-id="73e65-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="73e65-112">Authenticode</span></span>](index.md)
