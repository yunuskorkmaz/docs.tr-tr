---
title: EmitInternalExportedTypes Yöntemi
ms.date: 03/30/2017
api_name:
- EmitInternalExportedTypes
- IALink2.EmitInternalExportedTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitInternalExportedTypes
helpviewer_keywords:
- EmitInternalExportedTypes method
ms.assetid: 28c8b00d-2c14-40b4-aed5-a1db0e2428eb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 55b9d185804f25c7431f2696d67753cc3ba02d1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402047"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="8b021-102">EmitInternalExportedTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b021-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="8b021-103">Derlemeye eklenen türleri yayar.</span><span class="sxs-lookup"><span data-stu-id="8b021-103">Emits types added to the assembly.</span></span> <span data-ttu-id="8b021-104">İç türleri eklenmiştir bilinen sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="8b021-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b021-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8b021-105">Syntax</span></span>  
  
```  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b021-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8b021-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8b021-107">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="8b021-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b021-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8b021-108">Return Value</span></span>  
 <span data-ttu-id="8b021-109">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="8b021-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b021-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b021-110">Requirements</span></span>  
 <span data-ttu-id="8b021-111">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="8b021-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b021-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8b021-112">See Also</span></span>  
 [<span data-ttu-id="8b021-113">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b021-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="8b021-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b021-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="8b021-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="8b021-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
