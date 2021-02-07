---
description: 'Daha fazla bilgi edinin: GetPublicKeyToken yöntemi'
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
ms.openlocfilehash: b864c1dc61c7498ccca6aa04ef29b57a30e1a9ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718427"
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="b8b98-103">GetPublicKeyToken Metodu</span><span class="sxs-lookup"><span data-stu-id="b8b98-103">GetPublicKeyToken Method</span></span>

<span data-ttu-id="b8b98-104">Belirli bir keyfile veya anahtar kapsayıcısı için ortak anahtar belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="b8b98-104">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8b98-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8b98-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8b98-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b8b98-106">Parameters</span></span>  

 `pszKeyFile`  
 <span data-ttu-id="b8b98-107">Anahtarın dosya adı.</span><span class="sxs-lookup"><span data-stu-id="b8b98-107">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="b8b98-108">Anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="b8b98-108">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="b8b98-109">Anahtar belirtecinin depolanacağı adres.</span><span class="sxs-lookup"><span data-stu-id="b8b98-109">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="b8b98-110">Tarafından gösterilen arabelleğin boyutunu bayt cinsinden belirtir `pvPublicKeyToken` .</span><span class="sxs-lookup"><span data-stu-id="b8b98-110">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="b8b98-111">Dönüş sonrasında, kullanılan gerçek bayt sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="b8b98-111">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b8b98-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b8b98-112">Return Value</span></span>  

 <span data-ttu-id="b8b98-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="b8b98-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8b98-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b8b98-114">Requirements</span></span>  

 <span data-ttu-id="b8b98-115">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b8b98-115">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8b98-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8b98-116">See also</span></span>

- [<span data-ttu-id="b8b98-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b8b98-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="b8b98-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b8b98-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="b8b98-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="b8b98-119">ALink API</span></span>](index.md)
