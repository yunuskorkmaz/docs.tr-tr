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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d3b65ecc226c1caf7b53d746f0583e1f57c7d8c1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052464"
---
# <a name="memberinfocachecreation-mda"></a>memberInfoCacheCreation MDA
Yönetilen `memberInfoCacheCreation` hata ayıklama Yardımcısı (MDA), bir <xref:System.Reflection.MemberInfo> önbellek oluşturulduğunda etkinleştirilir. Bu, kaynak maliyetli yansıma özelliklerini kullanan bir programın güçlü bir göstergesidir.  
  
## <a name="symptoms"></a>Belirtiler  
 Program kaynak maliyetli yansıma kullandığından programın çalışma kümesi artar.  
  
## <a name="cause"></a>Sebep  
 <xref:System.Reflection.MemberInfo> Nesneleri içeren yansıma işlemleri, soğuk sayfalarda depolanan meta verileri okuması ve genel olarak programın bazı tür geç bağlantılı senaryolar kullandığını belirtmesi gerektiğinden kaynak maliyetli olarak değerlendirilir.  
  
## <a name="resolution"></a>Çözüm  
 Bu MDA ' ı etkinleştirerek ve sonra kodunuzu bir hata ayıklayıcıda çalıştırarak veya MDA etkinleştirildiğinde bir hata ayıklayıcı ile iliştirerek, yansıma programınızda nerede kullanıldığını belirleyebilirsiniz. Bir hata ayıklayıcı altında, <xref:System.Reflection.MemberInfo> önbelleğin nerede oluşturulduğunu gösteren bir yığın izlemesi alırsınız ve bu noktada programınızın yansıma kullandığını belirleyebilirsiniz.  
  
 Çözüm, kodun hedeflerine bağımlıdır. Bu MDA, programınızın geç bağlanan bir senaryoya sahip olduğunu uyarır. Erken bağlantılı bir senaryoyu değiştirebilir veya geç bağlantılı senaryonun performansını göz önünde bulundurup belirleyemeyebilirsiniz.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu mda, oluşturulan her <xref:System.Reflection.MemberInfo> önbellek için etkinleştirilir. Performans etkisi göz ardı edilebilir değil.  
  
## <a name="output"></a>Çıkış  
 MDA, <xref:System.Reflection.MemberInfo> önbelleğin oluşturulduğunu belirten bir ileti çıkışı verir. Programınızın yansıma kullandığını gösteren bir yığın izlemesi almak için bir hata ayıklayıcı kullanın.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek kod, `memberInfoCacheCreation` MDA öğesini etkinleştirececektir.  
  
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
