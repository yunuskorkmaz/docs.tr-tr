---
title: nonComVisibleBaseClass MDA
ms.date: 03/30/2017
helpviewer_keywords:
- visible classes
- managed debugging assistants (MDAs), COM visible classes
- nonComVisibleBaseClass MDA
- COM visible classes
- QueryInterface call failures
- MDAs (managed debugging assistants), COM visible classes
ms.assetid: 9ec1af27-604b-477e-9ee2-e833eb10d3ce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb0810a9e0ffce825abecc87eb2698920209d86f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61753770"
---
# <a name="noncomvisiblebaseclass-mda"></a>nonComVisibleBaseClass MDA
`nonComVisibleBaseClass` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş olduğunda bir `QueryInterface` Çağrının yapıldığı COM çağrılabilir sarmalayıcı (CCW) yerel veya yönetilmeyen kodla COM görünür olmayan bir taban sınıftan türetilen bir COM yönetilen görünür sınıfı.  `QueryInterface` Çağrının sebep olur yalnızca çağrı burada istekleri sınıf arabirimi veya varsayılan durumda etkinleştirmek MDA `IDispatch` sınıfı için Yönetilen COM-görünür.  MDA değil etkinleştirildiği zaman `QueryInterface` olan açık bir arabirim için <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> özniteliği uygulanan ve açıkça COM görünür bir sınıf tarafından uygulanır.  
  
## <a name="symptoms"></a>Belirtiler  
 A `QueryInterface` yapılan bir COR_E_INVALIDOPERATION HRESULT başarısız olduğu yerel koddan çağrı.  HRESULT engelleyerek runtime nedeniyle olabilir `QueryInterface` bu mda'nın etkinleştirilmesinden neden çağırır.  
  
## <a name="cause"></a>Sebep  
 Çalışma zamanı izin veremez `QueryInterface` çağırır sınıf arabirimi veya varsayılan için `IDispatch` COM-görünür olası sürüm oluşturma sorunları nedeniyle değil bir sınıftan türetilen bir COM görünür bir sınıfın arabirim.  COM görünür olmayan taban sınıfa herhangi bir ortak üye eklendiyse, türetilen sınıfın temel sınıf üyelerini içeren vtable gibi tarafından değiştirilmesi çünkü gibi türetilmiş bir sınıf kullanarak mevcut COM istemcileri olası uğratabilir bir değiştirin.  Açık arabirimler com'a vtable içinde arabirimin temel üyelerini içermediği için bu sorun yok.  
  
## <a name="resolution"></a>Çözüm  
 Sınıf arabirimi gösterme. Açık bir arabirim tanımlayın ve uygulayın <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> için özniteliği.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bu mda'nın CLR üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Bir örnek iletisidir aşağıdaki bir `QueryInterface` COM görünür bir sınıf üzerinde çağrı `Derived` COM görünür olmayan bir sınıftan türetilen `Base`.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
