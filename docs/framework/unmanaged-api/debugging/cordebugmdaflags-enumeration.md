---
description: 'Bu konuda daha fazla bilgi edinin: CorDebugMDAFlags numaralandırması'
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
ms.openlocfilehash: d7e9178d76286b112035729e997b1f68e2a93fb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661941"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="3a830-103">CorDebugMDAFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3a830-103">CorDebugMDAFlags Enumeration</span></span>

<span data-ttu-id="3a830-104">Yönetilen hata ayıklama Yardımcısı 'nın (MDA) harekete geçirildiği iş parçacığının durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3a830-104">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a830-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3a830-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="3a830-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3a830-106">Members</span></span>  
  
|<span data-ttu-id="3a830-107">Üye</span><span class="sxs-lookup"><span data-stu-id="3a830-107">Member</span></span>|<span data-ttu-id="3a830-108">Description</span><span class="sxs-lookup"><span data-stu-id="3a830-108">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="3a830-109">Mda 'ın tetiklenme iş parçacığı, MDA ' ın tetiklenmesinden sonra kaymış.</span><span class="sxs-lookup"><span data-stu-id="3a830-109">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a830-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3a830-110">Remarks</span></span>  

 <span data-ttu-id="3a830-111">Çağrı yığını artık MDA ' ın ilk olarak oluşturulduğunu açıkladığında, iş parçacığının *kaymış* olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="3a830-111">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="3a830-112">Bu, iş parçacığının çıkış sırasında geçersiz bir işlemin yürütülmesi ile ilgili olarak ortaya çıkan olağan dışı bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="3a830-112">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a830-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3a830-113">Requirements</span></span>  

 <span data-ttu-id="3a830-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a830-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a830-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3a830-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a830-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3a830-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a830-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a830-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a830-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a830-118">See also</span></span>

- [<span data-ttu-id="3a830-119">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="3a830-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
