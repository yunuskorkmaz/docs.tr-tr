---
title: "SetNonAssemblyFlags Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.SetNonAssemblyFlags
api_location: alink.dll
api_type: COM
f1_keywords: SetNonAssemblyFlags
helpviewer_keywords: SetNonAssemblyFlags method
ms.assetid: f8ba6fc8-f5aa-4066-ac96-56332758f5ec
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c5f8761259e89b4befd0eeaf893ffbe5d4142350
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="24222-102">SetNonAssemblyFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="24222-102">SetNonAssemblyFlags Method</span></span>
<span data-ttu-id="24222-103">Derleme özgü olmayan bayrakları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="24222-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24222-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24222-104">Syntax</span></span>  
  
```  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24222-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="24222-105">Parameters</span></span>  
 `afFlags`  
 <span data-ttu-id="24222-106">ALink bayraklar.</span><span class="sxs-lookup"><span data-stu-id="24222-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24222-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="24222-107">Return Value</span></span>  
 <span data-ttu-id="24222-108">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="24222-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24222-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="24222-109">Requirements</span></span>  
 <span data-ttu-id="24222-110">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="24222-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24222-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24222-111">See Also</span></span>  
 [<span data-ttu-id="24222-112">Ialink arabirimi</span><span class="sxs-lookup"><span data-stu-id="24222-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="24222-113">Ialink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="24222-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="24222-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="24222-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
