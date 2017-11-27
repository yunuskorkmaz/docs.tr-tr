---
title: "SYMLINEDELTA Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: SYMLINEDELTA
api_location: diasymreader.dll
api_type: COM
f1_keywords: SYMLINEDELTA
helpviewer_keywords: SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cbd83560516e946c03a0ea71cf79fe6d3396bacb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="cd089-102">SYMLINEDELTA Yapısı</span><span class="sxs-lookup"><span data-stu-id="cd089-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="cd089-103">Sembol işleyicisine sonucunda düzenlemeleri taşındı yöntemleri hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd089-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd089-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd089-104">Syntax</span></span>  
  
```  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="cd089-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="cd089-105">Members</span></span>  
  
|<span data-ttu-id="cd089-106">Üye</span><span class="sxs-lookup"><span data-stu-id="cd089-106">Member</span></span>|<span data-ttu-id="cd089-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd089-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="cd089-108">Yöntemin meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="cd089-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="cd089-109">Yöntem taşınmış satır sayısı.</span><span class="sxs-lookup"><span data-stu-id="cd089-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd089-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cd089-110">Requirements</span></span>  
 <span data-ttu-id="cd089-111">**Başlık:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="cd089-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd089-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cd089-112">See Also</span></span>  
 [<span data-ttu-id="cd089-113">Tanılama sembol deposu yapıları</span><span class="sxs-lookup"><span data-stu-id="cd089-113">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
