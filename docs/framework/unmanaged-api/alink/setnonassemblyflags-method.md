---
title: SetNonAssemblyFlags Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.SetNonAssemblyFlags
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetNonAssemblyFlags
helpviewer_keywords:
- SetNonAssemblyFlags method
ms.assetid: f8ba6fc8-f5aa-4066-ac96-56332758f5ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c7716db814e86258c4cb81047b39142f33798782
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143201"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="24875-102">SetNonAssemblyFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="24875-102">SetNonAssemblyFlags Method</span></span>
<span data-ttu-id="24875-103">Derleme özgü olmayan bayrağı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="24875-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24875-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24875-104">Syntax</span></span>  
  
```  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="24875-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="24875-105">Parameters</span></span>  
 `afFlags`  
 <span data-ttu-id="24875-106">ALINK bayraklar.</span><span class="sxs-lookup"><span data-stu-id="24875-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24875-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="24875-107">Return Value</span></span>  
 <span data-ttu-id="24875-108">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="24875-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24875-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="24875-109">Requirements</span></span>  
 <span data-ttu-id="24875-110">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="24875-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24875-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24875-111">See also</span></span>

- [<span data-ttu-id="24875-112">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="24875-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="24875-113">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="24875-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="24875-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="24875-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
