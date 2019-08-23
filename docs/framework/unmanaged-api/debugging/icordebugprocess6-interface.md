---
title: ICorDebugProcess6 Arabirimi
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d180d57431e34d872ff077e6bc597175029688e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962715"
---
# <a name="icordebugprocess6-interface"></a><span data-ttu-id="d3099-102">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3099-102">ICorDebugProcess6 Interface</span></span>
<span data-ttu-id="d3099-103">Yerel özel durum ayıklama olayları ve sanal modül bölünmesi içinde kodlanmış yönetilen hata ayıklama olaylarının kodunu çözme gibi özellikleri etkinleştirmek için ICorDebugProcess arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="d3099-103">Logically extends the ICorDebugProcess interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d3099-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d3099-104">Methods</span></span>  
  
|<span data-ttu-id="d3099-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d3099-105">Method</span></span>|<span data-ttu-id="d3099-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3099-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3099-107">DecodeEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3099-107">DecodeEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)|<span data-ttu-id="d3099-108">Özel olarak hazırlanmış yerel özel durum hata ayıklama olaylarının yükünde kapsüllenmiş yönetilen hata ayıklama olaylarının kodunu çözer.</span><span class="sxs-lookup"><span data-stu-id="d3099-108">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>|  
|[<span data-ttu-id="d3099-109">EnableVirtualModuleSplitting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3099-109">EnableVirtualModuleSplitting Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)|<span data-ttu-id="d3099-110">Sanal modül bölmeyi etkinleştirilir veya devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="d3099-110">Enables or disables virtual module splitting.</span></span>|  
|[<span data-ttu-id="d3099-111">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3099-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getcode-method.md)|<span data-ttu-id="d3099-112">Belirli bir kod adresindeki yönetilen kodla ilgili bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="d3099-112">Gets information about the managed code at a particular code address.</span></span>|  
|[<span data-ttu-id="d3099-113">GetExportStepInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3099-113">GetExportStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)|<span data-ttu-id="d3099-114">Yönetilen kodda adım adım yardım için çalışma zamanına aktarılmış işlevler hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3099-114">Provides information on runtime exported functions to help step through managed code.</span></span>|  
|[<span data-ttu-id="d3099-115">MarkDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3099-115">MarkDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-markdebuggerattached-method.md)|<span data-ttu-id="d3099-116">.NET Framework sınıf kitaplığındaki <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> yöntemin döndürdüğü `true`şekilde, hata ayıklayıcı 'nın iç durumunu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="d3099-116">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>|  
|[<span data-ttu-id="d3099-117">ProcessStateChanged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3099-117">ProcessStateChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)|<span data-ttu-id="d3099-118">İşlemin çalıştığını [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) öğesine bildirir.</span><span class="sxs-lookup"><span data-stu-id="d3099-118">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3099-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3099-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3099-120">Arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d3099-120">The interface is available with .NET Native only.</span></span> <span data-ttu-id="d3099-121">.NET Native dışında ICorDebug senaryolarına `QueryInterface` `E_NOINTERFACE` yönelik bir arabirim işaretçisi alma çağrısı yapılmaya çalışılıyor.</span><span class="sxs-lookup"><span data-stu-id="d3099-121">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3099-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3099-122">Requirements</span></span>  
 <span data-ttu-id="d3099-123">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3099-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3099-124">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d3099-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3099-125">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d3099-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3099-126">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3099-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3099-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3099-127">See also</span></span>

- [<span data-ttu-id="d3099-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d3099-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="d3099-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="d3099-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
