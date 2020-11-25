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
ms.openlocfilehash: 1bb99503481d917d41ae00a5ef73c8fa59e2a999
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696459"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="c48e9-102">CorDebugMDAFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c48e9-102">CorDebugMDAFlags Enumeration</span></span>

<span data-ttu-id="c48e9-103">Yönetilen hata ayıklama Yardımcısı 'nın (MDA) harekete geçirildiği iş parçacığının durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c48e9-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c48e9-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="c48e9-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="c48e9-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c48e9-105">Members</span></span>  
  
|<span data-ttu-id="c48e9-106">Üye</span><span class="sxs-lookup"><span data-stu-id="c48e9-106">Member</span></span>|<span data-ttu-id="c48e9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c48e9-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="c48e9-108">Mda 'ın tetiklenme iş parçacığı, MDA ' ın tetiklenmesinden sonra kaymış.</span><span class="sxs-lookup"><span data-stu-id="c48e9-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c48e9-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c48e9-109">Remarks</span></span>  

 <span data-ttu-id="c48e9-110">Çağrı yığını artık MDA ' ın ilk olarak oluşturulduğunu açıkladığında, iş parçacığının *kaymış* olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c48e9-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="c48e9-111">Bu, iş parçacığının çıkış sırasında geçersiz bir işlemin yürütülmesi ile ilgili olarak ortaya çıkan olağan dışı bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="c48e9-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c48e9-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c48e9-112">Requirements</span></span>  

 <span data-ttu-id="c48e9-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c48e9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c48e9-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c48e9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c48e9-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c48e9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c48e9-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c48e9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c48e9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c48e9-117">See also</span></span>

- [<span data-ttu-id="c48e9-118">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="c48e9-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
