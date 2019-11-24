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
# <a name="corparamattr-enumeration"></a><span data-ttu-id="b8774-102">CorParamAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b8774-102">CorParamAttr Enumeration</span></span>
<span data-ttu-id="b8774-103">Contains values that describe the metadata of a method parameter.</span><span class="sxs-lookup"><span data-stu-id="b8774-103">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8774-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8774-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="b8774-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b8774-105">Members</span></span>  
  
|<span data-ttu-id="b8774-106">Üye</span><span class="sxs-lookup"><span data-stu-id="b8774-106">Member</span></span>|<span data-ttu-id="b8774-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8774-107">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="b8774-108">Specifies that the parameter is passed into the method call.</span><span class="sxs-lookup"><span data-stu-id="b8774-108">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="b8774-109">Specifies that the parameter is passed from the method return.</span><span class="sxs-lookup"><span data-stu-id="b8774-109">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="b8774-110">Specifies that the parameter is optional.</span><span class="sxs-lookup"><span data-stu-id="b8774-110">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="b8774-111">Reserved for internal use by the common language runtime.</span><span class="sxs-lookup"><span data-stu-id="b8774-111">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="b8774-112">Specifies that the parameter has a default value.</span><span class="sxs-lookup"><span data-stu-id="b8774-112">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="b8774-113">Specifies that the parameter has marshaling information.</span><span class="sxs-lookup"><span data-stu-id="b8774-113">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="b8774-114">Unused.</span><span class="sxs-lookup"><span data-stu-id="b8774-114">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b8774-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b8774-115">Requirements</span></span>  
 <span data-ttu-id="b8774-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8774-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8774-117">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="b8774-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b8774-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8774-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8774-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8774-119">See also</span></span>

- [<span data-ttu-id="b8774-120">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="b8774-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
