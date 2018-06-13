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
ms.openlocfilehash: 7078b2eb98c15b7229132076da8af4691032bb08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441798"
---
# <a name="corimportoptions-enumeration"></a><span data-ttu-id="63733-102">CorImportOptions Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="63733-102">CorImportOptions Enumeration</span></span>
<span data-ttu-id="63733-103">Geçerli kapsam dışında bir derlemeyi içe aktarılmasını sırasında davranışını denetleyen bayrak değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="63733-103">Contains flag values that control the behavior during importation of an assembly outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63733-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63733-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="63733-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="63733-105">Members</span></span>  
  
|<span data-ttu-id="63733-106">Üye</span><span class="sxs-lookup"><span data-stu-id="63733-106">Member</span></span>|<span data-ttu-id="63733-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63733-107">Description</span></span>|  
|------------|-----------------|  
|`MDImportOptionDefault`|<span data-ttu-id="63733-108">Silinmiş kayıtlar atlamak için varsayılan davranış gösterir.</span><span class="sxs-lookup"><span data-stu-id="63733-108">Indicates the default behavior, which is to skip deleted records.</span></span>|  
|`MDImportOptionAll`|<span data-ttu-id="63733-109">Tüm meta veriler numaralandırılan olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="63733-109">Indicates that all metadata should be enumerated.</span></span>|  
|`MDImportOptionAllTypeDefs`|<span data-ttu-id="63733-110">Silinen olanlar da dahil olmak üzere tüm tür tanımları numaralandırılan olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="63733-110">Indicates that all TypeDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllMethodDefs`|<span data-ttu-id="63733-111">Silinen olanlar da dahil olmak üzere tüm MethodDefs numaralandırılan olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="63733-111">Indicates that all MethodDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllFieldDefs`|<span data-ttu-id="63733-112">Silinen olanlar da dahil olmak üzere tüm FieldDefs numaralandırılan olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="63733-112">Indicates that all FieldDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllProperties`|<span data-ttu-id="63733-113">Silinen olanlar da dahil olmak üzere tüm PropertyDefs numaralandırılan olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="63733-113">Indicates that all PropertyDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllEvents`|<span data-ttu-id="63733-114">Silinen olanlar da dahil olmak üzere tüm EventDefs numaralandırılan olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="63733-114">Indicates that all EventDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllCustomAttributes`|<span data-ttu-id="63733-115">Silinen olanlar da dahil olmak üzere tüm özel öznitelikleri numaralandırılan olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="63733-115">Indicates that all custom attributes, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllExportedTypes`|<span data-ttu-id="63733-116">Silinen olanlar da dahil olmak üzere tüm dışarı aktarılan türleri numaralandırılan olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="63733-116">Indicates that all exported types, including deleted ones, should be enumerated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63733-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63733-117">Requirements</span></span>  
 <span data-ttu-id="63733-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63733-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63733-119">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="63733-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="63733-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63733-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63733-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="63733-121">See Also</span></span>  
 [<span data-ttu-id="63733-122">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="63733-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
