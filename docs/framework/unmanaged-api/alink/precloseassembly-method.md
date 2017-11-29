---
title: "PreCloseAssembly Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.PreCloseAssembly
api_location: alink.dll
api_type: COM
f1_keywords: PreCloseAssembly
helpviewer_keywords: PreCloseAssembly method
ms.assetid: 6d23ac54-15ea-4027-a172-9ebef43e8f56
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8d940cbdeddc7030c679fae8c8694bb3542123b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="precloseassembly-method"></a><span data-ttu-id="20782-102">PreCloseAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="20782-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="20782-103">Derleme dosyası kapatır.</span><span class="sxs-lookup"><span data-stu-id="20782-103">Closes the assembly file.</span></span> <span data-ttu-id="20782-104">Diğer tüm dosyalar kapattıktan sonra ancak derleme dosyası kapatmadan önce bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="20782-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="20782-105">İlişkisiz modülleri için bu yöntemi çağırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="20782-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20782-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20782-106">Syntax</span></span>  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20782-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="20782-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="20782-108">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="20782-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20782-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="20782-109">Return Value</span></span>  
 <span data-ttu-id="20782-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="20782-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20782-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="20782-111">Requirements</span></span>  
 <span data-ttu-id="20782-112">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="20782-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20782-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="20782-113">See Also</span></span>  
 [<span data-ttu-id="20782-114">Ialink arabirimi</span><span class="sxs-lookup"><span data-stu-id="20782-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="20782-115">Ialink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="20782-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="20782-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="20782-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
