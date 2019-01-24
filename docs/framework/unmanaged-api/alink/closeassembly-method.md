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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aa415926f4a818f697812f1a3c5531cb0ab7081b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510175"
---
# <a name="closeassembly-method"></a><span data-ttu-id="e0149-102">CloseAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0149-102">CloseAssembly Method</span></span>
<span data-ttu-id="e0149-103">Derleme işlemleri sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="e0149-103">Finalizes assembly operations.</span></span> <span data-ttu-id="e0149-104">Yeni bir derleme veya ilişkisiz modülü başlamadan önce bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="e0149-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0149-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0149-105">Syntax</span></span>  
  
```  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e0149-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e0149-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e0149-107">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="e0149-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0149-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e0149-108">Return Value</span></span>  
 <span data-ttu-id="e0149-109">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="e0149-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0149-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e0149-110">Requirements</span></span>  
 <span data-ttu-id="e0149-111">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e0149-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0149-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0149-112">See also</span></span>
- [<span data-ttu-id="e0149-113">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e0149-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="e0149-114">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e0149-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="e0149-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="e0149-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
