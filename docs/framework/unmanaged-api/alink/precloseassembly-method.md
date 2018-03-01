---
title: "PreCloseAssembly Yöntemi"
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
- IALink.PreCloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- PreCloseAssembly
helpviewer_keywords:
- PreCloseAssembly method
ms.assetid: 6d23ac54-15ea-4027-a172-9ebef43e8f56
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a4d1f2eed036552ab17b6768b7b2d84f4a52c9c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="precloseassembly-method"></a><span data-ttu-id="48d3c-102">PreCloseAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="48d3c-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="48d3c-103">Derleme dosyası kapatır.</span><span class="sxs-lookup"><span data-stu-id="48d3c-103">Closes the assembly file.</span></span> <span data-ttu-id="48d3c-104">Diğer tüm dosyalar kapattıktan sonra ancak derleme dosyası kapatmadan önce bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="48d3c-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="48d3c-105">İlişkisiz modülleri için bu yöntemi çağırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="48d3c-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48d3c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48d3c-106">Syntax</span></span>  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48d3c-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="48d3c-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="48d3c-108">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="48d3c-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48d3c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="48d3c-109">Return Value</span></span>  
 <span data-ttu-id="48d3c-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="48d3c-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48d3c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="48d3c-111">Requirements</span></span>  
 <span data-ttu-id="48d3c-112">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="48d3c-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48d3c-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="48d3c-113">See Also</span></span>  
 [<span data-ttu-id="48d3c-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="48d3c-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="48d3c-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="48d3c-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="48d3c-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="48d3c-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
