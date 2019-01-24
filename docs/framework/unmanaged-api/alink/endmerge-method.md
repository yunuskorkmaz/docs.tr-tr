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
ms.openlocfilehash: 9ba7c2d0c5ea29d5db429139f1831e8d71dd23f3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739147"
---
# <a name="endmerge-method"></a><span data-ttu-id="d82d5-102">EndMerge Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d82d5-102">EndMerge Method</span></span>
<span data-ttu-id="d82d5-103">Tüm özel öznitelikleri emit kapsamına birleştirildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d82d5-103">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d82d5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d82d5-104">Syntax</span></span>  
  
```  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d82d5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d82d5-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d82d5-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="d82d5-106">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d82d5-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d82d5-107">Return Value</span></span>  
 <span data-ttu-id="d82d5-108">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="d82d5-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d82d5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d82d5-109">Requirements</span></span>  
 <span data-ttu-id="d82d5-110">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="d82d5-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d82d5-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d82d5-111">See also</span></span>
- [<span data-ttu-id="d82d5-112">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d82d5-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="d82d5-113">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d82d5-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="d82d5-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="d82d5-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
