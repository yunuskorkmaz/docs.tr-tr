---
title: ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82fcddd7a3f89a92cc79285930b30342333fbec2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940107"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a>ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi
Her yöntem simge için isteğe bağlı zaman uyumsuz yöntem bilgilerini tanımlamanızı sağlar. Her zaman açık bir yöntemle kullanın. diğer bir deyişle, yapılan çağrılar arasında [OpenMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) ve [CloseMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a>Yöntemler  
 Bu arabirimi aşağıdaki yöntemleri içerir:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[DefineAsyncStepInfo Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|Zaman uyumsuz grubu tanımlamanız geçerli yöntemi işlemleri bekler.<br /><br /> Her yield uzaklığı olası yield tanımlayan bir await'ın dönüş yönergesi, eşleşir. Her `breakpointMethod` / `breakpointOffset` çifti tanımlar burada zaman uyumsuz işlemi devam edecek; farklı bir yöntem olabilir.|  
|[DefineCatchHandlerILOffset Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|IL uzaklığı bir zaman uyumsuz yöntem sarmalayan derleyicinin ürettiği catch işleyicisi için ayarlar.<br /><br /> Oluşturulan yakalama IL uzaklığı, hata ayıklayıcı tarafından kullanıcı olmayan kod gibi bir kullanıcı kodu yöntemde oluşsa yakalama işlemek için kullanılır. Özellikle, yanıt olarak kullanılır bir **CatchHandlerFound** özel durum olayı.|  
|[DefineKickoffMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|Zaman uyumsuz işlem başlattığı başlangıç yöntemini ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Simge Deposu Arabirimleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
