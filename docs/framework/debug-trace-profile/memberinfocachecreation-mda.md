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
ms.openlocfilehash: 028ff1048813ccbc845d5ad3e7f522b492348f87
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651038"
---
# <a name="memberinfocachecreation-mda"></a>memberInfoCacheCreation MDA
`memberInfoCacheCreation` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş olduğunda bir <xref:System.Reflection.MemberInfo> önbellek oluşturulur. Bu güçlü bir gösterge yapan bir programın, kaynak açısından pahalı yansıma özelliklerini kullanın.  
  
## <a name="symptoms"></a>Belirtiler  
 Programı kaynak açısından pahalı yansıma kullandığından bir program kümesi arttıkça çalışma.  
  
## <a name="cause"></a>Sebep  
 İlgili yansıma işlemleri <xref:System.Reflection.MemberInfo> nesneleri doğrudan sayfalarına depolanan meta veri okuması gerekir ve bunlar programın genel gösterir çünkü pahalı kaynak bazı tür geç bağlama senaryosu kullanarak değerlendirilir.  
  
## <a name="resolution"></a>Çözüm  
 Yansıma programınızda bu MDA etkinleştirme ve ardından bir hata ayıklayıcıda kod çalıştıran veya MDA etkinleştirildiğinde, hata ayıklayıcısı ile iliştirme kullanıldığı yerin belirleyebilirsiniz. Hata ayıklayıcı altında nerede gösteren bir yığın izlemesi alırsınız <xref:System.Reflection.MemberInfo> önbellek oluşturuldu ve buradan programınızı yansıma burada kullanarak belirleyebilirsiniz.  
  
 Çözüm üzerinde kod amaçlarını bağlıdır. Bu MDA, programınızın geç bağlama senaryosu olduğunu uyarır. Bir erken bağlanan senaryo değiştirin veya geç bağlanan senaryo performansını göz önünde bulundurun, belirlemek isteyebilirsiniz.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bu mda'nın için etkinleştirilen her <xref:System.Reflection.MemberInfo> oluşturulan önbellek. Performans etkisini göz ardı edilebilir.  
  
## <a name="output"></a>Çıkış  
 MDA belirten bir ileti çıkarır <xref:System.Reflection.MemberInfo> önbellek oluşturuldu. Bir hata ayıklayıcı, programınızın yansıma burada kullanarak gösteren bir yığın izlemesi almak için kullanın.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek kod etkinleştirecek `memberInfoCacheCreation` MDA.  
  
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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
