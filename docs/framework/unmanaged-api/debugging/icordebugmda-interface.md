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
ms.openlocfilehash: d711f36b4e2071dac9458a023e1d3cf4743e77b3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212639"
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="87771-102">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87771-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="87771-103">Yönetilen bir hata ayıklama yardımcısı (MDA) iletisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="87771-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="87771-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="87771-104">Methods</span></span>  
  
|<span data-ttu-id="87771-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="87771-105">Method</span></span>|<span data-ttu-id="87771-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87771-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="87771-107">GetDescription Yöntemi</span><span class="sxs-lookup"><span data-stu-id="87771-107">GetDescription Method</span></span>](icordebugmda-getdescription-method.md)|<span data-ttu-id="87771-108">Bu MDA 'ın açıklamasını içeren bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="87771-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="87771-109">GetFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="87771-109">GetFlags Method</span></span>](icordebugmda-getflags-method.md)|<span data-ttu-id="87771-110">Bu MDA ile ilişkili bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="87771-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="87771-111">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="87771-111">GetName Method</span></span>](icordebugmda-getname-method.md)|<span data-ttu-id="87771-112">Bu MDA 'ın adını içeren bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="87771-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="87771-113">GetOSThreadId Yöntemi</span><span class="sxs-lookup"><span data-stu-id="87771-113">GetOSThreadId Method</span></span>](icordebugmda-getosthreadid-method.md)|<span data-ttu-id="87771-114">Bu MDA 'ın üzerinde yürütüldüğü işletim sistemi iş parçacığı tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="87771-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="87771-115">GetXML Yöntemi</span><span class="sxs-lookup"><span data-stu-id="87771-115">GetXML Method</span></span>](icordebugmda-getxml-method.md)|<span data-ttu-id="87771-116">Bu MDA ile ilişkili tam XML akışını alır.</span><span class="sxs-lookup"><span data-stu-id="87771-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87771-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87771-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87771-118">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="87771-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87771-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87771-119">Requirements</span></span>  
 <span data-ttu-id="87771-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87771-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87771-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="87771-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87771-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="87771-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87771-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87771-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87771-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87771-124">See also</span></span>

- [<span data-ttu-id="87771-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="87771-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="87771-126">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="87771-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
