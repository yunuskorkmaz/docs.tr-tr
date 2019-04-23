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
ms.openlocfilehash: 0c797378f5e13f39c1c786237a3a7b9cf577fccc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59198861"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="2f9a5-102">CorSymVarFlag Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="2f9a5-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="2f9a5-103">Bir değişken, derleyicinin ürettiği olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2f9a5-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f9a5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f9a5-104">Syntax</span></span>  
  
```  
typedef enum CorSymVarFlag   
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="2f9a5-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2f9a5-105">Members</span></span>  
  
|<span data-ttu-id="2f9a5-106">Üye</span><span class="sxs-lookup"><span data-stu-id="2f9a5-106">Member</span></span>|<span data-ttu-id="2f9a5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f9a5-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="2f9a5-108">Belirtilen değişken, derleyicinin ürettiği olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f9a5-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2f9a5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2f9a5-109">Requirements</span></span>  
 <span data-ttu-id="2f9a5-110">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2f9a5-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f9a5-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f9a5-111">See also</span></span>

- [<span data-ttu-id="2f9a5-112">Tanılama Simge Deposu Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="2f9a5-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
