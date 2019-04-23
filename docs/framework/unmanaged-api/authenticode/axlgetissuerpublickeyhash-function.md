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
ms.openlocfilehash: 448712561f1531a055ac141db9825581525c779c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59106710"
---
# <a name="axlgetissuerpublickeyhash-function"></a><span data-ttu-id="c91db-102">_AxlGetIssuerPublicKeyHash İşlevi</span><span class="sxs-lookup"><span data-stu-id="c91db-102">_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="c91db-103">Belirtilen sertifika imzalamak için kullanılan özel anahtarıyla ilişkilendirilmiş ortak anahtar SHA-1 karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="c91db-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c91db-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c91db-104">Syntax</span></span>  
  
```  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c91db-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c91db-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="c91db-106">[in] CSP ortak anahtar blob'u.</span><span class="sxs-lookup"><span data-stu-id="c91db-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="c91db-107">Bkz: [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) yapısı.</span><span class="sxs-lookup"><span data-stu-id="c91db-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="c91db-108">[out] WCHAR işaretçisi \* onaltılık kodlanmış ortak anahtar belirteci almak için.</span><span class="sxs-lookup"><span data-stu-id="c91db-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c91db-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c91db-109">Return Value</span></span>  
 <span data-ttu-id="c91db-110">`S_OK` işlev başarılı olursa; Aksi takdirde `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="c91db-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c91db-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c91db-111">See also</span></span>

- [<span data-ttu-id="c91db-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="c91db-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
