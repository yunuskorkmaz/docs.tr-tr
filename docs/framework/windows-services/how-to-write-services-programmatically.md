---
title: 'Nasıl yapılır: Hizmetleri Program Aracılığıyla Yazma'
description: Devralma ve diğer altyapı öğelerini kendiniz ayarlayarak bkz. Hizmetleri programlama yoluyla yazma.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
author: ghogen
ms.openlocfilehash: 9693e3d387f38319519ab04211d8219fe1e5dda1
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925715"
---
# <a name="how-to-write-services-programmatically"></a>Nasıl yapılır: Hizmetleri Program Aracılığıyla Yazma
Windows hizmeti proje şablonunu kullanmayı tercih ederseniz, devralma ve diğer altyapı öğelerini kendiniz ayarlayarak kendi hizmetlerinizi yazabilirsiniz. Programlı olarak bir hizmet oluşturduğunuzda, şablonun sizin için başka bir tanıtıcı tutacağından birkaç adım gerçekleştirmeniz gerekir:  
  
- Sınıfından devralması için hizmet sınıfınızı ayarlamanız gerekir <xref:System.ServiceProcess.ServiceBase> .  
  
- `Main`Hizmet projeniz için çalıştırılacak hizmetleri tanımlayan bir yöntem oluşturmanız ve <xref:System.ServiceProcess.ServiceBase.Run%2A> üzerinde yöntemi çağırmalısınız.  
  
- Ve yordamlarını geçersiz kılmanız <xref:System.ServiceProcess.ServiceBase.OnStart%2A> <xref:System.ServiceProcess.ServiceBase.OnStop%2A> ve çalıştırmak istediğiniz kodu doldurmanız gerekir.  
  
### <a name="to-write-a-service-programmatically"></a>Program aracılığıyla bir hizmet yazmak için  
  
1. Boş bir proje oluşturun ve aşağıdaki adımları izleyerek gerekli ad alanlarına bir başvuru oluşturun:  
  
    1. **Çözüm Gezgini**, **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle**' ye tıklayın.  
  
    2. **.NET Framework** sekmesinde, **System.dll** ' ye kaydırın ve **Seç**' e tıklayın.  
  
    3. **System.ServiceProcess.dll** kaydırın ve **Seç**' e tıklayın.  
  
    4. **Tamam** düğmesine tıklayın.  
  
2. Bir sınıf ekleyin ve bunu öğesinden devralacak şekilde yapılandırın <xref:System.ServiceProcess.ServiceBase> :  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3. Hizmet sınıfınızı yapılandırmak için aşağıdaki kodu ekleyin:  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4. `Main`Sınıfınız için bir yöntem oluşturun ve sınıfınızın içereceği hizmeti tanımlamak için kullanın; `userService1` sınıfın adıdır:  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5. Yöntemini geçersiz kılın <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve hizmetiniz başlatıldığında gerçekleşmesini istediğiniz işlemleri tanımlayın.  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6. İçin özel işlem tanımlamak istediğiniz diğer yöntemleri geçersiz kılın ve hizmetin her durumda gerçekleşmesi gereken eylemleri belirlemek için kod yazın.  
  
7. Hizmet uygulamanız için gerekli yükleyicileri ekleyin. Daha fazla bilgi için bkz. [nasıl yapılır: hizmet uygulamanıza yükleyiciler ekleme](how-to-add-installers-to-your-service-application.md).  
  
8. **Build** menüsünden **Build Solution** ' i seçerek projenizi oluşturun.  
  
    > [!NOTE]
    > Projenizi çalıştırmak için F5 tuşuna basmayın; bir hizmet projesini bu şekilde çalıştıramazsınız.  
  
9. Hizmetinizi yüklemek için bir kurulum projesi ve özel eylemler oluşturun. Örnek için bkz. [Izlenecek yol: bileşen tasarımcısında Windows hizmet uygulaması oluşturma](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).  
  
10. Hizmeti yükler. Daha fazla bilgi için bkz. [nasıl yapılır: Hizmetleri yükleme ve kaldırma](how-to-install-and-uninstall-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Hizmet Uygulamalarına Giriş](introduction-to-windows-service-applications.md)
- [Nasıl yapılır: Windows Hizmetleri Oluşturma](how-to-create-windows-services.md)
- [Nasıl yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme](how-to-add-installers-to-your-service-application.md)
- [Nasıl yapılır: Hizmet Bilgilerini Günlüğe Kaydetme](how-to-log-information-about-services.md)
- [İzlenecek Yol: Bileşen Tasarımcısında Windows Hizmeti Uygulaması Oluşturma](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
