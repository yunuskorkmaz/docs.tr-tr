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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790097"
---
# <a name="closeassembly-method"></a><span data-ttu-id="f17ea-102">CloseAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f17ea-102">CloseAssembly Method</span></span>
<span data-ttu-id="f17ea-103">Derleme işlemleri sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="f17ea-103">Finalizes assembly operations.</span></span> <span data-ttu-id="f17ea-104">Yeni bir derleme veya ilişkisiz modülü başlamadan önce bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="f17ea-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f17ea-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f17ea-105">Syntax</span></span>  
  
```  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="f17ea-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f17ea-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f17ea-107">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="f17ea-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f17ea-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f17ea-108">Return Value</span></span>  
 <span data-ttu-id="f17ea-109">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="f17ea-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f17ea-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f17ea-110">Requirements</span></span>  
 <span data-ttu-id="f17ea-111">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f17ea-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f17ea-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f17ea-112">See also</span></span>

- [<span data-ttu-id="f17ea-113">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f17ea-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="f17ea-114">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f17ea-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="f17ea-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="f17ea-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
