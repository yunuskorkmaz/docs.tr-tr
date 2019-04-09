---
title: _AxlPublicKeyBlobToPublicKeyToken İşlevi
ms.date: 03/30/2017
api_name:
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b2535441da173ee13653c68f25039fd1431261a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147439"
---
# <a name="axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="12640-102">_AxlPublicKeyBlobToPublicKeyToken İşlevi</span><span class="sxs-lookup"><span data-stu-id="12640-102">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>
<span data-ttu-id="12640-103">Tanımlayıcı ad ortak anahtar belirteci, bir CSP PUBLICKEYBLOB biçiminden hesaplar.</span><span class="sxs-lookup"><span data-stu-id="12640-103">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12640-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12640-104">Syntax</span></span>  
  
```  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12640-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="12640-105">Parameters</span></span>  
 `pCspPublicKeyBlob`  
 <span data-ttu-id="12640-106">[in] CSP ortak anahtar blob'u.</span><span class="sxs-lookup"><span data-stu-id="12640-106">[in] The CSP public key blob.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="12640-107">[out] WCHAR işaretçisi \* onaltılık kodlanmış ortak anahtar karması almak için.</span><span class="sxs-lookup"><span data-stu-id="12640-107">[out] A pointer to WCHAR \* to receive the hex-encoded public key hash.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12640-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="12640-108">Return Value</span></span>  
 `S_OK` <span data-ttu-id="12640-109">işlev başarılı olursa; Aksi takdirde `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="12640-109">if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12640-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12640-110">See also</span></span>

- [<span data-ttu-id="12640-111">Authenticode</span><span class="sxs-lookup"><span data-stu-id="12640-111">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
