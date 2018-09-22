---
title: WF etkinlik yazma seçenekleri
ms.date: 03/30/2017
ms.assetid: b9061f5f-12c3-47f0-adbe-1330e2714c94
ms.openlocfilehash: 219d759cd1390a83abfb90af509b21047085f6e9
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46697678"
---
# <a name="activity-authoring-options-in-wf"></a>WF etkinlik yazma seçenekleri
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] özel etkinlikler oluşturmak için çeşitli seçenekler sunar. Belirli bir etkinlik yazma için kullanılacak doğru yöntemi hangi çalışma zamanı özellikleri gerekli mı olduğuna bağlıdır.  
  
## <a name="deciding-which-base-activity-class-to-use-for-authoring-custom-activities"></a>Hangi temel etkinlik sınıf özel etkinlikler yazmak için kullanılacak karar verme  
 Özel Etkinlik taban sınıflardaki kullanılabilen özellikler aşağıdaki tabloda listelenmektedir.  
  
|Temel etkinlik sınıfı|Kullanılabilir özellikler|  
|-------------------------|------------------------|  
|<xref:System.Activities.Activity>|Sistem tarafından sağlanan ve özel bileşik bir etkinlik etkinliklerine gruplarını oluşturur.|  
|<xref:System.Activities.CodeActivity>|Sağlayarak kesinlik temelli işlevselliğini uygulayan bir <xref:System.Activities.CodeActivity%601.Execute%2A> geçersiz kılınabilir bir yöntemi. Ayrıca, izleme, değişkenler ve bağımsız değişkenler erişim sağlar...|  
|<xref:System.Activities.NativeActivity>|Tüm özellikleri sağlayan <xref:System.Activities.CodeActivity>, Etkinlik yürütme iptal ediliyor, alt etkinlik yürütme iptal ediliyor, yer işaretlerini kullanma ve etkinliklerini, etkinlik eylemleri ve işlevleri zamanlama artı.|  
|<xref:System.Activities.DynamicActivity>|WF tasarımcı ve çalışma zamanı makineler aracılığıyla arabirimleri etkinlikleri oluşturmak için bir DOM benzeri yaklaşım sağlar <xref:System.ComponentModel.ICustomTypeDescriptor>, izin vererek yeni türleri tanımlama olmadan oluşturulacak yeni etkinlikler.|  
  
## <a name="authoring-activities-using-activity"></a>Geliştirme etkinlikleri etkinlik kullanma  
 Öğesinden türetilen etkinlikleri <xref:System.Activities.Activity> işlevselliği varolan diğer etkinlikleri birleştirerek oluşturun. Bu etkinlikler mevcut özel olabilir etkinlikleri ve etkinlikler [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] etkinlik kitaplığı. Bu etkinlikler derleyerek, özel işlevler oluşturmak için en temel bir yoludur. Bu yaklaşım, en yaygın iş akışları yazmak için bir görsel tasarım ortamı kullanarak alınır.  
  
## <a name="authoring-activities-using-codeactivity-or-asynccodeactivity"></a>Geliştirme etkinlikleri CodeActivity veya AsyncCodeActivity kullanma  
 Öğesinden türetilen etkinlikleri <xref:System.Activities.CodeActivity> veya <xref:System.Activities.AsyncCodeActivity> kesinlik temelli işlevi geçersiz kılarak uygulayabilirsiniz <xref:System.Activities.CodeActivity%601.Execute%2A> özel kesinlik temelli kod ile yöntemi. Etkinliğin çalışma zamanı tarafından yürütüldüğünde, özel kod yürütülür. Bu şekilde oluşturulan etkinlikleri özel işlevler için erişimi olsa da, bunlar erişiminiz yok çalışma zamanının yürütme ortamı için tam erişim gibi özelliklerin tümü için zamanlayabilme alt etkinlikleri, yer işareti oluşturma veya destek için bir İptal etme veya Abort yöntemi. Olduğunda bir <xref:System.Activities.CodeActivity> yürütür, Yürütme Ortamı'nın daha düşük bir sürüme erişiminin (aracılığıyla <xref:System.Activities.CodeActivityContext> veya <xref:System.Activities.AsyncCodeActivityContext> sınıfı). Kullanılarak oluşturulan etkinlikleri <xref:System.Activities.CodeActivity> bağımsız değişken ve değişken çözümü, uzantıları ve izleme erişebilir. Zaman uyumsuz bir etkinlik zamanlama yapılabilir kullanarak <xref:System.Activities.AsyncCodeActivity>.  
  
## <a name="authoring-activities-using-nativeactivity"></a>Geliştirme etkinlikleri NativeActivity kullanma  
 Öğesinden türetilen etkinlikleri <xref:System.Activities.NativeActivity>, ister, türetilen <xref:System.Activities.CodeActivity>, geçersiz kılarak kesinlik temelli işlevi oluşturma <xref:System.Activities.NativeActivity.Execute%2A>, ancak tüm işlevleri iş akışı çalışma zamanı erişimi de <xref:System.Activities.NativeActivityContext> alır yöntemlere geçirilen <xref:System.Activities.NativeActivity.Execute%2A> yöntemi. Bu bağlam için zamanlama ve yürütme, çocuk etkinliklerinin iptal etme desteği olan <xref:System.Activities.ActivityAction> ve <xref:System.Activities.ActivityFunc%601> nesneleri, zaman uyumsuz işlemlerin iptal etme ve yürütme iptal ediliyor çağrılırken bir iş akışı işlemleri akan erişmek için yürütme Özellikler ve uzantılar ve yer işaretlerini (işleç sürdürme duraklatılmış iş akışları için).  
  
## <a name="authoring-activities-using-dynamicactivity"></a>Geliştirme etkinlikleri DynamicActivity kullanma  
 Diğer üç tür etkinliği, yeni işlevsellik yeni türleri türetme tarafından oluşturulmaz <xref:System.Activities.DynamicActivity> (sınıfı korumalı), ancak bunun yerine, işlevlerini birleştirme tarafından <xref:System.Activities.DynamicActivity.Properties%2A> ve <xref:System.Activities.DynamicActivity.Implementation%2A> kullanarak bir etkinlik belge özellikleri Nesne Modeli (DOM).  
  
## <a name="authoring-activities-that-return-a-result"></a>Bir sonuç yazma etkinliği  
 Birçok etkinlik kendi yürütme sonrasında bir sonuç döndürmesi gerekir. Her zaman özel bir tanımlamak mümkündür ancak <xref:System.Activities.OutArgument%601> kullanmayı önerilen bu amaç için bir etkinliğe bağlı <xref:System.Activities.Activity%601>, ya da türetilen <xref:System.Activities.CodeActivity%601> veya <xref:System.Activities.NativeActivity%601>. Bu temel sınıfların her bir <xref:System.Activities.OutArgument%601> adlı dönüş değeri için etkinliğinizi kullanan sonucu. Tek bir sonuç etkinliği döndürülmesi gereken yalnızca bir sonuç etkinlikleri yalnızca kullanılmalıdır; birden çok sonuç döndürülmesi gerekiyorsa ayrı <xref:System.Activities.OutArgument%601> üyeleri bunun yerine kullanılmalıdır.
