---
title: _AxlPublicKeyBlobToPublicKeyToken İşlevi
ms.date: 03/30/2017
api_name:
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
ms.openlocfilehash: 33b8f47813a3bf43bd69741c9febb150fa3a92e3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099900"
---
# <a name="_axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="814f8-102">\_AxlPublicKeyBlobToPublicKeyToken Işlevi</span><span class="sxs-lookup"><span data-stu-id="814f8-102">\_AxlPublicKeyBlobToPublicKeyToken Function</span></span>
<span data-ttu-id="814f8-103">Bir CSP PUBLICKEYBLOB biçiminden tanımlayıcı ad ortak anahtar belirtecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="814f8-103">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="814f8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="814f8-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="814f8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="814f8-105">Parameters</span></span>  
 `pCspPublicKeyBlob`  
 <span data-ttu-id="814f8-106">'ndaki CSP ortak anahtar blobu.</span><span class="sxs-lookup"><span data-stu-id="814f8-106">[in] The CSP public key blob.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="814f8-107">dışı Onaltılık kodlanmış ortak anahtar karmasını almak için bir WCHAR \* işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="814f8-107">[out] A pointer to WCHAR \* to receive the hex-encoded public key hash.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="814f8-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="814f8-108">Return Value</span></span>  
 <span data-ttu-id="814f8-109">işlev başarılı olursa `S_OK`; Aksi takdirde `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="814f8-109">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="814f8-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="814f8-110">See also</span></span>

- [<span data-ttu-id="814f8-111">Authenticode</span><span class="sxs-lookup"><span data-stu-id="814f8-111">Authenticode</span></span>](index.md)
