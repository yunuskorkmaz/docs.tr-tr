---
title: 'Nasıl Yapılır: Hizmet Bilgilerini Günlüğe Kaydetme'
ms.date: 03/30/2017
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
author: ghogen
ms.openlocfilehash: 5556b83346aba5bc48eddb930dedc56f4786bdb5
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47113630"
---
# <a name="how-to-log-information-about-services"></a>Nasıl Yapılır: Hizmet Bilgilerini Günlüğe Kaydetme
Varsayılan olarak, tüm Windows Service projeleri uygulama olay günlüğü ile etkileşimli ve bilgi ve özel durumlar yazma olanağı vardır. Kullandığınız <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> uygulamanızda bu işlevi isteyip istemediğinizi belirtmek için özelliği. Varsayılan olarak, Windows hizmeti proje şablonu ile oluşturduğunuz herhangi bir hizmeti için günlüğe kaydetme açıktır. Statik bir formu kullanabilirsiniz <xref:System.Diagnostics.EventLog> sınıfı örneğini oluşturmak zorunda kalmadan hizmet bilgilerini günlüğe yazılacak bir <xref:System.Diagnostics.EventLog> bileşen veya el ile bir kaynak kaydı.  
  
 Hizmetiniz için yükleyici, projenizdeki her hizmet günlüğe kaydetme açık olduğunda, hizmet, yüklü olduğu geçerli bir kaynak bilgisayardaki Uygulama günlüğünü içeren olayların sayısını otomatik olarak kaydeder. Hizmet, hizmet çalışmaya, durdurulmuş, duraklatılmış, sürdürüldü, yüklü veya her saat bilgilerini günlüğe kaydeder. Ayrıca, oluşan tüm hataları kaydeder. Varsayılan davranış kullanırken girişleri günlüğüne yazmak için kod yazmanız gerekmez; Hizmet bunu sizin için otomatik olarak yönetir.  
  
 Uygulama günlüğünü dışındaki bir olay günlüğüne yazmak istiyorsanız, ayarlamalısınız <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> özelliğini `false`, kendi özel olay günlüğü Hizmetleri kodunuz içinde oluşturup hizmetiniz, günlük girişlerinin geçerli bir kaynak olarak kaydedin. Ardından, girişlerini ilginizi çeken bir eylem olduğunda günlüğe kaydetmek için kod yazmanız gerekir.  
  
> [!NOTE]
>  Eğer özel bir olay günlüğü'nün ve yazma service uygulamanızı yapılandırma, hizmetin ayarlamadan önce olay günlüğüne erişmek kullanmamanız gerekir <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> kodunuzdaki özellik. Olay günlüğü, hizmet geçerli bir olay kaynağı kaydetmek için bu özelliğin değerini gerekir.  
  
### <a name="to-enable-default-event-logging-for-your-service"></a>Hizmetiniz için varsayılan olay günlüğünü etkinleştirme  
  
-   Ayarlama <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> bileşeniniz için özellik `true`.  
  
    > [!NOTE]
    >  Varsayılan olarak, bu özellik kümesine `true`. Bir koşulu değerlendirmek ve ardından ayarlar gibi daha karmaşık bir işlem, oluşturmakta olduğunuz sürece bu açıkça ayarlamanız gerekmez <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> özelliği bu koşulun sonucuna bağlı.  
  
### <a name="to-disable-event-logging-for-your-service"></a>Hizmetiniz için olay günlüğünü devre dışı bırakmak için  
  
-   Ayarlama <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> bileşeniniz için özellik `false`.  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a>Özel günlük için'günlük kaydı ayarlamak için  
  
1.  Ayarlama <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> özelliğini `false`.  
  
    > [!NOTE]
    >  Ayarlamalısınız <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> özel bir günlük kullanmak için false.  
  
2.  Bir örneği bir <xref:System.Diagnostics.EventLog> Windows hizmeti uygulamanızda bileşen.  
  
3.  Özel günlük çağırarak oluşturmak <xref:System.Diagnostics.EventLog.CreateEventSource%2A> yöntemi ve kaynak dizeyi ve günlük adını dosyasını belirtme oluşturmak istiyorsanız.  
  
4.  Ayarlama <xref:System.Diagnostics.EventLog.Source%2A> özelliği <xref:System.Diagnostics.EventLog> bileşen örneği için 3. adımda oluşturduğunuz kaynak dizesi.  
  
5.  Girdilerinizi erişerek yazma <xref:System.Diagnostics.EventLog.WriteEntry%2A> metodunda <xref:System.Diagnostics.EventLog> bileşen örneği.  
  
     Aşağıdaki kod, özel bir günlük için günlük kaydı ayarlamak gösterilmektedir.  
  
    > [!NOTE]
    >  Bu kod örneğinde, örneği bir <xref:System.Diagnostics.EventLog> bileşeni adlı `eventLog1` (`EventLog1` Visual Basic'te). 2. adımda başka bir adla örneği oluşturduysanız, kodu uygun şekilde değiştirin.  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
