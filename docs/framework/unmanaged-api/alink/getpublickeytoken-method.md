---
title: GetPublicKeyToken Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 230c98e85bd0aa3bd2f368965b6f7ac028e43df4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="873c1-102">GetPublicKeyToken Metodu</span><span class="sxs-lookup"><span data-stu-id="873c1-102">GetPublicKeyToken Method</span></span>
<span data-ttu-id="873c1-103">Belirtilen keyfile veya anahtar kapsayıcısı için ortak anahtar belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="873c1-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="873c1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="873c1-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="873c1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="873c1-105">Parameters</span></span>  
 `pszKeyFile`  
 <span data-ttu-id="873c1-106">Anahtar adı.</span><span class="sxs-lookup"><span data-stu-id="873c1-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="873c1-107">Anahtar kapsayıcı adı.</span><span class="sxs-lookup"><span data-stu-id="873c1-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="873c1-108">Burada depolanması için anahtar belirteci, adres.</span><span class="sxs-lookup"><span data-stu-id="873c1-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="873c1-109">Tarafından gösterilen arabelleğin bayt cinsinden boyutu belirtir `pvPublicKeyToken`.</span><span class="sxs-lookup"><span data-stu-id="873c1-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="873c1-110">Return sırasında kullanılan bayt gerçek sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="873c1-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="873c1-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="873c1-111">Return Value</span></span>  
 <span data-ttu-id="873c1-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="873c1-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="873c1-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="873c1-113">Requirements</span></span>  
 <span data-ttu-id="873c1-114">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="873c1-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="873c1-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="873c1-115">See Also</span></span>  
 [<span data-ttu-id="873c1-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="873c1-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="873c1-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="873c1-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="873c1-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="873c1-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
