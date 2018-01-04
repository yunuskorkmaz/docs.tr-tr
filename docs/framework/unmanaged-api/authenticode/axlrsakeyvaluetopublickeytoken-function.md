---
title: "_AxlRSAKeyValueToPublicKeyToken İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _AxlRSAKeyValueToPublicKeyToken
api_location: clr.dll
api_type: DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1380f658d9c154d9ea41228cace5f9a3eed39b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="2dc44-102">_AxlRSAKeyValueToPublicKeyToken İşlevi</span><span class="sxs-lookup"><span data-stu-id="2dc44-102">_AxlRSAKeyValueToPublicKeyToken Function</span></span>
<span data-ttu-id="2dc44-103">Tanımlayıcı adlı bir ortak anahtar belirteci için bir mod ve üs dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="2dc44-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dc44-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2dc44-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2dc44-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2dc44-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="2dc44-106">[in] Base64 ile kodlanmış Modulus blob (gelen \<Modulus > öğesi).</span><span class="sxs-lookup"><span data-stu-id="2dc44-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="2dc44-107">Bkz: [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) yapısı.</span><span class="sxs-lookup"><span data-stu-id="2dc44-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="2dc44-108">[in] Base64 ile kodlanmış üs blob (gelen \<üs > öğesi).</span><span class="sxs-lookup"><span data-stu-id="2dc44-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="2dc44-109">Bkz: [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) yapısı.</span><span class="sxs-lookup"><span data-stu-id="2dc44-109">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="2dc44-110">[out] Bir işaretçi WCHAR * onaltılık kodlanmış ortak anahtar belirteci almak için.</span><span class="sxs-lookup"><span data-stu-id="2dc44-110">[out] A pointer to WCHAR * to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2dc44-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2dc44-111">Return Value</span></span>  
 <span data-ttu-id="2dc44-112">`S_OK`işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="2dc44-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="2dc44-113">Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="2dc44-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dc44-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2dc44-114">See Also</span></span>  
 [<span data-ttu-id="2dc44-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="2dc44-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
