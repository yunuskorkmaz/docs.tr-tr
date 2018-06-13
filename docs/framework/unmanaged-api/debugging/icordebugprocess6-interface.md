---
title: ICorDebugProcess6 Arabirimi
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 103a37d7549d7ec18617b74c777506b3ad225a18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422870"
---
# <a name="icordebugprocess6-interface"></a><span data-ttu-id="1d639-102">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d639-102">ICorDebugProcess6 Interface</span></span>
<span data-ttu-id="1d639-103">Mantıksal olarak yerel özel durum hata ayıklama olayları ve sanal modülü bölme kodlanmış yönetilen hata ayıklama olayları kod çözme gibi özellikleri etkinleştirmek için Icordebugprocess arabirimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="1d639-103">Logically extends the ICorDebugProcess interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1d639-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1d639-104">Methods</span></span>  
  
|<span data-ttu-id="1d639-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1d639-105">Method</span></span>|<span data-ttu-id="1d639-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d639-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1d639-107">DecodeEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d639-107">DecodeEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)|<span data-ttu-id="1d639-108">Özel olarak hazırlanmış yerel özel durum hata ayıklama olayları yükünde kapsüllenmiş yönetilen hata ayıklama olayları kodunu çözer.</span><span class="sxs-lookup"><span data-stu-id="1d639-108">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>|  
|[<span data-ttu-id="1d639-109">EnableVirtualModuleSplitting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d639-109">EnableVirtualModuleSplitting Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)|<span data-ttu-id="1d639-110">Etkinleştirir veya sanal modülü bölme devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="1d639-110">Enables or disables virtual module splitting.</span></span>|  
|[<span data-ttu-id="1d639-111">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d639-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getcode-method.md)|<span data-ttu-id="1d639-112">Yönetilen kodu hakkında bilgi belirli kod adresinde alır.</span><span class="sxs-lookup"><span data-stu-id="1d639-112">Gets information about the managed code at a particular code address.</span></span>|  
|[<span data-ttu-id="1d639-113">GetExportStepInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d639-113">GetExportStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)|<span data-ttu-id="1d639-114">Yönetilen kod ilerleyebilirsiniz yardımcı olmak için dışarı çalışma zamanı işlevleri hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d639-114">Provides information on runtime exported functions to help step through managed code.</span></span>|  
|[<span data-ttu-id="1d639-115">MarkDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d639-115">MarkDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-markdebuggerattached-method.md)|<span data-ttu-id="1d639-116">Debugee iç durumu değişir böylece <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> .NET Framework Sınıf Kitaplığı'nda yöntemi döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="1d639-116">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>|  
|[<span data-ttu-id="1d639-117">ProcessStateChanged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d639-117">ProcessStateChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)|<span data-ttu-id="1d639-118">Bildirir [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) işlemin çalıştığı.</span><span class="sxs-lookup"><span data-stu-id="1d639-118">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d639-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d639-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d639-120">Arabirimi yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1d639-120">The interface is available with .NET Native only.</span></span> <span data-ttu-id="1d639-121">Çağrı girişimi `QueryInterface` bir arabirim işaretçisi almak için döndürür `E_NOINTERFACE` .NET yerel dışında Icordebug senaryoları için.</span><span class="sxs-lookup"><span data-stu-id="1d639-121">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d639-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1d639-122">Requirements</span></span>  
 <span data-ttu-id="1d639-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d639-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d639-124">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d639-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d639-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d639-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d639-126">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d639-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d639-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1d639-127">See Also</span></span>  
 [<span data-ttu-id="1d639-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1d639-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="1d639-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="1d639-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
