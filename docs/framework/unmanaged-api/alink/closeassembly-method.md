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
ms.openlocfilehash: 68698aab0fd0872c6e6f67e4ec531ab0226e784f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401959"
---
# <a name="closeassembly-method"></a><span data-ttu-id="7e03e-102">CloseAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7e03e-102">CloseAssembly Method</span></span>
<span data-ttu-id="7e03e-103">Derleme işlemleri sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="7e03e-103">Finalizes assembly operations.</span></span> <span data-ttu-id="7e03e-104">Yeni bir derleme veya ilişkisiz modülü başlamadan önce bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="7e03e-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e03e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7e03e-105">Syntax</span></span>  
  
```  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e03e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7e03e-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="7e03e-107">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="7e03e-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e03e-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7e03e-108">Return Value</span></span>  
 <span data-ttu-id="7e03e-109">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="7e03e-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e03e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e03e-110">Requirements</span></span>  
 <span data-ttu-id="7e03e-111">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7e03e-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e03e-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7e03e-112">See Also</span></span>  
 [<span data-ttu-id="7e03e-113">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7e03e-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="7e03e-114">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7e03e-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="7e03e-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="7e03e-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
