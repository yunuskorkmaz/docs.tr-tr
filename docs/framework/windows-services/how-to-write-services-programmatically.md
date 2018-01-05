---
title: "Nasıl Yapılır: Hizmetleri Programlamayla Yazma"
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
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
caps.latest.revision: "21"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: cdb9c7bba564b71bfba86076218e48610cf73076
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-write-services-programmatically"></a>Nasıl Yapılır: Hizmetleri Programlamayla Yazma
Windows hizmeti proje şablonu kullanmayı seçerseniz, devralma ve diğer altyapı öğeleri kendiniz belirleyerek kendi hizmetlerinizi yazabilirsiniz. Bir hizmet programlı olarak oluşturduğunuzda, şablon Aksi takdirde sizin için yapar bazı adımlar gerçekleştirmeniz gerekir:  
  
-   Devralmak için hizmet sınıfınızı ayarlamalısınız <xref:System.ServiceProcess.ServiceBase> sınıfı.  
  
-   Oluşturmanız gerekir bir `Main` yöntemi çalıştırılacak hizmetleri tanımlayan hizmet projesi ve aramalar için <xref:System.ServiceProcess.ServiceBase.Run%2A> bunlardaki yöntemi.  
  
-   Geçersiz kılmanız gerekir <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yordamları ve herhangi bir kod doldurun istediğiniz bunları çalıştırmak için.  
  
### <a name="to-write-a-service-programmatically"></a>Bir hizmeti program aracılığıyla yazmak için  
  
1.  Boş bir proje oluşturun ve ad alanlarına başvuru aşağıdaki adımları izleyerek oluşturun:  
  
    1.  İçinde **Çözüm Gezgini**, sağ **başvuruları** düğümü ve tıklatın **Başvuru Ekle**.  
  
    2.  Üzerinde **.NET Framework** sekmesinde, kaydırarak **System.dll** tıklatıp **seçin**.  
  
    3.  Kaydırma **System.ServiceProcess.dll** tıklatıp **seçin**.  
  
    4.  **Tamam**'ı tıklatın.  
  
2.  Bir sınıf ekleyin ve devralınacak yapılandırın <xref:System.ServiceProcess.ServiceBase>:  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3.  Hizmet sınıfınızı yapılandırmak için aşağıdaki kodu ekleyin:  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4.  Oluşturma bir `Main` sınıfınız, yöntemi ve sınıfınız içerir; hizmet tanımlamak için kullanın `userService1` sınıfı adıdır:  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5.  Geçersiz kılma <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi ve hizmet başlatıldığında ortaya istediğiniz herhangi bir işlem tanımlayın.  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6.  Özel işlemeyi tanımlamak istediğiniz diğer yöntemleri geçersiz kılın ve hizmetin her durumda gerçekleştirmesi gereken eylemleri belirlemek için kod yazma.  
  
7.  Hizmet uygulamanız için gerekli yükleyicileri ekleyin. Daha fazla bilgi için bkz: [nasıl yapılır: Hizmet uygulamanız için yükleyiciler ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
8.  Seçerek projenizi derleme **yapı çözümü** gelen **yapı** menüsü.  
  
    > [!NOTE]
    >  Projenizi çalıştırmak için F5 tuşuna basmayın — bir hizmet projesi bu şekilde çalıştıramazsınız.  
  
9. Kurulum projesi ve hizmetinizi yüklemek için özel eylemler oluşturun. Bir örnek için bkz: [izlenecek yol: Bileşen tasarımcısında Windows hizmet uygulaması oluşturma](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).  
  
10. Hizmetini yükleyin. Daha fazla bilgi için bkz: [nasıl yapılır: yükleme ve kaldırma Hizmetleri](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Nasıl Yapılır: Windows Hizmetleri Oluşturma](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [Nasıl Yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Nasıl Yapılır: Hizmet Bilgilerini Günlüğe Kaydetme](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [İzlenecek Yol: Bileşen Tasarımcısında Windows Hizmeti Uygulaması Oluşturma](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
