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
ms.openlocfilehash: 62a7e3bf7caf60c6a532dbffeb8aac8b6c59deb9
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44129495"
---
# <a name="how-to-bind-data-using-a-project-data-source-wcf-data-services"></a>Nasıl yapılır: Proje veri kaynağı (WCF Veri Hizmetleri) kullanarak veri bağlama

Bir WCF Veri Hizmetleri istemci uygulamasında oluşturulan veri nesneleri temel alan veri kaynakları oluşturabilirsiniz. Kullanarak bir veri hizmetine başvuru eklerken **hizmet Başvurusu Ekle** iletişim kutusunda, bir proje veri kaynağı ile birlikte oluşturulan istemci veri sınıfları oluşturulur. Bir veri kaynağı hizmeti kullanıma sunan veriler her bir valık kümesi oluşturulur. Bu veri kaynağı öğe sürükleyerek hizmetten alınan verileri görüntüleyen formları oluşturabilirsiniz **veri kaynakları** tasarımcıya penceresi. Bu öğeler, veri kaynağına bağlı denetimler haline gelir. Yürütme sırasında bu veri kaynağı örneğine bağlı <xref:System.Data.Services.Client.DataServiceCollection%601> sınıfını, ki bu veri hizmetine bir sorgu tarafından döndürülen nesnelerle doldurulur. Daha fazla bilgi için [denetimlere veri bağlama](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).

 Otomatik olarak oluşturulan istemci verilerinin ve bu konuda kullanım Northwind örnek veri hizmeti sınıfları hizmeti. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).

## <a name="use-a-project-data-source-in-a-wpf-window"></a>Bir WPF penceresinde proje veri kaynağı kullanma

1.  Visual Studio'da bir WPF projesi Northwind verileri hizmeti bir başvuru ekleyin. Daha fazla bilgi için [nasıl yapılır: bir veri hizmeti başvurusu ekleme](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).

2.  İçinde **veri kaynakları** penceresini genişletin `Customers` düğümünde **NorthwindEntities** proje veri kaynağı.

3.  Tıklayın **CustomerID** öğesi, select **ComboBox** listesi ve sürükleme **CustomerID** öğesini **müşteriler** düğümü Tasarımcı.

     Bu pencere için XAML dosyasında aşağıdaki nesne öğeleri oluşturur:

    -   A <xref:System.Windows.Data.CollectionViewSource> adlı bir öğe `customersViewSource`. <xref:System.Windows.FrameworkElement.DataContext%2A> Özelliği üst düzey <xref:System.Windows.Controls.Grid> nesne öğesi ayarlandığından bu yeni <xref:System.Windows.Data.CollectionViewSource>.

    -   Verilere bağlı <xref:System.Windows.Controls.ComboBox> adlı `CustomerID`.

    -   A <xref:System.Windows.Controls.Label>.

4.  Sürükleme **siparişler** tasarımcıya gezinme özelliği.

     Bu pencere için XAML dosyasında aşağıdaki ek nesne öğeleri oluşturur:

    -   İkinci <xref:System.Windows.Data.CollectionViewSource> adlı bir öğe `customersOrdersViewSource`, kaynağı `customerViewSource`.

    -   Verilere bağlı <xref:System.Windows.Controls.DataGrid> adlı Denetim `ordersDataGrid`.

5.  (İsteğe bağlı) Ek öğeleri sürükleyin **müşteriler** tasarımcıya düğümü.

