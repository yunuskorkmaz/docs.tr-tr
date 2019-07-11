---
title: CorImportOptions Numaralandırması
ms.date: 03/30/2017
api_name:
- CorImportOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorImportOptions
helpviewer_keywords:
- CorImportOptions enumeration [.NET Framework metadata]
ms.assetid: 4e5d03cb-97c9-4ff4-8dbd-17d94ee374d3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 38c0937804eb82d1c96a605b55a00784ba58fe13
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781821"
---
# <a name="corimportoptions-enumeration"></a><span data-ttu-id="ac0c1-102">CorImportOptions Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ac0c1-102">CorImportOptions Enumeration</span></span>
<span data-ttu-id="ac0c1-103">Geçerli kapsam dışında bir derleme içeri aktarma sırasında davranışını denetleyen bayrak değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="ac0c1-103">Contains flag values that control the behavior during importation of an assembly outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac0c1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac0c1-104">Syntax</span></span>  
  
```cpp  
typedef enum CorImportOptions {  
  
    MDImportOptionDefault                = 0x00000000,  
    MDImportOptionAll                    = 0xFFFFFFFF,  
    MDImportOptionAllTypeDefs            = 0x00000001,  
    MDImportOptionAllMethodDefs          = 0x00000002,  
    MDImportOptionAllFieldDefs           = 0x00000004,  
    MDImportOptionAllProperties          = 0x00000008,  
    MDImportOptionAllEvents              = 0x00000010,  
    MDImportOptionAllCustomAttributes    = 0x00000020,  
    MDImportOptionAllExportedTypes       = 0x00000040  
  
} CorImportOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="ac0c1-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ac0c1-105">Members</span></span>  
  
|<span data-ttu-id="ac0c1-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ac0c1-106">Member</span></span>|<span data-ttu-id="ac0c1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac0c1-107">Description</span></span>|  
|------------|-----------------|  
|`MDImportOptionDefault`|<span data-ttu-id="ac0c1-108">Silinmiş kayıtlar atlamak için varsayılan davranış gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac0c1-108">Indicates the default behavior, which is to skip deleted records.</span></span>|  
|`MDImportOptionAll`|<span data-ttu-id="ac0c1-109">Tüm meta veriler listelenmiş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac0c1-109">Indicates that all metadata should be enumerated.</span></span>|  
|`MDImportOptionAllTypeDefs`|<span data-ttu-id="ac0c1-110">Silinmiş olanlar da dahil olmak üzere tüm tür tanımları, listelenmiş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac0c1-110">Indicates that all TypeDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllMethodDefs`|<span data-ttu-id="ac0c1-111">Silinmiş olanlar da dahil olmak üzere tüm MethodDefs listelenmiş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac0c1-111">Indicates that all MethodDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllFieldDefs`|<span data-ttu-id="ac0c1-112">Silinmiş olanlar da dahil olmak üzere tüm FieldDefs listelenmiş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac0c1-112">Indicates that all FieldDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllProperties`|<span data-ttu-id="ac0c1-113">Silinmiş olanlar da dahil olmak üzere tüm PropertyDefs listelenmiş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac0c1-113">Indicates that all PropertyDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllEvents`|<span data-ttu-id="ac0c1-114">Silinmiş olanlar da dahil olmak üzere tüm EventDefs listelenmiş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac0c1-114">Indicates that all EventDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllCustomAttributes`|<span data-ttu-id="ac0c1-115">Silinmiş olanlar da dahil olmak üzere tüm özel öznitelikleri listelenmiş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac0c1-115">Indicates that all custom attributes, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllExportedTypes`|<span data-ttu-id="ac0c1-116">Silinmiş olanlar da dahil olmak üzere dışarı aktarılan tüm türler listelenmiş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac0c1-116">Indicates that all exported types, including deleted ones, should be enumerated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ac0c1-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac0c1-117">Requirements</span></span>  
 <span data-ttu-id="ac0c1-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac0c1-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac0c1-119">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="ac0c1-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ac0c1-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac0c1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac0c1-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac0c1-121">See also</span></span>

- [<span data-ttu-id="ac0c1-122">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="ac0c1-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
