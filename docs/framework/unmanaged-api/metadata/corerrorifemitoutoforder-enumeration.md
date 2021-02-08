---
description: 'Daha fazla bilgi edinin: Corerrorifemıtoutoforder numaralandırması'
title: CorErrorIfEmitOutOfOrder Numaralandırması
ms.date: 03/30/2017
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
ms.openlocfilehash: b45d3204ae386b7ad9d7ab1daccdfdef35e2ad9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784534"
---
# <a name="corerrorifemitoutoforder-enumeration"></a><span data-ttu-id="f2f3b-103">CorErrorIfEmitOutOfOrder Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f2f3b-103">CorErrorIfEmitOutOfOrder Enumeration</span></span>

<span data-ttu-id="f2f3b-104">Meta veriler sıralı dışı bırakıldığında bir hata iletisinin oluşturulması gereken koşulları belirten bayrak değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="f2f3b-104">Contains flag values that indicate the conditions under which an error message should be generated when metadata is emitted out of order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2f3b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f2f3b-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="f2f3b-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f2f3b-106">Members</span></span>  
  
|<span data-ttu-id="f2f3b-107">Üye</span><span class="sxs-lookup"><span data-stu-id="f2f3b-107">Member</span></span>|<span data-ttu-id="f2f3b-108">Description</span><span class="sxs-lookup"><span data-stu-id="f2f3b-108">Description</span></span>|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|<span data-ttu-id="f2f3b-109">Hata iletileri oluşturabilen varsayılan davranışı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2f3b-109">Indicates the default behavior, which does not generate error messages.</span></span>|  
|`MDErrorOutOfOrderNone`|<span data-ttu-id="f2f3b-110">Derleyicinin hata iletileri üretmemelidir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f2f3b-110">Indicates that the compiler should not generate error messages.</span></span>|  
|`MDErrorOutOfOrderAll`|<span data-ttu-id="f2f3b-111">Bir alan, özellik, olay, yöntem veya parametre sıralı olarak yayıldığınızda derleyicinin bir hata mesajı oluşturması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2f3b-111">Indicates that the compiler should generate an error message when a field, property, event, method, or parameter is emitted out of order.</span></span>|  
|`MDMethodOutOfOrder`|<span data-ttu-id="f2f3b-112">Bir yöntem bir sıra dışına yayıldığınızda derleyicinin bir hata mesajı oluşturması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2f3b-112">Indicates that the compiler should generate an error message when a method is emitted out of order.</span></span>|  
|`MDFieldOutOfOrder`|<span data-ttu-id="f2f3b-113">Bir alan sipariş dışı bırakıldığında derleyicinin bir hata mesajı oluşturması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2f3b-113">Indicates that the compiler should generate an error message when a field is emitted out of order.</span></span>|  
|`MDParamOutOfOrder`|<span data-ttu-id="f2f3b-114">Bir parametre sıralı olarak yayıldığınızda derleyicinin bir hata mesajı oluşturması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2f3b-114">Indicates that the compiler should generate an error message when a parameter is emitted out of order.</span></span>|  
|`MDPropertyOutOfOrder`|<span data-ttu-id="f2f3b-115">Bir özellik sıralı olarak yayıldığınızda derleyicinin bir hata mesajı oluşturması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2f3b-115">Indicates that the compiler should generate an error message when a property is emitted out of order.</span></span>|  
|`MDEventOutOfOrder`|<span data-ttu-id="f2f3b-116">Bir olay bir sıra dışına yayıldığınızda derleyicinin bir hata mesajı oluşturması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2f3b-116">Indicates that the compiler should generate an error message when an event is emitted out of order.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f2f3b-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2f3b-117">Requirements</span></span>  

 <span data-ttu-id="f2f3b-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2f3b-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2f3b-119">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="f2f3b-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f2f3b-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2f3b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2f3b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2f3b-121">See also</span></span>

- [<span data-ttu-id="f2f3b-122">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="f2f3b-122">Metadata Enumerations</span></span>](metadata-enumerations.md)
