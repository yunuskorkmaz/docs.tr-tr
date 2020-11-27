---
title: memberInfoCacheCreation MDA
description: .NET 'teki memberInfoCacheCreation Managed hata ayıklama Yardımcısı 'nı (MDA), bir MemberInfo önbelleği oluşturulduğunda etkinleştirilen şekilde anlayın.
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
ms.openlocfilehash: 44d279a949ca0b35c46f805e65eb6f61ffb532f1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271167"
---
# <a name="memberinfocachecreation-mda"></a>memberInfoCacheCreation MDA

`memberInfoCacheCreation`Yönetilen hata ayıklama Yardımcısı (MDA), bir <xref:System.Reflection.MemberInfo> önbellek oluşturulduğunda etkinleştirilir. Bu, kaynak maliyetli yansıma özelliklerini kullanan bir programın güçlü bir göstergesidir.  
  
## <a name="symptoms"></a>Belirtiler  

 Program kaynak maliyetli yansıma kullandığından programın çalışma kümesi artar.  
  
## <a name="cause"></a>Nedeni  

 Nesneleri içeren yansıma işlemleri, <xref:System.Reflection.MemberInfo> soğuk sayfalarda depolanan meta verileri okuması ve genel olarak programın bazı tür geç bağlantılı senaryolar kullandığını belirtmesi gerektiğinden kaynak maliyetli olarak değerlendirilir.  
  
## <a name="resolution"></a>Çözüm  

 Bu MDA ' ı etkinleştirerek ve sonra kodunuzu bir hata ayıklayıcıda çalıştırarak veya MDA etkinleştirildiğinde bir hata ayıklayıcı ile iliştirerek, yansıma programınızda nerede kullanıldığını belirleyebilirsiniz. Bir hata ayıklayıcı altında, önbelleğin nerede oluşturulduğunu gösteren bir yığın izlemesi alırsınız ve bu noktada <xref:System.Reflection.MemberInfo> programınızın yansıma kullandığını belirleyebilirsiniz.  
  
 Çözüm, kodun hedeflerine bağımlıdır. Bu MDA, programınızın geç bağlanan bir senaryoya sahip olduğunu uyarır. Erken bağlantılı bir senaryoyu değiştirebilir veya geç bağlantılı senaryonun performansını göz önünde bulundurup belirleyemeyebilirsiniz.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  

 Bu MDA, oluşturulan her önbellek için etkinleştirilir <xref:System.Reflection.MemberInfo> . Performans etkisi göz ardı edilebilir değil.  
  
## <a name="output"></a>Çıkış  

 MDA, önbelleğin oluşturulduğunu belirten bir ileti çıkışı verir <xref:System.Reflection.MemberInfo> . Programınızın yansıma kullandığını gösteren bir yığın izlemesi almak için bir hata ayıklayıcı kullanın.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  

 Bu örnek kod, MDA öğesini etkinleştirececektir `memberInfoCacheCreation` .  
  
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
