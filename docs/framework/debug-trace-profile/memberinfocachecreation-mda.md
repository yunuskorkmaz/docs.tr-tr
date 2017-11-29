---
title: memberInfoCacheCreation MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member info cache creation
- MemberInfoCacheCreation MDA
- reflection, run-time errors
- MDAs (managed debugging assistants), cache
- cache [.NET Framework], reflection
- managed debugging assistants (MDAs), cache
- MemberInfo cache
ms.assetid: 5abdad23-1335-4744-8acb-934002c0b6fe
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1aeda59172e52c9880b39d6bf94ea9685a0203c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="memberinfocachecreation-mda"></a>memberInfoCacheCreation MDA
`memberInfoCacheCreation` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş olduğunda bir <xref:System.Reflection.MemberInfo> önbellek oluşturulur. Bu bir yapıyor bir program güçlü göstergesidir kaynak açısından pahalı yansıma özelliklerinin kullanımı.  
  
## <a name="symptoms"></a>Belirtiler  
 Program kaynak açısından pahalı yansıma kullandığından bir program kümesi artar çalışma.  
  
## <a name="cause"></a>Sebep  
 İçeren yansıma işlemleri <xref:System.Reflection.MemberInfo> nesneleri olarak kabul edilir çünkü soğuk sayfalarında depolanan meta veri okuması gerekir ve program Genel geldikleri pahalı kaynak geç bağlama senaryosu herhangi bir tür kullanıyor.  
  
## <a name="resolution"></a>Çözüm  
 Burada yansıma programınıza bu MDA etkinleştirme ve ardından bir hata ayıklayıcıda kodunuzu çalıştırmaya veya MDA etkinleştirilirken bir hata ayıklayıcısı ile ekleme kullanılıyor belirleyebilirsiniz. Hata ayıklayıcı altında yeri gösteren bir yığın izlemesi alırsınız <xref:System.Reflection.MemberInfo> önbellek oluşturuldu ve buradan programınızı yansıma burada kullanarak belirleyebilirsiniz.  
  
 Çözümleme kod amaçlarını bağlıdır. Bu MDA programınızı geç bağlama senaryosu olduğunu uyarır. Erken bağlama senaryosu değiştirin veya geç bağlama senaryosu performansını göz önünde bulundurun varsa belirlemek isteyebilirsiniz.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA için etkinleştirilen her <xref:System.Reflection.MemberInfo> oluşturulan önbelleği. Performans etkisi önemsizdir.  
  
## <a name="output"></a>Çıkış  
 MDA belirten bir ileti çıkarır <xref:System.Reflection.MemberInfo> önbellek oluşturuldu. Bir hata ayıklayıcısı programınızı yansıma burada kullanarak gösteren bir yığın izlemesi almak için kullanın.  
  
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
  
```  
using System;  
  
public class Exe  
{  
    public static void Main()  
    {  
        typeof(object).GetMethods();  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection.MemberInfo>  
 [Yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
