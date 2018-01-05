---
title: "Nasıl Yapılır: Hizmet Bilgilerini Günlüğe Kaydetme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutoLog property
- services, logging information
- Windows Service applications, logging information about
- event logs, service applications
- application event logs, service applications
- logs, service applications
ms.assetid: c0d8140f-c055-4d8e-a2e0-37358a550116
caps.latest.revision: "17"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 2dabc20c3cd3a97ed86dc45436eaad5e7a07c91a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-log-information-about-services"></a>Nasıl Yapılır: Hizmet Bilgilerini Günlüğe Kaydetme
Varsayılan olarak, tüm Windows hizmeti projelerinin uygulama olay günlüğü ile etkileşim ve bilgi ve özel durumları yazma özelliği vardır. Kullandığınız <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> özelliği, bu işlev, uygulamanızda isteyip istemediğinizi belirtin. Varsayılan olarak, Windows hizmeti proje şablonu ile oluşturduğunuz herhangi bir hizmeti için günlüğe kaydetme açıktır. Statik bir form, kullanabileceğiniz <xref:System.Diagnostics.EventLog> sınıfının bir örneğini oluşturmak zorunda kalmadan hizmet bilgilerini günlüğe yazma bir <xref:System.Diagnostics.EventLog> bileşeni veya el ile bir kaynak kaydı.  
  
 Hizmetiniz için yükleyici projenizde her bir hizmet olarak geçerli bir kaynak günlük kaydı etkinken hizmet, yüklendiği bilgisayarda uygulama günlüğü ile olayların otomatik olarak kaydeder. Hizmet bilgileri hizmet başlatıldı, durduruldu, sürdürüldü, yüklü, kaldırıldı veya duraklatıldı her zaman günlüğe kaydeder. Ortaya çıkan hataları günlüğe kaydeder. Varsayılan davranışı kullanırken girişleri günlüğüne yazılması için herhangi bir kod yazmak zorunda kalmazsınız; Hizmet bunu sizin için otomatik olarak yönetir.  
  
 Uygulama günlüğü dışında bir olay günlüğüne yazmak istiyorsanız, ayarlamalısınız <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> özelliğine `false`, kendi özel olay günlüğü Hizmetleri kodunuzu içinde oluşturun ve hizmetiniz, günlük girişlerinin geçerli bir kaynak olarak kaydedin. Ardından oluşur girişlerini ilgilendiğiniz bir eylem olduğunda günlüğe kaydetmek için kod yazmanız gerekir.  
  
> [!NOTE]
>  Özel bir olay günlüğü kullanın ve hizmet uygulamanızın yazma yapılandırırsanız, hizmetin ayarlamadan önce olay günlüğüne erişmek çalışmamalısınız <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> kodunuzda özelliği. Olay günlüğü hizmetinizi olayların geçerli bir kaynak kaydetmek için bu özelliğin değeri gerekir.  
  
### <a name="to-enable-default-event-logging-for-your-service"></a>Hizmetiniz için varsayılan olay günlüğünü etkinleştirmek için  
  
-   Ayarlama <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> bileşeniniz için özellik `true`.  
  
    > [!NOTE]
    >  Varsayılan olarak, bu özelliği ayarlamak `true`. Bir koşulu değerlendirmek ve ardından ayarlama gibi daha karmaşık işlem oluşturmakta olduğunuz sürece açıkça ayarlamanız gerekmez <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> özelliği bu koşulun sonucuna bağlı.  
  
### <a name="to-disable-event-logging-for-your-service"></a>Hizmetiniz için olay günlüğünü devre dışı bırakmak için  
  
-   Ayarlama <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> bileşeniniz için özellik `false`.  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a>Özel günlük günlüğünü ayarlamak için  
  
1.  Ayarlama <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> özelliğine `false`.  
  
    > [!NOTE]
    >  Ayarlamalısınız <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> özel bir günlük kullanmak için false.  
  
2.  Ayarlanan örneği bir <xref:System.Diagnostics.EventLog> Windows hizmeti uygulamanızda bileşen.  
  
3.  Özel günlük çağırarak oluşturun <xref:System.Diagnostics.EventLog.CreateEventSource%2A> yöntemi ve kaynak dizesi ve günlük adını dosyası belirterek oluşturmak istiyorsanız.  
  
4.  Ayarlama <xref:System.Diagnostics.EventLog.Source%2A> özellikte <xref:System.Diagnostics.EventLog> bileşen örneği için 3. adımda oluşturduğunuz kaynak dizesi.  
  
5.  Erişerek girişlerinizi yazma <xref:System.Diagnostics.EventLog.WriteEntry%2A> yöntemi <xref:System.Diagnostics.EventLog> bileşen örneği.  
  
     Aşağıdaki kod, özel bir günlük günlüklerini ayarlayın gösterilmektedir.  
  
    > [!NOTE]
    >  Bu kod örneğinde, örneği bir <xref:System.Diagnostics.EventLog> bileşen adlandırılan `eventLog1` (`EventLog1` Visual Basic'te). 2. adımda başka bir adla örneğini oluşturduysanız, kodu uygun şekilde değiştirin.  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
