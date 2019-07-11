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
ms.openlocfilehash: de55594db68e084009a095a083e065fbd0b8f0df
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741333"
---
# <a name="axlgetissuerpublickeyhash-function"></a><span data-ttu-id="b9b6d-102">\_AxlGetIssuerPublicKeyHash işlevi</span><span class="sxs-lookup"><span data-stu-id="b9b6d-102">\_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="b9b6d-103">Belirtilen sertifika imzalamak için kullanılan özel anahtarıyla ilişkilendirilmiş ortak anahtar SHA-1 karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="b9b6d-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9b6d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b9b6d-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9b6d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b9b6d-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="b9b6d-106">[in] CSP ortak anahtar blob'u.</span><span class="sxs-lookup"><span data-stu-id="b9b6d-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="b9b6d-107">Bkz: [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) yapısı.</span><span class="sxs-lookup"><span data-stu-id="b9b6d-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="b9b6d-108">[out] WCHAR işaretçisi \* onaltılık kodlanmış ortak anahtar belirteci almak için.</span><span class="sxs-lookup"><span data-stu-id="b9b6d-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9b6d-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b9b6d-109">Return Value</span></span>  
 <span data-ttu-id="b9b6d-110">`S_OK` işlev başarılı olursa; Aksi takdirde `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="b9b6d-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9b6d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9b6d-111">See also</span></span>

- [<span data-ttu-id="b9b6d-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="b9b6d-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
