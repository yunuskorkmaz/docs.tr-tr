---
title: "Hizmet Uygulaması Programlama Mimarisi"
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
- ServiceController components, programming architecture
- ServiceBase class, service states
- Windows Service applications, code model
- services, programming architecture
- ServiceController class
- services, states
- ServiceProcessInstaller class, service application code model
- Windows Service applications, states
ms.assetid: 83230026-d068-4174-97ff-e264c896eb2f
caps.latest.revision: "15"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: e9c16f2e603a3ce9bbc59be4e01aa492239d2c63
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="service-application-programming-architecture"></a>Hizmet Uygulaması Programlama Mimarisi
Windows hizmet uygulamaları öğesinden devralınan bir sınıf temel <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> sınıfı. Bu sınıftan yöntemleri geçersiz kılmak ve bunları hizmetinizin nasıl davranacağını belirlemek işlevsellik tanımlayın.  
  
 Hizmet oluşturulmasında yer ana sınıfları şunlardır:  
  
-   <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>— Yöntemleri geçersiz kılar <xref:System.ServiceProcess.ServiceBase> hizmet oluştururken, sınıf ve nasıl hizmetinizin Bu sınıf devralınan belirlemek için kod tanımlayın.  
  
-   <xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType>ve <xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType> — bu sınıfların yüklemek ve hizmetinizi kaldırmak için kullanın.  
  
 Ayrıca, adlı bir sınıf <xref:System.ServiceProcess.ServiceController> hizmeti işlemek için kullanılabilir. Bu sınıf bir hizmet oluşturmada yer alan değildir, ancak başlatmak ve hizmetini durdurun, komutları ona geçirmek ve numaralandırmalar bir dizi dönmek için kullanılabilir.  
  
## <a name="defining-your-services-behavior"></a>Hizmetinizin davranış tanımlama  
 Hizmet sınıfında, hizmetler Denetimi Yöneticisi'nde, hizmetin durumunu değiştirildiğinde ne olacağını belirleyen temel sınıf işlevleri geçersiz kılar. <xref:System.ServiceProcess.ServiceBase> Sınıfı özel davranış eklemeyi Geçersiz kılabileceğiniz aşağıdaki yöntemleri sunar.  
  
|Yöntem|İçin geçersiz kılın|  
|------------|-----------------|  
|<xref:System.ServiceProcess.ServiceBase.OnStart%2A>|Hizmetiniz çalışmaya başladığında hangi eylemlerin gerçekleştirilmesi gerektiğini gösterir. Hizmetinizin faydalı bir iş gerçekleştirmesi bu yordamdaki kod yazmanız gerekir.|  
|<xref:System.ServiceProcess.ServiceBase.OnPause%2A>|Hizmet duraklatıldığında ne olacağını gösterir.|  
|<xref:System.ServiceProcess.ServiceBase.OnStop%2A>|Hizmetiniz çalışmayı durdurduğunda ne olacağını gösterir.|  
|<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>|Hizmetinizi duraklatıldıktan sonra normal işlevine devam ettiğinde ne olacağını gösterir.|  
|<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>|Hizmetinizi o anda çalışıyorsa, ne, kapatma, sisteminizi önce olması gerektiğini belirtin.|  
|<xref:System.ServiceProcess.ServiceBase.OnCustomCommand%2A>|Hizmetiniz özel bir komut aldığında ne olacağını gösterir. Özel komutlar hakkında daha fazla bilgi için MSDN çevrimiçi konusuna bakın.|  
|<xref:System.ServiceProcess.ServiceBase.OnPowerEvent%2A>|Düşük pil ya da askıya alınmış işlemi gibi bir güç yönetimi olayı alındığında, hizmetin nasıl tepki gösterir.|  
  
> [!NOTE]
>  Bu yöntemler ömrü aracılığıyla hizmet taşır durumları temsil eder; sonraki hizmet geçişleri bir durumdan. Örneğin, hiçbir zaman yanıt verecek şekilde hizmet alırsınız bir <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> önce komutu <xref:System.ServiceProcess.ServiceBase.OnStart%2A> çağrıldı.  
  
 Diğer birçok özellik ve ilgilendiğiniz yöntemleri vardır. Bu güncelleştirmeler şunlardır:  
  
-   <xref:System.ServiceProcess.ServiceBase.Run%2A> Yöntemi <xref:System.ServiceProcess.ServiceBase> sınıfı. Bu hizmet için ana giriş noktasıdır. Windows hizmet şablonu kullanarak bir hizmet oluşturduğunuzda, kodu uygulamanızın eklenir `Main` hizmetini çalıştırmak için yöntem. Bu kod şu şekildedir:  
  
     [!code-csharp[VbRadconService#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#6)]
     [!code-vb[VbRadconService#6](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#6)]  
  
    > [!NOTE]
    >  Bu örnekleri türünde bir dizi kullanmak <xref:System.ServiceProcess.ServiceBase>hangi içine uygulamanızı içeren her bir hizmet eklenebilir ve ardından tüm hizmetlerin birlikte çalıştırılabilir. Yalnızca tek bir hizmeti oluşturuyorsanız, ancak, dizi kullanma ve yalnızca içinden devralma yeni bir nesne bildirme tercih edebileceğiniz <xref:System.ServiceProcess.ServiceBase> ve ardından çalıştırın. Bir örnek için bkz: [nasıl yapılır: Hizmetleri programlamayla yazma](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).  
  
-   Özellikleri, bir dizi <xref:System.ServiceProcess.ServiceBase> sınıfı. Bu hizmet yöntemleri çağrılabilir belirler. Örneğin, <xref:System.ServiceProcess.ServiceBase.CanStop%2A> özelliği ayarlanmış `true`, <xref:System.ServiceProcess.ServiceBase.OnStop%2A> hizmetinizi yöntemi çağrılabilir. Zaman <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> özelliği ayarlanmış `true`, <xref:System.ServiceProcess.ServiceBase.OnPause%2A> ve <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> yöntemleri çağrılamaz. Ayarladığınızda bu özelliklerden birini `true`, daha sonra geçersiz kılma ve işleme ilişkili yöntemleri için tanımlayın.  
  
    > [!NOTE]
    >  Hizmetinizi en az kılmalıdır <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yararlı olacak.  
  
 Adlı bir bileşen de kullanabilirsiniz <xref:System.ServiceProcess.ServiceController> ile iletişim kurmasını ve var olan bir hizmeti davranışını denetler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows hizmet uygulamalarına giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Nasıl yapılır: Windows Hizmetleri oluşturma](../../../docs/framework/windows-services/how-to-create-windows-services.md)
