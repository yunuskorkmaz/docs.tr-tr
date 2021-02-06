---
description: 'Daha fazla bilgi edinin: EmitInternalExportedTypes yöntemi'
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
ms.openlocfilehash: 5d23c593988b31c077d3b65b11b73113e164ed74
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638307"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="21c19-103">EmitInternalExportedTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21c19-103">EmitInternalExportedTypes Method</span></span>

<span data-ttu-id="21c19-104">Derlemeye eklenen türleri yayar.</span><span class="sxs-lookup"><span data-stu-id="21c19-104">Emits types added to the assembly.</span></span> <span data-ttu-id="21c19-105">Bilinen iç türler eklendikten sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="21c19-105">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21c19-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21c19-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="21c19-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21c19-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="21c19-108">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="21c19-108">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21c19-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="21c19-109">Return Value</span></span>  

 <span data-ttu-id="21c19-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="21c19-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21c19-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21c19-111">Requirements</span></span>  

 <span data-ttu-id="21c19-112">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="21c19-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21c19-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21c19-113">See also</span></span>

- [<span data-ttu-id="21c19-114">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21c19-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="21c19-115">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21c19-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="21c19-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="21c19-116">ALink API</span></span>](index.md)
