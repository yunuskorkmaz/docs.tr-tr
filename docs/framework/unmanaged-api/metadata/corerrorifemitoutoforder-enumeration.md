---
title: "CorErrorIfEmitOutOfOrder Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorErrorIfEmitOutOfOrder
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorErrorIfEmitOutOfOrder
helpviewer_keywords:
- CorErrorIfEmitOutOfOrder enumeration [.NET Framework metadata]
ms.assetid: 6d758aad-29a7-44fe-9481-bbff5b799a32
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7c049d78d8ba67ec5f08fc2beb584fef4987c9e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corerrorifemitoutoforder-enumeration"></a><span data-ttu-id="6a388-102">CorErrorIfEmitOutOfOrder Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6a388-102">CorErrorIfEmitOutOfOrder Enumeration</span></span>
<span data-ttu-id="6a388-103">Meta verileri bozuk yayılan zaman altında bir hata iletisi oluşturulan koşulları belirtmek bayrak değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6a388-103">Contains flag values that indicate the conditions under which an error message should be generated when metadata is emitted out of order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a388-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a388-104">Syntax</span></span>  
  
```  
typedef enum CorErrorIfEmitOutOfOrder {  
  
    MDErrorOutOfOrderDefault    = 0x00000000,  
    MDErrorOutOfOrderNone       = 0x00000000,  
    MDErrorOutOfOrderAll        = 0xffffffff,  
    MDMethodOutOfOrder          = 0x00000001,  
    MDFieldOutOfOrder           = 0x00000002,  
    MDParamOutOfOrder           = 0x00000004,  
    MDPropertyOutOfOrder        = 0x00000008,  
    MDEventOutOfOrder           = 0x00000010  
  
} CorErrorIfEmitOutOfOrder;  
```  
  
## <a name="members"></a><span data-ttu-id="6a388-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6a388-105">Members</span></span>  
  
|<span data-ttu-id="6a388-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6a388-106">Member</span></span>|<span data-ttu-id="6a388-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a388-107">Description</span></span>|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|<span data-ttu-id="6a388-108">Hata iletileri oluşturmaz varsayılan davranış gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a388-108">Indicates the default behavior, which does not generate error messages.</span></span>|  
|`MDErrorOutOfOrderNone`|<span data-ttu-id="6a388-109">Derleyici hatası iletileri üretmemelidir gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a388-109">Indicates that the compiler should not generate error messages.</span></span>|  
|`MDErrorOutOfOrderAll`|<span data-ttu-id="6a388-110">Derleyici bir hata iletisine yol bir alan, özellik, olay, yöntemi veya parametre bozuk yayılan gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a388-110">Indicates that the compiler should generate an error message when a field, property, event, method, or parameter is emitted out of order.</span></span>|  
|`MDMethodOutOfOrder`|<span data-ttu-id="6a388-111">Bir yöntem bozuk yayılan olduğunda derleyici bir hata iletisi oluşturur gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a388-111">Indicates that the compiler should generate an error message when a method is emitted out of order.</span></span>|  
|`MDFieldOutOfOrder`|<span data-ttu-id="6a388-112">Bir alan bozuk yayılan olduğunda derleyici bir hata iletisi oluşturur gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a388-112">Indicates that the compiler should generate an error message when a field is emitted out of order.</span></span>|  
|`MDParamOutOfOrder`|<span data-ttu-id="6a388-113">Bir parametre bozuk yayılan olduğunda derleyici bir hata iletisi oluşturur gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a388-113">Indicates that the compiler should generate an error message when a parameter is emitted out of order.</span></span>|  
|`MDPropertyOutOfOrder`|<span data-ttu-id="6a388-114">Bir özellik bozuk yayılan olduğunda derleyici bir hata iletisi oluşturur gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a388-114">Indicates that the compiler should generate an error message when a property is emitted out of order.</span></span>|  
|`MDEventOutOfOrder`|<span data-ttu-id="6a388-115">Bir olay bozuk yayılan olduğunda derleyici bir hata iletisi oluşturur gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a388-115">Indicates that the compiler should generate an error message when an event is emitted out of order.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6a388-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a388-116">Requirements</span></span>  
 <span data-ttu-id="6a388-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a388-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a388-118">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="6a388-118">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="6a388-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a388-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a388-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6a388-120">See Also</span></span>  
 [<span data-ttu-id="6a388-121">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="6a388-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
