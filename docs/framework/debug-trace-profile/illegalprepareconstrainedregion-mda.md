---
title: illegalPrepareConstrainedRegion MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b739cb76827a12a9928e0268e5e2cb8be686479
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="illegalprepareconstrainedregion-mda"></a>illegalPrepareConstrainedRegion MDA
`illegalPrepareConstrainedRegion` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş olduğunda bir <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> yöntem çağrısı yok hemen önünde `try` özel durum işleyici ifadesi. Kaynak kodu oluşturma çağrısı arasında sahip izin verilebilir mi bu kısıtlama MSIL düzeyi, olduğundan ve `try`, Yorumlar gibi.  
  
## <a name="symptoms"></a>Belirtiler  
 Hiçbir zaman, bu nedenle ancak blok işleme basit bir özel durum olarak kabul edilir kısıtlı yürütme bölge (CER) (`finally` veya `catch`). Sonuç olarak, bölge bellek yetersiz koşul veya bir iş parçacığı iptal olayında çalışmaz.  
  
## <a name="cause"></a>Sebep  
 Bir CER için hazırlık deseni doğru gelmez.  Bir hata olayı budur. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> Özel durum işleyicileri bir CER giriş olarak işaretlemek için kullanılan yöntem çağrısı kendi `catch` / `finally` / `fault` / `filter` blokları kullanılan, hemen önce `try` deyimi.  
  
## <a name="resolution"></a>Çözüm  
 Çağrı emin <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> hemen önce gerçekleşir `try` deyimi.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA CLR üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Yöntem çağırma adını MDA görüntüler <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> yöntemi, MSIL uzaklık ve çağrı değil hemen önünde deneyin blok başlangıcı belirten bir ileti.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bu mda'nın etkinleştirilmesi neden düzeni gösterir.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
