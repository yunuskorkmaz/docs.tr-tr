---
title: nonComVisibleBaseClass MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visible classes
- managed debugging assistants (MDAs), COM visible classes
- nonComVisibleBaseClass MDA
- COM visible classes
- QueryInterface call failures
- MDAs (managed debugging assistants), COM visible classes
ms.assetid: 9ec1af27-604b-477e-9ee2-e833eb10d3ce
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4b00d8396b07eb445414fb85cd830d595a513be0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="noncomvisiblebaseclass-mda"></a>nonComVisibleBaseClass MDA
`nonComVisibleBaseClass` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş olduğunda bir `QueryInterface` çağrısı yapıldığında COM aranabilir sarmalayıcısı (saat) yerel veya yönetilmeyen kodla COM görünür olmayan bir taban sınıftan türeyen bir COM-yönetilen görünür sınıfının.  `QueryInterface` Çağrısı neden yalnızca çağrı burada istekleri sınıf arabirimi veya varsayılan durumlarda etkinleştirmeyi MDA `IDispatch` COM görünür yönetilen sınıf.  MDA değil ne zaman etkin `QueryInterface` olan açık bir arabirim için <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> özniteliği uygulanan ve COM görünür sınıfı tarafından açıkça uygulanır.  
  
## <a name="symptoms"></a>Belirtiler  
 A `QueryInterface` COR_E_INVALIDOPERATION HRESULT başarısız olduğu yerel koddan yapılan çağrı.  Çalışma zamanı vermemek nedeniyle HRESULT olabilir `QueryInterface` çağrıları bu MDA etkinleştirme neden olur.  
  
## <a name="cause"></a>Sebep  
 Çalışma zamanı izin veremez `QueryInterface` çağırır ve sınıf arabirimi veya varsayılan için `IDispatch` COM görünür olası sürüm oluşturma sorunları nedeniyle olmayan bir sınıftan türeyen bir COM görünür sınıf arabirimi.  COM görünür değil taban sınıfı için herhangi bir ortak üye eklendiyse, taban sınıfı üyeleri içeren, türetilmiş sınıf vtable gibi tarafından değiştirilmesi çünkü Örneğin, türetilmiş sınıf kullanarak var olan COM istemcileri olası uğratabilir bir değiştirin.  Vtable arabirimleri temel üyeleri içermediği için açık arabirimler com'a Bu sorun yok.  
  
## <a name="resolution"></a>Çözüm  
 Sınıf arabirimi gösterme. Açık bir arabirim tanımlayın ve uygulayın <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> özniteliği için.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA CLR üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Bir örnek iletisidir aşağıdaki bir `QueryInterface` çağrısı COM görünür bir sınıf üzerinde `Derived` COM görünür olmayan bir sınıftan türetilen `Base`.  
  
```  
A QueryInterface call was made requesting the class interface of COM   
visible managed class 'Derived'. However since this class derives from   
non COM visible class 'Base', the QueryInterface call will fail. This   
is done to prevent the non COM visible base class from being   
constrained by the COM versioning rules.   
```  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
