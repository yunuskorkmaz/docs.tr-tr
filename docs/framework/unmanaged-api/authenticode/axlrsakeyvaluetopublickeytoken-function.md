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
ms.openlocfilehash: 4af27a2abf1a0bcf4d79eda389c5f79f0ecb1eef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="8ec9c-102">_AxlRSAKeyValueToPublicKeyToken İşlevi</span><span class="sxs-lookup"><span data-stu-id="8ec9c-102">_AxlRSAKeyValueToPublicKeyToken Function</span></span>
<span data-ttu-id="8ec9c-103">Tanımlayıcı adlı bir ortak anahtar belirteci için bir mod ve üs dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="8ec9c-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ec9c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ec9c-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ec9c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8ec9c-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="8ec9c-106">[in] Base64 ile kodlanmış Modulus blob (gelen \<Modulus > öğesi).</span><span class="sxs-lookup"><span data-stu-id="8ec9c-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="8ec9c-107">Bkz: [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) yapısı.</span><span class="sxs-lookup"><span data-stu-id="8ec9c-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="8ec9c-108">[in] Base64 ile kodlanmış üs blob (gelen \<üs > öğesi).</span><span class="sxs-lookup"><span data-stu-id="8ec9c-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="8ec9c-109">Bkz: [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) yapısı.</span><span class="sxs-lookup"><span data-stu-id="8ec9c-109">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="8ec9c-110">[out] Bir işaretçi WCHAR * onaltılık kodlanmış ortak anahtar belirteci almak için.</span><span class="sxs-lookup"><span data-stu-id="8ec9c-110">[out] A pointer to WCHAR * to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ec9c-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8ec9c-111">Return Value</span></span>  
 <span data-ttu-id="8ec9c-112">`S_OK`işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="8ec9c-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="8ec9c-113">Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="8ec9c-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ec9c-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ec9c-114">See Also</span></span>  
 [<span data-ttu-id="8ec9c-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="8ec9c-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
