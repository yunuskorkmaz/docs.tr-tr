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
ms.openlocfilehash: 97f62b082db11a5f0bb930e33cb47acef76e7a04
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906312"
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="1580b-102">CorParamAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="1580b-102">CorParamAttr Enumeration</span></span>
<span data-ttu-id="1580b-103">Bir yöntem parametresi meta verileri tanımlayan değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="1580b-103">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1580b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1580b-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="1580b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1580b-105">Members</span></span>  
  
|<span data-ttu-id="1580b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="1580b-106">Member</span></span>|<span data-ttu-id="1580b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1580b-107">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="1580b-108">Yöntem çağrısına parametre geçirildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1580b-108">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="1580b-109">Parametre yöntemden dönüş geçirildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1580b-109">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="1580b-110">Parametre isteğe bağlı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1580b-110">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="1580b-111">İç kullanım için ortak dil çalışma zamanı tarafından ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="1580b-111">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="1580b-112">Parametre bir varsayılan değer olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1580b-112">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="1580b-113">Parametre bilgisi sıralama olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1580b-113">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="1580b-114">Kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="1580b-114">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1580b-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1580b-115">Requirements</span></span>  
 <span data-ttu-id="1580b-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1580b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1580b-117">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="1580b-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="1580b-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1580b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1580b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1580b-119">See also</span></span>

- [<span data-ttu-id="1580b-120">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="1580b-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
