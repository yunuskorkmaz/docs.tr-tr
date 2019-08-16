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
ms.openlocfilehash: 1cfc2f5cde22bf63275dd4bdc65857ac1d51b3fe
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038426"
---
# <a name="_axlgetissuerpublickeyhash-function"></a><span data-ttu-id="0de88-102">\_Axlgetıserpublickeyhash Işlevi</span><span class="sxs-lookup"><span data-stu-id="0de88-102">\_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="0de88-103">Belirtilen sertifikayı imzalamak için kullanılan özel anahtarla ilişkili ortak anahtarın SHA-1 karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="0de88-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0de88-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0de88-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0de88-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0de88-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="0de88-106">'ndaki CSP ortak anahtar blobu.</span><span class="sxs-lookup"><span data-stu-id="0de88-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="0de88-107">Bkz. [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısı.</span><span class="sxs-lookup"><span data-stu-id="0de88-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="0de88-108">dışı Onaltılık kodlanmış ortak anahtar belirtecini almak için bir WCHAR \* işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0de88-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0de88-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0de88-109">Return Value</span></span>  
 <span data-ttu-id="0de88-110">`S_OK`işlev başarılı olursa; Aksi `S_FALSE`takdirde.</span><span class="sxs-lookup"><span data-stu-id="0de88-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0de88-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0de88-111">See also</span></span>

- [<span data-ttu-id="0de88-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="0de88-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
