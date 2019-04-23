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
ms.openlocfilehash: 23a36d1709f03583ce39af0e7c80bb1ecd7cf809
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158983"
---
# <a name="illegalprepareconstrainedregion-mda"></a>illegalPrepareConstrainedRegion MDA
`illegalPrepareConstrainedRegion` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş olduğunda bir <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> yöntem çağrısı değil hemen önünde `try` özel durum işleyicisinin bildirimi. Çağrı arasında kaynak kodu oluşturma için izin verilen, bu nedenle bu kısıtlama MSIL düzeyini ve `try`, açıklamalar gibi.  
  
## <a name="symptoms"></a>Belirtiler  
 Bu nedenle, ancak basit bir özel durum işleme bloğu asla kabul kısıtlı yürütme bölge (CER) (`finally` veya `catch`). Sonuç olarak, bölge içinde bir bellek yetersiz koşulu veya bir iş parçacığı iptal olması durumunda çalıştırmaz.  
  
## <a name="cause"></a>Sebep  
 Bir CER hazırlık desenini doğru şekilde izlenmiyor.  Bir hata olayı budur. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> Özel durum işleyicileri içinde bir CER giriş olarak işaretlemek için kullanılan yöntem çağrısı kendi `catch` / `finally` / `fault` / `filter` blokları, hemen önce kullanılmalıdır `try` deyimi.  
  
## <a name="resolution"></a>Çözüm  
 Çağrı emin <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> hemen önce gerçekleşir `try` deyimi.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bu mda'nın CLR üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 MDA yöntem çağırma adını görüntüler <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> yöntemi, MSIL uzaklığı ve çağrı değil hemen önünde try bloğunun başlangıcı belirten bir ileti.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bu mda'nın etkinleştirilmesi neden desenini gösterir.  
  
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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
