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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 88f594117fffedb6acafef26a9e834dd951ea5bb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787532"
---
# <a name="endmerge-method"></a><span data-ttu-id="35a59-102">EndMerge Yöntemi</span><span class="sxs-lookup"><span data-stu-id="35a59-102">EndMerge Method</span></span>
<span data-ttu-id="35a59-103">Tüm özel özniteliklerin yayma kapsamıyla birleştirildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="35a59-103">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35a59-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35a59-104">Syntax</span></span>  
  
```cpp  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="35a59-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="35a59-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="35a59-106">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="35a59-106">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="35a59-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="35a59-107">Return Value</span></span>  
 <span data-ttu-id="35a59-108">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="35a59-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35a59-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="35a59-109">Requirements</span></span>  
 <span data-ttu-id="35a59-110">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="35a59-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35a59-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35a59-111">See also</span></span>

- [<span data-ttu-id="35a59-112">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="35a59-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="35a59-113">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="35a59-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="35a59-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="35a59-114">ALink API</span></span>](index.md)
