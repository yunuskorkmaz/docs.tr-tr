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
ms.openlocfilehash: 27ad89f1910bc7bb08a23c9fdb0d50828fb8b5e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741440"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="17891-102">SetNonAssemblyFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="17891-102">SetNonAssemblyFlags Method</span></span>
<span data-ttu-id="17891-103">Derleme özgü olmayan bayrağı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="17891-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17891-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17891-104">Syntax</span></span>  
  
```cpp  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="17891-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="17891-105">Parameters</span></span>  
 `afFlags`  
 <span data-ttu-id="17891-106">ALINK bayraklar.</span><span class="sxs-lookup"><span data-stu-id="17891-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17891-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="17891-107">Return Value</span></span>  
 <span data-ttu-id="17891-108">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="17891-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17891-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="17891-109">Requirements</span></span>  
 <span data-ttu-id="17891-110">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="17891-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17891-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17891-111">See also</span></span>

- [<span data-ttu-id="17891-112">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17891-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="17891-113">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17891-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="17891-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="17891-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
