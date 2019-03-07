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
ms.openlocfilehash: b2597cf14f4f1fc9a99740b4a07502246f80087d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466602"
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="45f75-102">GetAssemblyRefHash Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45f75-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="45f75-103">Belirli bir derleme için bir karma blob alır.</span><span class="sxs-lookup"><span data-stu-id="45f75-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45f75-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45f75-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="45f75-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="45f75-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="45f75-106">Karma başvuruda bulunacak derlemesinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="45f75-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="45f75-107">Sonuçta elde edilen karma blob alır.</span><span class="sxs-lookup"><span data-stu-id="45f75-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="45f75-108">Karma blob bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="45f75-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45f75-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="45f75-109">Return Value</span></span>  
 <span data-ttu-id="45f75-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="45f75-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45f75-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="45f75-111">Requirements</span></span>  
 <span data-ttu-id="45f75-112">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="45f75-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45f75-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45f75-113">See also</span></span>
- [<span data-ttu-id="45f75-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="45f75-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="45f75-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="45f75-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="45f75-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="45f75-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
