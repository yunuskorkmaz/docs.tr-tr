---
title: COR_PUB_ENUMPROCESS Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PUB_ENUMPROCESS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_PUB_ENUMPROCESS
helpviewer_keywords:
- COR_PUB_ENUMPROCESS enumeration [.NET Framework debugging]
ms.assetid: 5d3ada6e-feea-47da-a7ed-b664107c137f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eab5fc13b74d8af4f0baaa3953c5c73ea255bfe6
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274014"
---
# <a name="cor_pub_enumprocess-enumeration"></a><span data-ttu-id="62817-102">COR_PUB_ENUMPROCESS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="62817-102">COR_PUB_ENUMPROCESS Enumeration</span></span>
<span data-ttu-id="62817-103">Numaralandırılacak işlemin türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="62817-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62817-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62817-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="62817-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="62817-105">Members</span></span>  
  
|<span data-ttu-id="62817-106">Üye adı</span><span class="sxs-lookup"><span data-stu-id="62817-106">Member name</span></span>|<span data-ttu-id="62817-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62817-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="62817-108">Yönetilen bir işlem.</span><span class="sxs-lookup"><span data-stu-id="62817-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62817-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62817-109">Remarks</span></span>  
 <span data-ttu-id="62817-110">Yönetilmeyen hata ayıklama API 'sinin geçerli sürümü yalnızca yönetilen işlemi numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="62817-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62817-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="62817-111">Requirements</span></span>  
 <span data-ttu-id="62817-112">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62817-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62817-113">**Üst bilgi** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="62817-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="62817-114">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="62817-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62817-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62817-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62817-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62817-116">See also</span></span>

- [<span data-ttu-id="62817-117">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="62817-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
