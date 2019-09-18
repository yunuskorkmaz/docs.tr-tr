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
ms.openlocfilehash: 1c197b487f1cb7596f507f663fe3f1fb83857cbd
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053496"
---
# <a name="service-application-programming-architecture"></a>Hizmet Uygulaması Programlama Mimarisi
Windows hizmeti uygulamaları <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> sınıfından devralan bir sınıfa dayalıdır. Bu sınıftan yöntemleri geçersiz kılar ve hizmetinizin nasıl davranacağını belirlemek için işlevleri tanımlayın.  
  
 Hizmet oluşturmaya dahil olan ana sınıflar şunlardır:  
  
- <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>— Bir hizmet oluştururken <xref:System.ServiceProcess.ServiceBase> sınıfından yöntemleri geçersiz kılar ve hizmetin bu devralınmış sınıfta nasıl işlevleyeceğini belirlemek için kodu tanımlarsınız.  
  
- <xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType>ve <xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType> — hizmetinizi yüklemek ve kaldırmak için bu sınıfları kullanırsınız.  
  
 Ayrıca, adlı <xref:System.ServiceProcess.ServiceController> bir sınıf hizmetin kendisini denetlemek için kullanılabilir. Bu sınıf, bir hizmetin oluşturulmasına dahil değildir, ancak hizmeti başlatmak ve durdurmak, komutlara iletmek ve bir dizi numaralandırma döndürmek için kullanılabilir.  
  
## <a name="defining-your-services-behavior"></a>Hizmetinizin davranışını tanımlama  
 Hizmet sınıfınıza, hizmet Denetim Yöneticisi 'nde hizmetinizin durumu değiştirildiğinde ne olacağını belirlemek için temel sınıf işlevlerini geçersiz kılarsınız. <xref:System.ServiceProcess.ServiceBase> Sınıfı, özel davranış eklemek için geçersiz kılabileceğiniz aşağıdaki yöntemleri ortaya koyar.  
  
|Yöntem|Geçersiz kıl|  
|------------|-----------------|  
|<xref:System.ServiceProcess.ServiceBase.OnStart%2A>|Hizmetiniz çalışmaya başladığında hangi eylemlerin alınacağını belirtin. Hizmetinizin yararlı işler gerçekleştirmesi için bu yordamda kod yazmanız gerekir.|  
|<xref:System.ServiceProcess.ServiceBase.OnPause%2A>|Hizmetiniz duraklatıldığında ne olacağını belirtin.|  
|<xref:System.ServiceProcess.ServiceBase.OnStop%2A>|Hizmetiniz çalışmayı durdurduğu zaman ne olacağını belirtin.|  
|<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>|Hizmetiniz duraklatıldıktan sonra normal çalışmaya devam ettiğinde ne olacağını belirtin.|  
|<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>|Hizmetiniz bu süre içinde çalışıyorsa sisteminizin kapanması için ne kadar önce olacağını belirtin.|  
|<xref:System.ServiceProcess.ServiceBase.OnCustomCommand%2A>|Hizmetiniz özel bir komut aldığında ne olacağını belirtin. Özel komutlar hakkında daha fazla bilgi için bkz. MSDN Online.|  
|<xref:System.ServiceProcess.ServiceBase.OnPowerEvent%2A>|Düşük pil veya askıya alınmış bir işlem gibi bir güç yönetimi olayı alındığında hizmetin nasıl yanıt vereceğini belirtin.|  
  
> [!NOTE]
> Bu yöntemler, hizmetin ömrü boyunca üzerinden taşınan durumları temsil eder; hizmet bir durumdan diğerine geçiş yapar. Örneğin, bir hizmetin çağrılmadan önce <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> <xref:System.ServiceProcess.ServiceBase.OnStart%2A> bir komuta yanıt vermesini hiçbir şekilde olmayacaktır.  
  
 İlgilendiğiniz birkaç başka özellik ve yöntem vardır. Bu güncelleştirmeler şunlardır:  
  
- <xref:System.ServiceProcess.ServiceBase> Sınıfında <xref:System.ServiceProcess.ServiceBase.Run%2A> yöntemi. Bu, hizmetin ana giriş noktasıdır. Windows hizmet şablonunu kullanarak bir hizmet oluşturduğunuzda, hizmet çalıştırmak için uygulamanızın `Main` yöntemine kod eklenir. Bu kod şöyle görünür:  
  
     [!code-csharp[VbRadconService#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#6)]
     [!code-vb[VbRadconService#6](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#6)]  
  
    > [!NOTE]
    > Bu örneklerde, uygulamanızın içerdiği her bir <xref:System.ServiceProcess.ServiceBase>hizmetin eklenebileceği ve sonra tüm hizmetlerin birlikte çalıştırılabileceği bir dizi türü kullanılır. Ancak yalnızca tek bir hizmet oluşturuyorsanız, diziyi kullanmayın ve ' den <xref:System.ServiceProcess.ServiceBase> devralan yeni bir nesne bildirmeniz ve sonra çalıştırmanız yeterlidir. Bir örnek için bkz [. nasıl yapılır: Hizmetleri programlı olarak](how-to-write-services-programmatically.md)yazın.  
  
- <xref:System.ServiceProcess.ServiceBase> Sınıftaki bir dizi özellik. Bunlar, hizmetinize hangi yöntemlerin çağrılabilecek olduğunu tespit edebilir. Örneğin, <xref:System.ServiceProcess.ServiceBase.CanStop%2A> özelliği olarak `true`ayarlandığında, <xref:System.ServiceProcess.ServiceBase.OnStop%2A> hizmetinizin yöntemi çağrılabilir. Özelliği olarak `true`ayarlandığında ,<xref:System.ServiceProcess.ServiceBase.OnPause%2A> ve<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>yöntemleriçağrılabilir. <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> Bu özelliklerden `true`birini ' a ayarladığınızda, ilişkili yöntemler için işlemeyi geçersiz kılmanız ve tanımlamanız gerekir.  
  
    > [!NOTE]
    > Hizmetiniz en az <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yararlı olacak şekilde geçersiz kılmalıdır.  
  
 İle iletişim kurmak ve var olan bir hizmetin <xref:System.ServiceProcess.ServiceController> davranışını denetlemek için adlı bir bileşeni de kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Hizmeti Uygulamalarına Giriş](introduction-to-windows-service-applications.md)
- [Nasıl yapılır: Windows Hizmetleri oluşturma](how-to-create-windows-services.md)
