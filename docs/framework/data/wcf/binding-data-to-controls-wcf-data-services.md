---
title: Denetimlere veri bağlama (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- data binding, WCF Data Services
ms.assetid: b32e1d49-c214-4cb1-867e-88fbb3d08c8d
ms.openlocfilehash: 178d77c225144497982487afa00f4493e17d1744
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91805219"
---
# <a name="binding-data-to-controls-wcf-data-services"></a>Denetimlere veri bağlama (WCF Veri Hizmetleri)

WCF Veri Hizmetleri ile, `ComboBox` ve denetimleri gibi denetimleri `ListView` sınıfının bir örneğine bağlayabilirsiniz <xref:System.Data.Services.Client.DataServiceCollection%601> . Sınıfından devralan bu koleksiyon, <xref:System.Collections.ObjectModel.ObservableCollection%601> bir açık veri Protokolü (OData) akışından gelen verileri içerir. Bu sınıf, öğeler eklendiğinde veya kaldırıldığında bildirim sağlayan dinamik bir veri koleksiyonunu temsil eder. Veri bağlama için bir örneğini kullandığınızda <xref:System.Data.Services.Client.DataServiceCollection%601> , WCF veri Hizmetleri istemci kitaplıkları, tarafından izlenen nesnelerin, <xref:System.Data.Services.Client.DataServiceContext> ilişkili kullanıcı arabirimi öğesindeki verilerle eşitlendiğinden emin olmak için bu olayları işler.  
  
 <xref:System.Data.Services.Client.DataServiceCollection%601>Sınıfı (dolaylı), <xref:System.Collections.Specialized.INotifyCollectionChanged> nesneleri koleksiyona eklendiğinde veya koleksiyondan kaldırıldığında bağlamı uyarmak için arabirimini uygular. İle kullanılan veri hizmeti türü nesneleri, <xref:System.Data.Services.Client.DataServiceCollection%601> <xref:System.ComponentModel.INotifyPropertyChanged> <xref:System.Data.Services.Client.DataServiceCollection%601> bağlama koleksiyonundaki nesnelerin özellikleri değiştiğinde uyarı almak için arabirimini de uygulamalıdır.  
  
> [!NOTE]
> İstemci veri hizmeti sınıfları oluşturma seçeneği ile **hizmet başvurusu Ekle** iletişim kutusunu veya [DataSvcUtil.exe](wcf-data-service-client-utility-datasvcutil-exe.md) aracını kullandığınızda `/dataservicecollection` , oluşturulan veri sınıfları <xref:System.ComponentModel.INotifyPropertyChanged> arabirimini uygular. Daha fazla bilgi için bkz. [nasıl yapılır: El Ile Istemci veri hizmeti sınıfları oluşturma](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
## <a name="creating-the-binding-collection"></a>Bağlama koleksiyonu oluşturma  

 Sınıf <xref:System.Data.Services.Client.DataServiceCollection%601> Oluşturucu yöntemlerinden birini sağlanan <xref:System.Data.Services.Client.DataServiceContext> örnekle ve isteğe bağlı olarak <xref:System.Data.Services.Client.DataServiceQuery%601> , yürütüldüğü zaman bir örnek döndüren bir LINQ sorgusuyla çağırarak sınıfının yeni bir örneğini oluşturun <xref:System.Collections.Generic.IEnumerable%601> . Bu, <xref:System.Collections.Generic.IEnumerable%601> bir OData akışından gerçekleştirilmiş olan bağlama koleksiyonu için nesne kaynağı sağlar. Daha fazla bilgi için bkz. [nesne materialization](object-materialization-wcf-data-services.md). Varsayılan olarak, bağlantılı nesnelerde yapılan değişiklikler ve koleksiyona eklenen öğeler tarafından otomatik olarak izlenir <xref:System.Data.Services.Client.DataServiceContext> . Bu değişiklikleri el ile izlemeniz gerekiyorsa, bir `trackingMode` parametre alan ve değerini belirten Oluşturucu yöntemlerinden birini çağırın <xref:System.Data.Services.Client.TrackingMode.None> .  
  
 Aşağıdaki örnek, <xref:System.Data.Services.Client.DataServiceCollection%601> <xref:System.Data.Services.Client.DataServiceContext> <xref:System.Data.Services.Client.DataServiceQuery%601> ilişkili ve tüm müşterileri iade eden bir, sağlanan ve içeren bir örneğinin nasıl oluşturulacağını gösterir:  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrders2Binding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders2.cs#customersorders2binding)]
 [!code-vb[Astoria Northwind Client#CustomersOrders2Binding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders2.vb#customersorders2binding)]  
  
## <a name="binding-data-to-windows-presentation-foundation-elements"></a>Windows Presentation Foundation öğelerine veri bağlama  

 Sınıfı sınıfından <xref:System.Data.Services.Client.DataServiceCollection%601> devraldığı için <xref:System.Collections.ObjectModel.ObservableCollection%601> , nesneleri bağlama için kullanırken yaptığınız gibi bir WINDOWS PRESENTATION FOUNDATION (WPF) uygulamasındaki bir öğeye veya denetime nesneleri bağlayabilirsiniz <xref:System.Collections.ObjectModel.ObservableCollection%601> . Daha fazla bilgi için bkz. [veri bağlama (Windows Presentation Foundation)](/dotnet/desktop/wpf/data/data-binding-overview). Veri hizmeti verilerini WPF denetimlerine bağlamak için bir yol, `DataContext` öğesinin özelliğini <xref:System.Data.Services.Client.DataServiceCollection%601> sorgu sonucunu içeren sınıfın örneğine ayarlamaya yönelik bir yoldur. Bu durumda, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> denetimin nesne kaynağını ayarlamak için özelliğini kullanın. <xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>Bağlantılı nesnenin hangi özelliğinin görüntüleneceğini belirtmek için özelliğini kullanın. Bir öğeyi bir gezinti özelliği tarafından döndürülen ilgili bir nesneye bağlıyorsanız, yolu özelliği için tanımlanan bağlamaya ekleyin <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> . Bu yol, üst denetimin özelliği tarafından ayarlanan kök nesneye göredir <xref:System.Windows.FrameworkElement.DataContext%2A> . Aşağıdaki örnek, <xref:System.Windows.FrameworkElement.DataContext%2A> bir öğesinin özelliğini, <xref:System.Windows.Controls.StackPanel> üst denetimi bir müşteri nesnesine bağlamak için ayarlar <xref:System.Data.Services.Client.DataServiceCollection%601> :  
  
 [!code-csharp[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#masterdetailbinding)]
 [!code-csharp[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#masterdetailbinding)]  
  
 Aşağıdaki örnek, alt ve denetimlerin XAML bağlama tanımını gösterir <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.ComboBox> :  
  
 [!code-xaml[Astoria Northwind Client#MasterDetailXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#masterdetailxaml)]  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: verileri Windows Presentation Foundation bağlama](bind-data-to-wpf-elements-wcf-data-services.md).  
  
 Bir varlık bire çok veya çoktan çoğa ilişkiye katılıyorsa, ilişkinin gezinti özelliği ilişkili nesnelerin bir koleksiyonunu döndürür. İstemci veri hizmeti sınıflarını oluşturmak için **hizmet başvurusu Ekle** iletişim kutusunu veya DataSvcUtil.exe aracını kullandığınızda, gezinti özelliği öğesinin bir örneğini döndürür <xref:System.Data.Services.Client.DataServiceCollection%601> . Bu, ilgili nesneleri bir denetime bağlamanıza ve ilgili varlıklar için ana ayrıntı bağlama deseninin gibi ortak WPF bağlama senaryolarına destek sağlamanıza olanak sağlar. Önceki XAML örneğinde, XAML kodu ana <xref:System.Data.Services.Client.DataServiceCollection%601> öğeyi kök veri öğesine bağlar. Düzen <xref:System.Windows.Controls.DataGrid> daha sonra <xref:System.Data.Services.Client.DataServiceCollection%601> Seçili müşteriler nesnesinden döndürülen siparişlere bağlanır, bu da ' ın kök veri öğesine bağımlıdır <xref:System.Windows.Window> .  
  
## <a name="binding-data-to-windows-forms-controls"></a>Windows Forms denetimlerine veri bağlama  

 Nesneleri bir Windows form denetimine bağlamak için `DataSource` denetimin özelliğini <xref:System.Data.Services.Client.DataServiceCollection%601> sorgu sonucunu içeren sınıfın örneğine ayarlayın.  
  
> [!NOTE]
> Veri bağlama yalnızca ve arabirimlerini uygulayarak değişiklik olaylarını dinleyen denetimler için desteklenir <xref:System.Collections.Specialized.INotifyCollectionChanged> <xref:System.ComponentModel.INotifyPropertyChanged> . Bir denetim bu tür değişiklik bildirimini desteklemiyorsa, temelde yapılan değişiklikler, <xref:System.Data.Services.Client.DataServiceCollection%601> ilişkili denetimde yansıtılmaz.  
  
 Aşağıdaki örnek bir denetime bağlar <xref:System.Data.Services.Client.DataServiceCollection%601> <xref:System.Windows.Forms.ComboBox> :  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdatabindingspecific)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdatabindingspecific)]  
  
 İstemci veri hizmeti sınıflarını oluşturmak için **hizmet başvurusu Ekle** iletişim kutusunu kullandığınızda, oluşturulan öğesini temel alan bir proje veri kaynağı da oluşturulur <xref:System.Data.Services.Client.DataServiceContext> . Bu veri kaynağıyla, verileri veri **kaynakları** penceresinden tasarımcıya sürükleyerek yalnızca veri hizmetinden veri görüntüleyen kullanıcı arabirimi öğeleri veya denetimleri oluşturabilirsiniz. Bu öğeler, uygulama kullanıcı arabiriminde veri kaynağına bağlanan öğeler haline gelir. Daha fazla bilgi için bkz. [nasıl yapılır: bir proje veri kaynağı kullanarak veri bağlama](how-to-bind-data-using-a-project-data-source-wcf-data-services.md).  
  
## <a name="binding-paged-data"></a>Disk belleğine alınan verileri bağlama  

 Bir veri hizmeti, tek bir yanıt iletisinde döndürülen sorgulanan veri miktarını sınırlayacak şekilde yapılandırılabilir. Daha fazla bilgi için bkz. [veri hizmetini yapılandırma](configuring-the-data-service-wcf-data-services.md). Veri hizmeti yanıt verisi olduğunda, her yanıt bir sonraki sonuç sayfasını döndürmek için kullanılan bir bağlantı içerir. Daha fazla bilgi için bkz. [ertelenmiş Içerik yükleme](loading-deferred-content-wcf-data-services.md). Bu durumda, <xref:System.Data.Services.Client.DataServiceCollection%601.Load%2A> <xref:System.Data.Services.Client.DataServiceCollection%601> <xref:System.Data.Services.Client.DataServiceQueryContinuation.NextLinkUri%2A> Aşağıdaki örnekte olduğu gibi, ÖZELLIĞINDEN elde edilen URI 'yi geçirerek, açıkça sayfa yüklemeniz gerekir:  
  
 [!code-csharp[Astoria Northwind Client#BindPagedDataSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddataspecific)]
 [!code-vb[Astoria Northwind Client#BindPagedDataSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddataspecific)]  
  
 İlgili nesneler benzer bir şekilde yüklenir. Daha fazla bilgi için bkz. [nasıl yapılır: verileri Windows Presentation Foundation bağlama](bind-data-to-wpf-elements-wcf-data-services.md).  
  
## <a name="customizing-data-binding-behaviors"></a>Veri bağlama davranışlarını özelleştirme  

 <xref:System.Data.Services.Client.DataServiceCollection%601>Sınıfı, koleksiyonda yapılan değişiklikler yapıldığında, eklenen veya kaldırılan bir nesne ve bir koleksiyondaki nesnenin özelliklerinde değişiklik yapıldığında oluşan olayları ele almanıza olanak sağlar. Aşağıdaki kısıtlamaları içeren varsayılan davranışı geçersiz kılmak için veri bağlama olaylarını değiştirebilirsiniz:  
  
- Temsilciler içinde herhangi bir doğrulama yapılmaz.  
  
- Bir varlık eklemek ilgili varlıkları otomatik olarak ekler.  
  
- Bir varlığı silmek ilgili varlıkları silmez.  
  
 ' In yeni bir örneğini oluşturduğunuzda <xref:System.Data.Services.Client.DataServiceCollection%601> , bağlantılı nesneler değiştirildiğinde oluşturulan olayları işleyen yöntemlere temsilciler tanımlayan aşağıdaki parametreleri belirtme seçeneğiniz vardır:  
  
- `entityChanged` -bir bağlantılı nesnenin özelliği değiştirildiğinde çağrılan bir yöntem. Bu <xref:System.Func%602> temsilci bir nesne kabul eder <xref:System.Data.Services.Client.EntityChangedParams> ve varsayılan davranışın, <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> üzerinde çağrılıp gerçekleşmeyeceğini belirten bir Boole değeri döndürür <xref:System.Data.Services.Client.DataServiceContext> .  
  
- `entityCollectionChanged` -bağlama koleksiyonuna bir nesne eklendiğinde veya kaldırıldığında çağrılan bir yöntem. Bu <xref:System.Func%602> temsilci bir nesne kabul eder <xref:System.Data.Services.Client.EntityCollectionChangedParams> ve bir eylem için ya da bir eylem için çağrı yapmak üzere varsayılan davranışın, <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Add> <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Remove> <xref:System.Data.Services.Client.DataServiceContext> yine de gerçekleşmeyeceğini belirten bir Boole değeri döndürür.  
  
> [!NOTE]
> WCF Veri Hizmetleri, bu Temsilcilerde uyguladığınız özel davranışlardan herhangi bir doğrulama gerçekleştirmediğini gerçekleştirir.  
  
 Aşağıdaki örnekte <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Remove> eylem, <xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A> <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> `Orders_Details` silinen bir varlığa ait olan varlıkları kaldırmak için ve metodunu çağırmak üzere özelleştirilir `Orders` . Bu özel eylem, üst varlık silindiği zaman bağımlı varlıklar otomatik olarak silinmediği için gerçekleştirilir.  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#customersordersdeleterelated)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#customersordersdeleterelated)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#customersordersdeleterelated)]  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: veri bağlama davranışlarını özelleştirme](how-to-customize-data-binding-behaviors-wcf-data-services.md).  
  
 Yöntemi kullanılarak bir nesne öğesinden kaldırıldığında <xref:System.Data.Services.Client.DataServiceCollection%601> <xref:System.Collections.ObjectModel.Collection%601.Remove%2A> , nesnenin içinde de Deleted olarak işaretlendiğinden, varsayılan davranış <xref:System.Data.Services.Client.DataServiceContext> . Bu davranışı değiştirmek için, `entityCollectionChanged` olay gerçekleştiğinde çağrılan parametresindeki bir yönteme bir temsilci belirtebilirsiniz <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> .  
  
## <a name="data-binding-with-custom-client-data-classes"></a>Özel Istemci veri sınıflarıyla veri bağlama  

 Nesneleri bir öğesine yükleyebilmek için <xref:System.Data.Services.Client.DataServiceCollection%601> nesnelerin kendisi arabirimini uygulaması gerekir <xref:System.ComponentModel.INotifyPropertyChanged> . **Hizmet başvurusu Ekle** iletişim kutusunu veya bu arabirimi uygulayan [DataSvcUtil.exe](wcf-data-service-client-utility-datasvcutil-exe.md) aracını kullandığınızda oluşturulan veri hizmeti istemci sınıfları. Kendi istemci veri sınıflarınızı sağlarsanız, veri bağlama için başka bir koleksiyon türü kullanmanız gerekir. Nesneler değiştiğinde, sınıfının aşağıdaki yöntemlerini çağırmak için veri bağlantılı denetimlerindeki olayları işlemeniz gerekir <xref:System.Data.Services.Client.DataServiceContext> :  
  
- <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> -koleksiyona yeni bir nesne eklendiğinde.  
  
- <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> -bir nesne koleksiyondan kaldırıldığında.  
  
- <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> -Koleksiyondaki bir nesne üzerinde bir özellik değiştirildiğinde.  
  
- <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> -bir nesne ilgili nesne koleksiyonuna eklendiğinde.  
  
- <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> -bir nesne ilgili nesneler koleksiyonuna eklendiğinde.  
  
 Daha fazla bilgi için bkz. [veri hizmetini güncelleştirme](updating-the-data-service-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: El İle İstemci Veri Hizmeti Sınıfları Oluşturma](how-to-manually-generate-client-data-service-classes-wcf-data-services.md)
- [Nasıl yapılır: Veri Hizmeti Başvurusu Ekleme](how-to-add-a-data-service-reference-wcf-data-services.md)
