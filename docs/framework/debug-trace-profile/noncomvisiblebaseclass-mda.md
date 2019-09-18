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
ms.openlocfilehash: e4340dd75e24ddeb01428159d5532b86e76fd8b4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052434"
---
# <a name="noncomvisiblebaseclass-mda"></a>nonComVisibleBaseClass MDA
Yönetilen hata ayıklama Yardımcısı (MDA), com görünebilir olmayan `QueryInterface` bir taban sınıftan türetilen com görünebilir bir yönetilen sınıfın com çağrılabilir sarmalayıcı (CCW) üzerinde yerel veya yönetilmeyen kod tarafından bir çağrı yapıldığında etkinleştirilir. `nonComVisibleBaseClass`  Bu çağrı, MDA öğesinin yalnızca çağrının sınıf arabirimini veya com görünebilir yönetilen sınıfın varsayılanını `IDispatch` istemesi durumunda etkinleştirmesini sağlar. `QueryInterface`  , `QueryInterface` <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> Özniteliği uygulanmış ve com görünebilir sınıfı tarafından açıkça uygulanan bir açık arabirim için olduğunda, MDA etkinleştirilmez.  
  
## <a name="symptoms"></a>Belirtiler  
 COR_E_INVALIDOPERATION HRESULT ile başarısız olan yerel koddan yapılan çağrı.`QueryInterface`  HRESULT, bu mda ' ın etkinleştirilmesine neden `QueryInterface` olabilecek çalışma zamanı izin vermez çağrılardan kaynaklanıyor olabilir.  
  
## <a name="cause"></a>Sebep  
 Çalışma zamanı, olası `QueryInterface` sürüm oluşturma sorunları nedeniyle com görünebilir olmayan `IDispatch` bir sınıftan türetilen com görünebilir bir sınıfın sınıf arabirimi veya varsayılan arabirimine yönelik çağrılara izin vermez.  Örneğin, hiçbir ortak üye, COM görünmeyen temel sınıfa eklendiyse, türetilmiş sınıfı kullanan mevcut COM istemcileri, temel sınıf üyelerini içeren bir sınıf olan vtable, bu tür bir değişebilir.  COM 'a sunulan açık arabirimler, vtable 'daki arabirimlerin temel üyelerini içermediği için bu soruna sahip değildir.  
  
## <a name="resolution"></a>Çözüm  
 Sınıf arabirimini kullanıma sunma. Açık bir arabirim tanımlayın ve <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> özniteliği buna uygulayın.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Aşağıda, com görünebilir olmayan bir sınıftan `QueryInterface` `Base`türetilen com görünebilir bir sınıftaki `Derived` çağrı için örnek bir ileti verilmiştir.  
  
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
