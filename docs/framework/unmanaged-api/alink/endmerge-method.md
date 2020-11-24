---
title: EndMerge Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.EndMerge
- EndMerge
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EndMerge
helpviewer_keywords:
- EndMerge method
ms.assetid: 1d03bb15-a2c8-4a04-8fc6-b126c89c3778
topic_type:
- apiref
ms.openlocfilehash: ed4ac7b12caa0dd78b79554258de62b8752553e0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684934"
---
# <a name="endmerge-method"></a><span data-ttu-id="827b5-102">EndMerge Yöntemi</span><span class="sxs-lookup"><span data-stu-id="827b5-102">EndMerge Method</span></span>

<span data-ttu-id="827b5-103">Tüm özel özniteliklerin yayma kapsamıyla birleştirildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="827b5-103">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="827b5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="827b5-104">Syntax</span></span>  
  
```cpp  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="827b5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="827b5-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="827b5-106">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="827b5-106">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="827b5-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="827b5-107">Return Value</span></span>  

 <span data-ttu-id="827b5-108">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="827b5-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="827b5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="827b5-109">Requirements</span></span>  

 <span data-ttu-id="827b5-110">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="827b5-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="827b5-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="827b5-111">See also</span></span>

- [<span data-ttu-id="827b5-112">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="827b5-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="827b5-113">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="827b5-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="827b5-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="827b5-114">ALink API</span></span>](index.md)
