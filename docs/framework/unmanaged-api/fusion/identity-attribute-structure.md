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
ms.openlocfilehash: da4b1d6f2a7079ef33859fce29c9555ac06fcfc2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725657"
---
# <a name="identity_attribute-structure"></a><span data-ttu-id="61749-102">IDENTITY_ATTRIBUTE Yapısı</span><span class="sxs-lookup"><span data-stu-id="61749-102">IDENTITY_ATTRIBUTE Structure</span></span>

<span data-ttu-id="61749-103">Bir [IDefinitionIdentity](idefinitionidentity-interface.md) örneği hakkında meta veri özniteliği bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="61749-103">Contains metadata attribute information about an [IDefinitionIdentity](idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61749-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="61749-104">Syntax</span></span>  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="61749-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="61749-105">Members</span></span>  
  
|<span data-ttu-id="61749-106">Üye</span><span class="sxs-lookup"><span data-stu-id="61749-106">Member</span></span>|<span data-ttu-id="61749-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61749-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="61749-108">Özniteliğin bulunduğu ad alanını içeren, null ile sonlandırılmış bir karakter dizesinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="61749-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="61749-109">Özniteliğin adını içeren, null ile sonlandırılmış bir karakter dizesinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="61749-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="61749-110">Özniteliğin değerini içeren, null ile sonlandırılmış bir karakter dizesinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="61749-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61749-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="61749-111">Remarks</span></span>  

 <span data-ttu-id="61749-112">`IDENTITY_ATTRIBUTE`Yapı, null ile sonlandırılmış karakter dizelerine yönelik üç işaretçi içerir.</span><span class="sxs-lookup"><span data-stu-id="61749-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="61749-113">Bu üç dize bir özniteliği tanımlıyor.</span><span class="sxs-lookup"><span data-stu-id="61749-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="61749-114">Bir yapının örneği bir `IDENTITY_ATTRIBUTE` [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) yapısının örneğiyle ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="61749-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="61749-115">`IDENTITY_ATTRIBUTE`Yapı gerçek dizeleri içerir ve ilgili `IDENTITY_ATTRIBUTE_BLOB` Yapı, yapıda listelenen üç dizenin farklarını listeler `IDENTITY_ATTRIBUTE` .</span><span class="sxs-lookup"><span data-stu-id="61749-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61749-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="61749-116">Requirements</span></span>  

 <span data-ttu-id="61749-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61749-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61749-118">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="61749-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="61749-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61749-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61749-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61749-120">See also</span></span>

- [<span data-ttu-id="61749-121">IDefinitionIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61749-121">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
- [<span data-ttu-id="61749-122">IDENTITY_ATTRIBUTE_BLOB Yapısı</span><span class="sxs-lookup"><span data-stu-id="61749-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](identity-attribute-blob-structure.md)
- [<span data-ttu-id="61749-123">Fusion Yapıları</span><span class="sxs-lookup"><span data-stu-id="61749-123">Fusion Structures</span></span>](fusion-structures.md)
