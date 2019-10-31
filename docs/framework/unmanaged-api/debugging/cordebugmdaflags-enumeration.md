---
title: CorDebugMDAFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugMDAFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMDAFlags
helpviewer_keywords:
- CorDebugMDAFlags enumeration [.NET Framework debugging]
ms.assetid: 7c0c92fe-8bd2-477f-b307-aca0143732ca
topic_type:
- apiref
ms.openlocfilehash: c7af194351290ad937e40a2fc8b960c2c242629c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132804"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="612d6-102">CorDebugMDAFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="612d6-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="612d6-103">Yönetilen hata ayıklama Yardımcısı 'nın (MDA) harekete geçirildiği iş parçacığının durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="612d6-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="612d6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="612d6-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="612d6-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="612d6-105">Members</span></span>  
  
|<span data-ttu-id="612d6-106">Üye</span><span class="sxs-lookup"><span data-stu-id="612d6-106">Member</span></span>|<span data-ttu-id="612d6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="612d6-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="612d6-108">Mda 'ın tetiklenme iş parçacığı, MDA ' ın tetiklenmesinden sonra kaymış.</span><span class="sxs-lookup"><span data-stu-id="612d6-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="612d6-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="612d6-109">Remarks</span></span>  
 <span data-ttu-id="612d6-110">Çağrı yığını artık MDA ' ın ilk olarak oluşturulduğunu açıkladığında, iş parçacığının *kaymış*olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="612d6-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="612d6-111">Bu, iş parçacığının çıkış sırasında geçersiz bir işlemin yürütülmesi ile ilgili olarak ortaya çıkan olağan dışı bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="612d6-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="612d6-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="612d6-112">Requirements</span></span>  
 <span data-ttu-id="612d6-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="612d6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="612d6-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="612d6-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="612d6-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="612d6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="612d6-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="612d6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="612d6-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="612d6-117">See also</span></span>

- [<span data-ttu-id="612d6-118">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="612d6-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
