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
ms.openlocfilehash: 5e88dd0053ec7562d6223c18479f4a4fadc68c12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701800"
---
# <a name="ceesectionattr-enumeration"></a><span data-ttu-id="64d19-102">CeeSectionAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="64d19-102">CeeSectionAttr Enumeration</span></span>
<span data-ttu-id="64d19-103">Tarafından kullanılmak üzere bir bölümün özniteliklerini belirten değerleri sağlayan [Iceegen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="64d19-103">Provides values that specify attributes of a section for use by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64d19-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64d19-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="64d19-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="64d19-105">Members</span></span>  
  
|<span data-ttu-id="64d19-106">Üye</span><span class="sxs-lookup"><span data-stu-id="64d19-106">Member</span></span>|<span data-ttu-id="64d19-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64d19-107">Description</span></span>|  
|------------|-----------------|  
|`sdNone`|<span data-ttu-id="64d19-108">Bölüm öznitelikleri yok.</span><span class="sxs-lookup"><span data-stu-id="64d19-108">Section has no attributes.</span></span>|  
|`sdReadOnly`|<span data-ttu-id="64d19-109">Bölüm yalnızca, güncelleştirilmiş okunabilir başlatılmış veriler içerir.</span><span class="sxs-lookup"><span data-stu-id="64d19-109">Section contains initialized data that can be only read, not updated.</span></span>|  
|`sdReadWrite`|<span data-ttu-id="64d19-110">Bölüm, okuma veya güncelleştirilen başlatılmış veriler içerir.</span><span class="sxs-lookup"><span data-stu-id="64d19-110">Section contains initialized data that can be read or updated.</span></span>|  
|`sdExecute`|<span data-ttu-id="64d19-111">Bölüm okuyup yürütülen izin yürütülebilir kod içerir.</span><span class="sxs-lookup"><span data-stu-id="64d19-111">Section contains executable code that is allowed to be read and executed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="64d19-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64d19-112">Requirements</span></span>  
 <span data-ttu-id="64d19-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64d19-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64d19-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="64d19-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="64d19-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="64d19-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="64d19-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64d19-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64d19-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64d19-117">See also</span></span>
- [<span data-ttu-id="64d19-118">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="64d19-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
