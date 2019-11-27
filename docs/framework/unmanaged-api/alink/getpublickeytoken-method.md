---
title: GetPublicKeyToken Metodu
ms.date: 03/30/2017
api_name:
- IALink2.GetPublicKeyToken
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetPublicKeyToken
helpviewer_keywords:
- GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type:
- apiref
ms.openlocfilehash: 2e7ed4e1529104db30b0b06665f74342d9ca9a01
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447237"
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="3bc2a-102">GetPublicKeyToken Metodu</span><span class="sxs-lookup"><span data-stu-id="3bc2a-102">GetPublicKeyToken Method</span></span>
<span data-ttu-id="3bc2a-103">Belirli bir keyfile veya anahtar kapsayıcısı için ortak anahtar belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="3bc2a-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bc2a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3bc2a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="3bc2a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3bc2a-105">Parameters</span></span>  
 `pszKeyFile`  
 <span data-ttu-id="3bc2a-106">Anahtarın dosya adı.</span><span class="sxs-lookup"><span data-stu-id="3bc2a-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="3bc2a-107">Anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="3bc2a-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="3bc2a-108">Anahtar belirtecinin depolanacağı adres.</span><span class="sxs-lookup"><span data-stu-id="3bc2a-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="3bc2a-109">`pvPublicKeyToken`tarafından gösterilen arabelleğin boyutunu bayt cinsinden belirtir.</span><span class="sxs-lookup"><span data-stu-id="3bc2a-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="3bc2a-110">Dönüş sonrasında, kullanılan gerçek bayt sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="3bc2a-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3bc2a-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3bc2a-111">Return Value</span></span>  
 <span data-ttu-id="3bc2a-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="3bc2a-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bc2a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3bc2a-113">Requirements</span></span>  
 <span data-ttu-id="3bc2a-114">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3bc2a-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bc2a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3bc2a-115">See also</span></span>

- [<span data-ttu-id="3bc2a-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3bc2a-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="3bc2a-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3bc2a-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="3bc2a-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="3bc2a-118">ALink API</span></span>](index.md)
