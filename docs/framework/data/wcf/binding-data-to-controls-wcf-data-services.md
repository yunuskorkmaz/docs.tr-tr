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
ms.openlocfilehash: e5448d837d6234198fb1f3652918776675a4a1cf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965835"
---
# <a name="binding-data-to-controls-wcf-data-services"></a>Denetimlere veri bağlama (WCF Veri Hizmetleri)
İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], `ComboBox` ve <xref:System.Data.Services.Client.DataServiceCollection%601> denetimleri gibi denetimleri sınıfının bir örneğine bağlayabilirsiniz. `ListView` <xref:System.Collections.ObjectModel.ObservableCollection%601> Sınıfından devralan bu koleksiyon, [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akıştan alınan verileri içerir. Bu sınıf, öğeler eklendiğinde veya kaldırıldığında bildirim sağlayan dinamik bir veri koleksiyonunu temsil eder. Veri bağlama <xref:System.Data.Services.Client.DataServiceCollection%601> için bir örneğini kullandığınızda [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] , istemci kitaplıkları, tarafından izlenen nesnelerin, <xref:System.Data.Services.Client.DataServiceContext> ilişkili kullanıcı arabirimi öğesindeki verilerle eşitlendiğinden emin olmak için bu olayları işler.  
  
 Sınıfı (dolaylı), nesneleri koleksiyona <xref:System.Collections.Specialized.INotifyCollectionChanged> eklendiğinde veya koleksiyondan kaldırıldığında bağlamı uyarmak için arabirimini uygular. <xref:System.Data.Services.Client.DataServiceCollection%601> İle <xref:System.Data.Services.Client.DataServiceCollection%601> kullanılan veri hizmeti türü nesneleri, bağlama koleksiyonundaki nesnelerin özellikleri <xref:System.ComponentModel.INotifyPropertyChanged> değiştiğinde uyarı <xref:System.Data.Services.Client.DataServiceCollection%601> almak için arabirimini de uygulamalıdır.  
  
> [!NOTE]
> İstemci veri hizmeti sınıfları oluşturma `/dataservicecollection` seçeneğiyle **hizmet başvurusu Ekle** iletişim kutusunu veya [DataSvcUtil. exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) aracını kullandığınızda, oluşturulan veri sınıfları <xref:System.ComponentModel.INotifyPropertyChanged> arabirimini uygular. Daha fazla bilgi için [nasıl yapılır: Istemci veri hizmeti sınıflarını](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)el ile oluşturun.  
  
## <a name="creating-the-binding-collection"></a>Bağlama koleksiyonu oluşturma  
 Sınıf <xref:System.Data.Services.Client.DataServiceCollection%601> Oluşturucu yöntemlerinden birini sağlanan <xref:System.Data.Services.Client.DataServiceContext> örnekle ve isteğe bağlı olarak <xref:System.Collections.Generic.IEnumerable%601> , yürütüldüğü zaman bir örnek döndüren bir <xref:System.Data.Services.Client.DataServiceQuery%601> LINQ sorgusuyla çağırarak sınıfının yeni bir örneğini oluşturun. Bu <xref:System.Collections.Generic.IEnumerable%601> , bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akıştan gerçekleştirilmiş olan bağlama koleksiyonu için nesne kaynağı sağlar. Daha fazla bilgi için bkz. [nesne materialization](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md). Varsayılan olarak, bağlantılı nesnelerde yapılan değişiklikler ve koleksiyona eklenen öğeler tarafından <xref:System.Data.Services.Client.DataServiceContext>otomatik olarak izlenir. Bu değişiklikleri el ile izlemeniz gerekiyorsa, bir `trackingMode` parametre alan ve <xref:System.Data.Services.Client.TrackingMode.None>değerini belirten Oluşturucu yöntemlerinden birini çağırın.  
  
 Aşağıdaki örnek, ilişkili ve tüm müşterileri iade eden bir <xref:System.Data.Services.Client.DataServiceCollection%601> , sağlanan <xref:System.Data.Services.Client.DataServiceContext> ve içeren bir <xref:System.Data.Services.Client.DataServiceQuery%601> örneğinin nasıl oluşturulacağını gösterir:  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrders2Binding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders2.cs#customersorders2binding)]
 [!code-vb[Astoria Northwind Client#CustomersOrders2Binding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders2.vb#customersorders2binding)]  
  
## <a name="binding-data-to-windows-presentation-foundation-elements"></a>Windows Presentation Foundation öğelerine veri bağlama  
 Sınıfı sınıfından devraldığı <xref:System.Collections.ObjectModel.ObservableCollection%601> için, nesneleri bağlama için kullanırken <xref:System.Collections.ObjectModel.ObservableCollection%601> yaptığınız gibi bir Windows Presentation Foundation (WPF) uygulamasındaki bir öğeye veya denetime nesneleri bağlayabilirsiniz. <xref:System.Data.Services.Client.DataServiceCollection%601> Daha fazla bilgi için bkz. [veri bağlama (Windows Presentation Foundation)](../../../../docs/framework/wpf/data/data-binding-wpf.md). Veri hizmeti verilerini WPF denetimlerine bağlamak için bir yol, öğesinin `DataContext` özelliğini sorgu sonucunu içeren <xref:System.Data.Services.Client.DataServiceCollection%601> sınıfın örneğine ayarlamaya yönelik bir yoldur. Bu durumda, denetimin nesne kaynağını ayarlamak <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> için özelliğini kullanın. Bağlantılı nesnenin hangi özelliğinin görüntüleneceğini belirtmek için özelliğinikullanın.<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A> Bir öğeyi bir gezinti özelliği tarafından döndürülen ilgili bir nesneye bağlıyorsanız, yolu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği için tanımlanan bağlamaya ekleyin. Bu yol, üst denetimin <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği tarafından ayarlanan kök nesneye göredir. Aşağıdaki örnek, bir <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.StackPanel> öğesinin özelliğini, üst denetimi <xref:System.Data.Services.Client.DataServiceCollection%601> bir müşteri nesnesine bağlamak için ayarlar:  
  
 [!code-csharp[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#masterdetailbinding)]
 [!code-csharp[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#masterdetailbinding)]  
  
 Aşağıdaki örnek, alt <xref:System.Windows.Controls.DataGrid> ve <xref:System.Windows.Controls.ComboBox> denetimlerin xaml bağlama tanımını gösterir:  
  
 [!code-xaml[Astoria Northwind Client#MasterDetailXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#masterdetailxaml)]  
  
 Daha fazla bilgi için [nasıl yapılır: Verileri Windows Presentation Foundation öğelerine](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)bağlayın.  
  
 Bir varlık bire çok veya çoktan çoğa ilişkiye katılıyorsa, ilişkinin gezinti özelliği ilişkili nesnelerin bir koleksiyonunu döndürür. İstemci veri hizmeti sınıflarını oluşturmak için **hizmet başvurusu Ekle** iletişim kutusunu veya DataSvcUtil. exe aracını kullandığınızda, gezinti özelliği öğesinin <xref:System.Data.Services.Client.DataServiceCollection%601>bir örneğini döndürür. Bu, ilgili nesneleri bir denetime bağlamanıza ve ilgili varlıklar için ana ayrıntı bağlama deseninin gibi ortak WPF bağlama senaryolarına destek sağlamanıza olanak sağlar. Önceki xaml örneğinde, XAML kodu ana <xref:System.Data.Services.Client.DataServiceCollection%601> öğeyi kök veri öğesine bağlar. Düzen <xref:System.Windows.Controls.DataGrid> daha sonra seçili müşteriler nesnesinden döndürülen siparişlere <xref:System.Data.Services.Client.DataServiceCollection%601> bağlanır, bu da ' ın <xref:System.Windows.Window>kök veri öğesine bağımlıdır.  
  
## <a name="binding-data-to-windows-forms-controls"></a>Windows Forms denetimlerine veri bağlama  
 Nesneleri bir Windows form denetimine bağlamak için denetimin `DataSource` özelliğini sorgu sonucunu içeren <xref:System.Data.Services.Client.DataServiceCollection%601> sınıfın örneğine ayarlayın.  
  
> [!NOTE]
> Veri bağlama yalnızca <xref:System.Collections.Specialized.INotifyCollectionChanged> ve <xref:System.ComponentModel.INotifyPropertyChanged> arabirimlerini uygulayarak değişiklik olaylarını dinleyen denetimler için desteklenir. Bir denetim bu tür değişiklik bildirimini desteklemiyorsa, temelde <xref:System.Data.Services.Client.DataServiceCollection%601> yapılan değişiklikler, ilişkili denetimde yansıtılmaz.  
  
 Aşağıdaki örnek bir <xref:System.Data.Services.Client.DataServiceCollection%601> <xref:System.Windows.Forms.ComboBox> denetime bağlar:  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdatabindingspecific)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdatabindingspecific)]  
  
 İstemci veri hizmeti sınıflarını oluşturmak için **hizmet başvurusu Ekle** iletişim kutusunu kullandığınızda, oluşturulan <xref:System.Data.Services.Client.DataServiceContext>öğesini temel alan bir proje veri kaynağı da oluşturulur. Bu veri kaynağıyla, verileri veri **kaynakları** penceresinden tasarımcıya sürükleyerek yalnızca veri hizmetinden veri görüntüleyen kullanıcı arabirimi öğeleri veya denetimleri oluşturabilirsiniz. Bu öğeler, uygulama kullanıcı arabiriminde veri kaynağına bağlanan öğeler haline gelir. Daha fazla bilgi için [nasıl yapılır: Bir proje veri kaynağı](../../../../docs/framework/data/wcf/how-to-bind-data-using-a-project-data-source-wcf-data-services.md)kullanarak veri bağlayın.  
  
## <a name="binding-paged-data"></a>Disk belleğine alınan verileri bağlama  
 Bir veri hizmeti, tek bir yanıt iletisinde döndürülen sorgulanan veri miktarını sınırlayacak şekilde yapılandırılabilir. Daha fazla bilgi için bkz. [veri hizmetini yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md). Veri hizmeti yanıt verisi olduğunda, her yanıt bir sonraki sonuç sayfasını döndürmek için kullanılan bir bağlantı içerir. Daha fazla bilgi için bkz. [ertelenmiş Içerik yükleme](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md). Bu durumda, aşağıdaki örnekte olduğu gibi, <xref:System.Data.Services.Client.DataServiceCollection%601.Load%2A> <xref:System.Data.Services.Client.DataServiceQueryContinuation.NextLinkUri%2A> özelliğinden elde edilen URI 'yi geçirerek, <xref:System.Data.Services.Client.DataServiceCollection%601> açıkça sayfa yüklemeniz gerekir:  
  
 [!code-csharp[Astoria Northwind Client#BindPagedDataSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddataspecific)]
 [!code-vb[Astoria Northwind Client#BindPagedDataSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddataspecific)]  
  
 İlgili nesneler benzer bir şekilde yüklenir. Daha fazla bilgi için [nasıl yapılır: Verileri Windows Presentation Foundation öğelerine](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)bağlayın.  
  
## <a name="customizing-data-binding-behaviors"></a>Veri bağlama davranışlarını özelleştirme  
 <xref:System.Data.Services.Client.DataServiceCollection%601> Sınıfı, koleksiyonda yapılan değişiklikler yapıldığında, eklenen veya kaldırılan bir nesne ve bir koleksiyondaki nesnenin özelliklerinde değişiklik yapıldığında oluşan olayları ele almanıza olanak sağlar. Aşağıdaki kısıtlamaları içeren varsayılan davranışı geçersiz kılmak için veri bağlama olaylarını değiştirebilirsiniz:  
  
- Temsilciler içinde herhangi bir doğrulama yapılmaz.  
  
- Bir varlık eklemek ilgili varlıkları otomatik olarak ekler.  
  
- Bir varlığı silmek ilgili varlıkları silmez.  
  
 ' In <xref:System.Data.Services.Client.DataServiceCollection%601>yeni bir örneğini oluşturduğunuzda, bağlantılı nesneler değiştirildiğinde oluşturulan olayları işleyen yöntemlere temsilciler tanımlayan aşağıdaki parametreleri belirtme seçeneğiniz vardır:  
  
- `entityChanged`-bir bağlantılı nesnenin özelliği değiştirildiğinde çağrılan bir yöntem. Bu <xref:System.Func%602> temsilci bir <xref:System.Data.Services.Client.EntityChangedParams> nesne kabul eder ve varsayılan davranışın, üzerinde <xref:System.Data.Services.Client.DataServiceContext>çağrılıp <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> gerçekleşmeyeceğini belirten bir Boole değeri döndürür.  
  
- `entityCollectionChanged`-bağlama koleksiyonuna bir nesne eklendiğinde veya kaldırıldığında çağrılan bir yöntem. Bu <xref:System.Func%602> temsilci bir <xref:System.Data.Services.Client.EntityCollectionChangedParams> nesne kabul eder ve varsayılan davranışın, bir <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Add> eylem için veya bir eylem için mi çağrılacağını <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> , yoksa bir <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> eylem için <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Remove> mi yükleneceğini belirten bir Boole değeri döndürür. <xref:System.Data.Services.Client.DataServiceContext>, yine de gerçekleşmelidir.  
  
> [!NOTE]
> [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Bu Temsilcilerde uyguladığınız özel davranışlardan herhangi bir doğrulama gerçekleştirir.  
  
 Aşağıdaki <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Remove> örnekte eylem, silinen `Orders_Details` <xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A> <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> birvarlığaaitolanvarlıklarıkaldırmakiçinvemetodunu`Orders` çağırmak üzere özelleştirilir. Bu özel eylem, üst varlık silindiği zaman bağımlı varlıklar otomatik olarak silinmediği için gerçekleştirilir.  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#customersordersdeleterelated)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#customersordersdeleterelated)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#customersordersdeleterelated)]  
  
 Daha fazla bilgi için [nasıl yapılır: Veri bağlama davranışlarını](../../../../docs/framework/data/wcf/how-to-customize-data-binding-behaviors-wcf-data-services.md)özelleştirin.  
  
 Yöntemi kullanılarak bir <xref:System.Data.Services.Client.DataServiceCollection%601> nesne öğesinden kaldırıldığında, <xref:System.Data.Services.Client.DataServiceContext>nesnenin içinde de Deleted olarak işaretlendiğinden, varsayılan davranış. <xref:System.Collections.ObjectModel.Collection%601.Remove%2A> Bu davranışı değiştirmek için, `entityCollectionChanged` <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> olay gerçekleştiğinde çağrılan parametresindeki bir yönteme bir temsilci belirtebilirsiniz.  
  
## <a name="data-binding-with-custom-client-data-classes"></a>Özel Istemci veri sınıflarıyla veri bağlama  
 Nesneleri bir <xref:System.Data.Services.Client.DataServiceCollection%601>öğesine yükleyebilmek için nesnelerin kendisi <xref:System.ComponentModel.INotifyPropertyChanged> arabirimini uygulaması gerekir. Bu arabirimi uygulayan **hizmet başvurusu Ekle** iletişim kutusunu veya [DataSvcUtil. exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) aracını kullandığınızda oluşturulan veri hizmeti istemci sınıfları. Kendi istemci veri sınıflarınızı sağlarsanız, veri bağlama için başka bir koleksiyon türü kullanmanız gerekir. Nesneler değiştiğinde, <xref:System.Data.Services.Client.DataServiceContext> sınıfının aşağıdaki yöntemlerini çağırmak için veri bağlantılı denetimlerindeki olayları işlemeniz gerekir:  
  
- <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A>-koleksiyona yeni bir nesne eklendiğinde.  
  
- <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A>-bir nesne koleksiyondan kaldırıldığında.  
  
- <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A>-Koleksiyondaki bir nesne üzerinde bir özellik değiştirildiğinde.  
  
- <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>-bir nesne ilgili nesne koleksiyonuna eklendiğinde.  
  
- <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>-bir nesne ilgili nesneler koleksiyonuna eklendiğinde.  
  
 Daha fazla bilgi için bkz. [veri hizmetini güncelleştirme](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Istemci veri hizmeti sınıflarını el ile oluştur](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)
- [Nasıl yapılır: Veri hizmeti başvurusu ekleme](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
