---
title: 'Nasıl yapılır: Hizmetleri Program Aracılığıyla Yazma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
author: ghogen
ms.openlocfilehash: 5637d569ad5261bff6865af4ab2ed8b7631d2d38
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053553"
---
# <a name="how-to-write-services-programmatically"></a>Nasıl yapılır: Hizmetleri Program Aracılığıyla Yazma
Windows hizmeti proje şablonunu kullanmayı tercih ederseniz, devralma ve diğer altyapı öğelerini kendiniz ayarlayarak kendi hizmetlerinizi yazabilirsiniz. Programlı olarak bir hizmet oluşturduğunuzda, şablonun sizin için başka bir tanıtıcı tutacağından birkaç adım gerçekleştirmeniz gerekir:  
  
- <xref:System.ServiceProcess.ServiceBase> Sınıfından devralması için hizmet sınıfınızı ayarlamanız gerekir.  
  
- Hizmet projeniz için çalıştırılacak `Main` hizmetleri tanımlayan bir yöntem oluşturmanız ve üzerinde <xref:System.ServiceProcess.ServiceBase.Run%2A> yöntemi çağırmalısınız.  
  
- <xref:System.ServiceProcess.ServiceBase.OnStart%2A> Ve<xref:System.ServiceProcess.ServiceBase.OnStop%2A> yordamlarını geçersiz kılmanız ve çalıştırmak istediğiniz kodu doldurmanız gerekir.  
  
### <a name="to-write-a-service-programmatically"></a>Program aracılığıyla bir hizmet yazmak için  
  
1. Boş bir proje oluşturun ve aşağıdaki adımları izleyerek gerekli ad alanlarına bir başvuru oluşturun:  
  
    1. **Çözüm Gezgini**, **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle**' ye tıklayın.  
  
    2. **.NET Framework** sekmesinde **System. dll** ' ye kaydırın ve **Seç**' e tıklayın.  
  
    3. **System. ServiceProcess. dll** ' ye kaydırın ve **Seç**' e tıklayın.  
  
    4. **Tamam**'ı tıklatın.  
  
2. Bir sınıf ekleyin ve bunu öğesinden <xref:System.ServiceProcess.ServiceBase>devralacak şekilde yapılandırın:  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3. Hizmet sınıfınızı yapılandırmak için aşağıdaki kodu ekleyin:  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4. Sınıfınız için `Main` bir yöntem oluşturun ve sınıfınızın içereceği hizmeti tanımlamak için kullanın; `userService1` , sınıfının adıdır:  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5. <xref:System.ServiceProcess.ServiceBase.OnStart%2A> Yöntemini geçersiz kılın ve hizmetiniz başlatıldığında gerçekleşmesini istediğiniz işlemleri tanımlayın.  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6. İçin özel işlem tanımlamak istediğiniz diğer yöntemleri geçersiz kılın ve hizmetin her durumda gerçekleşmesi gereken eylemleri belirlemek için kod yazın.  
  
7. Hizmet uygulamanız için gerekli yükleyicileri ekleyin. Daha fazla bilgi için [nasıl yapılır: Hizmet uygulamanıza](how-to-add-installers-to-your-service-application.md)yükleyicileri ekleyin.  
  
8. **Build** menüsünden **Build Solution** ' i seçerek projenizi oluşturun.  
  
    > [!NOTE]
    > Projenizi çalıştırmak için F5 tuşuna basmayın; bir hizmet projesini bu şekilde çalıştıramazsınız.  
  
9. Hizmetinizi yüklemek için bir kurulum projesi ve özel eylemler oluşturun. Bir örnek için bkz [. İzlenecek yol: Bileşen tasarımcısında](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)bir Windows hizmeti uygulaması oluşturma.  
  
10. Hizmetini yükleyin. Daha fazla bilgi için [nasıl yapılır: Hizmetleri](how-to-install-and-uninstall-services.md)yükleme ve kaldırma.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Hizmeti Uygulamalarına Giriş](introduction-to-windows-service-applications.md)
- [Nasıl yapılır: Windows Hizmetleri oluşturma](how-to-create-windows-services.md)
- [Nasıl yapılır: Hizmet uygulamanıza yükleyiciler ekleme](how-to-add-installers-to-your-service-application.md)
- [Nasıl yapılır: Hizmetlerle Ilgili bilgileri günlüğe kaydet](how-to-log-information-about-services.md)
- [İzlenecek yol: Bileşen tasarımcısında bir Windows hizmeti uygulaması oluşturma](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
