---
title: "EmitAssembly Yöntemi"
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
- IALink2.EmitAssembly
- EmitAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssembly
helpviewer_keywords:
- EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f012ea89fec0e64bc1639e6c47fb79249c25411a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="emitassembly-method"></a><span data-ttu-id="10588-102">EmitAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10588-102">EmitAssembly Method</span></span>
<span data-ttu-id="10588-103">Bütünleştirilmiş kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="10588-103">Creates the assembly.</span></span> <span data-ttu-id="10588-104">Diğer tüm dosyalar dışında derleme dosyası kapatıldıktan sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="10588-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="10588-105">Bu yöntem, ilişkisiz modülleri üretirken çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="10588-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10588-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10588-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10588-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="10588-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="10588-108">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="10588-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10588-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="10588-109">Return Value</span></span>  
 <span data-ttu-id="10588-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="10588-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10588-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="10588-111">Requirements</span></span>  
 <span data-ttu-id="10588-112">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="10588-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10588-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="10588-113">See Also</span></span>  
 [<span data-ttu-id="10588-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="10588-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="10588-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="10588-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="10588-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="10588-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
