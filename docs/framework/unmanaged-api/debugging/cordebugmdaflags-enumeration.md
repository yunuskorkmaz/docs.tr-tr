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
ms.openlocfilehash: 34a66a8afa118ecaaaeea0b7b78daaadf1da7509
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778269"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="21dac-102">CorDebugMDAFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="21dac-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="21dac-103">Yönetilen hata ayıklama Yardımcısı 'nın (MDA) harekete geçirildiği iş parçacığının durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="21dac-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21dac-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21dac-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="21dac-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="21dac-105">Members</span></span>  
  
|<span data-ttu-id="21dac-106">Üye</span><span class="sxs-lookup"><span data-stu-id="21dac-106">Member</span></span>|<span data-ttu-id="21dac-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21dac-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="21dac-108">Mda 'ın tetiklenme iş parçacığı, MDA ' ın tetiklenmesinden sonra kaymış.</span><span class="sxs-lookup"><span data-stu-id="21dac-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21dac-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21dac-109">Remarks</span></span>  
 <span data-ttu-id="21dac-110">Çağrı yığını artık MDA ' ın ilk olarak oluşturulduğunu açıkladığında, iş parçacığının *kaymış*olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="21dac-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="21dac-111">Bu, iş parçacığının çıkış sırasında geçersiz bir işlemin yürütülmesi ile ilgili olarak ortaya çıkan olağan dışı bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="21dac-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21dac-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21dac-112">Requirements</span></span>  
 <span data-ttu-id="21dac-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21dac-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21dac-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="21dac-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21dac-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="21dac-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21dac-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21dac-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21dac-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21dac-117">See also</span></span>

- [<span data-ttu-id="21dac-118">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="21dac-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
