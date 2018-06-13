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
ms.openlocfilehash: b197aa539e60a9dbcee55cf190c44b45da3a5fb4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402021"
---
# <a name="axlgetissuerpublickeyhash-function"></a><span data-ttu-id="98d70-102">_AxlGetIssuerPublicKeyHash İşlevi</span><span class="sxs-lookup"><span data-stu-id="98d70-102">_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="98d70-103">Belirtilen sertifika imzalamak için kullanılan özel anahtar ile ilişkili ortak anahtarın SHA-1 karma alır.</span><span class="sxs-lookup"><span data-stu-id="98d70-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98d70-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98d70-104">Syntax</span></span>  
  
```  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="98d70-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="98d70-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="98d70-106">[in] CSP ortak anahtarı blob.</span><span class="sxs-lookup"><span data-stu-id="98d70-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="98d70-107">Bkz: [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) yapısı.</span><span class="sxs-lookup"><span data-stu-id="98d70-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="98d70-108">[out] Bir işaretçi WCHAR \* onaltılık kodlanmış ortak anahtar belirteci almak için.</span><span class="sxs-lookup"><span data-stu-id="98d70-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="98d70-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="98d70-109">Return Value</span></span>  
 <span data-ttu-id="98d70-110">`S_OK` işlev başarılı olursa; Aksi takdirde `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="98d70-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98d70-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="98d70-111">See Also</span></span>  
 [<span data-ttu-id="98d70-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="98d70-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
