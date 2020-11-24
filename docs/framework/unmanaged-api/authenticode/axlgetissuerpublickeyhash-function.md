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
ms.openlocfilehash: 49674e43109108e41b135cecbec061ad61e14865
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679968"
---
# <a name="_axlgetissuerpublickeyhash-function"></a><span data-ttu-id="c6b2c-102">\_Axlgetıserpublickeyhash Işlevi</span><span class="sxs-lookup"><span data-stu-id="c6b2c-102">\_AxlGetIssuerPublicKeyHash Function</span></span>

<span data-ttu-id="c6b2c-103">Belirtilen sertifikayı imzalamak için kullanılan özel anahtarla ilişkili ortak anahtarın SHA-1 karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="c6b2c-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6b2c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c6b2c-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6b2c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c6b2c-105">Parameters</span></span>  

 `pChainContext`  
 <span data-ttu-id="c6b2c-106">'ndaki CSP ortak anahtar blobu.</span><span class="sxs-lookup"><span data-stu-id="c6b2c-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="c6b2c-107">[CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısına bakın.</span><span class="sxs-lookup"><span data-stu-id="c6b2c-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="c6b2c-108">dışı Onaltılık kodlanmış ortak anahtar belirtecini almak için bir WCHAR \* işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c6b2c-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6b2c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c6b2c-109">Return Value</span></span>  

 <span data-ttu-id="c6b2c-110">`S_OK` işlev başarılı olursa; Aksi takdirde `S_FALSE` .</span><span class="sxs-lookup"><span data-stu-id="c6b2c-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6b2c-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6b2c-111">See also</span></span>

- [<span data-ttu-id="c6b2c-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="c6b2c-112">Authenticode</span></span>](index.md)
