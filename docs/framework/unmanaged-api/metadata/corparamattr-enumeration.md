---
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
ms.openlocfilehash: e8afcb972cab9757458c7032c3678d45c6418fac
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007578"
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="34d85-102">CorParamAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="34d85-102">CorParamAttr Enumeration</span></span>
<span data-ttu-id="34d85-103">Bir yöntem parametresinin meta verilerini tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="34d85-103">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34d85-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34d85-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="34d85-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="34d85-105">Members</span></span>  
  
|<span data-ttu-id="34d85-106">Üye</span><span class="sxs-lookup"><span data-stu-id="34d85-106">Member</span></span>|<span data-ttu-id="34d85-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34d85-107">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="34d85-108">Parametrenin yöntem çağrısına geçtiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="34d85-108">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="34d85-109">Parametrenin dönüş yönteminden geçtiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="34d85-109">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="34d85-110">Parametrenin isteğe bağlı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="34d85-110">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="34d85-111">Ortak dil çalışma zamanı tarafından iç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="34d85-111">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="34d85-112">Parametrenin varsayılan bir değere sahip olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="34d85-112">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="34d85-113">Parametrenin sıralama bilgilerine sahip olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="34d85-113">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="34d85-114">Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="34d85-114">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="34d85-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34d85-115">Requirements</span></span>  
 <span data-ttu-id="34d85-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34d85-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34d85-117">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="34d85-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="34d85-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34d85-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34d85-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34d85-119">See also</span></span>

- [<span data-ttu-id="34d85-120">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="34d85-120">Metadata Enumerations</span></span>](metadata-enumerations.md)
