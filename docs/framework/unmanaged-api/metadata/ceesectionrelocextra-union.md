---
description: 'Daha fazla bilgi edinin: CeeSectionRelocExtra birleşimi'
title: CeeSectionRelocExtra Birleşimi
ms.date: 03/30/2017
api_name:
- CeeSectionRelocExtra Union
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocExtra
helpviewer_keywords:
- CeeSectionRelocExtra union [.NET Framework metadata]
ms.assetid: d9568cf6-7f98-4cd6-ab36-0a2bd509afcc
topic_type:
- apiref
ms.openlocfilehash: 40001c1a0772e24633f4232da8e7817f3747f8ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678854"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="98339-103">CeeSectionRelocExtra Birleşimi</span><span class="sxs-lookup"><span data-stu-id="98339-103">CeeSectionRelocExtra Union</span></span>

<span data-ttu-id="98339-104">Bir bölümün yerini değiştirmek için [ICeeGen](iceegen-interface.md) arabirimi tarafından kullanılan bir adres sapmasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="98339-104">Represents an address offset that is used by the [ICeeGen](iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98339-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="98339-105">Syntax</span></span>  
  
```cpp  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="98339-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="98339-106">Members</span></span>  
  
|<span data-ttu-id="98339-107">Üye</span><span class="sxs-lookup"><span data-stu-id="98339-107">Member</span></span>|<span data-ttu-id="98339-108">Description</span><span class="sxs-lookup"><span data-stu-id="98339-108">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="98339-109">Bölüm için üst adres ayarlama.</span><span class="sxs-lookup"><span data-stu-id="98339-109">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="98339-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98339-110">Requirements</span></span>  

 <span data-ttu-id="98339-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98339-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98339-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="98339-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="98339-113">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="98339-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="98339-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98339-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98339-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98339-115">See also</span></span>

- [<span data-ttu-id="98339-116">Meta Veri Birleşmeleri</span><span class="sxs-lookup"><span data-stu-id="98339-116">Metadata Unions</span></span>](metadata-unions.md)
