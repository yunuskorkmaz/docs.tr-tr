---
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
ms.openlocfilehash: d11fefe220fdb00457cc48a6cd166673350be049
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006044"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="52a81-102">CeeSectionRelocExtra Birleşimi</span><span class="sxs-lookup"><span data-stu-id="52a81-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="52a81-103">Bir bölümün yerini değiştirmek için [ICeeGen](iceegen-interface.md) arabirimi tarafından kullanılan bir adres sapmasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="52a81-103">Represents an address offset that is used by the [ICeeGen](iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52a81-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52a81-104">Syntax</span></span>  
  
```cpp  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="52a81-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="52a81-105">Members</span></span>  
  
|<span data-ttu-id="52a81-106">Üye</span><span class="sxs-lookup"><span data-stu-id="52a81-106">Member</span></span>|<span data-ttu-id="52a81-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52a81-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="52a81-108">Bölüm için üst adres ayarlama.</span><span class="sxs-lookup"><span data-stu-id="52a81-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="52a81-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52a81-109">Requirements</span></span>  
 <span data-ttu-id="52a81-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52a81-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52a81-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="52a81-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="52a81-112">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="52a81-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="52a81-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52a81-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52a81-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52a81-114">See also</span></span>

- [<span data-ttu-id="52a81-115">Meta Veri Birleşimleri</span><span class="sxs-lookup"><span data-stu-id="52a81-115">Metadata Unions</span></span>](metadata-unions.md)
