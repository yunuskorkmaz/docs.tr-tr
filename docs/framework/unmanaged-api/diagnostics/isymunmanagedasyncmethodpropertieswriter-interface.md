---
title: ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
ms.openlocfilehash: db065357e22ac576600a3ca61dda0882b9206a86
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129160"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a>ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi
Her yöntem sembolü için isteğe bağlı zaman uyumsuz yöntem bilgilerini tanımlamanızı sağlar. Her zaman açık bir yöntemle kullanın; diğer bir deyişle, [OpenMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) ve [CloseMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)çağrıları arasında.  
  
## <a name="syntax"></a>Sözdizimi  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a>Yöntemler  
 Bu arabirim aşağıdaki yöntemleri içerir:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[DefineAsyncStepInfo Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|Geçerli yöntemde zaman uyumsuz await işlemleri grubunu tanımlayın.<br /><br /> Her bir yield boşluğu bir await 'ın dönüş yönergesiyle eşleşir ve potansiyel bir verimi tanımlar. Her bir `breakpointMethod`/`breakpointOffset` çifti, zaman uyumsuz işlemin nerede sürdürüleceği belirtir; farklı bir yöntemde olabilir.|  
|[DefineCatchHandlerILOffset Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|Bir zaman uyumsuz yöntemi sarmalayan derleyicinin ürettiği catch işleyicisinin Il sapmasını belirler.<br /><br /> Oluşturulan catch 'in Il kayması, hata ayıklayıcı tarafından, Kullanıcı kodu yönteminde meydana gelse bile, Kullanıcı olmayan kod gibi catch 'i işlemek için kullanılır. Özellikle, bir **catch Handlerfound** özel durum olayına yanıt olarak kullanılır.|  
|[DefineKickoffMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|Zaman uyumsuz işlemi başlatan başlangıç yöntemini ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Simge Deposu Arabirimleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
