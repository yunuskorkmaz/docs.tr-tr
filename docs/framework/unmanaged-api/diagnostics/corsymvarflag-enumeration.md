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
ms.openlocfilehash: a6a9c5ff91989fc1ad7da4e23df0e80d9d74ec7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424982"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="b2e3c-102">CorSymVarFlag Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b2e3c-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="b2e3c-103">Bir değişken derleyicinin ürettiği olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2e3c-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2e3c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2e3c-104">Syntax</span></span>  
  
```  
typedef enum CorSymVarFlag   
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="b2e3c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b2e3c-105">Members</span></span>  
  
|<span data-ttu-id="b2e3c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="b2e3c-106">Member</span></span>|<span data-ttu-id="b2e3c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2e3c-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="b2e3c-108">Belirtilen değişken derleyicinin ürettiği olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2e3c-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2e3c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2e3c-109">Requirements</span></span>  
 <span data-ttu-id="b2e3c-110">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b2e3c-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2e3c-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b2e3c-111">See Also</span></span>  
 [<span data-ttu-id="b2e3c-112">Tanılama Simge Deposu Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="b2e3c-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
