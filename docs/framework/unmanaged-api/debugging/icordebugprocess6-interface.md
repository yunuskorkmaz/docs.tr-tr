---
title: ICorDebugProcess6 Arabirimi
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 518c6ec99e4062bf8432809d3472baa395017da3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147270"
---
# <a name="icordebugprocess6-interface"></a><span data-ttu-id="fa82d-102">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa82d-102">ICorDebugProcess6 Interface</span></span>
<span data-ttu-id="fa82d-103">Icordebugprocess arabirimi yerel özel durum hata ayıklama olaylarını ve sanal modül bölme kodlanmış yönetilen hata ayıklama olaylarını kod çözme gibi özellikleri etkinleştirmek için mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="fa82d-103">Logically extends the ICorDebugProcess interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fa82d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fa82d-104">Methods</span></span>  
  
|<span data-ttu-id="fa82d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fa82d-105">Method</span></span>|<span data-ttu-id="fa82d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa82d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fa82d-107">DecodeEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa82d-107">DecodeEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)|<span data-ttu-id="fa82d-108">Özel olarak hazırlanmış yerel özel durum hata ayıklama olaylarını yükteki kapsüllenmiş yönetilen hata ayıklama olaylarını kodunu çözer.</span><span class="sxs-lookup"><span data-stu-id="fa82d-108">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>|  
|[<span data-ttu-id="fa82d-109">EnableVirtualModuleSplitting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa82d-109">EnableVirtualModuleSplitting Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)|<span data-ttu-id="fa82d-110">Etkinleştirir veya sanal modül bölme devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="fa82d-110">Enables or disables virtual module splitting.</span></span>|  
|[<span data-ttu-id="fa82d-111">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa82d-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getcode-method.md)|<span data-ttu-id="fa82d-112">Belirli kod adresinde yönetilen kodu hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="fa82d-112">Gets information about the managed code at a particular code address.</span></span>|  
|[<span data-ttu-id="fa82d-113">GetExportStepInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa82d-113">GetExportStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)|<span data-ttu-id="fa82d-114">Yönetilen kodu adımlayın yardımcı olmak için çalışma zamanı dışa aktarılan işlevleri hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa82d-114">Provides information on runtime exported functions to help step through managed code.</span></span>|  
|[<span data-ttu-id="fa82d-115">MarkDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa82d-115">MarkDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-markdebuggerattached-method.md)|<span data-ttu-id="fa82d-116">Debugee iç durumunu değiştiren böylece <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> yöntem .NET Framework sınıf kitaplığındaki döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="fa82d-116">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>|  
|[<span data-ttu-id="fa82d-117">ProcessStateChanged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa82d-117">ProcessStateChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)|<span data-ttu-id="fa82d-118">Bildirir [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , işlem çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="fa82d-118">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa82d-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa82d-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa82d-120">Arabirimi yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fa82d-120">The interface is available with .NET Native only.</span></span> <span data-ttu-id="fa82d-121">Arama girişimi `QueryInterface` bir arabirim işaretçisini almak için döndürür `E_NOINTERFACE` .NET Native dışında Icordebug senaryolar için.</span><span class="sxs-lookup"><span data-stu-id="fa82d-121">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa82d-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa82d-122">Requirements</span></span>  
 <span data-ttu-id="fa82d-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa82d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa82d-124">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa82d-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa82d-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa82d-125">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="fa82d-126">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="fa82d-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fa82d-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa82d-127">See also</span></span>

- [<span data-ttu-id="fa82d-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fa82d-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="fa82d-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="fa82d-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
