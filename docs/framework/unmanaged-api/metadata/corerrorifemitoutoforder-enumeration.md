---
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
ms.openlocfilehash: 1d1b0cbb8be33f285b63e7353da973455e0fd752
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718858"
---
# <a name="corerrorifemitoutoforder-enumeration"></a><span data-ttu-id="c7186-102">CorErrorIfEmitOutOfOrder Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c7186-102">CorErrorIfEmitOutOfOrder Enumeration</span></span>

<span data-ttu-id="c7186-103">Meta veriler sıralı dışı bırakıldığında bir hata iletisinin oluşturulması gereken koşulları belirten bayrak değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="c7186-103">Contains flag values that indicate the conditions under which an error message should be generated when metadata is emitted out of order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7186-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="c7186-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="c7186-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c7186-105">Members</span></span>  
  
|<span data-ttu-id="c7186-106">Üye</span><span class="sxs-lookup"><span data-stu-id="c7186-106">Member</span></span>|<span data-ttu-id="c7186-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7186-107">Description</span></span>|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|<span data-ttu-id="c7186-108">Hata iletileri oluşturabilen varsayılan davranışı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7186-108">Indicates the default behavior, which does not generate error messages.</span></span>|  
|`MDErrorOutOfOrderNone`|<span data-ttu-id="c7186-109">Derleyicinin hata iletileri üretmemelidir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c7186-109">Indicates that the compiler should not generate error messages.</span></span>|  
|`MDErrorOutOfOrderAll`|<span data-ttu-id="c7186-110">Bir alan, özellik, olay, yöntem veya parametre sıralı olarak yayıldığınızda derleyicinin bir hata mesajı oluşturması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7186-110">Indicates that the compiler should generate an error message when a field, property, event, method, or parameter is emitted out of order.</span></span>|  
|`MDMethodOutOfOrder`|<span data-ttu-id="c7186-111">Bir yöntem bir sıra dışına yayıldığınızda derleyicinin bir hata mesajı oluşturması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7186-111">Indicates that the compiler should generate an error message when a method is emitted out of order.</span></span>|  
|`MDFieldOutOfOrder`|<span data-ttu-id="c7186-112">Bir alan sipariş dışı bırakıldığında derleyicinin bir hata mesajı oluşturması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7186-112">Indicates that the compiler should generate an error message when a field is emitted out of order.</span></span>|  
|`MDParamOutOfOrder`|<span data-ttu-id="c7186-113">Bir parametre sıralı olarak yayıldığınızda derleyicinin bir hata mesajı oluşturması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7186-113">Indicates that the compiler should generate an error message when a parameter is emitted out of order.</span></span>|  
|`MDPropertyOutOfOrder`|<span data-ttu-id="c7186-114">Bir özellik sıralı olarak yayıldığınızda derleyicinin bir hata mesajı oluşturması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7186-114">Indicates that the compiler should generate an error message when a property is emitted out of order.</span></span>|  
|`MDEventOutOfOrder`|<span data-ttu-id="c7186-115">Bir olay bir sıra dışına yayıldığınızda derleyicinin bir hata mesajı oluşturması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7186-115">Indicates that the compiler should generate an error message when an event is emitted out of order.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c7186-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7186-116">Requirements</span></span>  

 <span data-ttu-id="c7186-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7186-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7186-118">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="c7186-118">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c7186-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7186-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7186-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7186-120">See also</span></span>

- [<span data-ttu-id="c7186-121">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="c7186-121">Metadata Enumerations</span></span>](metadata-enumerations.md)
