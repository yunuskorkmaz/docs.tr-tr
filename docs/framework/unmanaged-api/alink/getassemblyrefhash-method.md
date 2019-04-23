---
title: GetAssemblyRefHash Yöntemi
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
ms.openlocfilehash: 6fa8d42f9e849db6a02f6c62b37e04cf5dee016e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119658"
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="9a7c5-102">GetAssemblyRefHash Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9a7c5-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="9a7c5-103">Belirli bir derleme için bir karma blob alır.</span><span class="sxs-lookup"><span data-stu-id="9a7c5-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a7c5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a7c5-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a7c5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9a7c5-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="9a7c5-106">Karma başvuruda bulunacak derlemesinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="9a7c5-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="9a7c5-107">Sonuçta elde edilen karma blob alır.</span><span class="sxs-lookup"><span data-stu-id="9a7c5-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="9a7c5-108">Karma blob bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="9a7c5-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a7c5-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9a7c5-109">Return Value</span></span>  
 <span data-ttu-id="9a7c5-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a7c5-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a7c5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a7c5-111">Requirements</span></span>  
 <span data-ttu-id="9a7c5-112">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="9a7c5-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a7c5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a7c5-113">See also</span></span>

- [<span data-ttu-id="9a7c5-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a7c5-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="9a7c5-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a7c5-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="9a7c5-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="9a7c5-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
