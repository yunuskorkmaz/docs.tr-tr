---
title: CeeSectionAttr Numaralandırması
ms.date: 03/30/2017
api_name:
- CeeSectionAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionAttr
helpviewer_keywords:
- CeeSectionAttr enumeration [.NET Framework metadata]
ms.assetid: 0db51881-b869-4677-a715-1726a9216489
topic_type:
- apiref
ms.openlocfilehash: 6da8a111f716906e403d85bc0b1a29eba7238100
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006070"
---
# <a name="ceesectionattr-enumeration"></a><span data-ttu-id="44d0d-102">CeeSectionAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="44d0d-102">CeeSectionAttr Enumeration</span></span>
<span data-ttu-id="44d0d-103">[ICeeGen](iceegen-interface.md) arabirimi tarafından kullanılmak üzere bir bölümün özniteliklerini belirten değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="44d0d-103">Provides values that specify attributes of a section for use by the [ICeeGen](iceegen-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44d0d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44d0d-104">Syntax</span></span>  
  
```cpp  
typedef enum  {  
    sdNone      = 0,  
    sdReadOnly  = IMAGE_SCN_CNT_INITIALIZED_DATA |  
                  IMAGE_SCN_MEM_READ,  
    sdReadWrite = sdReadOnly | IMAGE_SCN_MEM_WRITE,  
    sdExecute   = IMAGE_SCN_MEM_READ | IMAGE_SCN_CNT_CODE |  
                  IMAGE_SCN_MEM_EXECUTE  
} CeeSectionAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="44d0d-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="44d0d-105">Members</span></span>  
  
|<span data-ttu-id="44d0d-106">Üye</span><span class="sxs-lookup"><span data-stu-id="44d0d-106">Member</span></span>|<span data-ttu-id="44d0d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44d0d-107">Description</span></span>|  
|------------|-----------------|  
|`sdNone`|<span data-ttu-id="44d0d-108">Bölümünde hiç öznitelik yok.</span><span class="sxs-lookup"><span data-stu-id="44d0d-108">Section has no attributes.</span></span>|  
|`sdReadOnly`|<span data-ttu-id="44d0d-109">Bölüm yalnızca okunabilir, güncelleştirilmemiş, başlatılmamış verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="44d0d-109">Section contains initialized data that can be only read, not updated.</span></span>|  
|`sdReadWrite`|<span data-ttu-id="44d0d-110">Bölüm, okunabilecek veya güncelleştirilebilen başlatılmış verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="44d0d-110">Section contains initialized data that can be read or updated.</span></span>|  
|`sdExecute`|<span data-ttu-id="44d0d-111">Bölüm, okunve yürütülmesine izin verilen yürütülebilir kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="44d0d-111">Section contains executable code that is allowed to be read and executed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="44d0d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="44d0d-112">Requirements</span></span>  
 <span data-ttu-id="44d0d-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44d0d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44d0d-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="44d0d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="44d0d-115">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="44d0d-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="44d0d-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44d0d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44d0d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44d0d-117">See also</span></span>

- [<span data-ttu-id="44d0d-118">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="44d0d-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
