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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 732523935eec62bffbc15705bc93c97f14c90064
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792723"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="fc2f1-102">CorDebugMDAFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="fc2f1-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="fc2f1-103">Yönetilen hata ayıklama Yardımcısı (MDA) harekete geçirilen iş parçacığı durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc2f1-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc2f1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc2f1-104">Syntax</span></span>  
  
```  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="fc2f1-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fc2f1-105">Members</span></span>  
  
|<span data-ttu-id="fc2f1-106">Üye</span><span class="sxs-lookup"><span data-stu-id="fc2f1-106">Member</span></span>|<span data-ttu-id="fc2f1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc2f1-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="fc2f1-108">MDA harekete geçirildi beri MDA harekete geçirildi iş parçacığı kaymış.</span><span class="sxs-lookup"><span data-stu-id="fc2f1-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc2f1-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc2f1-109">Remarks</span></span>  
 <span data-ttu-id="fc2f1-110">Çağrı yığınını artık burada MDA başlangıçta tetiklendi açıkladığında, iş parçacığının sahip olduğu kabul edildiği *kaymış*.</span><span class="sxs-lookup"><span data-stu-id="fc2f1-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="fc2f1-111">Bu, iş parçacığının yürütülmesini çıkarken geçersiz bir işlem tarafından hazırlanmıştır olağan dışı bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="fc2f1-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc2f1-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc2f1-112">Requirements</span></span>  
 <span data-ttu-id="fc2f1-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc2f1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc2f1-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc2f1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc2f1-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc2f1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc2f1-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc2f1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc2f1-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc2f1-117">See also</span></span>

- [<span data-ttu-id="fc2f1-118">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="fc2f1-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
