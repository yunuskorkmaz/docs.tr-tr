---
title: ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
ms.openlocfilehash: 04876483fd42e3f6e55222416fd0747891734a52
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501865"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a>ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi
Her yöntem sembolü için isteğe bağlı zaman uyumsuz yöntem bilgilerini tanımlamanızı sağlar. Her zaman açık bir yöntemle kullanın; diğer bir deyişle, [OpenMethod yöntemi](isymunmanagedwriter-openmethod-method.md) ve [CloseMethod yöntemi](isymunmanagedwriter-closemethod-method.md)çağrıları arasında.  
  
## <a name="syntax"></a>Sözdizimi  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a>Yöntemler  
 Bu arabirim aşağıdaki yöntemleri içerir:  
  
|Yöntem|Description|  
|------------|-----------------|  
|[DefineAsyncStepInfo Yöntemi](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|Geçerli yöntemde zaman uyumsuz await işlemleri grubunu tanımlayın.<br /><br /> Her bir yield boşluğu bir await 'ın dönüş yönergesiyle eşleşir ve potansiyel bir verimi tanımlar. Her bir `breakpointMethod` / `breakpointOffset` çift zaman uyumsuz işlemin hangi noktada sürdürüleceği tanımlar; farklı bir yöntemde olabilir.|  
|[DefineCatchHandlerILOffset Yöntemi](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|Bir zaman uyumsuz yöntemi sarmalayan derleyicinin ürettiği catch işleyicisinin Il sapmasını belirler.<br /><br /> Oluşturulan catch 'in Il kayması, hata ayıklayıcı tarafından, Kullanıcı kodu yönteminde meydana gelse bile, Kullanıcı olmayan kod gibi catch 'i işlemek için kullanılır. Özellikle, bir **catch Handlerfound** özel durum olayına yanıt olarak kullanılır.|  
|[DefineKickoffMethod Yöntemi](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|Zaman uyumsuz işlemi başlatan başlangıç yöntemini ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Simge Deposu Arabirimleri](diagnostics-symbol-store-interfaces.md)
