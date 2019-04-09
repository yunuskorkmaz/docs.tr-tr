---
title: CeeSectionAttr Numaralandırması
ms.date: 03/30/2017
api_name:
- CeeSectionAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionAttr
helpviewer_keywords:
- CeeSectionAttr enumeration [.NET Framework metadata]
ms.assetid: 0db51881-b869-4677-a715-1726a9216489
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c317524cefd7ed654e76bdd7051cdcd7653062db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101796"
---
# <a name="ceesectionattr-enumeration"></a><span data-ttu-id="404d5-102">CeeSectionAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="404d5-102">CeeSectionAttr Enumeration</span></span>
<span data-ttu-id="404d5-103">Tarafından kullanılmak üzere bir bölümün özniteliklerini belirten değerleri sağlayan [Iceegen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="404d5-103">Provides values that specify attributes of a section for use by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="404d5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="404d5-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="404d5-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="404d5-105">Members</span></span>  
  
|<span data-ttu-id="404d5-106">Üye</span><span class="sxs-lookup"><span data-stu-id="404d5-106">Member</span></span>|<span data-ttu-id="404d5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="404d5-107">Description</span></span>|  
|------------|-----------------|  
|`sdNone`|<span data-ttu-id="404d5-108">Bölüm öznitelikleri yok.</span><span class="sxs-lookup"><span data-stu-id="404d5-108">Section has no attributes.</span></span>|  
|`sdReadOnly`|<span data-ttu-id="404d5-109">Bölüm yalnızca, güncelleştirilmiş okunabilir başlatılmış veriler içerir.</span><span class="sxs-lookup"><span data-stu-id="404d5-109">Section contains initialized data that can be only read, not updated.</span></span>|  
|`sdReadWrite`|<span data-ttu-id="404d5-110">Bölüm, okuma veya güncelleştirilen başlatılmış veriler içerir.</span><span class="sxs-lookup"><span data-stu-id="404d5-110">Section contains initialized data that can be read or updated.</span></span>|  
|`sdExecute`|<span data-ttu-id="404d5-111">Bölüm okuyup yürütülen izin yürütülebilir kod içerir.</span><span class="sxs-lookup"><span data-stu-id="404d5-111">Section contains executable code that is allowed to be read and executed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="404d5-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="404d5-112">Requirements</span></span>  
 <span data-ttu-id="404d5-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="404d5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="404d5-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="404d5-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="404d5-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="404d5-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="404d5-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="404d5-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="404d5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="404d5-117">See also</span></span>

- [<span data-ttu-id="404d5-118">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="404d5-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
