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
ms.openlocfilehash: a147aee1ebba57b86dbbf8a7648456b8d7494936
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793191"
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="34c3f-102">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="34c3f-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="34c3f-103">Yönetilen bir hata ayıklama yardımcısı (MDA) iletisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="34c3f-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="34c3f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="34c3f-104">Methods</span></span>  
  
|<span data-ttu-id="34c3f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="34c3f-105">Method</span></span>|<span data-ttu-id="34c3f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34c3f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="34c3f-107">GetDescription Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34c3f-107">GetDescription Method</span></span>](icordebugmda-getdescription-method.md)|<span data-ttu-id="34c3f-108">Bu MDA 'ın açıklamasını içeren bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="34c3f-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="34c3f-109">GetFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34c3f-109">GetFlags Method</span></span>](icordebugmda-getflags-method.md)|<span data-ttu-id="34c3f-110">Bu MDA ile ilişkili bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="34c3f-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="34c3f-111">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34c3f-111">GetName Method</span></span>](icordebugmda-getname-method.md)|<span data-ttu-id="34c3f-112">Bu MDA 'ın adını içeren bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="34c3f-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="34c3f-113">GetOSThreadId Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34c3f-113">GetOSThreadId Method</span></span>](icordebugmda-getosthreadid-method.md)|<span data-ttu-id="34c3f-114">Bu MDA 'ın üzerinde yürütüldüğü işletim sistemi iş parçacığı tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="34c3f-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="34c3f-115">GetXML Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34c3f-115">GetXML Method</span></span>](icordebugmda-getxml-method.md)|<span data-ttu-id="34c3f-116">Bu MDA ile ilişkili tam XML akışını alır.</span><span class="sxs-lookup"><span data-stu-id="34c3f-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34c3f-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34c3f-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34c3f-118">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="34c3f-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34c3f-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34c3f-119">Requirements</span></span>  
 <span data-ttu-id="34c3f-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34c3f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34c3f-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="34c3f-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34c3f-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="34c3f-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34c3f-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34c3f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34c3f-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34c3f-124">See also</span></span>

- [<span data-ttu-id="34c3f-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="34c3f-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="34c3f-126">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="34c3f-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
