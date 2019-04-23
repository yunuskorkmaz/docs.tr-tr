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
ms.openlocfilehash: 0d1b28eadc9f09abff799f99d1d6012c98b1d3dd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215774"
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="84897-102">GetPublicKeyToken Metodu</span><span class="sxs-lookup"><span data-stu-id="84897-102">GetPublicKeyToken Method</span></span>
<span data-ttu-id="84897-103">Belirtilen keyfile veya anahtar kapsayıcısı için ortak anahtar belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="84897-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84897-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84897-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="84897-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="84897-105">Parameters</span></span>  
 `pszKeyFile`  
 <span data-ttu-id="84897-106">Anahtarın adı.</span><span class="sxs-lookup"><span data-stu-id="84897-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="84897-107">Anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="84897-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="84897-108">Depolanacak anahtar belirteci olduğu adresi.</span><span class="sxs-lookup"><span data-stu-id="84897-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="84897-109">Tarafından belirtilen arabellek, bayt cinsinden boyutunu belirtir `pvPublicKeyToken`.</span><span class="sxs-lookup"><span data-stu-id="84897-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="84897-110">İade, gerçek kullanılan bayt sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="84897-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84897-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="84897-111">Return Value</span></span>  
 <span data-ttu-id="84897-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="84897-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84897-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="84897-113">Requirements</span></span>  
 <span data-ttu-id="84897-114">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="84897-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84897-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84897-115">See also</span></span>

- [<span data-ttu-id="84897-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="84897-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="84897-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="84897-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="84897-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="84897-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
