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
ms.openlocfilehash: b7bcf530947c161decc9c01c07df310550d69738
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733769"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="85826-102">SetNonAssemblyFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85826-102">SetNonAssemblyFlags Method</span></span>

<span data-ttu-id="85826-103">Derlemeye özgü olmayan bayrakları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="85826-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85826-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="85826-104">Syntax</span></span>  
  
```cpp  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="85826-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="85826-105">Parameters</span></span>  

 `afFlags`  
 <span data-ttu-id="85826-106">ALink bayrakları.</span><span class="sxs-lookup"><span data-stu-id="85826-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85826-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="85826-107">Return Value</span></span>  

 <span data-ttu-id="85826-108">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="85826-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85826-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="85826-109">Requirements</span></span>  

 <span data-ttu-id="85826-110">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="85826-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85826-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85826-111">See also</span></span>

- [<span data-ttu-id="85826-112">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85826-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="85826-113">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85826-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="85826-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="85826-114">ALink API</span></span>](index.md)
