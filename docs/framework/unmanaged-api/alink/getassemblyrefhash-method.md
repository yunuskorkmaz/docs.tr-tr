---
title: GetAssemblyRefHash Metodu
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 99ae38025f223d669a428738783676ebc0687554
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="04bb5-102">GetAssemblyRefHash Metodu</span><span class="sxs-lookup"><span data-stu-id="04bb5-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="04bb5-103">Karma blob için belirli bir derleme alır.</span><span class="sxs-lookup"><span data-stu-id="04bb5-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04bb5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04bb5-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04bb5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="04bb5-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="04bb5-106">Karma başvuruda bulunacak derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="04bb5-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="04bb5-107">Sonuçta elde edilen karma blob alır.</span><span class="sxs-lookup"><span data-stu-id="04bb5-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="04bb5-108">Karma blob bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="04bb5-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04bb5-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="04bb5-109">Return Value</span></span>  
 <span data-ttu-id="04bb5-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="04bb5-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04bb5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04bb5-111">Requirements</span></span>  
 <span data-ttu-id="04bb5-112">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="04bb5-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04bb5-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="04bb5-113">See Also</span></span>  
 [<span data-ttu-id="04bb5-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04bb5-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="04bb5-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04bb5-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="04bb5-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="04bb5-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
