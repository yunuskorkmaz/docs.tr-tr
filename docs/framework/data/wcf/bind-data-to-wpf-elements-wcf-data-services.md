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
ms.openlocfilehash: da89eebb366cebca9933a30b4753e1fbbe2707c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363901"
---
# <a name="how-to-bind-data-to-windows-presentation-foundation-elements-wcf-data-services"></a>Nasıl yapılır: Windows Presentation Foundation öğelerine (WCF Veri Hizmetleri) veri bağlama
İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], Windows Presentation Foundation (WPF) öğelerini aşağıdaki gibi bağlayabileceğiniz bir <xref:System.Windows.Controls.ListBox>'' veya <xref:System.Windows.Controls.ComboBox> örneğine <xref:System.Data.Services.Client.DataServiceCollection%601>, tutmak için denetimler tarafından oluşturulan olayları işleme <xref:System.Data.Services.Client.DataServiceContext> değişikliklerle eşitlenmesi denetimlerinde verileri için yapılır. Daha fazla bilgi için bkz: [denetimlere veri bağlama](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulur istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturduğunuz [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Tanımlayan bir Genişletilebilir uygulama biçimlendirme dili (XAML) sayfası için arka plan kod sayfası aşağıdaki örnek kaynaklı `SalesOrders` WPF penceresi. Pencerenin yüklendiğinde bir <xref:System.Data.Services.Client.DataServiceCollection%601> ülkeye göre filtrelenmiş müşteriler, döndüren bir sorgu sonucunu temel alınarak oluşturulur. Tüm bu disk belleğine alınan sonucu sayfaları, ilgili siparişleri birlikte yüklenir ve bağlı <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği <xref:System.Windows.Controls.StackPanel> diğer bir deyişle kök düzen denetimi WPF penceresi için. Daha fazla bilgi için bkz: [ertelenmiş içerik yüklenirken](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML tanımlar `SalesOrders` WPF penceresinde önceki örnek.  
  
 [!code-xaml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## <a name="example"></a>Örnek  
 Tanımlayan bir Genişletilebilir uygulama biçimlendirme dili (XAML) sayfası için arka plan kod sayfası aşağıdaki örnek kaynaklı `SalesOrders` WPF penceresi. Pencerenin yüklendiğinde bir <xref:System.Data.Services.Client.DataServiceCollection%601> ülkeye göre filtrelenen ilgili nesne müşterilerle döndüren bir sorgu sonucunu temel alınarak oluşturulur. Bu sonuca bağlı <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği <xref:System.Windows.Controls.StackPanel> diğer bir deyişle kök düzen denetimi WPF penceresi için.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML tanımlar `SalesOrders` WPF penceresinde önceki örnek.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]
