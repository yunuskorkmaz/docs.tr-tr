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
ms.openlocfilehash: 97b28c961f43388679615ac0d5b19c4c69df1e3d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444253"
---
# <a name="ceesectionattr-enumeration"></a><span data-ttu-id="75955-102">CeeSectionAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="75955-102">CeeSectionAttr Enumeration</span></span>
<span data-ttu-id="75955-103">[ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) arabirimi tarafından kullanılmak üzere bir bölümün özniteliklerini belirten değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="75955-103">Provides values that specify attributes of a section for use by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75955-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75955-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="75955-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="75955-105">Members</span></span>  
  
|<span data-ttu-id="75955-106">Üye</span><span class="sxs-lookup"><span data-stu-id="75955-106">Member</span></span>|<span data-ttu-id="75955-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75955-107">Description</span></span>|  
|------------|-----------------|  
|`sdNone`|<span data-ttu-id="75955-108">Bölümünde hiç öznitelik yok.</span><span class="sxs-lookup"><span data-stu-id="75955-108">Section has no attributes.</span></span>|  
|`sdReadOnly`|<span data-ttu-id="75955-109">Bölüm yalnızca okunabilir, güncelleştirilmemiş, başlatılmamış verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="75955-109">Section contains initialized data that can be only read, not updated.</span></span>|  
|`sdReadWrite`|<span data-ttu-id="75955-110">Bölüm, okunabilecek veya güncelleştirilebilen başlatılmış verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="75955-110">Section contains initialized data that can be read or updated.</span></span>|  
|`sdExecute`|<span data-ttu-id="75955-111">Bölüm, okunve yürütülmesine izin verilen yürütülebilir kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="75955-111">Section contains executable code that is allowed to be read and executed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="75955-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75955-112">Requirements</span></span>  
 <span data-ttu-id="75955-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75955-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75955-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="75955-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="75955-115">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="75955-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="75955-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75955-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75955-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75955-117">See also</span></span>

- [<span data-ttu-id="75955-118">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="75955-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
