---
title: CorPropertyAttr Numaralandırması
ms.date: 03/30/2017
api_name:
- CorPropertyAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPropertyAttr
helpviewer_keywords:
- CorPropertyAttr enumeration [.NET Framework metadata]
ms.assetid: 58ac8202-854d-4efd-acfb-d2da8b446e12
topic_type:
- apiref
ms.openlocfilehash: 95a798d662b44cf2e088af84d3b1eec97da8e7fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177939"
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="05a09-102">CorPropertyAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="05a09-102">CorPropertyAttr Enumeration</span></span>
<span data-ttu-id="05a09-103">Bir özelliğin meta verilerini açıklayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="05a09-103">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05a09-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05a09-104">Syntax</span></span>  
  
```cpp  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="05a09-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="05a09-105">Members</span></span>  
  
|<span data-ttu-id="05a09-106">Üye</span><span class="sxs-lookup"><span data-stu-id="05a09-106">Member</span></span>|<span data-ttu-id="05a09-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05a09-107">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="05a09-108">Özelliğin özel olduğunu ve adının nasıl olduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="05a09-108">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="05a09-109">Ortak dil çalışma zamanı tarafından dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="05a09-109">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="05a09-110">Ortak dil çalışma zamanı meta veri iç API'lerinin özellik adının kodlayıcılığını denetlemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="05a09-110">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="05a09-111">Özelliğin varsayılan bir değeri olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="05a09-111">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="05a09-112">Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="05a09-112">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="05a09-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05a09-113">Requirements</span></span>  
 <span data-ttu-id="05a09-114">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05a09-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05a09-115">**Üstbilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="05a09-115">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="05a09-116">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05a09-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05a09-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05a09-117">See also</span></span>

- [<span data-ttu-id="05a09-118">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="05a09-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
