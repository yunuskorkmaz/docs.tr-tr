---
description: 'Daha fazla bilgi edinin: SetNonAssemblyFlags yöntemi'
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
ms.openlocfilehash: 9cf311ec8f04f97da03be626e20c1c07065eac38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662318"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="14994-103">SetNonAssemblyFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="14994-103">SetNonAssemblyFlags Method</span></span>

<span data-ttu-id="14994-104">Derlemeye özgü olmayan bayrakları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="14994-104">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14994-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14994-105">Syntax</span></span>  
  
```cpp  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="14994-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="14994-106">Parameters</span></span>  

 `afFlags`  
 <span data-ttu-id="14994-107">ALink bayrakları.</span><span class="sxs-lookup"><span data-stu-id="14994-107">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14994-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="14994-108">Return Value</span></span>  

 <span data-ttu-id="14994-109">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="14994-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14994-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14994-110">Requirements</span></span>  

 <span data-ttu-id="14994-111">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="14994-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14994-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14994-112">See also</span></span>

- [<span data-ttu-id="14994-113">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="14994-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="14994-114">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="14994-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="14994-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="14994-115">ALink API</span></span>](index.md)
