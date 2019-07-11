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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16f6d7bf6fa1730d50cfe81526817e492a453dad
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781979"
---
# <a name="corerrorifemitoutoforder-enumeration"></a><span data-ttu-id="4ac0d-102">CorErrorIfEmitOutOfOrder Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4ac0d-102">CorErrorIfEmitOutOfOrder Enumeration</span></span>
<span data-ttu-id="4ac0d-103">Meta veri sıralamaya yayıldığını zaman altında bir hata iletisi oluşturulan koşulları belirten bayrak değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="4ac0d-103">Contains flag values that indicate the conditions under which an error message should be generated when metadata is emitted out of order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ac0d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ac0d-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="4ac0d-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4ac0d-105">Members</span></span>  
  
|<span data-ttu-id="4ac0d-106">Üye</span><span class="sxs-lookup"><span data-stu-id="4ac0d-106">Member</span></span>|<span data-ttu-id="4ac0d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ac0d-107">Description</span></span>|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|<span data-ttu-id="4ac0d-108">Hata iletileri oluşturmaz varsayılan davranış gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ac0d-108">Indicates the default behavior, which does not generate error messages.</span></span>|  
|`MDErrorOutOfOrderNone`|<span data-ttu-id="4ac0d-109">Derleyici hatası iletileri üretmemelidir gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ac0d-109">Indicates that the compiler should not generate error messages.</span></span>|  
|`MDErrorOutOfOrderAll`|<span data-ttu-id="4ac0d-110">Derleyici bir hata iletisi oluşturur, bir alan, özellik, olay, yöntemi veya parametre sıralamaya yayıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ac0d-110">Indicates that the compiler should generate an error message when a field, property, event, method, or parameter is emitted out of order.</span></span>|  
|`MDMethodOutOfOrder`|<span data-ttu-id="4ac0d-111">Bir yöntem sıralamaya yayıldığını, derleyici bir hata iletisi oluşturmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ac0d-111">Indicates that the compiler should generate an error message when a method is emitted out of order.</span></span>|  
|`MDFieldOutOfOrder`|<span data-ttu-id="4ac0d-112">Bir alan sıralamaya yayıldığını, derleyici bir hata iletisi oluşturmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ac0d-112">Indicates that the compiler should generate an error message when a field is emitted out of order.</span></span>|  
|`MDParamOutOfOrder`|<span data-ttu-id="4ac0d-113">Bir parametre sıralamaya yayıldığını, derleyici bir hata iletisi oluşturmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ac0d-113">Indicates that the compiler should generate an error message when a parameter is emitted out of order.</span></span>|  
|`MDPropertyOutOfOrder`|<span data-ttu-id="4ac0d-114">Bir özellik sıralamaya yayıldığını, derleyici bir hata iletisi oluşturmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ac0d-114">Indicates that the compiler should generate an error message when a property is emitted out of order.</span></span>|  
|`MDEventOutOfOrder`|<span data-ttu-id="4ac0d-115">Bir olay sıralamaya yayıldığını, derleyici bir hata iletisi oluşturmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ac0d-115">Indicates that the compiler should generate an error message when an event is emitted out of order.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4ac0d-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4ac0d-116">Requirements</span></span>  
 <span data-ttu-id="4ac0d-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ac0d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ac0d-118">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="4ac0d-118">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="4ac0d-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ac0d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ac0d-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ac0d-120">See also</span></span>

- [<span data-ttu-id="4ac0d-121">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="4ac0d-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
