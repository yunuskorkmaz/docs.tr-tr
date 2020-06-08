---
title: ISymUnmanagedAsyncMethod Arabirimi
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
ms.openlocfilehash: 448ed719331469dce8f15500f14d5c1b0707ecf7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504458"
---
# <a name="isymunmanagedasyncmethod-interface"></a>ISymUnmanagedAsyncMethod Arabirimi
Bu arabirim, [ıvmunmanagedasyncmethodpropertieswriter arabirimini](isymunmanagedasyncmethodpropertieswriter-interface.md)tamamlayan okuma işlemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a>Yöntemler  
 Bu arabirim aşağıdaki yöntemleri içerir:  
  
|Yöntem|Description|  
|------------|-----------------|  
|[GetAsyncStepInfo Yöntemi](isymunmanagedasyncmethod-getasyncstepinfo-method.md)|Bkz. [DefineAsyncStepInfo Yöntemi](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).|  
|[GetAsyncStepInfoCount Yöntemi](isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|Bkz. [DefineAsyncStepInfo Yöntemi](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).|  
|[GetCatchHandlerILOffset Yöntemi](isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|Bkz. [Definecatch Handlerılsapmasını metodu](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).|  
|[GetKickoffMethod Yöntemi](isymunmanagedasyncmethod-getkickoffmethod-method.md)|Bkz. [DefineKickoffMethod Yöntemi](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).|  
|[HasCatchHandlerILOffset Yöntemi](isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|Bkz. [Definecatch Handlerılsapmasını metodu](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).|  
|[IsAsyncMethod Yöntemi](isymunmanagedasyncmethod-isasyncmethod-method.md)|Metodun zaman uyumsuz bilgilere sahip olup olmadığını denetler.<br /><br /> Bu yöntem döndürürse `FALSE` , bu arabirimdeki diğer yöntemleri çağırmak geçersizdir. Hepsi `E_UNEXPECTED` Bu durumda döndürülür.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Simge Deposu Arabirimleri](diagnostics-symbol-store-interfaces.md)
