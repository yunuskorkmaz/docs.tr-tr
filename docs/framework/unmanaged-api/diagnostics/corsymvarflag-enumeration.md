---
title: "CorSymVarFlag Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSymVarFlag
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSymVarFlag
helpviewer_keywords: CorSymVarFlag enumeration [.NET Framework debugging]
ms.assetid: c3f7d307-4047-4f9a-be8c-f152fca42fd0
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: edbbc8109eb44494c7f4fac0ed8756e23bdc955b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="5968e-102">CorSymVarFlag Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="5968e-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="5968e-103">Bir değişken derleyicinin ürettiği olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5968e-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5968e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5968e-104">Syntax</span></span>  
  
```  
typedef enum CorSymVarFlag   
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="5968e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="5968e-105">Members</span></span>  
  
|<span data-ttu-id="5968e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="5968e-106">Member</span></span>|<span data-ttu-id="5968e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5968e-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="5968e-108">Belirtilen değişken derleyicinin ürettiği olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5968e-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5968e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5968e-109">Requirements</span></span>  
 <span data-ttu-id="5968e-110">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5968e-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5968e-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5968e-111">See Also</span></span>  
 [<span data-ttu-id="5968e-112">Tanılama sembol deposu numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="5968e-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
