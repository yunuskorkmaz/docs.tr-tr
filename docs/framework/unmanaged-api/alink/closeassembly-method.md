---
title: "CloseAssembly Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.CloseAssembly
- CloseAssembly
api_location: alink.dll
api_type: COM
f1_keywords: CloseAssembly
helpviewer_keywords: CloseAssembly method
ms.assetid: f66a43bc-a5c5-4190-acbe-63fd27640634
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: be68348b619f342eca4841a6052088bf7152f453
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="closeassembly-method"></a><span data-ttu-id="10e0e-102">CloseAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10e0e-102">CloseAssembly Method</span></span>
<span data-ttu-id="10e0e-103">Derleme işlemleri sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="10e0e-103">Finalizes assembly operations.</span></span> <span data-ttu-id="10e0e-104">Yeni bir derleme veya ilişkisiz modülü başlamadan önce bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="10e0e-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10e0e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10e0e-105">Syntax</span></span>  
  
```  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10e0e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="10e0e-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="10e0e-107">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="10e0e-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10e0e-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="10e0e-108">Return Value</span></span>  
 <span data-ttu-id="10e0e-109">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="10e0e-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10e0e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="10e0e-110">Requirements</span></span>  
 <span data-ttu-id="10e0e-111">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="10e0e-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10e0e-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="10e0e-112">See Also</span></span>  
 [<span data-ttu-id="10e0e-113">Ialink arabirimi</span><span class="sxs-lookup"><span data-stu-id="10e0e-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="10e0e-114">Ialink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="10e0e-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="10e0e-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="10e0e-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
