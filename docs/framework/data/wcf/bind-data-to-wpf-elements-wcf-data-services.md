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
ms.openlocfilehash: 44f3361aa56d9f15e62852000accd0b4d4d8eb43
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791136"
---
# <a name="how-to-bind-data-to-windows-presentation-foundation-elements-wcf-data-services"></a>Nasıl yapılır: Windows Presentation Foundation öğelerine veri bağlama (WCF Veri Hizmetleri)
İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], <xref:System.Data.Services.Client.DataServiceContext> <xref:System.Windows.Controls.ListBox> veya<xref:System.Windows.Controls.ComboBox>gibi Windows Presentation Foundation (WPF) öğelerini ,değişikliklerileeşitlenmişhaldetutmakiçindenetimlertarafındanoluşturulanolaylarıişleyenbirörneğinebağlayabilirsiniz.<xref:System.Data.Services.Client.DataServiceCollection%601> denetimlerde verilere yapılır. Daha fazla bilgi için bkz. [verileri denetimlere bağlama](binding-data-to-controls-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, WPF 'de `SalesOrders` pencereyi tanımlayan bir Extensible Application Markup Language (XAML) sayfası için arka plan kod sayfasından verilmiştir. Pencere yüklendiğinde, <xref:System.Data.Services.Client.DataServiceCollection%601> müşterileri döndüren, ülkeye/bölgeye göre filtrelenmiş bir sorgunun sonucuna göre oluşturulur. Bu disk belleğine alınan sonucun tüm sayfaları, ilişkili siparişlerle birlikte yüklenir ve WPF penceresi için kök Düzen denetimi <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.StackPanel> olan öğesinin özelliğine bağlanır. Daha fazla bilgi için bkz. [ertelenmiş Içerik yükleme](loading-deferred-content-wcf-data-services.md).  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML, önceki örnek `SalesOrders` için WPF 'deki pencereyi tanımlar.  
  
 [!code-xaml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, WPF 'de `SalesOrders` pencereyi tanımlayan bir Extensible Application Markup Language (XAML) sayfası için arka plan kod sayfasından verilmiştir. Pencere yüklendiğinde, <xref:System.Data.Services.Client.DataServiceCollection%601> müşterileri ilgili nesneler, ülkeye/bölgeye göre filtrelenmiş bir sorgu sonucuna göre oluşturulur. Bu sonuç, <xref:System.Windows.Controls.StackPanel> WPF penceresi için <xref:System.Windows.FrameworkElement.DataContext%2A> kök Düzen denetimi olan öğesinin özelliğine bağımlıdır.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML, önceki örnek `SalesOrders` için WPF 'deki pencereyi tanımlar.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]
