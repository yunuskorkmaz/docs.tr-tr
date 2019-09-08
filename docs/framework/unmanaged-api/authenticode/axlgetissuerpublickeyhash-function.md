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
ms.openlocfilehash: 4b101a912eb58ed14f81d847ea2fd6ce9f22c065
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787091"
---
# <a name="_axlgetissuerpublickeyhash-function"></a><span data-ttu-id="c2510-102">\_Axlgetıserpublickeyhash Işlevi</span><span class="sxs-lookup"><span data-stu-id="c2510-102">\_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="c2510-103">Belirtilen sertifikayı imzalamak için kullanılan özel anahtarla ilişkili ortak anahtarın SHA-1 karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="c2510-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2510-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2510-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2510-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c2510-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="c2510-106">'ndaki CSP ortak anahtar blobu.</span><span class="sxs-lookup"><span data-stu-id="c2510-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="c2510-107">Bkz. [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısı.</span><span class="sxs-lookup"><span data-stu-id="c2510-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="c2510-108">dışı Onaltılık kodlanmış ortak anahtar belirtecini almak için bir WCHAR \* işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c2510-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2510-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c2510-109">Return Value</span></span>  
 <span data-ttu-id="c2510-110">`S_OK`işlev başarılı olursa; Aksi `S_FALSE`takdirde.</span><span class="sxs-lookup"><span data-stu-id="c2510-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2510-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2510-111">See also</span></span>

- [<span data-ttu-id="c2510-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="c2510-112">Authenticode</span></span>](index.md)
