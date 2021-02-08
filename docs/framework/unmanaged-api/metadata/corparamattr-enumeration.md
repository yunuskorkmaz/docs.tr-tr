---
description: 'Daha fazla bilgi edinin: CorParamAttr numaralandırması'
title: CorParamAttr Numaralandırması
ms.date: 03/30/2017
api_name:
- CorParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorParamAttr
helpviewer_keywords:
- CorParamAttr enumeration [.NET Framework metadata]
ms.assetid: a7ff90ad-dad8-48e8-917d-4aa9a118cbc8
topic_type:
- apiref
ms.openlocfilehash: c07569d3fb92b20a7985dbfeb2205af727866051
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784294"
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="22922-103">CorParamAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="22922-103">CorParamAttr Enumeration</span></span>

<span data-ttu-id="22922-104">Bir yöntem parametresinin meta verilerini tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="22922-104">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22922-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="22922-105">Syntax</span></span>  
  
```cpp  
typedef enum CorParamAttr {  
  
    pdIn                        =   0x0001,  
    pdOut                       =   0x0002,  
    pdOptional                  =   0x0010,  
  
    pdReservedMask              =   0xf000,  
    pdHasDefault                =   0x1000,  
    pdHasFieldMarshal           =   0x2000,  
  
    pdUnused                    =   0xcfe0  
  
} CorParamAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="22922-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="22922-106">Members</span></span>  
  
|<span data-ttu-id="22922-107">Üye</span><span class="sxs-lookup"><span data-stu-id="22922-107">Member</span></span>|<span data-ttu-id="22922-108">Description</span><span class="sxs-lookup"><span data-stu-id="22922-108">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="22922-109">Parametrenin yöntem çağrısına geçtiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="22922-109">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="22922-110">Parametrenin dönüş yönteminden geçtiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="22922-110">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="22922-111">Parametrenin isteğe bağlı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="22922-111">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="22922-112">Ortak dil çalışma zamanı tarafından iç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="22922-112">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="22922-113">Parametrenin varsayılan bir değere sahip olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="22922-113">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="22922-114">Parametrenin sıralama bilgilerine sahip olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="22922-114">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="22922-115">Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="22922-115">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="22922-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="22922-116">Requirements</span></span>  

 <span data-ttu-id="22922-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22922-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22922-118">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="22922-118">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="22922-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22922-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22922-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22922-120">See also</span></span>

- [<span data-ttu-id="22922-121">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="22922-121">Metadata Enumerations</span></span>](metadata-enumerations.md)
