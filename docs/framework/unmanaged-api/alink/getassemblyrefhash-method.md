---
title: GetAssemblyRefHash Metodu
ms.date: 03/30/2017
api_name:
- IALink.GetAssemblyRefHash
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetAssemblyRefHash
helpviewer_keywords:
- GetAssemblyRefHash method
ms.assetid: 091a18bd-e901-46f6-b999-74d71c8a7c41
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ccf60d067af356dda1870a2fb1dcca21966f16a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401492"
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="ffef0-102">GetAssemblyRefHash Metodu</span><span class="sxs-lookup"><span data-stu-id="ffef0-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="ffef0-103">Karma blob için belirli bir derleme alır.</span><span class="sxs-lookup"><span data-stu-id="ffef0-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffef0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ffef0-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ffef0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ffef0-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="ffef0-106">Karma başvuruda bulunacak derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="ffef0-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="ffef0-107">Sonuçta elde edilen karma blob alır.</span><span class="sxs-lookup"><span data-stu-id="ffef0-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="ffef0-108">Karma blob bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="ffef0-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ffef0-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ffef0-109">Return Value</span></span>  
 <span data-ttu-id="ffef0-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="ffef0-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffef0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ffef0-111">Requirements</span></span>  
 <span data-ttu-id="ffef0-112">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="ffef0-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffef0-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ffef0-113">See Also</span></span>  
 [<span data-ttu-id="ffef0-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ffef0-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="ffef0-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ffef0-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="ffef0-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="ffef0-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
