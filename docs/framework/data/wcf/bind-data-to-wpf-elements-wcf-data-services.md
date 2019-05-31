---
title: 'Nasıl yapılır: Windows Presentation Foundation öğelerine (WCF Veri Hizmetleri) veri bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: d6538ab0-0abe-426a-b9d9-e6f3a5ca2016
ms.openlocfilehash: cecfa42035d4c09eade708417c338ef04ab09ad9
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423831"
---
# <a name="how-to-bind-data-to-windows-presentation-foundation-elements-wcf-data-services"></a>Nasıl yapılır: Windows Presentation Foundation öğelerine (WCF Veri Hizmetleri) veri bağlama
İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], Windows Presentation Foundation (WPF) öğeleri gibi adlarınıza bağlayabileceğiniz bir <xref:System.Windows.Controls.ListBox> veya <xref:System.Windows.Controls.ComboBox> örneğine <xref:System.Data.Services.Client.DataServiceCollection%601>, tutmak denetimleri tarafından tetiklenen olayları işler <xref:System.Data.Services.Client.DataServiceContext> değişikliklerle eşitlenir denetimleri verilere yapılan. Daha fazla bilgi için [denetimlere veri bağlama](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulan istemci veri hizmeti sınıfları kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tanımlayan Extensible Application Markup Language (XAML) sayfası için arka plan kod sayfasından, `SalesOrders` WPF penceresi. Penceresi yüklendiğinde bir <xref:System.Data.Services.Client.DataServiceCollection%601> müşteriler, ülke/bölgeye göre filtrelenen döndüren bir sorgu sonucu temel alınarak oluşturulur. Tüm bu disk belleğine alınan sonuç sayfaları, ilgili Siparişler birlikte yüklü olduğundan ve bağlı <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği <xref:System.Windows.Controls.StackPanel> diğer bir deyişle WPF penceresi için kök düzen denetimi. Daha fazla bilgi için [ertelenmiş içerik yükleme](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML tanımlar `SalesOrders` WPF penceresinde önceki örneğin.  
  
 [!code-xaml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tanımlayan Extensible Application Markup Language (XAML) sayfası için arka plan kod sayfasından, `SalesOrders` WPF penceresi. Penceresi yüklendiğinde bir <xref:System.Data.Services.Client.DataServiceCollection%601> ülke/bölgeye göre filtrelenen, ilgili nesneleri müşterilerle döndüren bir sorgu sonucu temel alınarak oluşturulur. Bu sonuca bağlı <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği <xref:System.Windows.Controls.StackPanel> diğer bir deyişle WPF penceresi için kök düzen denetimi.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML tanımlar `SalesOrders` WPF penceresinde önceki örneğin.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]
