---
title: 'Nasıl yapılır: Windows Presentation Foundation öğelerine veri bağlama (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: d6538ab0-0abe-426a-b9d9-e6f3a5ca2016
ms.openlocfilehash: d6f50fb849d958ae1109324f1055b84451bde5a9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191638"
---
# <a name="how-to-bind-data-to-windows-presentation-foundation-elements-wcf-data-services"></a>Nasıl yapılır: Windows Presentation Foundation öğelerine veri bağlama (WCF Veri Hizmetleri)

WCF Veri Hizmetleri ile, bir veya gibi Windows Presentation Foundation (WPF) öğelerini <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ComboBox> , denetimlerin <xref:System.Data.Services.Client.DataServiceCollection%601> <xref:System.Data.Services.Client.DataServiceContext> içindeki verilerde yapılan değişikliklerle eşitlenmiş halde tutmak için denetimler tarafından oluşturulan olayları işleyen bir örneğine bağlayabilirsiniz. Daha fazla bilgi için bkz. [verileri denetimlere bağlama](binding-data-to-controls-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, WPF 'de pencereyi tanımlayan bir Extensible Application Markup Language (XAML) sayfası için arka plan kod sayfasından verilmiştir `SalesOrders` . Pencere yüklendiğinde, <xref:System.Data.Services.Client.DataServiceCollection%601> müşterileri döndüren, ülkeye/bölgeye göre filtrelenmiş bir sorgunun sonucuna göre oluşturulur. Bu disk belleğine alınan sonucun tüm sayfaları, ilişkili siparişlerle birlikte yüklenir ve <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.StackPanel> WPF penceresi için kök Düzen denetimi olan öğesinin özelliğine bağlanır. Daha fazla bilgi için bkz. [ertelenmiş Içerik yükleme](loading-deferred-content-wcf-data-services.md).  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki XAML, `SalesOrders` önceki örnek IÇIN WPF 'deki pencereyi tanımlar.  
  
 [!code-xaml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, WPF 'de pencereyi tanımlayan bir Extensible Application Markup Language (XAML) sayfası için arka plan kod sayfasından verilmiştir `SalesOrders` . Pencere yüklendiğinde, <xref:System.Data.Services.Client.DataServiceCollection%601> müşterileri ilgili nesneler, ülkeye/bölgeye göre filtrelenmiş bir sorgu sonucuna göre oluşturulur. Bu sonuç <xref:System.Windows.FrameworkElement.DataContext%2A> , <xref:System.Windows.Controls.StackPanel> WPF penceresi için kök Düzen denetimi olan öğesinin özelliğine bağımlıdır.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki XAML, `SalesOrders` önceki örnek IÇIN WPF 'deki pencereyi tanımlar.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]
