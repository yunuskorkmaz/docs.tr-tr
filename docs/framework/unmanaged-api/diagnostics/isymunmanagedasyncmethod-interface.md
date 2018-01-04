---
title: ISymUnmanagedAsyncMethod Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b9f83723b59f525c06f04b7edeeae953dbf94556
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethod-interface"></a>ISymUnmanagedAsyncMethod Arabirimi
Bu bir arabirimdir okuma tamamlayan [Isymunmanagedasyncmethodpropertieswriter arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a>Yöntemler  
 Bu arabirim, aşağıdaki yöntemleri içerir:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetAsyncStepInfo Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfo-method.md)|Bkz: [Defineasyncstepınfo yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).|  
|[GetAsyncStepInfoCount Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|Bkz: [Defineasyncstepınfo yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).|  
|[GetCatchHandlerILOffset Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|Bkz: [Definecatchhandlerıloffset yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).|  
|[GetKickoffMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getkickoffmethod-method.md)|Bkz: [DefineKickoffMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).|  
|[HasCatchHandlerILOffset Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|Bkz: [Definecatchhandlerıloffset yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).|  
|[IsAsyncMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-isasyncmethod-method.md)|Metodu zaman uyumsuz bilgi olup olmadığını denetler.<br /><br /> Bu yöntem döndürürse `FALSE` sonra da bu arabirimi diğer yöntemleri çağırmak için geçersiz. Tüm iade edecek `E_UNEXPECTED` bu durumda.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tanılama Simge Deposu Arabirimleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
