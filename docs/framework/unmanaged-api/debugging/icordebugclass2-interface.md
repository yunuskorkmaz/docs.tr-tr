---
title: ICorDebugClass2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugClass2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2
helpviewer_keywords:
- ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 5416de70-43f2-4cdf-a11f-d570759c9c0c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f6a8b0ead430ffdd0e4e30cacae54d68fa9d730
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969257"
---
# <a name="icordebugclass2-interface"></a><span data-ttu-id="cf27c-102">ICorDebugClass2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf27c-102">ICorDebugClass2 Interface</span></span>

<span data-ttu-id="cf27c-103">Bir genel sınıfı veya türünde <xref:System.Type>bir yöntem parametresi olan bir sınıfı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cf27c-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="cf27c-104">Bu arabirim [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)'ı genişletir.</span><span class="sxs-lookup"><span data-stu-id="cf27c-104">This interface extends [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cf27c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cf27c-105">Methods</span></span>  
  
|<span data-ttu-id="cf27c-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cf27c-106">Method</span></span>|<span data-ttu-id="cf27c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf27c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cf27c-108">GetParameterizedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf27c-108">GetParameterizedType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="cf27c-109">Bu sınıf için tür bildirimini alır.</span><span class="sxs-lookup"><span data-stu-id="cf27c-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="cf27c-110">SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf27c-110">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="cf27c-111">Bu sınıfın her bir yöntemi için, yöntemin Kullanıcı tanımlı kod olup olmadığını belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cf27c-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf27c-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf27c-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf27c-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="cf27c-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf27c-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf27c-114">Requirements</span></span>  
 <span data-ttu-id="cf27c-115">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf27c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf27c-116">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cf27c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf27c-117">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cf27c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf27c-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf27c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf27c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf27c-119">See also</span></span>

- [<span data-ttu-id="cf27c-120">ICorDebugClass arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf27c-120">ICorDebugClass Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)
- [<span data-ttu-id="cf27c-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cf27c-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
