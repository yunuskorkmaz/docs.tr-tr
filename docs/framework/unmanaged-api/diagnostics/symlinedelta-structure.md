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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fabc8f77b12865d0d971b5934d7de27b52f3e813
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61914647"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="847a0-102">SYMLINEDELTA Yapısı</span><span class="sxs-lookup"><span data-stu-id="847a0-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="847a0-103">Sembol işleyici sonucunda düzenlemeleri taşınan yöntemleri hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="847a0-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="847a0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="847a0-104">Syntax</span></span>  
  
```  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="847a0-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="847a0-105">Members</span></span>  
  
|<span data-ttu-id="847a0-106">Üye</span><span class="sxs-lookup"><span data-stu-id="847a0-106">Member</span></span>|<span data-ttu-id="847a0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="847a0-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="847a0-108">Yöntemin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="847a0-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="847a0-109">Yöntem taşındı satırların sayısı.</span><span class="sxs-lookup"><span data-stu-id="847a0-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="847a0-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="847a0-110">Requirements</span></span>  
 <span data-ttu-id="847a0-111">**Üst bilgi:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="847a0-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="847a0-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="847a0-112">See also</span></span>

- [<span data-ttu-id="847a0-113">Tanılama Simge Deposu Yapıları</span><span class="sxs-lookup"><span data-stu-id="847a0-113">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
