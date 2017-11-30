---
title: "EmitAssembly Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink2.EmitAssembly
- EmitAssembly
api_location: alink.dll
api_type: COM
f1_keywords: EmitAssembly
helpviewer_keywords: EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3471c4ad2d06443e0f05dc344be5f791817f2d2f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="emitassembly-method"></a><span data-ttu-id="54fc0-102">EmitAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="54fc0-102">EmitAssembly Method</span></span>
<span data-ttu-id="54fc0-103">Bütünleştirilmiş kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="54fc0-103">Creates the assembly.</span></span> <span data-ttu-id="54fc0-104">Diğer tüm dosyalar dışında derleme dosyası kapatıldıktan sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="54fc0-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="54fc0-105">Bu yöntem, ilişkisiz modülleri üretirken çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="54fc0-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54fc0-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54fc0-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="54fc0-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="54fc0-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="54fc0-108">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="54fc0-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54fc0-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="54fc0-109">Return Value</span></span>  
 <span data-ttu-id="54fc0-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="54fc0-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54fc0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54fc0-111">Requirements</span></span>  
 <span data-ttu-id="54fc0-112">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="54fc0-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54fc0-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="54fc0-113">See Also</span></span>  
 [<span data-ttu-id="54fc0-114">Ialink arabirimi</span><span class="sxs-lookup"><span data-stu-id="54fc0-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="54fc0-115">Ialink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="54fc0-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="54fc0-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="54fc0-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
