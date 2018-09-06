---
title: .NET Framework istemci uygulaması oluşturma (WCF Veri Hizmetleri Hızlı Başlangıç)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
ms.openlocfilehash: 86ded7351d435b3a7077f0354d8a923b33a3f2b6
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43854963"
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a>.NET Framework istemci uygulaması oluşturma (WCF Veri Hizmetleri Hızlı Başlangıç)

Bu, WCF Veri Hizmetleri Hızlı Başlangıç Son görevdir. Bu görevde, bir konsol uygulaması çözüme ekleyin, bir başvuru ekleyin [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] bu yeni istemci uygulamasına akışı ve OData istemci kitaplıkları ve oluşturulan istemci veri hizmeti sınıfları kullanarak istemci uygulamasından akışına erişim .

> [!NOTE]
> .NET Framework tabanlı bir istemci uygulama bir veri akışına erişmek için gerekli değildir. Veri Hizmeti, bir OData akışına kullanan herhangi bir uygulama bileşeni tarafından erişilebilir. Daha fazla bilgi için [bir istemci uygulamasında veri hizmeti kullanma](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).

## <a name="to-create-the-client-application-by-using-visual-studio"></a>Visual Studio kullanarak istemci uygulamasını oluşturmak için

1.  İçinde **Çözüm Gezgini**, çözüme sağ tıklayın, **Ekle**ve ardından **yeni proje**.

2.  Sol bölmede seçin **yüklü** > [**Visual C#** veya **Visual Basic**] > **Windows Masaüstü**seçip **WPF uygulaması** şablonu.

3.  Girin `NorthwindClient` proje adı ve ardından **Tamam**.

4.  MainWindow.xaml dosyasını açın ve XAML kodu aşağıdaki kodla değiştirin:

     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml#window1xaml)]

## <a name="to-add-a-data-service-reference-to-the-project"></a>Projeye veri hizmeti başvurusu eklemek için

1.  İçinde **Çözüm Gezgini**, northwindclient & lt projeye sağ tıklayın, **Ekle** > **hizmet başvurusu**ve ardından **Bul** .

     Bu ilk görevde oluşturduğunuz Northwind verileri hizmeti görüntüler.

2.  İçinde **Namespace** metin kutusunda, `Northwind`ve ardından **Tamam**.

     Bu, yeni bir kod dosyası erişmek ve veri hizmeti kaynaklarına nesneler olarak etkileşim için kullanılan veri sınıfları içeren projeyi ekler. Veri sınıfları ad alanında oluşturulan `NorthwindClient.Northwind`.

## <a name="to-access-data-service-data-in-the-wpf-application"></a>WPF uygulamasında veri hizmeti verilere erişmek için

1.  İçinde **Çözüm Gezgini** altında **; northwindclient & lt**, projeye sağ tıklayın ve tıklayın **Başvuru Ekle**.

2.  İçinde **Başvuru Ekle** iletişim kutusu, tıklayın **.NET** sekmesinde System.Data.Services.Client.dll derlemeyi seçin ve ardından **Tamam**.

3. İçinde **Çözüm Gezgini** altında **; northwindclient & lt**MainWindow.xaml dosyanın kod sayfasını açın ve aşağıdakini ekleyin `using` deyimi (`Imports` Visual Basic'te).

     [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#using)]
     [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#using)]

3.  Bu veri hizmetini sorgular ve sonuca bağlar aşağıdaki kodu bir <xref:System.Data.Services.Client.DataServiceCollection%601> içine `MainWindow` sınıfı:

    > [!NOTE]
    > Ana bilgisayar adını değiştirmelisiniz `localhost:12345` Northwind verileri hizmeti örneğinizi barındırma bağlantı noktası ve sunucu.

     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#querycode)]

4.  Değişiklikleri kaydeder aşağıdaki kodu ekleyin `MainWindow` sınıfı:

     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#savechanges)]

## <a name="to-build-and-run-the-northwindclient-application"></a>Northwindclient & lt uygulaması derleme ve çalıştırma için

1.  İçinde **Çözüm Gezgini**; northwindclient & lt projeye sağ tıklayın ve seçin **başlangıç projesi olarak ayarla**.

2.  Tuşuna **F5** uygulamayı başlatmak için.

     Bu çözüm derlenir ve istemci uygulamayı başlatır. Veriler hizmetten istenen ve konsolda görüntülenir.

3.  Bir değeri de düzenlemeniz **miktar** veri kılavuzu ve ardından sütunun **Kaydet**.

     Veri hizmetine değişiklikler kaydedildi.

    > [!NOTE]
    > Ekleme ve silme varlıklarının; northwindclient & lt uygulamanın bu sürümü desteklemiyor.

## <a name="next-steps"></a>Sonraki Adımlar

Bulunan örnek Northwind OData akışındaki erişen istemci uygulaması başarıyla oluşturdunuz. WCF Veri Hizmetleri hızlı başlangıç ayrıca tamamladınız!

Gelen OData erişme hakkında daha fazla bilgi akışına bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulaması, bakın [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).

## <a name="see-also"></a>Ayrıca Bkz.

- [Başlarken](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
- [Kaynaklar](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)
