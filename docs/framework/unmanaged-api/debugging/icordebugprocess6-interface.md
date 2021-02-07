---
description: 'Daha fazla bilgi edinin: ICorDebugProcess6 Interface'
title: ICorDebugProcess6 Arabirimi
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
ms.openlocfilehash: f303670d0667a80507bc623f9af037759fdde463
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691464"
---
# <a name="icordebugprocess6-interface"></a><span data-ttu-id="bd5c0-103">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bd5c0-103">ICorDebugProcess6 Interface</span></span>

<span data-ttu-id="bd5c0-104">Yerel özel durum ayıklama olayları ve sanal modül bölünmesi içinde kodlanmış yönetilen hata ayıklama olaylarının kodunu çözme gibi özellikleri etkinleştirmek için ICorDebugProcess arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="bd5c0-104">Logically extends the ICorDebugProcess interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bd5c0-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bd5c0-105">Methods</span></span>  
  
|<span data-ttu-id="bd5c0-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bd5c0-106">Method</span></span>|<span data-ttu-id="bd5c0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd5c0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bd5c0-108">DecodeEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd5c0-108">DecodeEvent Method</span></span>](icordebugprocess6-decodeevent-method.md)|<span data-ttu-id="bd5c0-109">Özel olarak hazırlanmış yerel özel durum hata ayıklama olaylarının yükünde kapsüllenmiş yönetilen hata ayıklama olaylarının kodunu çözer.</span><span class="sxs-lookup"><span data-stu-id="bd5c0-109">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>|  
|[<span data-ttu-id="bd5c0-110">EnableVirtualModuleSplitting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd5c0-110">EnableVirtualModuleSplitting Method</span></span>](icordebugprocess6-enablevirtualmodulesplitting-method.md)|<span data-ttu-id="bd5c0-111">Sanal modül bölmeyi etkinleştirilir veya devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="bd5c0-111">Enables or disables virtual module splitting.</span></span>|  
|[<span data-ttu-id="bd5c0-112">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd5c0-112">GetCode Method</span></span>](icordebugprocess6-getcode-method.md)|<span data-ttu-id="bd5c0-113">Belirli bir kod adresindeki yönetilen kodla ilgili bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="bd5c0-113">Gets information about the managed code at a particular code address.</span></span>|  
|[<span data-ttu-id="bd5c0-114">GetExportStepInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd5c0-114">GetExportStepInfo Method</span></span>](icordebugprocess6-getexportstepinfo-method.md)|<span data-ttu-id="bd5c0-115">Yönetilen kodda adım adım yardım için çalışma zamanına aktarılmış işlevler hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd5c0-115">Provides information on runtime exported functions to help step through managed code.</span></span>|  
|[<span data-ttu-id="bd5c0-116">MarkDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd5c0-116">MarkDebuggerAttached Method</span></span>](icordebugprocess6-markdebuggerattached-method.md)|<span data-ttu-id="bd5c0-117"><xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType>.NET Framework sınıf kitaplığındaki yöntemin döndürdüğü şekilde, hata ayıklayıcı 'nın iç durumunu değiştirir `true` .</span><span class="sxs-lookup"><span data-stu-id="bd5c0-117">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>|  
|[<span data-ttu-id="bd5c0-118">ProcessStateChanged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd5c0-118">ProcessStateChanged Method</span></span>](icordebugprocess6-processstatechanged-method.md)|<span data-ttu-id="bd5c0-119">İşlemin çalıştığını [ICorDebug](icordebug-interface.md) öğesine bildirir.</span><span class="sxs-lookup"><span data-stu-id="bd5c0-119">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd5c0-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bd5c0-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd5c0-121">Arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bd5c0-121">The interface is available with .NET Native only.</span></span> <span data-ttu-id="bd5c0-122">`QueryInterface` `E_NOINTERFACE` .NET Native dışında ICorDebug senaryolarına yönelik bir arabirim işaretçisi alma çağrısı yapılmaya çalışılıyor.</span><span class="sxs-lookup"><span data-stu-id="bd5c0-122">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd5c0-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bd5c0-123">Requirements</span></span>  

 <span data-ttu-id="bd5c0-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd5c0-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd5c0-125">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bd5c0-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd5c0-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bd5c0-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd5c0-127">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd5c0-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd5c0-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd5c0-128">See also</span></span>

- [<span data-ttu-id="bd5c0-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bd5c0-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="bd5c0-130">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="bd5c0-130">Debugging</span></span>](index.md)
