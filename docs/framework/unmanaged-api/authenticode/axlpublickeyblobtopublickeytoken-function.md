---
title: "_AxlPublicKeyBlobToPublicKeyToken İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7c9dfd42d0908032ed9a652f6f4f5736ba775ce8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="416d6-102">_AxlPublicKeyBlobToPublicKeyToken İşlevi</span><span class="sxs-lookup"><span data-stu-id="416d6-102">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>
<span data-ttu-id="416d6-103">Güçlü ad ve ortak anahtar belirteci CSP PUBLICKEYBLOB biçimden hesaplar.</span><span class="sxs-lookup"><span data-stu-id="416d6-103">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="416d6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="416d6-104">Syntax</span></span>  
  
```  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="416d6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="416d6-105">Parameters</span></span>  
 `pCspPublicKeyBlob`  
 <span data-ttu-id="416d6-106">[in] CSP ortak anahtarı blob.</span><span class="sxs-lookup"><span data-stu-id="416d6-106">[in] The CSP public key blob.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="416d6-107">[out] Bir işaretçi WCHAR \* onaltılık kodlanmış ortak anahtar karma almak için.</span><span class="sxs-lookup"><span data-stu-id="416d6-107">[out] A pointer to WCHAR \* to receive the hex-encoded public key hash.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="416d6-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="416d6-108">Return Value</span></span>  
 <span data-ttu-id="416d6-109">`S_OK`işlev başarılı olursa; Aksi takdirde `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="416d6-109">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="416d6-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="416d6-110">See Also</span></span>  
 [<span data-ttu-id="416d6-111">Authenticode</span><span class="sxs-lookup"><span data-stu-id="416d6-111">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
