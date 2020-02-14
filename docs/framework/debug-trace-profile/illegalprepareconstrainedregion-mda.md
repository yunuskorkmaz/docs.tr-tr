---
title: illegalPrepareConstrainedRegion MDA
ms.date: 03/30/2017
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
ms.openlocfilehash: b80d6160876834b22e8d9d1eb7112b8b67c15fcc
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216472"
---
# <a name="illegalprepareconstrainedregion-mda"></a>illegalPrepareConstrainedRegion MDA
`illegalPrepareConstrainedRegion` yönetilen hata ayıklama Yardımcısı (MDA), bir <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> yöntemi çağrısı özel durum işleyicisinin `try` deyimiyle hemen önce olmadığında etkinleştirilir. Bu kısıtlama MSIL düzeyindedir; bu nedenle, çağrı ve `try`arasında kod oluşturma dışı kaynağa (Yorumlar gibi) izin verilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Bu şekilde hiçbir şekilde kabul edilen kısıtlı bir yürütme bölgesi (CER), ancak basit bir özel durum işleme bloğu (`finally` veya `catch`). Sonuç olarak, bölge bellek dışı bir koşul veya bir iş parçacığı iptali durumunda çalışmaz.  
  
## <a name="cause"></a>Nedeni  
 Bir CER için hazırlık deseninin doğru şekilde izlenmiyor.  Bu bir hata olayıdır. Özel durum işleyicilerini, `catch`/`finally`/`fault`/`filter` blokları üzerinde bir CER 'ye giriş olarak işaretlemek için kullanılan <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> yöntemi çağrısı `try` deyimlerinden hemen önce kullanılmalıdır.  
  
## <a name="resolution"></a>Çözüm  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> çağrısının `try` deyimden hemen önce yapıldığından emin olun.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıktı  
 MDA, <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> yöntemini çağıran yöntemin adını, MSIL sapmasını ve çağrının, try bloğunun başlangıcından hemen önce gelmediğini belirten bir ileti görüntüler.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bu MDA 'ın etkinleştirilmesini sağlayan bir model gösterir.  
  
```csharp
void MethodWithInvalidPCR()  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    Object o = new Object();  
    try  
    {  
        …  
    }  
    finally  
    {  
        …  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../interop/interop-marshaling.md)