6.  Form için kod sayfasını açın ve aşağıdakileri ekleyin `using` deyimleri (`Imports` Visual Basic'te):

     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf2.xaml.cs#customersordersusingwpf)]

7.  Form tanımlayan kısmi class içinde oluşturan aşağıdaki kodu ekleyin. bir <xref:System.Data.Objects.ObjectContext> tanımlar ve örnek `customerID` sabit.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf2.xaml.cs#customersordersdefinitionwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf2.xaml.vb#customersordersdefinitionwpf)]

8.  Tasarımcıda penceresi seçin.

    > [!NOTE]
    > Kendisi yerine seçme içinde pencerenin içerik pencere seçtiğinizden emin olun. Pencerenin seçtiyseniz **adı** metin kutusunun üstüne yakın bir yere **özellikleri** penceresini, pencerenin adını içermelidir.

9. İçinde **özellikleri** penceresinde **olayları** düğmesi.

10. Bulma **Loaded** olay ve bu olayın yanındaki aşağı açılan listesinde çift tıklatarak.

     Visual Studio pencere için arka plan kod dosyasını açıp oluşturur bir <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisi.

11. Yeni oluşturulan <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisine aşağıdaki kodu kopyalayıp yapıştırın.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf2.xaml.cs#customersordersdatabindingwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf2.xaml.vb#customersordersdatabindingwpf)]

12. Bu kod örneği oluşturur <xref:System.Data.Services.Client.DataServiceCollection%601> için `Customers` türüne göre döndüren bir LINQ Sorgu yürütme bir <xref:System.Collections.Generic.IEnumerable%601> , `Customers` yanı sıra ilgili `Orders` Northwind veri hizmetinden nesneleri ve içinbağlar`customersViewSource`.

## <a name="use-a-project-data-source-in-a-windows-form"></a>Bir Windows formda proje veri kaynağı kullanma

1.  İçinde **veri kaynakları** penceresini genişletin **müşteriler** düğümünde **NorthwindEntities** proje veri kaynağı.

2.  Tıklayın **CustomerID** öğesi, select **ComboBox** listesi ve sürükleme **CustomerID** öğesini **müşteriler** düğümü Tasarımcı.

     Bu form aşağıdaki denetimleri oluşturur:

    -   Örneği <xref:System.Windows.Forms.BindingSource> adlı `customersBindingSource`.

    -   Örneği <xref:System.Windows.Forms.BindingNavigator> adlı `customersBindingNavigator`. Gerekmeyen şekilde, bu denetim silebilirsiniz.

    -   Verilere bağlı <xref:System.Windows.Forms.ComboBox> adlı `CustomerID`.

    -   A <xref:System.Windows.Forms.Label>.

3.  Sürükleme **siparişler** forma gezinme özelliği.

4.  Bu oluşturur `ordersBindingSource` denetimini <xref:System.Windows.Forms.BindingSource.DataSource%2A> ayarlamak denetim özelliğini `customersBindingSource` ve <xref:System.Windows.Forms.BindingSource.DataMember%2A> özelliğini `Customers`. Ayrıca oluşturur `ordersDataGridView` formunda bir uygun şekilde başlıklı etiket denetimi tarafından eşlik veriye bağlı denetim.

5.  (İsteğe bağlı) Ek öğeleri sürükleyin **müşteriler** tasarımcıya düğümü.

6.  Form için kod sayfasını açın ve aşağıdakileri ekleyin `using` deyimleri (`Imports` Visual Basic'te):

     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersusing)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersusing)]

7.  Form tanımlayan kısmi class içinde oluşturan aşağıdaki kodu ekleyin. bir <xref:System.Data.Objects.ObjectContext> tanımlar ve örnek `customerID` sabit.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersdefinition)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersdefinition)]

8.  Form Tasarımcısı'nda formu çift tıklatın.

     Bu form için kod sayfası açılır ve işleyen yöntem oluşturur `Load` olayı.

9. İçinde `Load` olay işleyicisine aşağıdaki kodu kopyalayıp yapıştırın.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersdatabinding)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersdatabinding)]

10. Bu kod örneği oluşturur <xref:System.Data.Services.Client.DataServiceCollection%601> için `Customers` türüne göre yürütülmesini bir <xref:System.Data.Services.Client.DataServiceQuery%601> döndüren bir <xref:System.Collections.Generic.IEnumerable%601> , `Customers` Northwind verileri hizmeti ve bağlar `customersBindingSource`.

## <a name="see-also"></a>Ayrıca Bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Nasıl yapılır: Windows Presentation Foundation Öğelerine Veri Bağlama](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)
