---
title: _AxlRSAKeyValueToPublicKeyToken İşlevi
ms.date: 03/30/2017
api_name:
- _AxlRSAKeyValueToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ef73f0f7599fdff887437756a5995591fd8ec89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402419"
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="af007-102">_AxlRSAKeyValueToPublicKeyToken İşlevi</span><span class="sxs-lookup"><span data-stu-id="af007-102">_AxlRSAKeyValueToPublicKeyToken Function</span></span>
<span data-ttu-id="af007-103">Tanımlayıcı adlı bir ortak anahtar belirteci için bir mod ve üs dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="af007-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af007-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af007-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af007-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="af007-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="af007-106">[in] Base64 ile kodlanmış Modulus blob (gelen \<Modulus > öğesi).</span><span class="sxs-lookup"><span data-stu-id="af007-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="af007-107">Bkz: [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) yapısı.</span><span class="sxs-lookup"><span data-stu-id="af007-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="af007-108">[in] Base64 ile kodlanmış üs blob (gelen \<üs > öğesi).</span><span class="sxs-lookup"><span data-stu-id="af007-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="af007-109">Bkz: [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) yapısı.</span><span class="sxs-lookup"><span data-stu-id="af007-109">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="af007-110">[out] Bir işaretçi WCHAR \* onaltılık kodlanmış ortak anahtar belirteci almak için.</span><span class="sxs-lookup"><span data-stu-id="af007-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af007-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="af007-111">Return Value</span></span>  
 <span data-ttu-id="af007-112">`S_OK` işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="af007-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="af007-113">Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="af007-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af007-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="af007-114">See Also</span></span>  
 [<span data-ttu-id="af007-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="af007-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
