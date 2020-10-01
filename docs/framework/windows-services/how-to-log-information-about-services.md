---
title: 'Nasıl yapılır: Hizmet Bilgilerini Günlüğe Kaydetme'
description: Hizmetlerle ilgili bilgilerin nasıl günlüğe alınacağını öğrenin. Windows hizmeti projenizin uygulama olay günlüğü ile etkileşimini istiyorsanız, oto günlüğü özelliğini ayarlayın.
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
ms.openlocfilehash: 0d6c245e3defb7d518093cca904572d3db00fcf8
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608562"
---
# <a name="how-to-log-information-about-services"></a>Nasıl yapılır: Hizmet Bilgilerini Günlüğe Kaydetme
Varsayılan olarak, tüm Windows hizmeti projelerinin uygulama olay günlüğü ile etkileşim kurma ve bu bilgilere yazma bilgileri ve özel durumları vardır. <xref:System.ServiceProcess.ServiceBase.AutoLog%2A>Uygulamanızda bu işlevselliği isteyip istemediğinizi belirtmek için özelliğini kullanın. Varsayılan olarak, Windows hizmeti proje şablonuyla oluşturduğunuz her hizmet için günlük kaydı açıktır. Bir <xref:System.Diagnostics.EventLog> bileşenin örneğini oluşturmak <xref:System.Diagnostics.EventLog> veya bir kaynağı el ile kaydetmek zorunda kalmadan hizmet bilgilerini bir günlüğe yazmak için sınıfının statik bir biçimini kullanabilirsiniz.  
  
 Hizmetiniz için yükleyici, günlük kaydı açık olduğunda, hizmetin yüklendiği bilgisayardaki uygulama günlüğü ile projenizdeki her hizmeti otomatik olarak geçerli bir olay kaynağı olarak kaydeder. Hizmetin başlatıldığı, durdurulduğu, duraklatıldığı, kaldığı, yüklendiği veya kaldırıldığı her seferinde hizmet bilgileri günlüğe kaydedilir. Ayrıca oluşan tüm sorunları günlüğe kaydeder. Varsayılan davranışı kullanırken günlüğe giriş yazmak için herhangi bir kod yazmanız gerekmez; hizmet bunu sizin için otomatik olarak işler.  
  
 Uygulama günlüğü dışında bir olay günlüğüne yazmak isterseniz, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> özelliği olarak ayarlamanız `false` , hizmet kodunuzda kendi özel olay günlüğlerinizi oluşturmanız ve hizmetinizi bu günlük için geçerli bir giriş kaynağı olarak kaydetmeniz gerekir. Ardından, ilgilendiğiniz bir eylem olduğunda günlüğe girdileri kaydetmek için kod yazmalısınız.  
  
> [!NOTE]
> Özel bir olay günlüğü kullanır ve hizmet uygulamanızı ona yazacak şekilde yapılandırırsanız, kodunuzda hizmetin özelliğini ayarlamadan önce olay günlüğüne erişmeye çalışmamalıdır <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> . Olay günlüğü, hizmetinizi geçerli bir olay kaynağı olarak kaydetmek için bu özelliğin değerine ihtiyaç duyuyor.  
  
### <a name="to-enable-default-event-logging-for-your-service"></a>Hizmetiniz için varsayılan olay günlüğünü etkinleştirmek için  
  
- <xref:System.ServiceProcess.ServiceBase.AutoLog%2A>Bileşeninizin özelliğini olarak ayarlayın `true` .  
  
    > [!NOTE]
    > Varsayılan olarak, bu özellik olarak ayarlanır `true` . Bir koşulu değerlendirme ve sonra <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> özelliği bu koşulun sonucuna göre ayarlama gibi daha karmaşık bir işlem oluşturulmadığınız sürece bunu açıkça ayarlamanız gerekmez.  
  
### <a name="to-disable-event-logging-for-your-service"></a>Hizmetiniz için olay günlüğünü devre dışı bırakmak için  
  
- <xref:System.ServiceProcess.ServiceBase.AutoLog%2A>Bileşeninizin özelliğini olarak ayarlayın `false` .  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a>Özel bir günlüğe günlük kaydı ayarlamak için  
  
1. <xref:System.ServiceProcess.ServiceBase.AutoLog%2A>Özelliğini olarak ayarlayın `false` .  
  
    > [!NOTE]
    > <xref:System.ServiceProcess.ServiceBase.AutoLog%2A>Özel bir günlük kullanabilmeniz için false olarak ayarlamanız gerekir.  
  
2. <xref:System.Diagnostics.EventLog>Windows hizmet uygulamanızda bir bileşen örneği ayarlayın.  
  
3. <xref:System.Diagnostics.EventLog.CreateEventSource%2A>Yöntemini çağırarak ve kaynak dizeyi ve oluşturmak istediğiniz günlük dosyasının adını belirterek özel bir günlük oluşturun.  
  
4. <xref:System.Diagnostics.EventLog.Source%2A> <xref:System.Diagnostics.EventLog> Bileşen örneğindeki özelliği adım 3 ' te oluşturduğunuz kaynak dizeye ayarlayın.  
  
5. Bileşen örneğindeki yöntemine erişerek girdilerinizi yazın <xref:System.Diagnostics.EventLog.WriteEntry%2A> <xref:System.Diagnostics.EventLog> .  
  
     Aşağıdaki kod, özel bir günlüğe kaydetmenin nasıl ayarlanacağını gösterir.  
  
    > [!NOTE]
    > Bu kod örneğinde, bir <xref:System.Diagnostics.EventLog> bileşenin örneği `eventLog1` ( `EventLog1` Visual Basic) olarak adlandırılır. 2. adımda başka bir ada sahip bir örnek oluşturduysanız, kodu uygun şekilde değiştirin.  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Hizmet Uygulamalarına Giriş](introduction-to-windows-service-applications.md)
