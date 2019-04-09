---
title: CorSetENC Numaralandırması
ms.date: 03/30/2017
api_name:
- CorSetENC
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetENC
helpviewer_keywords:
- CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1fd903cb4a9ce664b7a1c958a3fef0c639d6845d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122323"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="876d0-102">CorSetENC Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="876d0-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="876d0-103">Meta veri oluşturma sırasında davranışını etkilemek için kullanılan değerler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="876d0-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="876d0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="876d0-104">Syntax</span></span>  
  
```  
typedef enum CorSetENC {  
  
    MDSetENCOn                  = 0x00000001,  
    MDSetENCOff                 = 0x00000002,  
  
    MDUpdateENC                 = 0x00000001,  
    MDUpdateFull                = 0x00000002,  
    MDUpdateExtension           = 0x00000003,  
    MDUpdateIncremental         = 0x00000004,  
    MDUpdateDelta               = 0x00000005,  
    MDUpdateMask                = 0x00000007  
  
} CorSetENC;  
```  
  
## <a name="members"></a><span data-ttu-id="876d0-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="876d0-105">Members</span></span>  
  
|<span data-ttu-id="876d0-106">Üye</span><span class="sxs-lookup"><span data-stu-id="876d0-106">Member</span></span>|<span data-ttu-id="876d0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="876d0-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="876d0-108">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="876d0-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="876d0-109">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="876d0-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="876d0-110">Meta veri güncelleştirilebilir gelirken, belirteçleri taşınamaz gösterir.</span><span class="sxs-lookup"><span data-stu-id="876d0-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="876d0-111">Güncelleştirmeler sırasında belirteçleri taşınabilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="876d0-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="876d0-112">Güncelleştirmeleri yalnızca yapılan eklemeleri oluşabilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="876d0-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="876d0-113">Belirteçleri taşınamaz.</span><span class="sxs-lookup"><span data-stu-id="876d0-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="876d0-114">Derleme artımlı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="876d0-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="876d0-115">Yalnızca değiştirilen meta verilerin kaydedilmesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="876d0-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="876d0-116">İçerir `MDUpdateENC`, `MDUpdateFull` ve `MDUpdateIncremental`.</span><span class="sxs-lookup"><span data-stu-id="876d0-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="876d0-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="876d0-117">Requirements</span></span>  
 <span data-ttu-id="876d0-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="876d0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="876d0-119">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="876d0-119">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="876d0-120">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="876d0-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="876d0-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="876d0-121">See also</span></span>

- [<span data-ttu-id="876d0-122">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="876d0-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
