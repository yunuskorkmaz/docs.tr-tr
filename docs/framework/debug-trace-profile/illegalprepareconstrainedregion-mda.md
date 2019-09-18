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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 623aff91eb801b4b32fc180bd97ed3822ad7f163
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052671"
---
# <a name="illegalprepareconstrainedregion-mda"></a>illegalPrepareConstrainedRegion MDA
Yönetilen hata ayıklama Yardımcısı (MDA), bir <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> Yöntem çağrısı özel durum işleyicisinin `try` ifadesinden hemen önce gelmediğinde etkinleştirilir. `illegalPrepareConstrainedRegion` Bu kısıtlama MSIL düzeyindedir, bu nedenle çağrı ile `try`yorum gibi kod oluşturma olmayan kaynağa izin verilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Bu, basit bir özel durum işleme bloğu (`finally` veya `catch`) olarak hiçbir şekilde kabul edilen kısıtlı bir yürütme bölgesi (cer). Sonuç olarak, bölge bellek dışı bir koşul veya bir iş parçacığı iptali durumunda çalışmaz.  
  
## <a name="cause"></a>Sebep  
 Bir CER için hazırlık deseninin doğru şekilde izlenmiyor.  Bu bir hata olayıdır. `catch` Özeldurum`finally` işleyicilerini / <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> blok`filter` içindeki birceriletanışınolarakişaretlemekiçinkullanılanyöntemçağrısı,/ `fault` / `try` bildirim.  
  
## <a name="resolution"></a>Çözüm  
 Çağrısının <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> ,`try` deyimden hemen önce yapıldığından emin olun.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 MDA, <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> yöntemi çağıran yöntemin adını, MSIL farkını ve çağrının try bloğunun başlangıcından hemen önce gelmesini belirten bir iletiyi görüntüler.  
  
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
