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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4d720480e4c8b21b3aa56ce81634a26ac9c75de
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776679"
---
# <a name="_axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="e41e8-102">\_AxlPublicKeyBlobToPublicKeyToken Işlevi</span><span class="sxs-lookup"><span data-stu-id="e41e8-102">\_AxlPublicKeyBlobToPublicKeyToken Function</span></span>
<span data-ttu-id="e41e8-103">Bir CSP PUBLICKEYBLOB biçiminden tanımlayıcı ad ortak anahtar belirtecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="e41e8-103">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e41e8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e41e8-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e41e8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e41e8-105">Parameters</span></span>  
 `pCspPublicKeyBlob`  
 <span data-ttu-id="e41e8-106">'ndaki CSP ortak anahtar blobu.</span><span class="sxs-lookup"><span data-stu-id="e41e8-106">[in] The CSP public key blob.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="e41e8-107">dışı Onaltılık kodlanmış ortak anahtar karmasını almak için bir WCHAR \* işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e41e8-107">[out] A pointer to WCHAR \* to receive the hex-encoded public key hash.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e41e8-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e41e8-108">Return Value</span></span>  
 <span data-ttu-id="e41e8-109">`S_OK`işlev başarılı olursa; Aksi `S_FALSE`takdirde.</span><span class="sxs-lookup"><span data-stu-id="e41e8-109">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e41e8-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e41e8-110">See also</span></span>

- [<span data-ttu-id="e41e8-111">Authenticode</span><span class="sxs-lookup"><span data-stu-id="e41e8-111">Authenticode</span></span>](index.md)
