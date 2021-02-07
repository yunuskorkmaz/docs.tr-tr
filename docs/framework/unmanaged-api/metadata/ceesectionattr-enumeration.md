---
description: 'Daha fazla bilgi edinin: CeeSectionAttr numaralandırması'
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
ms.openlocfilehash: 13cfb635aaa606905745146d7c3caae3f9162e91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678880"
---
# <a name="ceesectionattr-enumeration"></a><span data-ttu-id="02b45-103">CeeSectionAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="02b45-103">CeeSectionAttr Enumeration</span></span>

<span data-ttu-id="02b45-104">[ICeeGen](iceegen-interface.md) arabirimi tarafından kullanılmak üzere bir bölümün özniteliklerini belirten değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="02b45-104">Provides values that specify attributes of a section for use by the [ICeeGen](iceegen-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02b45-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="02b45-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="02b45-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="02b45-106">Members</span></span>  
  
|<span data-ttu-id="02b45-107">Üye</span><span class="sxs-lookup"><span data-stu-id="02b45-107">Member</span></span>|<span data-ttu-id="02b45-108">Description</span><span class="sxs-lookup"><span data-stu-id="02b45-108">Description</span></span>|  
|------------|-----------------|  
|`sdNone`|<span data-ttu-id="02b45-109">Bölümünde hiç öznitelik yok.</span><span class="sxs-lookup"><span data-stu-id="02b45-109">Section has no attributes.</span></span>|  
|`sdReadOnly`|<span data-ttu-id="02b45-110">Bölüm yalnızca okunabilir, güncelleştirilmemiş, başlatılmamış verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="02b45-110">Section contains initialized data that can be only read, not updated.</span></span>|  
|`sdReadWrite`|<span data-ttu-id="02b45-111">Bölüm, okunabilecek veya güncelleştirilebilen başlatılmış verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="02b45-111">Section contains initialized data that can be read or updated.</span></span>|  
|`sdExecute`|<span data-ttu-id="02b45-112">Bölüm, okunve yürütülmesine izin verilen yürütülebilir kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="02b45-112">Section contains executable code that is allowed to be read and executed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="02b45-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="02b45-113">Requirements</span></span>  

 <span data-ttu-id="02b45-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02b45-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02b45-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="02b45-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="02b45-116">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="02b45-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="02b45-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02b45-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02b45-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02b45-118">See also</span></span>

- [<span data-ttu-id="02b45-119">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="02b45-119">Metadata Enumerations</span></span>](metadata-enumerations.md)
