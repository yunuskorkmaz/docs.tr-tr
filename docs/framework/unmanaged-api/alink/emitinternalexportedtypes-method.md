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
ms.openlocfilehash: c196bcc159b18b9dc04329d817ebe16e07bb8bb7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218257"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="ee825-102">EmitInternalExportedTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ee825-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="ee825-103">Derlemeye eklenen tür yayar.</span><span class="sxs-lookup"><span data-stu-id="ee825-103">Emits types added to the assembly.</span></span> <span data-ttu-id="ee825-104">Dahili türler eklenmiş olan bilinen sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="ee825-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee825-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee825-105">Syntax</span></span>  
  
```  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee825-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ee825-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ee825-107">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="ee825-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ee825-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ee825-108">Return Value</span></span>  
 <span data-ttu-id="ee825-109">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="ee825-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee825-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ee825-110">Requirements</span></span>  
 <span data-ttu-id="ee825-111">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="ee825-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee825-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee825-112">See also</span></span>

- [<span data-ttu-id="ee825-113">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee825-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="ee825-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee825-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="ee825-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="ee825-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
