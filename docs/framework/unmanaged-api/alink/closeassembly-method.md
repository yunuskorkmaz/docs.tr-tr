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
ms.openlocfilehash: 94c1c083d010cd82fd9e9e2f02b23e81d88fedd5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116447"
---
# <a name="closeassembly-method"></a><span data-ttu-id="5aae6-102">CloseAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5aae6-102">CloseAssembly Method</span></span>
<span data-ttu-id="5aae6-103">Derleme işlemleri sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="5aae6-103">Finalizes assembly operations.</span></span> <span data-ttu-id="5aae6-104">Yeni bir derleme veya ilişkisiz modülü başlamadan önce bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="5aae6-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5aae6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5aae6-105">Syntax</span></span>  
  
```  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="5aae6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5aae6-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="5aae6-107">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="5aae6-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5aae6-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5aae6-108">Return Value</span></span>  
 <span data-ttu-id="5aae6-109">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="5aae6-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5aae6-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5aae6-110">Requirements</span></span>  
 <span data-ttu-id="5aae6-111">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5aae6-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aae6-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5aae6-112">See also</span></span>

- [<span data-ttu-id="5aae6-113">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5aae6-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="5aae6-114">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5aae6-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="5aae6-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="5aae6-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
