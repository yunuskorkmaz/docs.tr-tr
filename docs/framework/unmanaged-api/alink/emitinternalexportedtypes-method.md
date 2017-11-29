---
title: "EmitInternalExportedTypes Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EmitInternalExportedTypes
- IALink2.EmitInternalExportedTypes
api_location: alink.dll
api_type: COM
f1_keywords: EmitInternalExportedTypes
helpviewer_keywords: EmitInternalExportedTypes method
ms.assetid: 28c8b00d-2c14-40b4-aed5-a1db0e2428eb
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f354058e0de944bbce9d128d3f4baa9b941fda08
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="e9683-102">EmitInternalExportedTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9683-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="e9683-103">Derlemeye eklenen türleri yayar.</span><span class="sxs-lookup"><span data-stu-id="e9683-103">Emits types added to the assembly.</span></span> <span data-ttu-id="e9683-104">İç türleri eklenmiştir bilinen sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="e9683-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9683-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9683-105">Syntax</span></span>  
  
```  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9683-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e9683-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e9683-107">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="e9683-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9683-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e9683-108">Return Value</span></span>  
 <span data-ttu-id="e9683-109">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="e9683-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9683-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9683-110">Requirements</span></span>  
 <span data-ttu-id="e9683-111">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="e9683-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9683-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e9683-112">See Also</span></span>  
 [<span data-ttu-id="e9683-113">Ialink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9683-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="e9683-114">Ialink arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9683-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="e9683-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="e9683-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
