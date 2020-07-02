---
title: nonComVisibleBaseClass MDA
description: COR_E_INVALIDOPERATION ile başarısız olan yerel koddan QueryInterface çağrılarında çağrılan nonComVisibleBaseClass yönetilen hata ayıklama Yardımcısı ' na (MDA) bakın.
ms.date: 03/30/2017
helpviewer_keywords:
- visible classes
- managed debugging assistants (MDAs), COM visible classes
- nonComVisibleBaseClass MDA
- COM visible classes
- QueryInterface call failures
- MDAs (managed debugging assistants), COM visible classes
ms.assetid: 9ec1af27-604b-477e-9ee2-e833eb10d3ce
ms.openlocfilehash: 9f32b2c57f50fcd900b1fd78f4f8df1ec656a6db
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803930"
---
# <a name="noncomvisiblebaseclass-mda"></a>nonComVisibleBaseClass MDA
`nonComVisibleBaseClass`Yönetilen hata ayıklama Yardımcısı (MDA), com `QueryInterface` görünebilir olmayan bir taban sınıftan türetilen com görünebilir bir YÖNETILEN sınıfın com çağrılabilir SARMALAYıCı (CCW) üzerinde yerel veya yönetilmeyen kod tarafından bir çağrı yapıldığında etkinleştirilir.  Bu `QueryInterface` çağrı, MDA öğesinin yalnızca çağrının sınıf arabirimini veya `IDispatch` com görünebilir yönetilen sınıfın varsayılanını istemesi durumunda etkinleştirmesini sağlar.  , `QueryInterface` <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> Özniteliği uygulanmış ve com görünebilir sınıfı tarafından açıkça uygulanan bir açık arabirim için olduğunda, MDA etkinleştirilmez.  
  
## <a name="symptoms"></a>Belirtiler  
 `QueryInterface`BIR HRESULT COR_E_INVALIDOPERATION başarısız olan yerel koddan yapılan bir çağrı.  HRESULT, `QueryInterface` Bu mda ' ın etkinleştirilmesine neden olabilecek çalışma zamanı izin vermez çağrılardan kaynaklanıyor olabilir.  
  
## <a name="cause"></a>Nedeni  
 Çalışma zamanı, `QueryInterface` `IDispatch` olası sürüm oluşturma sorunları nedeniyle com görünebilir olmayan bir SıNıFTAN türetilen com görünebilir bir sınıfın sınıf arabirimi veya varsayılan arabirimine yönelik çağrılara izin vermez.  Örneğin, hiçbir ortak üye, COM görünmeyen temel sınıfa eklendiyse, türetilmiş sınıfı kullanan mevcut COM istemcileri, temel sınıf üyelerini içeren bir bu tür değişikliğe göre değiştirilebilecek olan türetilmiş sınıfın vtable 'ı kesintiye neden olabilir.  COM 'a sunulan açık arabirimler, vtable 'daki arabirimlerin temel üyelerini içermediği için bu soruna sahip değildir.  
  
## <a name="resolution"></a>Çözüm  
 Sınıf arabirimini kullanıma sunma. Açık bir arabirim tanımlayın ve <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> özniteliği buna uygulayın.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıktı  
 Aşağıda, `QueryInterface` `Derived` com görünebilir olmayan bir SıNıFTAN türetilen com görünebilir bir sınıftaki çağrı için örnek bir ileti verilmiştir `Base` .  
  
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
