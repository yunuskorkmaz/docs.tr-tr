---
title: "CeeSectionAttr Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CeeSectionAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CeeSectionAttr
helpviewer_keywords: CeeSectionAttr enumeration [.NET Framework metadata]
ms.assetid: 0db51881-b869-4677-a715-1726a9216489
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 212d9be02a3c4ca97a6a69391ff82edb1d013d93
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ceesectionattr-enumeration"></a><span data-ttu-id="a26bc-102">CeeSectionAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="a26bc-102">CeeSectionAttr Enumeration</span></span>
<span data-ttu-id="a26bc-103">Tarafından kullanım için bir bölüm özniteliklerini belirtmek değerleri sağlayan [Iceegen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a26bc-103">Provides values that specify attributes of a section for use by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a26bc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a26bc-104">Syntax</span></span>  
  
```  
typedef enum  {  
    sdNone      = 0,  
    sdReadOnly  = IMAGE_SCN_CNT_INITIALIZED_DATA |  
                  IMAGE_SCN_MEM_READ,  
    sdReadWrite = sdReadOnly | IMAGE_SCN_MEM_WRITE,  
    sdExecute   = IMAGE_SCN_MEM_READ | IMAGE_SCN_CNT_CODE |  
                  IMAGE_SCN_MEM_EXECUTE  
} CeeSectionAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="a26bc-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a26bc-105">Members</span></span>  
  
|<span data-ttu-id="a26bc-106">Üye</span><span class="sxs-lookup"><span data-stu-id="a26bc-106">Member</span></span>|<span data-ttu-id="a26bc-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a26bc-107">Description</span></span>|  
|------------|-----------------|  
|`sdNone`|<span data-ttu-id="a26bc-108">Bölüm öznitelikleri yok.</span><span class="sxs-lookup"><span data-stu-id="a26bc-108">Section has no attributes.</span></span>|  
|`sdReadOnly`|<span data-ttu-id="a26bc-109">Bölüm yalnızca, güncelleştirilmiş okunabilir başlatılmış verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="a26bc-109">Section contains initialized data that can be only read, not updated.</span></span>|  
|`sdReadWrite`|<span data-ttu-id="a26bc-110">Bölüm okuma veya güncelleştirilen başlatılmış verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="a26bc-110">Section contains initialized data that can be read or updated.</span></span>|  
|`sdExecute`|<span data-ttu-id="a26bc-111">Bölüm okuyup yürütülen izin yürütülebilir kod içerir.</span><span class="sxs-lookup"><span data-stu-id="a26bc-111">Section contains executable code that is allowed to be read and executed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a26bc-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a26bc-112">Requirements</span></span>  
 <span data-ttu-id="a26bc-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a26bc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a26bc-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a26bc-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a26bc-115">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a26bc-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a26bc-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a26bc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a26bc-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a26bc-117">See Also</span></span>  
 [<span data-ttu-id="a26bc-118">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="a26bc-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
