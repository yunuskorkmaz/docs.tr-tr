---
title: ISymUnmanagedAsyncMethod Arabirimi
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd524446cd9fd5cf9c067ab5778a654ed000ffb3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179809"
---
# <a name="isymunmanagedasyncmethod-interface"></a>ISymUnmanagedAsyncMethod Arabirimi
Bu bir arabirimdir okuma tamamlayan [Isymunmanagedasyncmethodpropertieswriter arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a>Yöntemler  
 Bu arabirimi aşağıdaki yöntemleri içerir:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetAsyncStepInfo Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfo-method.md)|Bkz: [Defineasyncstepınfo yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).|  
|[GetAsyncStepInfoCount Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|Bkz: [Defineasyncstepınfo yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).|  
|[GetCatchHandlerILOffset Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|Bkz: [Definecatchhandlerıloffset yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).|  
|[GetKickoffMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getkickoffmethod-method.md)|Bkz: [DefineKickoffMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).|  
|[HasCatchHandlerILOffset Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|Bkz: [Definecatchhandlerıloffset yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).|  
|[IsAsyncMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-isasyncmethod-method.md)|Yöntemi zaman uyumsuz bilgi olup olmadığını denetler.<br /><br /> Bu yöntem döndürürse `FALSE` sonra bu arabirimde diğer yöntemleri çağırmak geçersizdir. Tüm dönüş göründükleri `E_UNEXPECTED` bu durumda.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Simge Deposu Arabirimleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
