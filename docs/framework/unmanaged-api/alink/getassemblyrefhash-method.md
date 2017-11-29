---
title: GetAssemblyRefHash Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.GetAssemblyRefHash
api_location: alink.dll
api_type: COM
f1_keywords: GetAssemblyRefHash
helpviewer_keywords: GetAssemblyRefHash method
ms.assetid: 091a18bd-e901-46f6-b999-74d71c8a7c41
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0a5987bac2a874b01a24732a7c78a926fad0e011
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="c6d0f-102">GetAssemblyRefHash Metodu</span><span class="sxs-lookup"><span data-stu-id="c6d0f-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="c6d0f-103">Karma blob için belirli bir derleme alır.</span><span class="sxs-lookup"><span data-stu-id="c6d0f-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6d0f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6d0f-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6d0f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c6d0f-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="c6d0f-106">Karma başvuruda bulunacak derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="c6d0f-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="c6d0f-107">Sonuçta elde edilen karma blob alır.</span><span class="sxs-lookup"><span data-stu-id="c6d0f-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="c6d0f-108">Karma blob bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="c6d0f-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6d0f-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c6d0f-109">Return Value</span></span>  
 <span data-ttu-id="c6d0f-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="c6d0f-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6d0f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c6d0f-111">Requirements</span></span>  
 <span data-ttu-id="c6d0f-112">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="c6d0f-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6d0f-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6d0f-113">See Also</span></span>  
 [<span data-ttu-id="c6d0f-114">Ialink arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6d0f-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="c6d0f-115">Ialink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6d0f-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="c6d0f-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="c6d0f-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
