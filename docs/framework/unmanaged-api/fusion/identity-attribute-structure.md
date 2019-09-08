---
title: IDENTITY_ATTRIBUTE Yapısı
ms.date: 03/30/2017
api_name:
- IDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE
helpviewer_keywords:
- IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0bcabb32d50b236d42a555c073b50ba3a234dde
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796492"
---
# <a name="identity_attribute-structure"></a><span data-ttu-id="f5d12-102">IDENTITY_ATTRIBUTE Yapısı</span><span class="sxs-lookup"><span data-stu-id="f5d12-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="f5d12-103">Bir [IDefinitionIdentity](idefinitionidentity-interface.md) örneği hakkında meta veri özniteliği bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="f5d12-103">Contains metadata attribute information about an [IDefinitionIdentity](idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5d12-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5d12-104">Syntax</span></span>  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="f5d12-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f5d12-105">Members</span></span>  
  
|<span data-ttu-id="f5d12-106">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d12-106">Member</span></span>|<span data-ttu-id="f5d12-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5d12-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="f5d12-108">Özniteliğin bulunduğu ad alanını içeren, null ile sonlandırılmış bir karakter dizesinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f5d12-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="f5d12-109">Özniteliğin adını içeren, null ile sonlandırılmış bir karakter dizesinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f5d12-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="f5d12-110">Özniteliğin değerini içeren, null ile sonlandırılmış bir karakter dizesinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f5d12-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5d12-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5d12-111">Remarks</span></span>  
 <span data-ttu-id="f5d12-112">Yapı `IDENTITY_ATTRIBUTE` , null ile sonlandırılmış karakter dizelerine yönelik üç işaretçi içerir.</span><span class="sxs-lookup"><span data-stu-id="f5d12-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="f5d12-113">Bu üç dize bir özniteliği tanımlıyor.</span><span class="sxs-lookup"><span data-stu-id="f5d12-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="f5d12-114">Bir `IDENTITY_ATTRIBUTE` yapının örneği bir [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) yapısının örneğiyle ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="f5d12-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="f5d12-115">Yapı gerçek dizeleri içerir ve ilgili `IDENTITY_ATTRIBUTE_BLOB` yapı, `IDENTITY_ATTRIBUTE` yapıda listelenen üç dizenin farklarını listeler. `IDENTITY_ATTRIBUTE`</span><span class="sxs-lookup"><span data-stu-id="f5d12-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5d12-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5d12-116">Requirements</span></span>  
 <span data-ttu-id="f5d12-117">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5d12-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5d12-118">**Üst bilgi** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="f5d12-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="f5d12-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5d12-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5d12-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5d12-120">See also</span></span>

- [<span data-ttu-id="f5d12-121">IDefinitionIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5d12-121">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
- [<span data-ttu-id="f5d12-122">IDENTITY_ATTRIBUTE_BLOB Yapısı</span><span class="sxs-lookup"><span data-stu-id="f5d12-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](identity-attribute-blob-structure.md)
- [<span data-ttu-id="f5d12-123">Fusion Yapıları</span><span class="sxs-lookup"><span data-stu-id="f5d12-123">Fusion Structures</span></span>](fusion-structures.md)
