---
title: ".NET Framework istemci uygulaması oluşturma (WCF Veri Hizmetleri Hızlı Başlangıç)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2d654ad24f8d23a47d2a3be3b07c42c104bb9b70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a>.NET Framework istemci uygulaması oluşturma (WCF Veri Hizmetleri Hızlı Başlangıç)
Bu, son görevdir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] hızlı başlangıç. Bu görevde, bir konsol uygulaması çözüme eklemek için bir başvuru ekleyin [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akış bu yeni istemci uygulaması ve erişim [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] oluşturulan istemci veri hizmeti sınıfları ve istemci kullanarak istemci uygulamasından akışı kitaplıkları.  
  
> [!NOTE]
>  Bir .NET Framework tabanlı bir istemci uygulaması veri akışına erişmek için gerekli değildir. Veri Hizmeti tüketen uygulama bileşeni tarafından erişilebilen bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış. Daha fazla bilgi için bkz: [veri hizmeti istemci uygulamasında kullanma](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).  
  
### <a name="to-create-the-client-application-by-using-visual-studio"></a>Visual Studio kullanarak istemci uygulaması oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, çözüme sağ tıklayın, **Ekle**ve ardından **yeni proje**.  
  
2.  İçinde **proje türleri**, tıklatın **Windows**ve ardından **WPF uygulaması** içinde **şablonları** bölmesi.  
  
3.  Girin `NorthwindClient` proje adı ve ardından **Tamam**.  
  
4.  MainWindow.xaml dosyasını açın ve XAML kodu aşağıdaki kodla değiştirin:  
  
     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml#window1xaml)]  
  
### <a name="to-add-a-data-service-reference-to-the-project"></a>Veri hizmeti başvurusu projeye eklemek için  
  
1.  NorthwindClient projesine sağ tıklayın, **hizmet Başvurusu Ekle**ve ardından **bulma**.  
  
     Bu ilk görevde oluşturduğunuz Northwind veri hizmeti görüntüler.  
  
2.  İçinde **Namespace** metin kutusunda, `Northwind`ve ardından **Tamam**.  
  
     Bu, yeni bir kod dosyası erişmek ve nesneler olarak veri hizmeti kaynakları ile etkileşim kurmak için kullanılan veri sınıfları içeren projeye ekler. Veri sınıflarını ad alanında oluşturulan `NorthwindClient.Northwind`.  
  
### <a name="to-access-data-service-data-in-the-wpf-application"></a>WPF uygulamasında veri hizmeti verilere erişmek için  
  
1.  İçinde **Çözüm Gezgini** altında **NorthwindClient**, projeyi sağ tıklatın ve **Başvuru Ekle**.  
  
2.  Başvuru Ekle iletişim kutusunda tıklatın **.NET** sekmesinde, System.Data.Services.Client.dll derlemesi seçin ve ardından **Tamam**. İçinde **Çözüm Gezgini** altında **NorthwindClient**MainWindow.xaml dosyası için kod sayfasını açın ve aşağıdakileri ekleyin `using` deyimi (`Imports` Visual Basic'te).  
  
     [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#using)]
     [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#using)]  
  
3.  Bu veri hizmeti sorgular ve sonucu bağlar aşağıdaki kodu ekleyin bir <xref:System.Data.Services.Client.DataServiceCollection%601> içine `MainWindow` sınıfı:  
  
    > [!NOTE]
    >  Ana bilgisayar adını değiştirmeniz gerekir `localhost:12345` Northwind veri hizmeti örneğiniz barındırma bağlantı noktası ve sunucu.  
  
     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#querycode)]  
  
4.  Değişiklikleri kaydeder aşağıdaki kodu ekleyin `MainWindow` sınıfı:  
  
     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#savechanges)]  
  
### <a name="to-build-and-run-the-northwindclient-application"></a>Derleme ve NorthwindClient uygulamayı çalıştırmak için  
  
1.  İçinde **Çözüm Gezgini**, NorthwindClient projesine sağ tıklatın ve **başlangıç projesi olarak ayarla**.  
  
2.  Uygulamayı başlatmak için F5 tuşuna basın.  
  
     Bu çözüm oluşturur ve istemci uygulaması başlatır. Veri hizmetinden istenen ve konsolda görüntülenir.  
  
3.  Bir değeri **miktar** veri kılavuzu ve ardından sütunu **kaydetmek**.  
  
     Değişiklikler veri hizmetine kaydedilir.  
  
    > [!NOTE]
    >  NorthwindClient uygulamasının bu sürümü, ekleme ve silme varlıklarının desteklemez.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Northwind örnek erişen istemci uygulaması başarıyla oluşturdunuz [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış. Ayrıca tamamladınız [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] hızlı başlangıç. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]erişen bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] besleme yeri bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulama, bkz: [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 [Kaynakları](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)
