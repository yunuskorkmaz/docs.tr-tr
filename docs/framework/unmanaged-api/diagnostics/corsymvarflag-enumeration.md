---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 50367358ba5bcf335f8cc2ca3222f6cf7ea2ff70
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54670146"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="b7e93-102">CorSymVarFlag Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b7e93-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="b7e93-103">Bir değişken, derleyicinin ürettiği olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7e93-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7e93-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7e93-104">Syntax</span></span>  
  
```  
typedef enum CorSymVarFlag   
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="b7e93-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b7e93-105">Members</span></span>  
  
|<span data-ttu-id="b7e93-106">Üye</span><span class="sxs-lookup"><span data-stu-id="b7e93-106">Member</span></span>|<span data-ttu-id="b7e93-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7e93-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="b7e93-108">Belirtilen değişken, derleyicinin ürettiği olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7e93-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b7e93-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b7e93-109">Requirements</span></span>  
 <span data-ttu-id="b7e93-110">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b7e93-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7e93-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7e93-111">See also</span></span>
- [<span data-ttu-id="b7e93-112">Tanılama Simge Deposu Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="b7e93-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
