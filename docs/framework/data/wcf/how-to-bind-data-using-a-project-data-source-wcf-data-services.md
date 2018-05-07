---
title: 'Nasıl yapılır: Proje veri kaynağı (WCF Veri Hizmetleri) kullanarak veri bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: 2477af0a-676f-44f7-b73d-e66208785509
ms.openlocfilehash: 0807b8de6bad5e70fbf522cb1cc20872c59fe1b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-bind-data-using-a-project-data-source-wcf-data-services"></a>Nasıl yapılır: Proje veri kaynağı (WCF Veri Hizmetleri) kullanarak veri bağlama
Oluşturulan veri nesneleri temel alan veri kaynakları oluşturabileceğiniz bir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci uygulaması. Kullanarak veri hizmetine başvuru eklediğinizde **hizmet Başvurusu Ekle** iletişim kutusunda, proje veri kaynağı ile birlikte oluşturulan istemci veri sınıflarını oluşturulur. Bir veri kaynağına veri çıkarır hizmeti her varlık kümesi için oluşturulur. Bu veri kaynağı öğeleri sürükleyerek hizmetinden alınan verileri görüntüleyen formlar oluşturabilirsiniz **veri kaynakları** tasarımcıya penceresi. Bu öğeler, veri kaynağı ile ilişkili denetimleri haline gelir. Yürütme sırasında bu veri kaynağı bir örneğine bağlanır <xref:System.Data.Services.Client.DataServiceCollection%601> veri hizmetine bir sorgu tarafından döndürülen nesnelerle doldurulur sınıfı. Daha fazla bilgi için bkz: [denetimlere veri bağlama](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
 Bu konuda kullanımda Northwind örnek veri hizmeti örnekleri ve otomatik olarak oluşturulur istemci veri sınıfları hizmeti. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturduğunuz [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-use-a-project-data-source-in-a-wpf-window"></a>Bir WPF penceresinde proje veri kaynağı kullanmak için  
  
1.  Bir WPF projesi, Northwind veri hizmeti için bir başvuru ekleyin. Daha fazla bilgi için bkz: [nasıl yapılır: bir veri hizmet Başvurusu Ekle](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).  
  
2.  İçinde **veri kaynakları** penceresinde genişletin `Customers` düğümünde **NorthwindEntities** proje veri kaynağı.  
  
3.  Tıklatın **CustomerID** öğesi, select **ComboBox** listesi ve sürükleme **CustomerID** gelen öğe **müşteriler** düğüme Tasarımcısı.  
  
     Bu pencere için XAML dosyasında aşağıdaki nesne öğeleri oluşturur:  
  
    -   A <xref:System.Windows.Data.CollectionViewSource> adlı öğe `customersViewSource`. <xref:System.Windows.FrameworkElement.DataContext%2A> Özelliğinin üst düzey <xref:System.Windows.Controls.Grid> object öğesi ayarlanmış bu yeni <xref:System.Windows.Data.CollectionViewSource>.  
  
    -   Veri bağlama <xref:System.Windows.Controls.ComboBox> adlı `CustomerID`.  
  
    -   A <xref:System.Windows.Controls.Label>.  
  
4.  Sürükleme **siparişleri** Tasarımcısı için gezinme özelliği.  
  
     Bu pencere için XAML dosyasında aşağıdaki ek nesne öğeleri oluşturur:  
  
    -   İkinci bir <xref:System.Windows.Data.CollectionViewSource> adlı öğe `customersOrdersViewSource`, kaynağı `customerViewSource`.  
  
    -   Veri bağlama <xref:System.Windows.Controls.DataGrid> adlı Denetim `ordersDataGrid`.  
  
5.  (İsteğe bağlı) Sürükleme ek öğelerinden **müşteriler** Tasarımcı düğüme.  
  
6.  Form için kod sayfasını açın ve aşağıdakileri ekleyin `using` deyimleri (`Imports` Visual Basic'te):  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf2.xaml.cs#customersordersusingwpf)]  
  
7.  Formun tanımlayan kısmi sınıfında oluşturan aşağıdaki kodu ekleyin bir <xref:System.Data.Objects.ObjectContext> örneği ve tanımlar `customerID` sabit.  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf2.xaml.cs#customersordersdefinitionwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf2.xaml.vb#customersordersdefinitionwpf)]  
  
8.  Tasarımcıda penceresi seçin.  
  
    > [!NOTE]
    >  Kendisi yerine pencere içinde içerik seçerek penceresi seçtiğinizden emin olun. Penceresinde seçili ise, **adı** metin kutusunun üst kısmına yakın **özellikleri** penceresi penceresinin adını içermelidir.  
  
9. İçinde **özellikleri** penceresinde, seçin **olayları** düğmesi.  
  
10. Bul **yüklenen** olay ve bu olay yanında aşağı açılan listeden çift tıklatarak.  
  
     Visual Studio penceresinin arka plan kodu dosyayı açar ve oluşturur bir <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisi.  
  
11. Yeni oluşturulan <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisi, aşağıdaki kodu kopyalayıp yapıştırın.  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf2.xaml.cs#customersordersdatabindingwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf2.xaml.vb#customersordersdatabindingwpf)]  
  
12. Bu kod örneği oluşturur <xref:System.Data.Services.Client.DataServiceCollection%601> için `Customers` türü döndüren bir LINQ Sorgu yürütme üzerinde dayalı bir <xref:System.Collections.Generic.IEnumerable%601> , `Customers` ilgili birlikte `Orders` nesneleri Northwind veri hizmetinden ve bağlar`customersViewSource`.  
  
### <a name="to-use-a-project-data-source-in-a-windows-form"></a>Bir Windows formunda proje veri kaynağı kullanmak için  
  
1.  İçinde **veri kaynakları** penceresinde genişletin **müşteriler** düğümünde **NorthwindEntities** proje veri kaynağı.  
  
2.  Tıklatın **CustomerID** öğesi, select **ComboBox** listesi ve sürükleme **CustomerID** gelen öğe **müşteriler** düğüme Tasarımcısı.  
  
     Bu form üzerinde aşağıdaki denetimleri oluşturur:  
  
    -   Örneği <xref:System.Windows.Forms.BindingSource> adlı `customersBindingSource`.  
  
    -   Örneği <xref:System.Windows.Forms.BindingNavigator> adlı `customersBindingNavigator`. Gerekmeyen şekilde, bu denetim silebilirsiniz.  
  
    -   Veri bağlama <xref:System.Windows.Forms.ComboBox> adlı `CustomerID`.  
  
    -   A <xref:System.Windows.Forms.Label>.  
  
3.  Sürükleme **siparişleri** form için gezinme özelliği.  
  
4.  Bu oluşturur `ordersBindingSource` ile kontrol <xref:System.Windows.Forms.BindingSource.DataSource%2A> özellik kümesine denetiminin `customersBindingSource` ve <xref:System.Windows.Forms.BindingSource.DataMember%2A> özelliğini `Customers`. Ayrıca oluşturur `ordersDataGridView` uygun şekilde başlıklı etiket denetimi tarafından eşlik formunda veri bağlama denetimi.  
  
5.  (İsteğe bağlı) Sürükleme ek öğelerinden **müşteriler** Tasarımcı düğüme.  
  
6.  Form için kod sayfasını açın ve aşağıdakileri ekleyin `using` deyimleri (`Imports` Visual Basic'te):  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersusing)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersusing)]  
  
7.  Formun tanımlayan kısmi sınıfında oluşturan aşağıdaki kodu ekleyin bir <xref:System.Data.Objects.ObjectContext> örneği ve tanımlar `customerID` sabit.  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersdefinition)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersdefinition)]  
  
8.  Form Tasarımcısı'nda formu çift tıklatın.  
  
     Bu form için kod sayfası açılır ve işleyen yöntem oluşturur `Load` olayını formu.  
  
9. İçinde `Load` olay işleyicisi, aşağıdaki kodu kopyalayıp yapıştırın.  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersdatabinding)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersdatabinding)]  
  
10. Bu kod örneği oluşturur <xref:System.Data.Services.Client.DataServiceCollection%601> için `Customers` tipiyle yürütme işlemi bir <xref:System.Data.Services.Client.DataServiceQuery%601> döndüren bir <xref:System.Collections.Generic.IEnumerable%601> , `Customers` Northwind veri hizmeti ve kendisine bağlar `customersBindingSource`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Nasıl yapılır: Windows Presentation Foundation Öğelerine Veri Bağlama](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)
