---
description: ': ICorDebugMDA arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 8e6e779c58d71b07edc9b63dff72aef728ebe050
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801132"
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="e044f-103">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e044f-103">ICorDebugMDA Interface</span></span>

<span data-ttu-id="e044f-104">Yönetilen bir hata ayıklama yardımcısı (MDA) iletisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e044f-104">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e044f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e044f-105">Methods</span></span>  
  
|<span data-ttu-id="e044f-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e044f-106">Method</span></span>|<span data-ttu-id="e044f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e044f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e044f-108">GetDescription Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e044f-108">GetDescription Method</span></span>](icordebugmda-getdescription-method.md)|<span data-ttu-id="e044f-109">Bu MDA 'ın açıklamasını içeren bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="e044f-109">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="e044f-110">GetFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e044f-110">GetFlags Method</span></span>](icordebugmda-getflags-method.md)|<span data-ttu-id="e044f-111">Bu MDA ile ilişkili bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="e044f-111">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="e044f-112">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e044f-112">GetName Method</span></span>](icordebugmda-getname-method.md)|<span data-ttu-id="e044f-113">Bu MDA 'ın adını içeren bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="e044f-113">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="e044f-114">GetOSThreadId Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e044f-114">GetOSThreadId Method</span></span>](icordebugmda-getosthreadid-method.md)|<span data-ttu-id="e044f-115">Bu MDA 'ın üzerinde yürütüldüğü işletim sistemi iş parçacığı tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="e044f-115">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="e044f-116">GetXML Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e044f-116">GetXML Method</span></span>](icordebugmda-getxml-method.md)|<span data-ttu-id="e044f-117">Bu MDA ile ilişkili tam XML akışını alır.</span><span class="sxs-lookup"><span data-stu-id="e044f-117">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e044f-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e044f-118">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e044f-119">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="e044f-119">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e044f-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e044f-120">Requirements</span></span>  

 <span data-ttu-id="e044f-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e044f-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e044f-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e044f-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e044f-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e044f-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e044f-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e044f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e044f-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e044f-125">See also</span></span>

- [<span data-ttu-id="e044f-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e044f-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e044f-127">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="e044f-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
