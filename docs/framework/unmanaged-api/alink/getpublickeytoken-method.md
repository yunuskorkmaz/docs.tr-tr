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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 158ecc036d56e2ad9a3fa650677c04ebcbfd7696
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777218"
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="edb97-102">GetPublicKeyToken Metodu</span><span class="sxs-lookup"><span data-stu-id="edb97-102">GetPublicKeyToken Method</span></span>
<span data-ttu-id="edb97-103">Belirli bir keyfile veya anahtar kapsayıcısı için ortak anahtar belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="edb97-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edb97-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="edb97-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="edb97-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="edb97-105">Parameters</span></span>  
 `pszKeyFile`  
 <span data-ttu-id="edb97-106">Anahtarın dosya adı.</span><span class="sxs-lookup"><span data-stu-id="edb97-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="edb97-107">Anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="edb97-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="edb97-108">Anahtar belirtecinin depolanacağı adres.</span><span class="sxs-lookup"><span data-stu-id="edb97-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="edb97-109">Tarafından `pvPublicKeyToken`gösterilen arabelleğin boyutunu bayt cinsinden belirtir.</span><span class="sxs-lookup"><span data-stu-id="edb97-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="edb97-110">Dönüş sonrasında, kullanılan gerçek bayt sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="edb97-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="edb97-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="edb97-111">Return Value</span></span>  
 <span data-ttu-id="edb97-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="edb97-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edb97-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="edb97-113">Requirements</span></span>  
 <span data-ttu-id="edb97-114">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="edb97-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edb97-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edb97-115">See also</span></span>

- [<span data-ttu-id="edb97-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="edb97-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="edb97-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="edb97-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="edb97-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="edb97-118">ALink API</span></span>](index.md)
