---
title: _AxlGetIssuerPublicKeyHash İşlevi
ms.date: 03/30/2017
api_name:
- _AxlGetIssuerPublicKeyHash
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: fb626b41-b888-4625-84c3-2c02b5e3866f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 408b71bf38427d12418e05f8b509fe841bc95ef1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43395240"
---
# <a name="axlgetissuerpublickeyhash-function"></a><span data-ttu-id="066a2-102">_AxlGetIssuerPublicKeyHash İşlevi</span><span class="sxs-lookup"><span data-stu-id="066a2-102">_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="066a2-103">Belirtilen sertifika imzalamak için kullanılan özel anahtarıyla ilişkilendirilmiş ortak anahtar SHA-1 karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="066a2-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="066a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="066a2-104">Syntax</span></span>  
  
```  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="066a2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="066a2-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="066a2-106">[in] CSP ortak anahtar blob'u.</span><span class="sxs-lookup"><span data-stu-id="066a2-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="066a2-107">Bkz: [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) yapısı.</span><span class="sxs-lookup"><span data-stu-id="066a2-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="066a2-108">[out] WCHAR işaretçisi \* onaltılık kodlanmış ortak anahtar belirteci almak için.</span><span class="sxs-lookup"><span data-stu-id="066a2-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="066a2-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="066a2-109">Return Value</span></span>  
 <span data-ttu-id="066a2-110">`S_OK` işlev başarılı olursa; Aksi takdirde `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="066a2-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="066a2-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="066a2-111">See Also</span></span>  
 [<span data-ttu-id="066a2-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="066a2-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
