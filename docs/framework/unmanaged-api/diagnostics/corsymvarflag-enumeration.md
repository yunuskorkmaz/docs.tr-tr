---
description: 'Daha fazla bilgi edinin: CorSymVarFlag numaralandırması'
title: CorSymVarFlag Numaralandırması
ms.date: 03/30/2017
api_name:
- CorSymVarFlag
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymVarFlag
helpviewer_keywords:
- CorSymVarFlag enumeration [.NET Framework debugging]
ms.assetid: c3f7d307-4047-4f9a-be8c-f152fca42fd0
topic_type:
- apiref
ms.openlocfilehash: 28f4b4775e20703e5dcaa7daf69affd3548aa3f2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800467"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="e98bd-103">CorSymVarFlag Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e98bd-103">CorSymVarFlag Enumeration</span></span>

<span data-ttu-id="e98bd-104">Bir değişkenin derleyici tarafından oluşturulup oluşturulmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e98bd-104">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e98bd-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e98bd-105">Syntax</span></span>  
  
```cpp  
typedef enum CorSymVarFlag
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="e98bd-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e98bd-106">Members</span></span>  
  
|<span data-ttu-id="e98bd-107">Üye</span><span class="sxs-lookup"><span data-stu-id="e98bd-107">Member</span></span>|<span data-ttu-id="e98bd-108">Description</span><span class="sxs-lookup"><span data-stu-id="e98bd-108">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="e98bd-109">Verilen değişkenin derleyicinin ürettiği olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e98bd-109">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e98bd-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e98bd-110">Requirements</span></span>  

 <span data-ttu-id="e98bd-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e98bd-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e98bd-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e98bd-112">See also</span></span>

- [<span data-ttu-id="e98bd-113">Tanılama Sembol Deposu Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="e98bd-113">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
