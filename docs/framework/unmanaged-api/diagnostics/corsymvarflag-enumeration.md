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
ms.openlocfilehash: e5b387ee7fd4cc0088c90d2b8278fbf18bb36f51
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755686"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="f9a66-102">CorSymVarFlag Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f9a66-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="f9a66-103">Bir değişken, derleyicinin ürettiği olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9a66-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9a66-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9a66-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSymVarFlag   
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="f9a66-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f9a66-105">Members</span></span>  
  
|<span data-ttu-id="f9a66-106">Üye</span><span class="sxs-lookup"><span data-stu-id="f9a66-106">Member</span></span>|<span data-ttu-id="f9a66-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9a66-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="f9a66-108">Belirtilen değişken, derleyicinin ürettiği olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f9a66-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f9a66-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9a66-109">Requirements</span></span>  
 <span data-ttu-id="f9a66-110">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f9a66-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9a66-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9a66-111">See also</span></span>

- [<span data-ttu-id="f9a66-112">Tanılama Simge Deposu Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="f9a66-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
