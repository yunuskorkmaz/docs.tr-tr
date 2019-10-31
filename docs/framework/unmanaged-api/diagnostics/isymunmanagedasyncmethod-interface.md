---
title: ISymUnmanagedAsyncMethod Arabirimi
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
ms.openlocfilehash: 0b8adba9dbffbdc47bb526cef9aad3ffa4b48065
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129220"
---
# <a name="isymunmanagedasyncmethod-interface"></a>ISymUnmanagedAsyncMethod Arabirimi
Bu arabirim, [ıvmunmanagedasyncmethodpropertieswriter arabirimini](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)tamamlayan okuma işlemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a>Yöntemler  
 Bu arabirim aşağıdaki yöntemleri içerir:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetAsyncStepInfo Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfo-method.md)|Bkz. [DefineAsyncStepInfo Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).|  
|[GetAsyncStepInfoCount Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|Bkz. [DefineAsyncStepInfo Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).|  
|[GetCatchHandlerILOffset Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|Bkz. [Definecatch Handlerılsapmasını metodu](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).|  
|[GetKickoffMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getkickoffmethod-method.md)|Bkz. [DefineKickoffMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).|  
|[HasCatchHandlerILOffset Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|Bkz. [Definecatch Handlerılsapmasını metodu](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).|  
|[IsAsyncMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-isasyncmethod-method.md)|Metodun zaman uyumsuz bilgilere sahip olup olmadığını denetler.<br /><br /> Bu yöntem `FALSE` döndürürse, bu arabirimdeki diğer yöntemleri çağırmak geçersizdir. Bu durumda `E_UNEXPECTED` hepsi döndürülür.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Simge Deposu Arabirimleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
