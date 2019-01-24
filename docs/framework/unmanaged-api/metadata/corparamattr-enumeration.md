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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d07c6de47038d5c52d76ad8ca8e0a5684551d59
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491473"
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="e91c1-102">CorParamAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e91c1-102">CorParamAttr Enumeration</span></span>
<span data-ttu-id="e91c1-103">Bir yöntem parametresi meta verileri tanımlayan değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="e91c1-103">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e91c1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e91c1-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="e91c1-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e91c1-105">Members</span></span>  
  
|<span data-ttu-id="e91c1-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e91c1-106">Member</span></span>|<span data-ttu-id="e91c1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e91c1-107">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="e91c1-108">Yöntem çağrısına parametre geçirildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e91c1-108">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="e91c1-109">Parametre yöntemden dönüş geçirildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e91c1-109">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="e91c1-110">Parametre isteğe bağlı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e91c1-110">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="e91c1-111">İç kullanım için ortak dil çalışma zamanı tarafından ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="e91c1-111">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="e91c1-112">Parametre bir varsayılan değer olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e91c1-112">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="e91c1-113">Parametre bilgisi sıralama olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e91c1-113">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="e91c1-114">Kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="e91c1-114">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e91c1-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e91c1-115">Requirements</span></span>  
 <span data-ttu-id="e91c1-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e91c1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e91c1-117">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="e91c1-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e91c1-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e91c1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e91c1-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e91c1-119">See also</span></span>
- [<span data-ttu-id="e91c1-120">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="e91c1-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
