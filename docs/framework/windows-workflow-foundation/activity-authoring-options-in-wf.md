---
description: "Daha fazla bilgi edinin: WF 'de etkinlik yazma seçenekleri"
title: WF 'de etkinlik yazma seçenekleri
ms.date: 03/30/2017
ms.assetid: b9061f5f-12c3-47f0-adbe-1330e2714c94
ms.openlocfilehash: 5f200f11f1643a9da6c8a14a40ef9c0bb1d607b6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787987"
---
# <a name="activity-authoring-options-in-wf"></a>WF 'de etkinlik yazma seçenekleri

[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] özel etkinlikler oluşturmak için çeşitli seçenekler sağlar. Belirli bir etkinliği yazmak için kullanılan doğru yöntem, hangi çalışma zamanı özelliklerinin gerekli olduğuna bağlıdır.  
  
## <a name="deciding-which-base-activity-class-to-use-for-authoring-custom-activities"></a>Özel etkinlikler yazmak için hangi temel etkinlik sınıfının kullanılacağına karar verme  

 Aşağıdaki tabloda özel etkinlik taban sınıflarında kullanılabilen özellikler listelenmiştir.  
  
|Temel etkinlik sınıfı|Kullanılabilir özellikler|  
|-------------------------|------------------------|  
|<xref:System.Activities.Activity>|Sistem tarafından sağlanmış ve özel etkinliklerin gruplarını bileşik bir etkinliğe ayırır.|  
|<xref:System.Activities.CodeActivity>|Geçersiz kılınabilen bir yöntem sağlayarak zorunlu işlevselliği uygular <xref:System.Activities.CodeActivity%601.Execute%2A> . Ayrıca, izleme, değişkenler ve bağımsız değişkenlere erişim sağlar.|  
|<xref:System.Activities.NativeActivity>|Tüm özelliklerinin <xref:System.Activities.CodeActivity> yanı sıra etkinlik yürütmeyi iptal etmeyi, alt etkinlik yürütmeyi iptal etmeyi, yer imlerini ve zamanlama etkinliklerini, etkinlik eylemlerini ve işlevleri sağlar.|  
|<xref:System.Activities.DynamicActivity>|, WF Tasarımcısı ve çalışma zamanı makineler ile arabirimleri olan etkinlikleri oluşturmak için DOM benzeri bir yaklaşım sağlar <xref:System.ComponentModel.ICustomTypeDescriptor> . yeni etkinliklerin yeni türler tanımlanmaksızın oluşturulmasını sağlar.|  
  
## <a name="authoring-activities-using-activity"></a>Etkinlik kullanarak etkinlikleri yazma  

 <xref:System.Activities.Activity>Diğer mevcut etkinlikleri derleyerek oluşturma işlevlerinden türeten etkinlikler. Bu etkinlikler, etkinlik kitaplığından var olan özel etkinlikler ve Etkinlikler olabilir [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] . Bu etkinlikleri montaj, özel işlevler oluşturmanın en temel yoludur. Bu yaklaşım genellikle iş akışları yazmak için görsel tasarım ortamı kullanılırken alınır.  
  
## <a name="authoring-activities-using-codeactivity-or-asynccodeactivity"></a>CodeActivity veya AsyncCodeActivity kullanarak etkinlikleri yazma  

 Veya ' den türetilen etkinlikler özel bir zorunlu <xref:System.Activities.CodeActivity> <xref:System.Activities.AsyncCodeActivity> kodla yöntemi geçersiz kılarak, zorunlu işlevselliği uygulayabilir <xref:System.Activities.CodeActivity%601.Execute%2A> . Özel kod, etkinlik çalışma zamanı tarafından yürütüldüğünde yürütülür. Bu şekilde oluşturulan etkinliklerin özel işlevlere erişimi olduğu sürece, yürütme ortamına tam erişim, alt etkinlikleri zamanlama, yer işareti oluşturma veya Iptal ya da Iptal yöntemi için destek gibi çalışma zamanının tüm özelliklerine erişemez. Bir <xref:System.Activities.CodeActivity> yürütüldüğünde, yürütme ortamının azaltılmış bir sürümüne erişimi vardır ( <xref:System.Activities.CodeActivityContext> veya <xref:System.Activities.AsyncCodeActivityContext> sınıfı aracılığıyla). Kullanılarak oluşturulan etkinliklerin <xref:System.Activities.CodeActivity> bağımsız değişken ve değişken çözümüne, uzantılarına ve izlemeye erişimi vardır. Zaman uyumsuz etkinlik zamanlaması kullanılarak yapılabilir <xref:System.Activities.AsyncCodeActivity> .  
  
## <a name="authoring-activities-using-nativeactivity"></a>NativeActivity kullanarak etkinlikleri yazma  

 Öğesinden <xref:System.Activities.NativeActivity> türeten türetilmiş olanlar gibi, ' den türetilen etkinlikler, <xref:System.Activities.CodeActivity> geçersiz kılan, zorunlu işlevsellik oluşturma <xref:System.Activities.NativeActivity.Execute%2A> , ancak aynı zamanda yöntemine geçirilen iş akışı çalışma zamanının tüm işlevlerine erişimi de vardır <xref:System.Activities.NativeActivityContext> <xref:System.Activities.NativeActivity.Execute%2A> . Bu bağlam, alt etkinlikleri zamanlama ve iptal etme, yürütme <xref:System.Activities.ActivityAction> ve <xref:System.Activities.ActivityFunc%601> nesneler, işlemleri bir iş akışında akışa alma, zaman uyumsuz işlemleri çağırma, yürütmeyi iptal etme ve iptal etme, yürütme özelliklerine ve uzantılarına erişme ve çalışma işaretlerine (duraklatılmış iş akışlarını sürdürmek için tutamaçlar) destek içerir.  
  
## <a name="authoring-activities-using-dynamicactivity"></a>DynamicActivity kullanarak etkinlikleri yazma  

 Diğer üç etkinlik türünden farklı olarak, yeni türler ' den türeterek <xref:System.Activities.DynamicActivity> (sınıf mühürlenmiş), ancak bunun yerine, <xref:System.Activities.DynamicActivity.Properties%2A> <xref:System.Activities.DynamicActivity.Implementation%2A> bir etkinlik belge nesne modeli (DOM) kullanarak ve özelliklerine işlevsellik derleyerek.  
  
## <a name="authoring-activities-that-return-a-result"></a>Sonuç döndüren etkinlikleri yazma  

 Birçok etkinlik yürütmeden sonra bir sonuç döndürmelidir. Bu amaçla bir etkinlik üzerinde her zaman özel bir şekilde tanımlanması mümkün olsa da <xref:System.Activities.OutArgument%601> , bunun yerine kullanılması önerilir <xref:System.Activities.Activity%601> veya veya ' dan türetebilirsiniz <xref:System.Activities.CodeActivity%601> <xref:System.Activities.NativeActivity%601> . Bu temel sınıfların her birinin, <xref:System.Activities.OutArgument%601> etkinliğinizin dönüş değeri için kullanabileceği adlandırılmış bir sonucu vardır. Bir sonuç döndüren etkinlikler yalnızca bir etkinliğin yalnızca bir sonucun döndürülmesi gerekiyorsa kullanılmalıdır; birden çok sonucun döndürülmesi gerekiyorsa, <xref:System.Activities.OutArgument%601> bunun yerine ayrı Üyeler kullanılmalıdır.
