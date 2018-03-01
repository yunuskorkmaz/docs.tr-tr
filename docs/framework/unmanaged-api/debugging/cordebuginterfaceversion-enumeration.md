---
title: "CorDebugInterfaceVersion Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorDebugInterfaceVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInterfaceVersion
helpviewer_keywords:
- CorDebugInterfaceVersion enumeration [.NET Framework debugging]
ms.assetid: 7d1e6cd9-2a15-41c6-9b68-008705a4ed90
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2b5d28e6def34c9263d519c2eeb9cc432656bd1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebuginterfaceversion-enumeration"></a>CorDebugInterfaceVersion Numaralandırması
Arabirim, .NET Framework sürümü veya arabirim kullanılmaya başlanan .NET Framework sürümünü belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorDebugInterfaceVersion {  
  
    CorDebugInvalidVersion            = 0,  
    CorDebugVersion_1_0               = CorDebugInvalidVersion + 1,  
  
    ver_ICorDebugManagedCallback      = CorDebugVersion_1_0,  
    ver_ICorDebugUnmanagedCallback    = CorDebugVersion_1_0,  
    ver_ICorDebug                     = CorDebugVersion_1_0,  
    ver_ICorDebugController           = CorDebugVersion_1_0,  
    ver_ICorDebugAppDomain            = CorDebugVersion_1_0,  
    ver_ICorDebugAssembly             = CorDebugVersion_1_0,  
    ver_ICorDebugProcess              = CorDebugVersion_1_0,  
    ver_ICorDebugBreakpoint           = CorDebugVersion_1_0,  
    ver_ICorDebugFunctionBreakpoint   = CorDebugVersion_1_0,  
    ver_ICorDebugModuleBreakpoint     = CorDebugVersion_1_0,  
    ver_ICorDebugValueBreakpoint      = CorDebugVersion_1_0,  
    ver_ICorDebugStepper              = CorDebugVersion_1_0,  
    ver_ICorDebugRegisterSet          = CorDebugVersion_1_0,  
    ver_ICorDebugThread               = CorDebugVersion_1_0,  
    ver_ICorDebugChain                = CorDebugVersion_1_0,  
    ver_ICorDebugFrame                = CorDebugVersion_1_0,  
    ver_ICorDebugILFrame              = CorDebugVersion_1_0,  
    ver_ICorDebugNativeFrame          = CorDebugVersion_1_0,  
    ver_ICorDebugModule               = CorDebugVersion_1_0,  
    ver_ICorDebugFunction             = CorDebugVersion_1_0,  
    ver_ICorDebugCode                 = CorDebugVersion_1_0,  
    ver_ICorDebugClass                = CorDebugVersion_1_0,  
    ver_ICorDebugEval                 = CorDebugVersion_1_0,  
    ver_ICorDebugValue                = CorDebugVersion_1_0,  
    ver_ICorDebugGenericValue         = CorDebugVersion_1_0,  
    ver_ICorDebugReferenceValue       = CorDebugVersion_1_0,  
    ver_ICorDebugHeapValue            = CorDebugVersion_1_0,  
    ver_ICorDebugObjectValue          = CorDebugVersion_1_0,  
    ver_ICorDebugBoxValue             = CorDebugVersion_1_0,  
    ver_ICorDebugStringValue          = CorDebugVersion_1_0,  
    ver_ICorDebugArrayValue           = CorDebugVersion_1_0,  
    ver_ICorDebugContext              = CorDebugVersion_1_0,  
    ver_ICorDebugEnum                 = CorDebugVersion_1_0,  
    ver_ICorDebugObjectEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugBreakpointEnum       = CorDebugVersion_1_0,  
    ver_ICorDebugStepperEnum          = CorDebugVersion_1_0,  
    ver_ICorDebugProcessEnum          = CorDebugVersion_1_0,  
    ver_ICorDebugThreadEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugFrameEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugChainEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugModuleEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugValueEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugCodeEnum             = CorDebugVersion_1_0,  
    ver_ICorDebugTypeEnum             = CorDebugVersion_1_0,  
    ver_ICorDebugErrorInfoEnum        = CorDebugVersion_1_0,  
    ver_ICorDebugAppDomainEnum        = CorDebugVersion_1_0,  
    ver_ICorDebugAssemblyEnum         = CorDebugVersion_1_0,  
    ver_ICorDebugEditAndContinueErrorInfo   
                                      = CorDebugVersion_1_0,  
    ver_ICorDebugEditAndContinueSnapshot   
                                      = CorDebugVersion_1_0,  
  
    CorDebugVersion_1_1               = CorDebugVersion_1_0 + 1,  
    // No interface definitions in version 1.1.  
  
    CorDebugVersion_2_0 = CorDebugVersion_1_1 + 1,  
  
    ver_ICorDebugManagedCallback2    = CorDebugVersion_2_0,  
    ver_ICorDebugAppDomain2          = CorDebugVersion_2_0,  
    ver_ICorDebugProcess2            = CorDebugVersion_2_0,  
    ver_ICorDebugStepper2            = CorDebugVersion_2_0,  
    ver_ICorDebugRegisterSet2        = CorDebugVersion_2_0,  
    ver_ICorDebugThread2             = CorDebugVersion_2_0,  
    ver_ICorDebugILFrame2            = CorDebugVersion_2_0,  
    ver_ICorDebugModule2             = CorDebugVersion_2_0,  
    ver_ICorDebugFunction2           = CorDebugVersion_2_0,  
    ver_ICorDebugCode2               = CorDebugVersion_2_0,  
    ver_ICorDebugClass2              = CorDebugVersion_2_0,  
    ver_ICorDebugValue2              = CorDebugVersion_2_0,  
    ver_ICorDebugEval2               = CorDebugVersion_2_0,  
    ver_ICorDebugObjectValue2        = CorDebugVersion_2_0,  
  
    // CLR v4 - next major CLR version after CLR v2  
    // Includes Silverlight 4  
    CorDebugVersion_4_0 = CorDebugVersion_2_0 + 1,  
  
    ver_ICorDebugThread3             = CorDebugVersion_4_0,  
    ver_ICorDebugThread4             = CorDebugVersion_4_0,  
    ver_ICorDebugStackWalk           = CorDebugVersion_4_0,  
    ver_ICorDebugNativeFrame2        = CorDebugVersion_4_0,  
    ver_ICorDebugInternalFrame2      = CorDebugVersion_4_0,  
    ver_ICorDebugRuntimeUnwindableFrame = CorDebugVersion_4_0,  
    ver_ICorDebugHeapValue3          = CorDebugVersion_4_0,  
    ver_ICorDebugBlockingObjectEnum  = CorDebugVersion_4_0,  
    ver_ICorDebugValue3 = CorDebugVersion_4_0,  
  
    CorDebugVersion_4_5 = CorDebugVersion_4_0 + 1,  
  
    ver_ICorDebugComObjectValue = CorDebugVersion_4_5,  
    ver_ICorDebugAppDomain3 = CorDebugVersion_4_5,  
    ver_ICorDebugCode3 = CorDebugVersion_4_5,  
    ver_ICorDebugILFrame3 = CorDebugVersion_4_5,  
  
    CorDebugLatestVersion = CorDebugVersion_4_5  
  
} CorDebugInterfaceVersion;  
```  
  
## <a name="members"></a>Üyeler  
 Aşağıdaki tabloda her numaralandırma değeri bağlanan karşılık gelen arabirimi sağlar. Ayrıca, tablo ilk arabirimi desteklenen .NET Framework sürümünü gösterir.  
  
|Üye|Belirler|.NET Framework sürümü|  
|------------|---------------|----------------------------|  
|`CorDebugInvalidVersion`|.NET Framework sürümü geçersiz.|-|  
|`CorDebugVersion_1_0`|Kendi hizmet paketleri de dahil olmak üzere, .NET Framework 1.0 sürümüdür.|1.0|  
|`CorDebugVersion_1_1`|Tüm hizmet paketlerini de dahil olmak üzere, .NET Framework 1.1 sürümüdür.|1.1|  
|`CorDebugVersion_2_0`|Tüm hizmet paketlerini de dahil olmak üzere, .NET Framework 2.0 sürümüdür.|2,0|  
|`CorDebugVersion_4_0`|Tüm hizmet paketlerini de dahil olmak üzere, .NET Framework sürüm 4'tür.|4|  
|`CorDebugVersion_4_5`|Tüm hizmet paketlerini de dahil olmak üzere, .NET Framework 4.5 sürümüdür.|4,5|  
|`ver_ICorDebugManagedCallback`|[Icordebugmanagedcallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)|1.0|  
|`ver_ICorDebugUnmanagedCallback`|[Icordebugunmanagedcallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)|1.0|  
|`ver_ICorDebug`|[Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)|1.0|  
|`ver_ICorDebugController`|[Icordebugcontroller](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)|1.0|  
|`ver_ICorDebugAppDomain`|[Icordebugappdomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)|1.0|  
|`ver_ICorDebugAssembly`|[Icordebugassembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)|1.0|  
|`ver_ICorDebugProcess`|[Icordebugprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)|1.0|  
|`ver_ICorDebugBreakpoint`|[Icordebugbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)|1.0|  
|`ver_ICorDebugFunctionBreakpoint`|[Icordebugfunctionbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)|1.0|  
|`ver_ICorDebugModuleBreakpoint`|[Icordebugmodulebreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)|1.0|  
|`ver_ICorDebugValueBreakpoint`|[Icordebugvaluebreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-interface.md)|1.0|  
|`ver_ICorDebugStepper`|[ICorDebugStepper](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)|1.0|  
|`ver_ICorDebugRegisterSet`|[Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)|1.0|  
|`ver_ICorDebugThread`|[Icordebugthread](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)|1.0|  
|`ver_ICorDebugChain`|[Icordebugchain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)|1.0|  
|`ver_ICorDebugFrame`|[Icordebugframe](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)|1.0|  
|`ver_ICorDebugILFrame`|[Icordebugılframe](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)|1.0|  
|`ver_ICorDebugNativeFrame`|[Icordebugnativeframe](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)|1.0|  
|`ver_ICorDebugModule`|[Icordebugmodule](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)|1.0|  
|`ver_ICorDebugFunction`|[ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)|1.0|  
|`ver_ICorDebugCode`|[Icordebugcode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)|1.0|  
|`ver_ICorDebugClass`|[Icordebugclass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)|1.0|  
|`ver_ICorDebugEval`|[Icordebugeval](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)|1.0|  
|`ver_ICorDebugValue`|[Icordebugvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md)|1.0|  
|`ver_ICorDebugGenericValue`|[Icordebuggenericvalue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)|1.0|  
|`ver_ICorDebugReferenceValue`|[Icordebugreferencevalue](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)|1.0|  
|`ver_ICorDebugHeapValue`|[Icordebugheapvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)|1.0|  
|`ver_ICorDebugObjectValue`|[Icordebugobjectvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)|1.0|  
|`ver_ICorDebugBoxValue`|[Icordebugboxvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)|1.0|  
|`ver_ICorDebugStringValue`|[Icordebugstringvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)|1.0|  
|`ver_ICorDebugArrayValue`|[Icordebugarrayvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)|1.0|  
|`ver_ICorDebugContext`|[Icordebugcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)|1.0|  
|`ver_ICorDebugEnum`|[Icordebugenum](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)|1.0|  
|`ver_ICorDebugObjectEnum`|[Icordebugobjectenum](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)|1.0|  
|`ver_ICorDebugBreakpointEnum`|[Icordebugbreakpointenum](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)|1.0|  
|`ver_ICorDebugStepperEnum`|[Icordebugstepperenum](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)|1.0|  
|`ver_ICorDebugProcessEnum`|[Icordebugprocessenum](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)|1.0|  
|`ver_ICorDebugThreadEnum`|[Icordebugthreadenum](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)|1.0|  
|`ver_ICorDebugFrameEnum`|[Icordebugframeenum](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)|1.0|  
|`ver_ICorDebugChainEnum`|[Icordebugchainenum](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)|1.0|  
|`ver_ICorDebugModuleEnum`|[Icordebugmoduleenum](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)|1.0|  
|`ver_ICorDebugValueEnum`|[Icordebugvalueenum](../../../../docs/framework/unmanaged-api/debugging/icordebugvalueenum-interface.md)|1.0|  
|`ver_ICorDebugCodeEnum`|[Icordebugcodeenum](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)|1.0|  
|`ver_ICorDebugTypeEnum`|[Icordebugtypeenum](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)|1.0|  
|`ver_ICorDebugErrorInfoEnum`|[Icordebugerrorınfoenum](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)|1.0|  
|`ver_ICorDebugAppDomainEnum`|[Icordebugappdomainenum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)|1.0|  
|`ver_ICorDebugAssemblyEnum`|[Icordebugassemblyenum](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)|1.0|  
|`ver_ICorDebugEditAndContinueErrorInfo`|[Icordebugeditandcontinueerrorınfo](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)|1.0|  
|`ver_ICorDebugEditAndContinueSnapshot`|[Icordebugeditandcontinuesnapshot](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)|1.0|  
|`ver_ICorDebugManagedCallback2`|[Icordebugmanagedcallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)|2,0|  
|`ver_ICorDebugAppDomain2`|[Icordebugappdomain2](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)|2,0|  
|`ver_ICorDebugProcess2`|[Icordebugprocess2](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)|2,0|  
|`ver_ICorDebugStepper2`|[Icordebugstepper2](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)|2,0|  
|`ver_ICorDebugRegisterSet2`|[Icordebugregisterset2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)|2,0|  
|`ver_ICorDebugThread2`|[Icordebugthread2](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)|2,0|  
|`ver_ICorDebugILFrame2`|[Icordebugılframe2](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)|2,0|  
|`ver_ICorDebugModule2`|[Icordebugmodule2](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)|2,0|  
|`ver_ICorDebugFunction2`|[Icordebugfunction2](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)|2,0|  
|`ver_ICorDebugCode2`|[Icordebugcode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)|2,0|  
|`ver_ICorDebugClass2`|"ICorDebugClass2"|2,0|  
|`ver_ICorDebugValue2`|"ICorDebugValue2"|2,0|  
|`ver_ICorDebugEval2`|"Icordebugeval2".|2,0|  
|`ver_ICorDebugObjectValue2`|"ICorDebugObjectValue2"|2,0|  
|`ver_ICorDebugThread3`|[Icordebugthread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)|4|  
|`ver_ICorDebugThread4`|[Icordebugthread4](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)|4|  
|`ver_ICorDebugStackWalk`|[Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)|4|  
|`ver_ICorDebugNativeFrame2`|[Icordebugnativeframe2](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)|4|  
|`ver_ICorDebugInternalFrame2`|[Icordebugınternalframe2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)|4|  
|`ver_ICorDebugRuntimeUnwindableFrame`|[Icordebugruntimeunwindableframe](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)|4|  
|`ver_ICorDebugHeapValue3`|[ICorDebugHeapValue3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)|4|  
|`ver_ICorDebugBlockingObjectEnum`|[ICorDebugBlockingObjectEnum Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)|4|  
|`ver_ICorDebugValue3`|[Icordebugvalue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)|4|  
|`ver_ICorDebugComObjectValue`|[Icordebugcomobjectvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)|4,5|  
|`ver_ICorDebugAppDomain3`|[Icordebugappdomain3](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)|4,5|  
|`ver_ICorDebugCode3`|[Icordebugcode3](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)|4,5|  
|`ver_ICorDebugILFrame3`|[Icordebugılframe3](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)|4,5|  
|`CorDebugLatestVersion`|En son sürümü tüm kendi hizmet paketleri de dahil olmak üzere, .NET Framework sürümüdür.|-|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir hata ayıklayıcısı kullanabilirsiniz `CorDebugInterfaceVersion` numaralandırmada [Createdebuggingınterfacefromversion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) işlevi yüksek hata ayıklayıcı destekleyen .NET Framework sürümünü belirtin.  
  
## <a name="interface-names"></a>Arabirim adları  
 Hata ayıklama API'si arabirimi adlarında sonunda görünür numarası (örneğin, "3" olarak `ICorDebugThread3`) değil, .NET Framework sürümünü arabirimi sürümünü belirtir. Tüm arabirimi adlarının hata ayıklama API'si .NET Framework sürüm 1 sunulan arabirimleri dışında sürüm numaralarını içerir. Arabirim sürüm numaralarını and.NET Framework sürüm numaralarını arasındaki bir ilişkiyi içerik olarak farklı.  
  
-   Tüm örtük olarak sürüm 1 olduğundan .NET Framework sürüm 1.0 sunulan arabirimleri sayılar dahil etmeyin.  
  
-   .NET Framework sürüm 1.1 sürüm 1.0 arayüzleri kullanır ve tüm yeni hata ayıklama arabirimleri sunmaz.  
  
-   .NET Framework 2.0 sürümünde sunulan 14 hata ayıklama arabirimleri kendi sürümünün mantıksal uzantıları 1 ortaklarınıza ve adlarında "2" sayısını içerir.  
  
-   .NET Framework sürüm 3.0 ve 3.5 var olan .NET Framework 2.0 arabirimleri kullanın ve yeni arabirimlerden tanıtmak değil.  
  
-   [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Arabirimi sürümleri bir karışımını sunar. Örneğin, her ikisi de `ICorDebugThread3` ve `ICorDebugThread4` üçüncü ve dördüncü sürümleri görünen `ICorDebugThread` arabirimi. [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] Ayrıca ilk sürümünü getirmektedir `ICorDebugStackWalk` arabirimi ve ikinci sürümü `ICorDebugNativeFrame` arabirimi (`ICorDebugNativeFrame2`).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
