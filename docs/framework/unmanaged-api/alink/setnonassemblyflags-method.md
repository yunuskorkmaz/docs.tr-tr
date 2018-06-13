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
ms.openlocfilehash: 0399a135eddfd87342db63e107c8eea59a6e54d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401709"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="64000-102">SetNonAssemblyFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="64000-102">SetNonAssemblyFlags Method</span></span>
<span data-ttu-id="64000-103">Derleme özgü olmayan bayrakları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="64000-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64000-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64000-104">Syntax</span></span>  
  
```  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64000-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="64000-105">Parameters</span></span>  
 `afFlags`  
 <span data-ttu-id="64000-106">ALink bayraklar.</span><span class="sxs-lookup"><span data-stu-id="64000-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64000-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="64000-107">Return Value</span></span>  
 <span data-ttu-id="64000-108">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="64000-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64000-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64000-109">Requirements</span></span>  
 <span data-ttu-id="64000-110">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="64000-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64000-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="64000-111">See Also</span></span>  
 [<span data-ttu-id="64000-112">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64000-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="64000-113">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64000-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="64000-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="64000-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
