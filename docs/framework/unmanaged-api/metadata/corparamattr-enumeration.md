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
ms.openlocfilehash: 1d58c8c0413346536c3e61e67ca0077c08c2b387
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436492"
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="0bb4d-102">CorParamAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="0bb4d-102">CorParamAttr Enumeration</span></span>
<span data-ttu-id="0bb4d-103">Bir yöntem parametresinin meta verilerini tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0bb4d-103">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bb4d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0bb4d-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="0bb4d-105">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="0bb4d-105">Members</span></span>  
  
|<span data-ttu-id="0bb4d-106">Üyesi</span><span class="sxs-lookup"><span data-stu-id="0bb4d-106">Member</span></span>|<span data-ttu-id="0bb4d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0bb4d-107">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="0bb4d-108">Parametrenin yöntem çağrısına geçtiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bb4d-108">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="0bb4d-109">Parametrenin dönüş yönteminden geçtiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bb4d-109">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="0bb4d-110">Parametrenin isteğe bağlı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bb4d-110">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="0bb4d-111">Ortak dil çalışma zamanı tarafından iç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0bb4d-111">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="0bb4d-112">Parametrenin varsayılan bir değere sahip olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bb4d-112">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="0bb4d-113">Parametrenin sıralama bilgilerine sahip olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bb4d-113">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="0bb4d-114">Kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="0bb4d-114">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0bb4d-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0bb4d-115">Requirements</span></span>  
 <span data-ttu-id="0bb4d-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bb4d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bb4d-117">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="0bb4d-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="0bb4d-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bb4d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bb4d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0bb4d-119">See also</span></span>

- [<span data-ttu-id="0bb4d-120">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="0bb4d-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
