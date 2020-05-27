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
ms.openlocfilehash: b6651f30e0df3a5ffc29d310b9067e76761dcf01
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007539"
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="cf65c-102">CorPropertyAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="cf65c-102">CorPropertyAttr Enumeration</span></span>
<span data-ttu-id="cf65c-103">Bir özelliğin meta verilerini tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="cf65c-103">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf65c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf65c-104">Syntax</span></span>  
  
```cpp  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="cf65c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="cf65c-105">Members</span></span>  
  
|<span data-ttu-id="cf65c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="cf65c-106">Member</span></span>|<span data-ttu-id="cf65c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf65c-107">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="cf65c-108">Özelliğin özel olduğunu ve adının nasıl kullanıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf65c-108">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="cf65c-109">Ortak dil çalışma zamanı tarafından iç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="cf65c-109">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="cf65c-110">Ortak dil çalışma zamanı meta veri iç API 'Lerinin, özellik adının kodlamasını denetlemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf65c-110">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="cf65c-111">Özelliğin varsayılan bir değere sahip olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf65c-111">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="cf65c-112">Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="cf65c-112">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cf65c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf65c-113">Requirements</span></span>  
 <span data-ttu-id="cf65c-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf65c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf65c-115">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="cf65c-115">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="cf65c-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf65c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf65c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf65c-117">See also</span></span>

- [<span data-ttu-id="cf65c-118">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="cf65c-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
