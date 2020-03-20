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
ms.openlocfilehash: 4c16432df201d19b65c91206ec529d07605e979a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181797"
---
# <a name="noncomvisiblebaseclass-mda"></a>nonComVisibleBaseClass MDA
Yönetilen `nonComVisibleBaseClass` hata ayıklama yardımcısı (MDA), COM `QueryInterface` görünür olmayan bir taban sınıftan türetilen COM görünür yönetilen sınıfın COM çağrılabilir sarıcı (CCW) üzerinde yerel veya yönetilmeyen kod tarafından bir çağrı yapıldığında etkinleştirilir.  Arama, `QueryInterface` MDA'nın yalnızca çağrının sınıf arabirimini `IDispatch` veya COM tarafından görünür yönetilen sınıfın varsayılanını talep ettiği durumlarda etkinleştirilmesine neden olur.  MDA, özniteliğe `QueryInterface` sahip açık bir arabirim <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> için olduğunda etkinleştirilmez ve COM-görünür sınıf tarafından açıkça uygulanır.  
  
## <a name="symptoms"></a>Belirtiler  
 COR_E_INVALIDOPERATION `QueryInterface` HRESULT ile başarısız olan yerel koddan yapılan bir arama.  HRESULT, bu MDA'nın etkinleştirilmesine `QueryInterface` neden olacak çalışma saatinden izin vermeme çağrılarına bağlı olabilir.  
  
## <a name="cause"></a>Nedeni  
 Çalışma süresi, `QueryInterface` olası sürüm sorunları nedeniyle `IDispatch` COM görünür olmayan bir sınıftan türeyen BIR COM görünür sınıfın sınıf arabirimi veya varsayılan arabirimi için çağrılara izin veremez.  Örneğin, com-görünür olmayan taban sınıfa herhangi bir ortak üye eklenirse, türemiş sınıfı kullanan varolan COM istemcileri, taban sınıf üyelerini içeren türemiş sınıfın vtable'ı bu tür bir Değiştirmek.  COM'a maruz kalan açık arabirimler, arabirimlerin temel üyelerini vtable'a içermedikleri için bu soruna sahip değildir.  
  
## <a name="resolution"></a>Çözüm  
 Sınıf arabirimini ifşa etmeyin. Açık bir arabirim <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> tanımlayın ve özniteliği uygulayın.  
  
## <a name="effect-on-the-runtime"></a>Çalışma Süresi üzerindeki etkisi  
 Bu MDA'nın CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıktı  
 Aşağıda, COM'da görünmeyen bir sınıftan `QueryInterface` `Derived` `Base`türeyen COM görünür sınıfındaki bir çağrı için örnek bir ileti verilmiştir.  
  
```output
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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma Hazırlama](../interop/interop-marshaling.md)
