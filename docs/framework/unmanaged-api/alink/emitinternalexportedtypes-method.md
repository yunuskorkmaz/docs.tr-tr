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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790019"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="6cbb1-102">EmitInternalExportedTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6cbb1-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="6cbb1-103">Derlemeye eklenen tür yayar.</span><span class="sxs-lookup"><span data-stu-id="6cbb1-103">Emits types added to the assembly.</span></span> <span data-ttu-id="6cbb1-104">Dahili türler eklenmiş olan bilinen sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="6cbb1-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cbb1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6cbb1-105">Syntax</span></span>  
  
```  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="6cbb1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6cbb1-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="6cbb1-107">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="6cbb1-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6cbb1-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6cbb1-108">Return Value</span></span>  
 <span data-ttu-id="6cbb1-109">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="6cbb1-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cbb1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6cbb1-110">Requirements</span></span>  
 <span data-ttu-id="6cbb1-111">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="6cbb1-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cbb1-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6cbb1-112">See also</span></span>

- [<span data-ttu-id="6cbb1-113">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6cbb1-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="6cbb1-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6cbb1-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="6cbb1-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="6cbb1-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
