---
description: 'Daha fazla bilgi edinin: IDENTITY_ATTRIBUTE Yapısı'
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
ms.openlocfilehash: 52610961ab202fc79351073eac1846a1a63889e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800181"
---
# <a name="identity_attribute-structure"></a><span data-ttu-id="112a2-103">IDENTITY_ATTRIBUTE Yapısı</span><span class="sxs-lookup"><span data-stu-id="112a2-103">IDENTITY_ATTRIBUTE Structure</span></span>

<span data-ttu-id="112a2-104">Bir [IDefinitionIdentity](idefinitionidentity-interface.md) örneği hakkında meta veri özniteliği bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="112a2-104">Contains metadata attribute information about an [IDefinitionIdentity](idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="112a2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="112a2-105">Syntax</span></span>  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="112a2-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="112a2-106">Members</span></span>  
  
|<span data-ttu-id="112a2-107">Üye</span><span class="sxs-lookup"><span data-stu-id="112a2-107">Member</span></span>|<span data-ttu-id="112a2-108">Description</span><span class="sxs-lookup"><span data-stu-id="112a2-108">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="112a2-109">Özniteliğin bulunduğu ad alanını içeren, null ile sonlandırılmış bir karakter dizesinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="112a2-109">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="112a2-110">Özniteliğin adını içeren, null ile sonlandırılmış bir karakter dizesinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="112a2-110">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="112a2-111">Özniteliğin değerini içeren, null ile sonlandırılmış bir karakter dizesinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="112a2-111">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="112a2-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="112a2-112">Remarks</span></span>  

 <span data-ttu-id="112a2-113">`IDENTITY_ATTRIBUTE`Yapı, null ile sonlandırılmış karakter dizelerine yönelik üç işaretçi içerir.</span><span class="sxs-lookup"><span data-stu-id="112a2-113">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="112a2-114">Bu üç dize bir özniteliği tanımlıyor.</span><span class="sxs-lookup"><span data-stu-id="112a2-114">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="112a2-115">Bir yapının örneği bir `IDENTITY_ATTRIBUTE` [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) yapısının örneğiyle ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="112a2-115">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="112a2-116">`IDENTITY_ATTRIBUTE`Yapı gerçek dizeleri içerir ve ilgili `IDENTITY_ATTRIBUTE_BLOB` Yapı, yapıda listelenen üç dizenin farklarını listeler `IDENTITY_ATTRIBUTE` .</span><span class="sxs-lookup"><span data-stu-id="112a2-116">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="112a2-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="112a2-117">Requirements</span></span>  

 <span data-ttu-id="112a2-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="112a2-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="112a2-119">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="112a2-119">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="112a2-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="112a2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="112a2-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="112a2-121">See also</span></span>

- [<span data-ttu-id="112a2-122">IDefinitionIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="112a2-122">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
- [<span data-ttu-id="112a2-123">IDENTITY_ATTRIBUTE_BLOB Yapısı</span><span class="sxs-lookup"><span data-stu-id="112a2-123">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](identity-attribute-blob-structure.md)
- [<span data-ttu-id="112a2-124">Fusion Yapıları</span><span class="sxs-lookup"><span data-stu-id="112a2-124">Fusion Structures</span></span>](fusion-structures.md)
