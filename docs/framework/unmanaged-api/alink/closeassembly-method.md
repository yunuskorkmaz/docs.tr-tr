---
description: 'Daha fazla bilgi edinin: CloseAssembly yöntemi'
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
ms.openlocfilehash: 927a66f948f691c00a695c626d9c31950a722cb5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638398"
---
# <a name="closeassembly-method"></a><span data-ttu-id="991eb-103">CloseAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="991eb-103">CloseAssembly Method</span></span>

<span data-ttu-id="991eb-104">Derleme işlemlerini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="991eb-104">Finalizes assembly operations.</span></span> <span data-ttu-id="991eb-105">Yeni bir derlemeye veya ilişkisiz modüle başlamadan önce bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="991eb-105">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="991eb-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="991eb-106">Syntax</span></span>  
  
```cpp  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="991eb-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="991eb-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="991eb-108">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="991eb-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="991eb-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="991eb-109">Return Value</span></span>  

 <span data-ttu-id="991eb-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="991eb-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="991eb-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="991eb-111">Requirements</span></span>  

 <span data-ttu-id="991eb-112">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="991eb-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="991eb-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="991eb-113">See also</span></span>

- [<span data-ttu-id="991eb-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="991eb-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="991eb-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="991eb-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="991eb-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="991eb-116">ALink API</span></span>](index.md)
