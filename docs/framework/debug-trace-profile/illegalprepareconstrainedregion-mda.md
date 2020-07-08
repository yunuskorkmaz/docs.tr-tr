---
title: illegalPrepareConstrainedRegion MDA
description: İllegalPrepareConstrainedRegion Managed hata ayıklama Yardımcısı ' nı gözden geçirin ve bir PrepareConstrainedRegions çağrısının ardından bir TRY deyiminden sonra çağrılır.
ms.date: 03/30/2017
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
ms.openlocfilehash: d6a0d1d95840ebd735806c5547730ae9e0b2aace
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051291"
---
# <a name="illegalprepareconstrainedregion-mda"></a>illegalPrepareConstrainedRegion MDA
`illegalPrepareConstrainedRegion`Yönetilen hata ayıklama Yardımcısı (MDA), bir <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> Yöntem çağrısı `try` özel durum işleyicisinin ifadesinden hemen önce gelmediğinde etkinleştirilir. Bu kısıtlama MSIL düzeyindedir, bu nedenle çağrı ile yorum gibi kod oluşturma olmayan kaynağa izin verilir `try` .  
  
## <a name="symptoms"></a>Belirtiler  
 Bu, basit bir özel durum işleme bloğu (veya) olarak hiçbir şekilde kabul edilen kısıtlı bir yürütme bölgesi (CER `finally` ) `catch` . Sonuç olarak, bölge bellek dışı bir koşul veya bir iş parçacığı iptali durumunda çalışmaz.  
  
## <a name="cause"></a>Nedeni  
 Bir CER için hazırlık deseninin doğru şekilde izlenmiyor.  Bu bir hata olayıdır. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>Özel durum işleyicilerini blok içindeki bir cer ile tanışın olarak işaretlemek için kullanılan yöntem çağrısı `catch` / `finally` / `fault` / `filter` , deyimden hemen önce kullanılmalıdır `try` .  
  
## <a name="resolution"></a>Çözüm  
 Çağrısının <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> , deyimden hemen önce yapıldığından emin olun `try` .  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıktı  
 MDA, yöntemi çağıran yöntemin adını <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> , MSIL farkını ve çağrının try bloğunun başlangıcından hemen önce gelmesini belirten bir iletiyi görüntüler.  
  
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
- [Birlikte Çalışma Hazırlama](../interop/interop-marshaling.md)
