---
description: 'Daha fazla bilgi edinin: CorImportOptions numaralandırması'
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
ms.openlocfilehash: b942ed3f5b1b3c400b4f901e3dd3c4364e1d588c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784450"
---
# <a name="corimportoptions-enumeration"></a><span data-ttu-id="33347-103">CorImportOptions Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="33347-103">CorImportOptions Enumeration</span></span>

<span data-ttu-id="33347-104">Geçerli kapsam dışında bir derlemenin içe aktarılması işlemini sırasında davranışı denetleyen bayrak değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="33347-104">Contains flag values that control the behavior during importation of an assembly outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33347-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="33347-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="33347-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="33347-106">Members</span></span>  
  
|<span data-ttu-id="33347-107">Üye</span><span class="sxs-lookup"><span data-stu-id="33347-107">Member</span></span>|<span data-ttu-id="33347-108">Description</span><span class="sxs-lookup"><span data-stu-id="33347-108">Description</span></span>|  
|------------|-----------------|  
|`MDImportOptionDefault`|<span data-ttu-id="33347-109">Silinen kayıtları atlamak için olan varsayılan davranışı gösterir.</span><span class="sxs-lookup"><span data-stu-id="33347-109">Indicates the default behavior, which is to skip deleted records.</span></span>|  
|`MDImportOptionAll`|<span data-ttu-id="33347-110">Tüm meta verilerin numaralandırılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="33347-110">Indicates that all metadata should be enumerated.</span></span>|  
|`MDImportOptionAllTypeDefs`|<span data-ttu-id="33347-111">Silinenler dahil olmak üzere tüm TypeDefs 'un numaralandırılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="33347-111">Indicates that all TypeDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllMethodDefs`|<span data-ttu-id="33347-112">Silinenler dahil olmak üzere tüm MethodDefs 'ın numaralandırılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="33347-112">Indicates that all MethodDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllFieldDefs`|<span data-ttu-id="33347-113">Silinen tüm FieldDefs 'ler dahil olmak üzere numaralandırılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="33347-113">Indicates that all FieldDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllProperties`|<span data-ttu-id="33347-114">Silinen gibi tüm PropertyDefs 'ler de dahil olmak üzere numaralandırılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="33347-114">Indicates that all PropertyDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllEvents`|<span data-ttu-id="33347-115">Silinen tüm EventDefs 'ler dahil olmak üzere numaralandırılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="33347-115">Indicates that all EventDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllCustomAttributes`|<span data-ttu-id="33347-116">Silinen olanlar da dahil olmak üzere tüm özel özniteliklerin numaralandırılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="33347-116">Indicates that all custom attributes, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllExportedTypes`|<span data-ttu-id="33347-117">Silinmiş olanlar dahil olmak üzere tüm dışarıya aktarılmış türlerin numaralandırılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="33347-117">Indicates that all exported types, including deleted ones, should be enumerated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="33347-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="33347-118">Requirements</span></span>  

 <span data-ttu-id="33347-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33347-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33347-120">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="33347-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="33347-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33347-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33347-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33347-122">See also</span></span>

- [<span data-ttu-id="33347-123">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="33347-123">Metadata Enumerations</span></span>](metadata-enumerations.md)
