---
title: "WF etkinlik yazma seçenekleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9061f5f-12c3-47f0-adbe-1330e2714c94
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4ef85d6eaeb0fdb79960ae166cb1e83e88f6d529
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="activity-authoring-options-in-wf"></a>WF etkinlik yazma seçenekleri
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]özel etkinlikler oluşturmak için çeşitli seçenekler sağlar. Belirli bir etkinlik yazmak için kullanılacak doğru yöntemi hangi çalışma zamanı özellikleri gerekli bağlıdır.  
  
## <a name="deciding-which-base-activity-class-to-use-for-authoring-custom-activities"></a>Temel hangi etkinliğin sınıf özel etkinlikler yazma kullanmaya karar verme  
 Özel Etkinlik temel sınıflarda kullanılabilir özellikler aşağıdaki tabloda listelenmektedir.  
  
|Temel etkinliğe sınıfı|Kullanılabilir özellikler|  
|-------------------------|------------------------|  
|<xref:System.Activities.Activity>|Bileşik etkinlik sistem tarafından sağlanan ve özel etkinliklerine grupları oluşturur.|  
|<xref:System.Activities.CodeActivity>|Uygulayan kesinlik temelli işlevselliği sağlayarak bir <xref:System.Activities.CodeActivity%601.Execute%2A> geçersiz kılınabilir yöntemi. Ayrıca izleme, değişkenleri ve bağımsız değişkenler erişim sağlar...|  
|<xref:System.Activities.NativeActivity>|Tüm özellikleri sağlayan <xref:System.Activities.CodeActivity>, Etkinlik yürütme iptal ediliyor, alt etkinlik yürütme iptal ediliyor, yer işaretlerini kullanma ve etkinliklerini, etkinlik eylemleri ve işlevleri zamanlama artı.|  
|<xref:System.Activities.DynamicActivity>|WF Tasarımcısı ve çalışma zamanı makineler aracılığıyla arabirimleri etkinlikleri oluşturmak için bir DOM benzeri yaklaşımını sunar <!--zz <xref:System.ComponentModel.IcustomTypeDescriptor>--> `IcustomTypeDescriptor`, yeni türleri tanımlamadan oluşturulacak yeni etkinlikler izin verme.|  
  
## <a name="authoring-activities-using-activity"></a>Yazma etkinlikleri etkinlik kullanma  
 Öğesinden türetilen etkinlikleri <xref:System.Activities.Activity> varolan diğer etkinlikleri birleştirerek işlevselliği oluşturun. Bu etkinlikler varolan özel olabilir etkinlikleri ve etkinlikten [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] etkinlik kitaplığı. Bu etkinlikler birleştirme, özel işlevsellik oluşturmak için en temel bir yoludur. Bu yaklaşım, en yaygın iş akışları yazmak için bir görsel tasarım ortamında kullanırken alınır.  
  
## <a name="authoring-activities-using-codeactivity-or-asynccodeactivity"></a>Yazma etkinlikleri CodeActivity veya AsyncCodeActivity kullanma  
 Öğesinden türetilen etkinlikleri <xref:System.Activities.CodeActivity> veya <xref:System.Activities.AsyncCodeActivity> kesinlik temelli işlevselliği kılarak uygulayabilirsiniz <xref:System.Activities.CodeActivity%601.Execute%2A> özel kesinlik temelli kod ile yöntemi. Etkinlik çalışma zamanı tarafından çalıştırıldığında özel kod yürütülür. Bu yolla oluşturulan etkinlikleri özel işlevine erişimi olsa da, bunlar erişiminiz yok yürütme ortamı için tam erişim gibi çalışma zamanı özelliklerini tümüne alt etkinlikler, yer işareti oluşturma ya da desteği zamanlama olanağı bir İptal edin veya Abort yöntemi. Zaman bir <xref:System.Activities.CodeActivity> yürütür, erişim yürütme ortamı azaltılmış bir sürümüne sahip (aracılığıyla <xref:System.Activities.CodeActivityContext> veya <xref:System.Activities.AsyncCodeActivityContext> sınıfı). Kullanılarak oluşturulan etkinlikleri <xref:System.Activities.CodeActivity> bağımsız değişkeni ve değişken çözümleme, uzantıları ve izleme erişimi. Zaman uyumsuz aktivitesi zamanlama yapılabilir kullanarak <xref:System.Activities.AsyncCodeActivity>.  
  
## <a name="authoring-activities-using-nativeactivity"></a>Yazma etkinlikleri NativeActivity kullanma  
 Öğesinden türetilen etkinlikleri <xref:System.Activities.NativeActivity>, ister öğesinden türetilen o <xref:System.Activities.CodeActivity>, kesinlik temelli işlevselliğe kılarak oluşturmak <xref:System.Activities.NativeActivity.Execute%2A>, ancak aynı zamanda tüm iş akışı çalışma zamanı işlevselliğini erişimi <xref:System.Activities.NativeActivityContext> alır içine aktarılan <xref:System.Activities.NativeActivity.Execute%2A> yöntemi. Bu bağlamı zamanlama ve yürütme alt etkinlikleri iptal etme desteği olan <xref:System.Activities.ActivityAction> ve <!--zz <xref:System.Activities.ActivityFunc>--> `ActivityFunc` nesneleri, iptal etme ve yürütme durduruluyor zaman uyumsuz işlemleri, çağırma bir iş akışı boyunca işlemlere erişim yürütme özellikler ve uzantılar ve yer işaretleri (işleç devam ettirme duraklatılmış iş akışları için).  
  
## <a name="authoring-activities-using-dynamicactivity"></a>Yazma etkinlikleri DynamicActivity kullanma  
 Diğer üç tür etkinlik farklı olarak, yeni işlevsellik yeni türlerinden türetme tarafından oluşturulmaz <xref:System.Activities.DynamicActivity> (sınıf korumalı değil), ancak bunun yerine, işlevsellik atayarak tarafından <xref:System.Activities.DynamicActivity.Properties%2A> ve <xref:System.Activities.DynamicActivity.Implementation%2A> kullanarak bir etkinlik belge özellikleri Nesne Modeli (DOM).  
  
## <a name="authoring-activities-that-return-a-result"></a>Bir sonuç yazma etkinliği  
 Birçok etkinlik kendi yürütme sonrasında bir sonuç döndürmesi gerekir. Her zaman özel tanımlama mümkün olmakla <xref:System.Activities.OutArgument%601> kullanmayı önerilen bu amaç için bir etkinlik üzerinde <xref:System.Activities.Activity%601>, veya öğesinden türetilen <xref:System.Activities.CodeActivity%601> veya <xref:System.Activities.NativeActivity%601>. Bu temel sınıfların her biri olan bir <xref:System.Activities.OutArgument%601> etkinliklerinizi dönüş değeri için kullanabileceğiniz sonuç adlı. Bir sonuç etkinliği döndürülmesi gereken yalnızca bir sonuç etkinlikleri yalnızca kullanılmalıdır; birden çok sonuç döndürülmesi gerekiyorsa, ayrı <xref:System.Activities.OutArgument%601> üyeleri bunun yerine kullanılmalıdır.
