---
title: Hizmet Uygulaması Programlama Mimarisi
ms.date: 03/30/2017
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
author: ghogen
ms.openlocfilehash: df969a634c84a7bccb048542cb768c920203e423
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599277"
---
# <a name="service-application-programming-architecture"></a>Hizmet Uygulaması Programlama Mimarisi
Windows hizmet uygulamaları öğesinden devralınan bir sınıf temel <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> sınıfı. Bu sınıftaki yöntemleri geçersiz kılın ve işlevselliği için hizmetinizin nasıl davranacağını belirlemek bunları tanımlayın.  
  
 Hizmet oluşturmada yer alan ana sınıfları şunlardır:  
  
- <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> — Yöntemleri geçersiz kılmak <xref:System.ServiceProcess.ServiceBase> hizmet oluştururken, sınıf ve nasıl sınıf hizmet işlevlerinizi bu devralınan belirlemek için kod tanımlayın.  
  
- <xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType> ve <xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType> — yüklemek ve hizmetinizi kaldırmak için bu sınıflar'ı kullanın.  
  
 Ayrıca, bir sınıf adlı <xref:System.ServiceProcess.ServiceController> hizmeti işlemek için kullanılabilir. Bu sınıf, bir hizmetin oluşturmada yer alan değildir, ancak başlatma ve hizmetini durdurun, komutları ona geçirin ve bir dizi bir numaralandırma döndürmek için kullanılabilir.  
  
## <a name="defining-your-services-behavior"></a>Hizmetinizin davranış tanımlama  
 Hizmet sınıfında, hizmetler Denetimi Yöneticisi'nde, hizmet durumu değiştirildiğinde ne olacağını belirleyen bir taban sınıf işlevlerini geçersiz kılar. <xref:System.ServiceProcess.ServiceBase> Sınıfı özel davranış eklemek için geçersiz kılmak aşağıdaki yöntemleri gösterir.  
  
|Yöntem|İçin geçersiz kılın|  
|------------|-----------------|  
|<xref:System.ServiceProcess.ServiceBase.OnStart%2A>|Hizmetiniz çalışmaya başladığında, hangi eylemlerin yapılması gerektiğini belirtir. Bu yordamda hizmetinizin yararlı çalışmayı gerçekleştirmek kod yazmanız gerekir.|  
|<xref:System.ServiceProcess.ServiceBase.OnPause%2A>|Hizmetinizin duraklatılmadığı olduğunda ne olacağını gösterir.|  
|<xref:System.ServiceProcess.ServiceBase.OnStop%2A>|Hizmetiniz çalışmayı durdurduğunda ne olması gerektiğini belirtin.|  
|<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>|Hizmetinizi duraklatıldıktan sonra normal çalışmasına devam ettiğinde ne olması gerektiğini belirtin.|  
|<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>|Hizmetiniz o anda çalışıyorsa ne, kapatma, sisteminizi önce olması gerektiğini belirtin.|  
|<xref:System.ServiceProcess.ServiceBase.OnCustomCommand%2A>|Hizmetiniz bir özel komutunu aldığında ne olması gerektiğini belirtin. Özel komutlar hakkında daha fazla bilgi için MSDN çevrimiçi konusuna bakın.|  
|<xref:System.ServiceProcess.ServiceBase.OnPowerEvent%2A>|Düşük pil veya askıya alınmış işlem gibi bir güç yönetimi olayının alındığında, hizmetin nasıl yanıt vermelidir gösterir.|  
  
> [!NOTE]
>  Bu yöntemler, yaşam sürelerinin başlarında aracılığıyla hizmet taşıyan sistem durumunu gösterir; sonraki hizmet geçişler bir durumdan. Örneğin, hiçbir zaman yanıt vermek için hizmet erişmenizi sağlayacak bir <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> önce komutunu <xref:System.ServiceProcess.ServiceBase.OnStart%2A> çağrıldı.  
  
 Diğer çeşitli özellikler ve ilgilendiğiniz yöntemleri vardır. Bu güncelleştirmeler şunlardır:  
  
- <xref:System.ServiceProcess.ServiceBase.Run%2A> Metodunda <xref:System.ServiceProcess.ServiceBase> sınıfı. Bu hizmet için ana giriş noktasıdır. Windows hizmet şablonunu kullanarak bir hizmet oluşturduğunuzda, kodun uygulamanızın eklendiği `Main` hizmeti çalıştırmak için yöntemi. Bu kod şu şekilde görünür:  
  
     [!code-csharp[VbRadconService#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#6)]
     [!code-vb[VbRadconService#6](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#6)]  
  
    > [!NOTE]
    >  Bu örneklerde bu tip bir dizide <xref:System.ServiceProcess.ServiceBase>, hangi uygulamanın içerdiği her bir hizmet eklenebilir ve ardından tüm hizmetlerin birlikte çalıştırılabilir. Yalnızca tek bir hizmet oluşturuyorsanız, ancak, dizinin kullanma ve yalnızca dan devralan yeni bir nesne bildirme tercih edebileceğiniz <xref:System.ServiceProcess.ServiceBase> ve ardından çalıştırın. Bir örnek için bkz [nasıl yapılır: Hizmetleri programlamayla yazma](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).  
  
- Bir dizi özellikleri <xref:System.ServiceProcess.ServiceBase> sınıfı. Bu hizmet yöntemleri çağrılabilir belirleyin. Örneğin, <xref:System.ServiceProcess.ServiceBase.CanStop%2A> özelliği `true`, <xref:System.ServiceProcess.ServiceBase.OnStop%2A> hizmetinizdeki yöntemi çağrılabilir. Zaman <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> özelliği `true`, <xref:System.ServiceProcess.ServiceBase.OnPause%2A> ve <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> yöntemler çağrılabilir. Ayarladığınızda bu özelliklerin herhangi birini `true`, daha sonra geçersiz kılma ve ilişkili yöntemleri için işleme tanımlayın.  
  
    > [!NOTE]
    >  En az hizmetiniz geçersiz kılmalısınız <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yararlı olacak.  
  
 Adlı bir bileşen kullanabilirsiniz <xref:System.ServiceProcess.ServiceController> ile iletişim kurmak ve mevcut bir hizmet davranışını denetlemek için.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Nasıl yapılır: Windows Hizmetleri oluşturma](../../../docs/framework/windows-services/how-to-create-windows-services.md)
