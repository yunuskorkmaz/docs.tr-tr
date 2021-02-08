---
description: 'Daha fazla bilgi edinin: CorPropertyAttr numaralandırması'
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
ms.openlocfilehash: 1f3e2fccb11a067c6c46350a2c36d47007875755
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784242"
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="0751b-103">CorPropertyAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="0751b-103">CorPropertyAttr Enumeration</span></span>

<span data-ttu-id="0751b-104">Bir özelliğin meta verilerini tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0751b-104">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0751b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0751b-105">Syntax</span></span>  
  
```cpp  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="0751b-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0751b-106">Members</span></span>  
  
|<span data-ttu-id="0751b-107">Üye</span><span class="sxs-lookup"><span data-stu-id="0751b-107">Member</span></span>|<span data-ttu-id="0751b-108">Description</span><span class="sxs-lookup"><span data-stu-id="0751b-108">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="0751b-109">Özelliğin özel olduğunu ve adının nasıl kullanıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0751b-109">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="0751b-110">Ortak dil çalışma zamanı tarafından iç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0751b-110">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="0751b-111">Ortak dil çalışma zamanı meta veri iç API 'Lerinin, özellik adının kodlamasını denetlemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0751b-111">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="0751b-112">Özelliğin varsayılan bir değere sahip olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0751b-112">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="0751b-113">Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="0751b-113">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0751b-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0751b-114">Requirements</span></span>  

 <span data-ttu-id="0751b-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0751b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0751b-116">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="0751b-116">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="0751b-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0751b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0751b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0751b-118">See also</span></span>

- [<span data-ttu-id="0751b-119">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="0751b-119">Metadata Enumerations</span></span>](metadata-enumerations.md)
