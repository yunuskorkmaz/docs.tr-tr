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
ms.openlocfilehash: 7becace679b62a635d8231c3d42213f247f44190
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444171"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="c11e5-102">CeeSectionRelocExtra Birleşimi</span><span class="sxs-lookup"><span data-stu-id="c11e5-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="c11e5-103">Bir bölümün yerini değiştirmek için [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) arabirimi tarafından kullanılan bir adres sapmasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c11e5-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c11e5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c11e5-104">Syntax</span></span>  
  
```cpp  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="c11e5-105">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="c11e5-105">Members</span></span>  
  
|<span data-ttu-id="c11e5-106">Üyesi</span><span class="sxs-lookup"><span data-stu-id="c11e5-106">Member</span></span>|<span data-ttu-id="c11e5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c11e5-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="c11e5-108">Bölüm için üst adres ayarlama.</span><span class="sxs-lookup"><span data-stu-id="c11e5-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c11e5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c11e5-109">Requirements</span></span>  
 <span data-ttu-id="c11e5-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c11e5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c11e5-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c11e5-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c11e5-112">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c11e5-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c11e5-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c11e5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c11e5-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c11e5-114">See also</span></span>

- [<span data-ttu-id="c11e5-115">Meta Veri Birleşimleri</span><span class="sxs-lookup"><span data-stu-id="c11e5-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
