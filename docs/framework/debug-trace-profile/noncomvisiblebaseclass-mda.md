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
ms.openlocfilehash: b46d5c6ffbf12efbae113a95bbfccd5742ec9ec9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217297"
---
# <a name="noncomvisiblebaseclass-mda"></a>nonComVisibleBaseClass MDA
`nonComVisibleBaseClass` yönetilen hata ayıklama Yardımcısı (MDA), com görünebilir olmayan bir taban sınıftan türetilen com görünebilir bir yönetilen sınıfın COM çağrılabilir sarmalayıcı (CCW) üzerinde yerel veya yönetilmeyen kod tarafından bir `QueryInterface` çağrısı yapıldığında etkinleştirilir.  `QueryInterface` çağrısı, MDA öğesinin yalnızca çağrının sınıf arabirimini veya COM görünebilir yönetilen sınıfın varsayılan `IDispatch` bir çağrı istemesi durumunda etkinleştirmesini sağlar.  `QueryInterface`, <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> özniteliği uygulanan ve COM görünebilir sınıfı tarafından açıkça uygulanan bir açık arabirim için olduğunda, MDA etkinleştirilmez.  
  
## <a name="symptoms"></a>Belirtiler  
 COR_E_INVALIDOPERATION HRESULT ile başarısız olan yerel koddan yapılan `QueryInterface` çağrısı.  HRESULT, bu MDA ' ın etkinleştirilmesine neden olacak çağrılardan `QueryInterface`, çalışma zamanının nedeni olabilir.  
  
## <a name="cause"></a>Nedeni  
 Çalışma zamanı, olası sürüm sorunları nedeniyle COM tarafından görülemeyen bir sınıftan türetilmiş bir COM görünebilir sınıfın sınıf arabirimi veya varsayılan `IDispatch` arabirimi için `QueryInterface` çağrılarına izin vermez.  Örneğin, hiçbir ortak üye, COM görünmeyen temel sınıfa eklendiyse, türetilmiş sınıfı kullanan mevcut COM istemcileri, temel sınıf üyelerini içeren bir sınıf olan vtable, bu tür bir değişebilir.  COM 'a sunulan açık arabirimler, vtable 'daki arabirimlerin temel üyelerini içermediği için bu soruna sahip değildir.  
  
## <a name="resolution"></a>Çözüm  
 Sınıf arabirimini kullanıma sunma. Açık bir arabirim tanımlayın ve <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> özniteliği buna uygulayın.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıktı  
 Aşağıda, COM görünebilir olmayan bir sınıftan `Base``Derived` bir COM görünebilir sınıf `QueryInterface` çağrısı için örnek bir ileti verilmiştir.  
  
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
- [Birlikte Çalışma için Hazırlama](../interop/interop-marshaling.md)
