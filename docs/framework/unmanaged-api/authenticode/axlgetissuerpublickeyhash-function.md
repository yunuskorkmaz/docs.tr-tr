---
title: "_AxlGetIssuerPublicKeyHash İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _AxlGetIssuerPublicKeyHash
api_location: clr.dll
api_type: DLLExport
ms.assetid: fb626b41-b888-4625-84c3-2c02b5e3866f
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fee2b3e0e74ec13009a9b02d226c6a99b0e2f34b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="axlgetissuerpublickeyhash-function"></a><span data-ttu-id="38717-102">_AxlGetIssuerPublicKeyHash İşlevi</span><span class="sxs-lookup"><span data-stu-id="38717-102">_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="38717-103">Belirtilen sertifika imzalamak için kullanılan özel anahtar ile ilişkili ortak anahtarın SHA-1 karma alır.</span><span class="sxs-lookup"><span data-stu-id="38717-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38717-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38717-104">Syntax</span></span>  
  
```  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38717-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="38717-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="38717-106">[in] CSP ortak anahtarı blob.</span><span class="sxs-lookup"><span data-stu-id="38717-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="38717-107">Bkz: [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) yapısı.</span><span class="sxs-lookup"><span data-stu-id="38717-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="38717-108">[out] Bir işaretçi WCHAR * onaltılık kodlanmış ortak anahtar belirteci almak için.</span><span class="sxs-lookup"><span data-stu-id="38717-108">[out] A pointer to WCHAR * to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38717-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="38717-109">Return Value</span></span>  
 <span data-ttu-id="38717-110">`S_OK`işlev başarılı olursa; Aksi takdirde `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="38717-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38717-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="38717-111">See Also</span></span>  
 [<span data-ttu-id="38717-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="38717-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
