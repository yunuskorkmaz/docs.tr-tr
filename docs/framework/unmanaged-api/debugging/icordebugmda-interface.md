---
title: ICorDebugMDA Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a662185bb84e9a66573b43b26ffcd256ecb943f5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909846"
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="7290b-102">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7290b-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="7290b-103">Yönetilen bir hata ayıklama yardımcısı (MDA) iletisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7290b-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7290b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7290b-104">Methods</span></span>  
  
|<span data-ttu-id="7290b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7290b-105">Method</span></span>|<span data-ttu-id="7290b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7290b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7290b-107">GetDescription Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7290b-107">GetDescription Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|<span data-ttu-id="7290b-108">Bu MDA 'ın açıklamasını içeren bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="7290b-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="7290b-109">GetFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7290b-109">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|<span data-ttu-id="7290b-110">Bu MDA ile ilişkili bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="7290b-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="7290b-111">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7290b-111">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|<span data-ttu-id="7290b-112">Bu MDA 'ın adını içeren bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="7290b-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="7290b-113">GetOSThreadId Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7290b-113">GetOSThreadId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|<span data-ttu-id="7290b-114">Bu MDA 'ın üzerinde yürütüldüğü işletim sistemi iş parçacığı tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="7290b-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="7290b-115">GetXML Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7290b-115">GetXML Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|<span data-ttu-id="7290b-116">Bu MDA ile ilişkili tam XML akışını alır.</span><span class="sxs-lookup"><span data-stu-id="7290b-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7290b-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7290b-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7290b-118">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="7290b-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7290b-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7290b-119">Requirements</span></span>  
 <span data-ttu-id="7290b-120">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7290b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7290b-121">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7290b-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7290b-122">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7290b-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7290b-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7290b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7290b-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7290b-124">See also</span></span>

- [<span data-ttu-id="7290b-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7290b-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7290b-126">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="7290b-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
