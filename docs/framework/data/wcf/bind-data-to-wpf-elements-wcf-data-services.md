---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Windows Presentation Foundation öğelerine veri bağlama (WCF Veri Hizmetleri)'
title: 'Nasıl yapılır: Windows Presentation Foundation öğelerine veri bağlama (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: d6538ab0-0abe-426a-b9d9-e6f3a5ca2016
ms.openlocfilehash: 57ad03770681fbedf9b0d5afae82a0a2590f0bc6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766536"
---
# <a name="how-to-bind-data-to-windows-presentation-foundation-elements-wcf-data-services"></a>Nasıl yapılır: Windows Presentation Foundation öğelerine veri bağlama (WCF Veri Hizmetleri)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

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
