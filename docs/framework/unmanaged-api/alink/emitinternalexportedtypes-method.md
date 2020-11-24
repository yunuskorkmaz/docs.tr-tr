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
ms.openlocfilehash: faf1438f56cd49b235ffbb18a0154e3e20c202b9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684973"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="8f118-102">EmitInternalExportedTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8f118-102">EmitInternalExportedTypes Method</span></span>

<span data-ttu-id="8f118-103">Derlemeye eklenen türleri yayar.</span><span class="sxs-lookup"><span data-stu-id="8f118-103">Emits types added to the assembly.</span></span> <span data-ttu-id="8f118-104">Bilinen iç türler eklendikten sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="8f118-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f118-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8f118-105">Syntax</span></span>  
  
```cpp  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f118-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f118-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="8f118-107">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="8f118-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f118-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8f118-108">Return Value</span></span>  

 <span data-ttu-id="8f118-109">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="8f118-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f118-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f118-110">Requirements</span></span>  

 <span data-ttu-id="8f118-111">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="8f118-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f118-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f118-112">See also</span></span>

- [<span data-ttu-id="8f118-113">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f118-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="8f118-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f118-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="8f118-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="8f118-115">ALink API</span></span>](index.md)
