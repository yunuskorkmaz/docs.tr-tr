---
title: 'Nasıl yapılır: Hizmetleri programlamayla yazma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
author: ghogen
ms.openlocfilehash: 70a2c184e7b39af7b4f0466ac9ac627cff98f0c0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672918"
---
# <a name="how-to-write-services-programmatically"></a>Nasıl yapılır: Hizmetleri programlamayla yazma
Windows hizmet proje şablonu kullanmayı tercih ederseniz, devralma ve diğer altyapı öğelerini kendiniz ayarlama hizmetlerinizi yazabilirsiniz. Program aracılığıyla bir hizmet oluşturduğunuzda, şablon, aksi takdirde gerçekleştirilir birkaç adım gerçekleştirmeniz gerekir:  
  
-   Hizmet sınıfınızı devralınacak ayarlamalısınız <xref:System.ServiceProcess.ServiceBase> sınıfı.  
  
-   Oluşturmalısınız bir `Main` yöntemi çağırır ve çalıştırmak için hizmeti tanımlayan bir hizmet projesi için <xref:System.ServiceProcess.ServiceBase.Run%2A> bunları yöntemi.  
  
-   Geçersiz kılmanız gerekir <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yordamlar ve herhangi bir kod girin, istediğiniz çalışmak üzere.  
  
### <a name="to-write-a-service-programmatically"></a>Bir hizmet programlı olarak yazmak için  
  
1.  Boş bir proje oluşturun ve aşağıdaki adımları izleyerek ad alanlarına başvuru oluşturun:  
  
    1.  İçinde **Çözüm Gezgini**, sağ **başvuruları** düğüm ve tıklatın **Başvuru Ekle**.  
  
    2.  Üzerinde **.NET Framework** sekmesinde, kaydırma **System.dll** tıklatıp **seçin**.  
  
    3.  Kaydırma **System.ServiceProcess.dll** tıklatıp **seçin**.  
  
    4.  **Tamam**'ı tıklatın.  
  
2.  Bir sınıf ekleyin ve devralınacak şekilde yapılandırmanız <xref:System.ServiceProcess.ServiceBase>:  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3.  Hizmet sınıfınızı yapılandırmak için aşağıdaki kodu ekleyin:  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4.  Oluşturma bir `Main` sınıfınız için bir yöntem ve sınıfınızın içerir; hizmet tanımlamak için kullanın `userService1` sınıf adıdır:  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5.  Geçersiz kılma <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi ve hizmetinizi başlatıldığında gerçekleşmesini istediğiniz herhangi bir işlemi tanımlar.  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6.  Özel işlemeyi tanımlamak istediğiniz diğer yöntemleri geçersiz kılın ve hizmetinin her durumda gerçekleştirmesi gereken eylemleri belirlemek için kod yazın.  
  
7.  Hizmet uygulamanız için gerekli yükleyicileri ekleyin. Daha fazla bilgi için [nasıl yapılır: Hizmet uygulamasına yükleyiciler ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
8.  Projenizi seçerek **Çözümü Derle** gelen **derleme** menüsü.  
  
    > [!NOTE]
    >  Projenizi çalıştırmak için F5 tuşuna basmayın-bu şekilde bir hizmet projesi çalıştıramazsınız.  
  
9. Bir kurulum projesi ve hizmetinizi yüklemek için özel eylemler oluşturun. Bir örnek için bkz [izlenecek yol: Oluşturma bir Windows hizmet uygulaması Bileşen Tasarımcısı'nda](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).  
  
10. Hizmetini yükleyin. Daha fazla bilgi için [nasıl yapılır: Hizmetleri Yükleme ve kaldırma](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Nasıl yapılır: Windows Hizmetleri oluşturma](../../../docs/framework/windows-services/how-to-create-windows-services.md)
- [Nasıl yapılır: Hizmet uygulamasına yükleyiciler ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [Nasıl yapılır: Günlük bilgilerini hizmetleri hakkında](../../../docs/framework/windows-services/how-to-log-information-about-services.md)
- [İzlenecek yol: Bileşen tasarımcısında Windows hizmeti uygulaması oluşturma](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
