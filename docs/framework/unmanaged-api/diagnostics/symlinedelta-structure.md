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
ms.openlocfilehash: a1e83e4b8cb6603029f3b42b1a3b9ba4810c9039
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438006"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="a860c-102">SYMLINEDELTA Yapısı</span><span class="sxs-lookup"><span data-stu-id="a860c-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="a860c-103">Düzenleme sonucu olarak taşınan yöntemler hakkında sembol işleyicisine bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a860c-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a860c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a860c-104">Syntax</span></span>  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="a860c-105">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="a860c-105">Members</span></span>  
  
|<span data-ttu-id="a860c-106">Üyesi</span><span class="sxs-lookup"><span data-stu-id="a860c-106">Member</span></span>|<span data-ttu-id="a860c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a860c-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="a860c-108">Metodun meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="a860c-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="a860c-109">Yöntemin taşındığı satır sayısı.</span><span class="sxs-lookup"><span data-stu-id="a860c-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a860c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a860c-110">Requirements</span></span>  
 <span data-ttu-id="a860c-111">**Üst bilgi:** Corsya. IDL</span><span class="sxs-lookup"><span data-stu-id="a860c-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a860c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a860c-112">See also</span></span>

- [<span data-ttu-id="a860c-113">Tanılama Simge Deposu Yapıları</span><span class="sxs-lookup"><span data-stu-id="a860c-113">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
