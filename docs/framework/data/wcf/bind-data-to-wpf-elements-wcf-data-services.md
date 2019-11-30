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
ms.openlocfilehash: b623dc10bfe1b723c62b2861b4142a138904e64a
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569336"
---
# <a name="how-to-bind-data-to-windows-presentation-foundation-elements-wcf-data-services"></a>Nasıl yapılır: Windows Presentation Foundation öğelerine veri bağlama (WCF Veri Hizmetleri)
WCF Veri Hizmetleri, <xref:System.Windows.Controls.ListBox> veya <xref:System.Windows.Controls.ComboBox> gibi Windows Presentation Foundation (WPF) öğelerini, denetimleri içindeki verilerde yapılan değişikliklerle eşitlenmiş halde tutmak için denetimler tarafından oluşturulan olayları işleyen bir <xref:System.Data.Services.Client.DataServiceCollection%601>örneğine bağlayabilirsiniz. Daha fazla bilgi için bkz. [verileri denetimlere bağlama](binding-data-to-controls-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, WPF 'de `SalesOrders` penceresini tanımlayan bir Extensible Application Markup Language (XAML) sayfası için arka plan kod sayfasından verilmiştir. Pencere yüklendiğinde, müşterileri döndüren bir sorgunun sonucuna göre, ülkeye/bölgeye göre filtrelenmiş bir <xref:System.Data.Services.Client.DataServiceCollection%601> oluşturulur. Bu disk belleğine alınan sonucun tüm sayfaları, ilişkili siparişlerle birlikte yüklenir ve WPF penceresi için kök Düzen denetimi olan <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.FrameworkElement.DataContext%2A> özelliğine bağlanır. Daha fazla bilgi için bkz. [ertelenmiş Içerik yükleme](loading-deferred-content-wcf-data-services.md).  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML, önceki örnek için WPF 'de `SalesOrders` penceresini tanımlar.  
  
 [!code-xaml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, WPF 'de `SalesOrders` penceresini tanımlayan bir Extensible Application Markup Language (XAML) sayfası için arka plan kod sayfasından verilmiştir. Pencere yüklendiğinde, müşterileri ilgili nesneler, ülkeye/bölgeye göre filtrelenmiş bir sorgu sonucuna göre bir <xref:System.Data.Services.Client.DataServiceCollection%601> oluşturulur. Bu sonuç WPF penceresi için kök Düzen denetimi olan <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.FrameworkElement.DataContext%2A> özelliğine bağımlıdır.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML, önceki örnek için WPF 'de `SalesOrders` penceresini tanımlar.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]
