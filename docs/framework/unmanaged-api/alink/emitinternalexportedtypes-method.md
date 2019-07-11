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
ms.openlocfilehash: 15174480c4345f2514572701a5525f0f192ad120
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742095"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="fb383-102">EmitInternalExportedTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fb383-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="fb383-103">Derlemeye eklenen tür yayar.</span><span class="sxs-lookup"><span data-stu-id="fb383-103">Emits types added to the assembly.</span></span> <span data-ttu-id="fb383-104">Dahili türler eklenmiş olan bilinen sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="fb383-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb383-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb383-105">Syntax</span></span>  
  
```cpp  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb383-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fb383-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="fb383-107">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="fb383-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb383-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fb383-108">Return Value</span></span>  
 <span data-ttu-id="fb383-109">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="fb383-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb383-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb383-110">Requirements</span></span>  
 <span data-ttu-id="fb383-111">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="fb383-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb383-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb383-112">See also</span></span>

- [<span data-ttu-id="fb383-113">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb383-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="fb383-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb383-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="fb383-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="fb383-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
