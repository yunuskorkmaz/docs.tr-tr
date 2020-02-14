---
title: memberInfoCacheCreation MDA
ms.date: 03/30/2017
helpviewer_keywords:
- member info cache creation
- MemberInfoCacheCreation MDA
- reflection, run-time errors
- MDAs (managed debugging assistants), cache
- cache [.NET Framework], reflection
- managed debugging assistants (MDAs), cache
- MemberInfo cache
ms.assetid: 5abdad23-1335-4744-8acb-934002c0b6fe
ms.openlocfilehash: e5dbc769bd634afae06582ee614addafd611fad9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217307"
---
# <a name="memberinfocachecreation-mda"></a>memberInfoCacheCreation MDA
`memberInfoCacheCreation` yönetilen hata ayıklama Yardımcısı (MDA), bir <xref:System.Reflection.MemberInfo> önbelleği oluşturulduğunda etkinleştirilir. Bu, kaynak maliyetli yansıma özelliklerini kullanan bir programın güçlü bir göstergesidir.  
  
## <a name="symptoms"></a>Belirtiler  
 Program kaynak maliyetli yansıma kullandığından programın çalışma kümesi artar.  
  
## <a name="cause"></a>Nedeni  
 <xref:System.Reflection.MemberInfo> nesneleri içeren yansıma işlemleri, soğuk sayfalarda depolanan meta verileri okuması ve genel olarak programın bir tür geç bağlantılı senaryo kullandığını belirtmesi gerektiğinden kaynak maliyetli olarak değerlendirilir.  
  
## <a name="resolution"></a>Çözüm  
 Bu MDA ' ı etkinleştirerek ve sonra kodunuzu bir hata ayıklayıcıda çalıştırarak veya MDA etkinleştirildiğinde bir hata ayıklayıcı ile iliştirerek, yansıma programınızda nerede kullanıldığını belirleyebilirsiniz. Bir hata ayıklayıcı altında, <xref:System.Reflection.MemberInfo> önbelleğinin nerede oluşturulduğunu ve buradan, programınızın yansıma kullandığını belirleyebileceğiniz bir yığın izlemesi alacaksınız.  
  
 Çözüm, kodun hedeflerine bağımlıdır. Bu MDA, programınızın geç bağlanan bir senaryoya sahip olduğunu uyarır. Erken bağlantılı bir senaryoyu değiştirebilir veya geç bağlantılı senaryonun performansını göz önünde bulundurup belirleyemeyebilirsiniz.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, oluşturulan her <xref:System.Reflection.MemberInfo> önbelleği için etkinleştirilir. Performans etkisi göz ardı edilebilir değil.  
  
## <a name="output"></a>Çıktı  
 MDA <xref:System.Reflection.MemberInfo> önbelleğinin oluşturulduğunu belirten bir ileti çıkışı verir. Programınızın yansıma kullandığını gösteren bir yığın izlemesi almak için bir hata ayıklayıcı kullanın.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek kod `memberInfoCacheCreation` MDA ' i etkinleştirir.  
  
```csharp
using System;  
  
public class Exe  
{  
    public static void Main()  
    {  
        typeof(object).GetMethods();  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.MemberInfo>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
