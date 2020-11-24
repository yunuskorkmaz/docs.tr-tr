---
title: SYMLINEDELTA Yapısı
ms.date: 03/30/2017
api_name:
- SYMLINEDELTA
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SYMLINEDELTA
helpviewer_keywords:
- SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type:
- apiref
ms.openlocfilehash: dd45703540f8dc41b746ca03b4f09d74186aa9aa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690947"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="6ce9c-102">SYMLINEDELTA Yapısı</span><span class="sxs-lookup"><span data-stu-id="6ce9c-102">SYMLINEDELTA Structure</span></span>

<span data-ttu-id="6ce9c-103">Düzenleme sonucu olarak taşınan yöntemler hakkında sembol işleyicisine bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ce9c-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ce9c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="6ce9c-104">Syntax</span></span>  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="6ce9c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6ce9c-105">Members</span></span>  
  
|<span data-ttu-id="6ce9c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6ce9c-106">Member</span></span>|<span data-ttu-id="6ce9c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6ce9c-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="6ce9c-108">Metodun meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="6ce9c-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="6ce9c-109">Yöntemin taşındığı satır sayısı.</span><span class="sxs-lookup"><span data-stu-id="6ce9c-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6ce9c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ce9c-110">Requirements</span></span>  

 <span data-ttu-id="6ce9c-111">**Üst bilgi:** Corsya. IDL</span><span class="sxs-lookup"><span data-stu-id="6ce9c-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ce9c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ce9c-112">See also</span></span>

- [<span data-ttu-id="6ce9c-113">Tanılama Sembol Deposu Yapıları</span><span class="sxs-lookup"><span data-stu-id="6ce9c-113">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
