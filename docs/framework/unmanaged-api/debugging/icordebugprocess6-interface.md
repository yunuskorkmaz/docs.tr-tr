---
title: ICorDebugProcess6 Arabirimi
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
ms.openlocfilehash: ba70bab28eeddad6e3cf3c2b82b196a69ce68647
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732612"
---
# <a name="icordebugprocess6-interface"></a><span data-ttu-id="08549-102">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08549-102">ICorDebugProcess6 Interface</span></span>

<span data-ttu-id="08549-103">Yerel özel durum ayıklama olayları ve sanal modül bölünmesi içinde kodlanmış yönetilen hata ayıklama olaylarının kodunu çözme gibi özellikleri etkinleştirmek için ICorDebugProcess arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="08549-103">Logically extends the ICorDebugProcess interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="08549-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="08549-104">Methods</span></span>  
  
|<span data-ttu-id="08549-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="08549-105">Method</span></span>|<span data-ttu-id="08549-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08549-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="08549-107">DecodeEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08549-107">DecodeEvent Method</span></span>](icordebugprocess6-decodeevent-method.md)|<span data-ttu-id="08549-108">Özel olarak hazırlanmış yerel özel durum hata ayıklama olaylarının yükünde kapsüllenmiş yönetilen hata ayıklama olaylarının kodunu çözer.</span><span class="sxs-lookup"><span data-stu-id="08549-108">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>|  
|[<span data-ttu-id="08549-109">EnableVirtualModuleSplitting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08549-109">EnableVirtualModuleSplitting Method</span></span>](icordebugprocess6-enablevirtualmodulesplitting-method.md)|<span data-ttu-id="08549-110">Sanal modül bölmeyi etkinleştirilir veya devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="08549-110">Enables or disables virtual module splitting.</span></span>|  
|[<span data-ttu-id="08549-111">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08549-111">GetCode Method</span></span>](icordebugprocess6-getcode-method.md)|<span data-ttu-id="08549-112">Belirli bir kod adresindeki yönetilen kodla ilgili bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="08549-112">Gets information about the managed code at a particular code address.</span></span>|  
|[<span data-ttu-id="08549-113">GetExportStepInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08549-113">GetExportStepInfo Method</span></span>](icordebugprocess6-getexportstepinfo-method.md)|<span data-ttu-id="08549-114">Yönetilen kodda adım adım yardım için çalışma zamanına aktarılmış işlevler hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="08549-114">Provides information on runtime exported functions to help step through managed code.</span></span>|  
|[<span data-ttu-id="08549-115">MarkDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08549-115">MarkDebuggerAttached Method</span></span>](icordebugprocess6-markdebuggerattached-method.md)|<span data-ttu-id="08549-116"><xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType>.NET Framework sınıf kitaplığındaki yöntemin döndürdüğü şekilde, hata ayıklayıcı 'nın iç durumunu değiştirir `true` .</span><span class="sxs-lookup"><span data-stu-id="08549-116">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>|  
|[<span data-ttu-id="08549-117">ProcessStateChanged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08549-117">ProcessStateChanged Method</span></span>](icordebugprocess6-processstatechanged-method.md)|<span data-ttu-id="08549-118">İşlemin çalıştığını [ICorDebug](icordebug-interface.md) öğesine bildirir.</span><span class="sxs-lookup"><span data-stu-id="08549-118">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08549-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08549-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08549-120">Arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="08549-120">The interface is available with .NET Native only.</span></span> <span data-ttu-id="08549-121">`QueryInterface` `E_NOINTERFACE` .NET Native dışında ICorDebug senaryolarına yönelik bir arabirim işaretçisi alma çağrısı yapılmaya çalışılıyor.</span><span class="sxs-lookup"><span data-stu-id="08549-121">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08549-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08549-122">Requirements</span></span>  

 <span data-ttu-id="08549-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08549-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08549-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="08549-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08549-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="08549-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08549-126">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08549-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08549-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08549-127">See also</span></span>

- [<span data-ttu-id="08549-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="08549-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="08549-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="08549-129">Debugging</span></span>](index.md)
