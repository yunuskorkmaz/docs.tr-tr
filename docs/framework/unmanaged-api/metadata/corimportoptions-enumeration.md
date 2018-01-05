---
title: "CorImportOptions Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorImportOptions
api_location: mscoree.dll
api_type: COM
f1_keywords: CorImportOptions
helpviewer_keywords: CorImportOptions enumeration [.NET Framework metadata]
ms.assetid: 4e5d03cb-97c9-4ff4-8dbd-17d94ee374d3
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e9af7bbb6dd7cfa488f72ec99f9cfd848f04e72f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corimportoptions-enumeration"></a><span data-ttu-id="9bccb-102">CorImportOptions Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9bccb-102">CorImportOptions Enumeration</span></span>
<span data-ttu-id="9bccb-103">Geçerli kapsam dışında bir derlemeyi içe aktarılmasını sırasında davranışını denetleyen bayrak değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9bccb-103">Contains flag values that control the behavior during importation of an assembly outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bccb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9bccb-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="9bccb-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="9bccb-105">Members</span></span>  
  
|<span data-ttu-id="9bccb-106">Üye</span><span class="sxs-lookup"><span data-stu-id="9bccb-106">Member</span></span>|<span data-ttu-id="9bccb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bccb-107">Description</span></span>|  
|------------|-----------------|  
|`MDImportOptionDefault`|<span data-ttu-id="9bccb-108">Silinmiş kayıtlar atlamak için varsayılan davranış gösterir.</span><span class="sxs-lookup"><span data-stu-id="9bccb-108">Indicates the default behavior, which is to skip deleted records.</span></span>|  
|`MDImportOptionAll`|<span data-ttu-id="9bccb-109">Tüm meta veriler numaralandırılan olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9bccb-109">Indicates that all metadata should be enumerated.</span></span>|  
|`MDImportOptionAllTypeDefs`|<span data-ttu-id="9bccb-110">Silinen olanlar da dahil olmak üzere tüm tür tanımları numaralandırılan olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9bccb-110">Indicates that all TypeDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllMethodDefs`|<span data-ttu-id="9bccb-111">Silinen olanlar da dahil olmak üzere tüm MethodDefs numaralandırılan olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9bccb-111">Indicates that all MethodDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllFieldDefs`|<span data-ttu-id="9bccb-112">Silinen olanlar da dahil olmak üzere tüm FieldDefs numaralandırılan olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9bccb-112">Indicates that all FieldDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllProperties`|<span data-ttu-id="9bccb-113">Silinen olanlar da dahil olmak üzere tüm PropertyDefs numaralandırılan olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9bccb-113">Indicates that all PropertyDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllEvents`|<span data-ttu-id="9bccb-114">Silinen olanlar da dahil olmak üzere tüm EventDefs numaralandırılan olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9bccb-114">Indicates that all EventDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllCustomAttributes`|<span data-ttu-id="9bccb-115">Silinen olanlar da dahil olmak üzere tüm özel öznitelikleri numaralandırılan olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9bccb-115">Indicates that all custom attributes, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllExportedTypes`|<span data-ttu-id="9bccb-116">Silinen olanlar da dahil olmak üzere tüm dışarı aktarılan türleri numaralandırılan olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9bccb-116">Indicates that all exported types, including deleted ones, should be enumerated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9bccb-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9bccb-117">Requirements</span></span>  
 <span data-ttu-id="9bccb-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bccb-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bccb-119">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="9bccb-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="9bccb-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bccb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bccb-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9bccb-121">See Also</span></span>  
 [<span data-ttu-id="9bccb-122">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="9bccb-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
