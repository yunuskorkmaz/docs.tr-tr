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
ms.openlocfilehash: 8b7edf1cc642228c4a79c855b51727264f31741c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107979"
---
# <a name="identity_attribute-structure"></a><span data-ttu-id="15e60-102">IDENTITY_ATTRIBUTE Yapısı</span><span class="sxs-lookup"><span data-stu-id="15e60-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="15e60-103">Bir [IDefinitionIdentity](idefinitionidentity-interface.md) örneği hakkında meta veri özniteliği bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="15e60-103">Contains metadata attribute information about an [IDefinitionIdentity](idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15e60-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15e60-104">Syntax</span></span>  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="15e60-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="15e60-105">Members</span></span>  
  
|<span data-ttu-id="15e60-106">Üye</span><span class="sxs-lookup"><span data-stu-id="15e60-106">Member</span></span>|<span data-ttu-id="15e60-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15e60-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="15e60-108">Özniteliğin bulunduğu ad alanını içeren, null ile sonlandırılmış bir karakter dizesinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="15e60-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="15e60-109">Özniteliğin adını içeren, null ile sonlandırılmış bir karakter dizesinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="15e60-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="15e60-110">Özniteliğin değerini içeren, null ile sonlandırılmış bir karakter dizesinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="15e60-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15e60-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15e60-111">Remarks</span></span>  
 <span data-ttu-id="15e60-112">`IDENTITY_ATTRIBUTE` yapısı, null ile sonlandırılmış karakter dizelerine yönelik üç işaretçi içerir.</span><span class="sxs-lookup"><span data-stu-id="15e60-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="15e60-113">Bu üç dize bir özniteliği tanımlıyor.</span><span class="sxs-lookup"><span data-stu-id="15e60-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="15e60-114">Bir `IDENTITY_ATTRIBUTE` yapısının örneği, bir [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) yapısının örneğiyle ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="15e60-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="15e60-115">`IDENTITY_ATTRIBUTE` yapısı gerçek dizeleri içerir ve karşılık gelen `IDENTITY_ATTRIBUTE_BLOB` yapısı `IDENTITY_ATTRIBUTE` yapısında listelenen üç dizeye olan uzaklıkları listeler.</span><span class="sxs-lookup"><span data-stu-id="15e60-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15e60-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15e60-116">Requirements</span></span>  
 <span data-ttu-id="15e60-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15e60-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15e60-118">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="15e60-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="15e60-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15e60-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15e60-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15e60-120">See also</span></span>

- [<span data-ttu-id="15e60-121">IDefinitionIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15e60-121">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
- [<span data-ttu-id="15e60-122">IDENTITY_ATTRIBUTE_BLOB Yapısı</span><span class="sxs-lookup"><span data-stu-id="15e60-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](identity-attribute-blob-structure.md)
- [<span data-ttu-id="15e60-123">Fusion Yapıları</span><span class="sxs-lookup"><span data-stu-id="15e60-123">Fusion Structures</span></span>](fusion-structures.md)
