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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198861"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="feba6-102">CorSymVarFlag Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="feba6-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="feba6-103">Bir değişken, derleyicinin ürettiği olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="feba6-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="feba6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="feba6-104">Syntax</span></span>  
  
```  
typedef enum CorSymVarFlag   
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="feba6-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="feba6-105">Members</span></span>  
  
|<span data-ttu-id="feba6-106">Üye</span><span class="sxs-lookup"><span data-stu-id="feba6-106">Member</span></span>|<span data-ttu-id="feba6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="feba6-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="feba6-108">Belirtilen değişken, derleyicinin ürettiği olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="feba6-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="feba6-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="feba6-109">Requirements</span></span>  
 <span data-ttu-id="feba6-110">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="feba6-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feba6-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="feba6-111">See also</span></span>

- [<span data-ttu-id="feba6-112">Tanılama Sembol Deposu Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="feba6-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
