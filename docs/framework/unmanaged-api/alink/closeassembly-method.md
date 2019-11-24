---
title: CloseAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.CloseAssembly
- CloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseAssembly
helpviewer_keywords:
- CloseAssembly method
ms.assetid: f66a43bc-a5c5-4190-acbe-63fd27640634
topic_type:
- apiref
ms.openlocfilehash: 70dca19075d8c896408ec78f89549b0c539280de
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446572"
---
# <a name="closeassembly-method"></a><span data-ttu-id="16bce-102">CloseAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="16bce-102">CloseAssembly Method</span></span>
<span data-ttu-id="16bce-103">Finalizes assembly operations.</span><span class="sxs-lookup"><span data-stu-id="16bce-103">Finalizes assembly operations.</span></span> <span data-ttu-id="16bce-104">Call this method before beginning a new assembly or unbound module.</span><span class="sxs-lookup"><span data-stu-id="16bce-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16bce-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16bce-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="16bce-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="16bce-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="16bce-107">ID of the assembly.</span><span class="sxs-lookup"><span data-stu-id="16bce-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16bce-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="16bce-108">Return Value</span></span>  
 <span data-ttu-id="16bce-109">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="16bce-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16bce-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16bce-110">Requirements</span></span>  
 <span data-ttu-id="16bce-111">Requires alink.h.</span><span class="sxs-lookup"><span data-stu-id="16bce-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16bce-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16bce-112">See also</span></span>

- [<span data-ttu-id="16bce-113">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="16bce-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="16bce-114">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="16bce-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="16bce-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="16bce-115">ALink API</span></span>](index.md)
