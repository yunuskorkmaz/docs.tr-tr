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
ms.openlocfilehash: a734240fd8a7ec5217674342dc20b3cf8cbdf4ab
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739632"
---
# <a name="binding-data-to-controls-wcf-data-services"></a>Denetimlere veri bağlama (WCF Veri Hizmetleri)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], `ComboBox` ve `ListView` denetimleri gibi denetimleri <xref:System.Data.Services.Client.DataServiceCollection%601> sınıfının bir örneğine bağlayabilirsiniz. <xref:System.Collections.ObjectModel.ObservableCollection%601> sınıfından devralan bu koleksiyon, [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akışından gelen verileri içerir. Bu sınıf, öğeler eklendiğinde veya kaldırıldığında bildirim sağlayan dinamik bir veri koleksiyonunu temsil eder. Veri bağlama için bir <xref:System.Data.Services.Client.DataServiceCollection%601> örneği kullandığınızda, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplıkları, <xref:System.Data.Services.Client.DataServiceContext> tarafından izlenen nesnelerin, ilişkili kullanıcı arabirimi öğesindeki verilerle eşitlenmiş kalmasını sağlamak için bu olayları işler.  
  
 <xref:System.Data.Services.Client.DataServiceCollection%601> sınıfı (dolaylı), nesneleri koleksiyona eklendiğinde veya koleksiyondan kaldırıldığında bağlamı uyarmak için <xref:System.Collections.Specialized.INotifyCollectionChanged> arabirimini uygular. <xref:System.Data.Services.Client.DataServiceCollection%601> ile kullanılan veri hizmeti türü nesneleri, bağlama koleksiyonundaki nesnelerin özellikleri değiştiğinde <xref:System.Data.Services.Client.DataServiceCollection%601> uyarmak için <xref:System.ComponentModel.INotifyPropertyChanged> arabirimini de uygulamalıdır.  
  
> [!NOTE]
> İstemci veri hizmeti sınıflarını oluşturmak için `/dataservicecollection` seçeneğiyle **hizmet başvurusu Ekle** iletişim kutusu veya [DataSvcUtil. exe](wcf-data-service-client-utility-datasvcutil-exe.md) aracını kullandığınızda, oluşturulan veri sınıfları <xref:System.ComponentModel.INotifyPropertyChanged> arabirimini uygular. Daha fazla bilgi için bkz. [nasıl yapılır: El Ile Istemci veri hizmeti sınıfları oluşturma](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
## <a name="creating-the-binding-collection"></a>Bağlama koleksiyonu oluşturma  
 Sağlanan bir <xref:System.Data.Services.Client.DataServiceContext> örneğiyle sınıf Oluşturucu yöntemlerinden birini çağırarak <xref:System.Data.Services.Client.DataServiceCollection%601> sınıfının yeni bir örneğini oluşturun ve isteğe bağlı <xref:System.Data.Services.Client.DataServiceQuery%601> olarak, yürütüldüğü zaman bir <xref:System.Collections.Generic.IEnumerable%601> örneğini döndürür. Bu <xref:System.Collections.Generic.IEnumerable%601>, bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışından gerçekleştirilmiş olan bağlama koleksiyonu için nesne kaynağı sağlar. Daha fazla bilgi için bkz. [nesne materialization](object-materialization-wcf-data-services.md). Varsayılan olarak, bağlantılı nesnelerde yapılan değişiklikler ve koleksiyona eklenen öğeler <xref:System.Data.Services.Client.DataServiceContext>tarafından otomatik olarak izlenir. Bu değişiklikleri el ile izlemeniz gerekiyorsa, bir `trackingMode` parametresi alan ve <xref:System.Data.Services.Client.TrackingMode.None>değerini belirten Oluşturucu yöntemlerinden birini çağırın.  
  
 Aşağıdaki örnek, sağlanan <xref:System.Data.Services.Client.DataServiceContext> ve ilgili siparişlere sahip tüm müşterileri döndüren bir <xref:System.Data.Services.Client.DataServiceQuery%601> <xref:System.Data.Services.Client.DataServiceCollection%601> örneğinin nasıl oluşturulacağını gösterir:  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrders2Binding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders2.cs#customersorders2binding)]
 [!code-vb[Astoria Northwind Client#CustomersOrders2Binding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders2.vb#customersorders2binding)]  
  
## <a name="binding-data-to-windows-presentation-foundation-elements"></a>Windows Presentation Foundation öğelerine veri bağlama  
 <xref:System.Data.Services.Client.DataServiceCollection%601> sınıfı <xref:System.Collections.ObjectModel.ObservableCollection%601> sınıfından devraldığından, Binding için <xref:System.Collections.ObjectModel.ObservableCollection%601> sınıfını kullanırken olduğu gibi, nesneleri bir Windows Presentation Foundation (WPF) uygulamasında bir öğeye veya denetime bağlayabilirsiniz. Daha fazla bilgi için bkz. [veri bağlama (Windows Presentation Foundation)](../../../desktop-wpf/data/data-binding-overview.md). Veri hizmeti verilerini WPF denetimlerine bağlamak için bir yol, öğesinin `DataContext` özelliğini sorgu sonucunu içeren <xref:System.Data.Services.Client.DataServiceCollection%601> sınıfının örneğine ayarlamaya yönelik bir yoldur. Bu durumda, denetimin nesne kaynağını ayarlamak için <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliğini kullanın. Hangi bağlantılı nesnenin görüntüleneceği özelliğini belirtmek için <xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A> özelliğini kullanın. Bir öğeyi bir gezinti özelliği tarafından döndürülen ilgili bir nesneye bağlıyorsanız, yolu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği için tanımlanan bağlamaya ekleyin. Bu yol, üst denetimin <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği tarafından ayarlanan kök nesneye göredir. Aşağıdaki örnek, bir <xref:System.Windows.Controls.StackPanel> öğesinin <xref:System.Windows.FrameworkElement.DataContext%2A> özelliğini, ana denetimi müşteri nesnelerinin bir <xref:System.Data.Services.Client.DataServiceCollection%601> bağlamak için ayarlar:  
  
 [!code-csharp[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#masterdetailbinding)]
 [!code-csharp[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#masterdetailbinding)]  
  
 Aşağıdaki örnek, alt <xref:System.Windows.Controls.DataGrid> ve <xref:System.Windows.Controls.ComboBox> denetimlerinin XAML bağlama tanımını gösterir:  
  
 [!code-xaml[Astoria Northwind Client#MasterDetailXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#masterdetailxaml)]  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: verileri Windows Presentation Foundation bağlama](bind-data-to-wpf-elements-wcf-data-services.md).  
  
 Bir varlık bire çok veya çoktan çoğa ilişkiye katılıyorsa, ilişkinin gezinti özelliği ilişkili nesnelerin bir koleksiyonunu döndürür. İstemci veri hizmeti sınıflarını oluşturmak için **hizmet başvurusu Ekle** iletişim kutusunu veya DataSvcUtil. exe aracını kullandığınızda, gezinti özelliği bir <xref:System.Data.Services.Client.DataServiceCollection%601>örneğini döndürür. Bu, ilgili nesneleri bir denetime bağlamanıza ve ilgili varlıklar için ana ayrıntı bağlama deseninin gibi ortak WPF bağlama senaryolarına destek sağlamanıza olanak sağlar. Önceki XAML örneğinde, XAML kodu ana <xref:System.Data.Services.Client.DataServiceCollection%601> kök veri öğesine bağlar. Order <xref:System.Windows.Controls.DataGrid> daha sonra seçili müşteriler nesnesinden döndürülen <xref:System.Data.Services.Client.DataServiceCollection%601> siparişlere bağlanır, bu da <xref:System.Windows.Window>kök veri öğesine bağımlıdır.  
  
## <a name="binding-data-to-windows-forms-controls"></a>Windows Forms denetimlerine veri bağlama  
 Nesneleri bir Windows form denetimine bağlamak için denetimin `DataSource` özelliğini sorgu sonucunu içeren <xref:System.Data.Services.Client.DataServiceCollection%601> sınıfının örneğine ayarlayın.  
  
> [!NOTE]
> Veri bağlama yalnızca <xref:System.Collections.Specialized.INotifyCollectionChanged> ve <xref:System.ComponentModel.INotifyPropertyChanged> arabirimlerini uygulayarak değişiklik olaylarını dinleyen denetimler için desteklenir. Bir denetim bu tür değişiklik bildirimini desteklemiyorsa, temeldeki <xref:System.Data.Services.Client.DataServiceCollection%601> yapılan değişiklikler, ilişkili denetimde yansıtılmaz.  
  
 Aşağıdaki örnek bir <xref:System.Data.Services.Client.DataServiceCollection%601> <xref:System.Windows.Forms.ComboBox> denetimine bağlar:  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdatabindingspecific)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdatabindingspecific)]  
  
 İstemci veri hizmeti sınıflarını oluşturmak için **hizmet başvurusu Ekle** iletişim kutusunu kullandığınızda, oluşturulan <xref:System.Data.Services.Client.DataServiceContext>dayalı bir proje veri kaynağı da oluşturulur. Bu veri kaynağıyla, verileri veri **kaynakları** penceresinden tasarımcıya sürükleyerek yalnızca veri hizmetinden veri görüntüleyen kullanıcı arabirimi öğeleri veya denetimleri oluşturabilirsiniz. Bu öğeler, uygulama kullanıcı arabiriminde veri kaynağına bağlanan öğeler haline gelir. Daha fazla bilgi için bkz. [nasıl yapılır: bir proje veri kaynağı kullanarak veri bağlama](how-to-bind-data-using-a-project-data-source-wcf-data-services.md).  
  
## <a name="binding-paged-data"></a>Disk belleğine alınan verileri bağlama  
 Bir veri hizmeti, tek bir yanıt iletisinde döndürülen sorgulanan veri miktarını sınırlayacak şekilde yapılandırılabilir. Daha fazla bilgi için bkz. [veri hizmetini yapılandırma](configuring-the-data-service-wcf-data-services.md). Veri hizmeti yanıt verisi olduğunda, her yanıt bir sonraki sonuç sayfasını döndürmek için kullanılan bir bağlantı içerir. Daha fazla bilgi için bkz. [ertelenmiş Içerik yükleme](loading-deferred-content-wcf-data-services.md). Bu durumda, aşağıdaki örnekte olduğu gibi <xref:System.Data.Services.Client.DataServiceQueryContinuation.NextLinkUri%2A> özelliğinden elde edilen URI 'yi geçirerek <xref:System.Data.Services.Client.DataServiceCollection%601> <xref:System.Data.Services.Client.DataServiceCollection%601.Load%2A> yöntemini çağırarak sayfaları açıkça yüklemeniz gerekir:  
  
 [!code-csharp[Astoria Northwind Client#BindPagedDataSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddataspecific)]
 [!code-vb[Astoria Northwind Client#BindPagedDataSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddataspecific)]  
  
 İlgili nesneler benzer bir şekilde yüklenir. Daha fazla bilgi için bkz. [nasıl yapılır: verileri Windows Presentation Foundation bağlama](bind-data-to-wpf-elements-wcf-data-services.md).  
  
## <a name="customizing-data-binding-behaviors"></a>Veri bağlama davranışlarını özelleştirme  
 <xref:System.Data.Services.Client.DataServiceCollection%601> sınıfı, koleksiyonda yapılan değişiklikler yapıldığında, eklenen veya kaldırılan bir nesne ve bir koleksiyondaki nesnenin özelliklerinde değişiklik yapıldığında oluşan olayları ele almanıza olanak sağlar. Aşağıdaki kısıtlamaları içeren varsayılan davranışı geçersiz kılmak için veri bağlama olaylarını değiştirebilirsiniz:  
  
- Temsilciler içinde herhangi bir doğrulama yapılmaz.  
  
- Bir varlık eklemek ilgili varlıkları otomatik olarak ekler.  
  
- Bir varlığı silmek ilgili varlıkları silmez.  
  
 <xref:System.Data.Services.Client.DataServiceCollection%601>yeni bir örneğini oluşturduğunuzda, bağlantılı nesneler değiştirildiğinde oluşturulan olayları işleyen yöntemlere temsilciler tanımlayan aşağıdaki parametreleri belirtme seçeneğiniz vardır:  
  
- `entityChanged`-bağlantılı nesnenin özelliği değiştirildiğinde çağrılan bir yöntem. Bu <xref:System.Func%602> temsilci bir <xref:System.Data.Services.Client.EntityChangedParams> nesnesini kabul eder ve <xref:System.Data.Services.Client.DataServiceContext>üzerinde <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> çağırmak için varsayılan davranışın yine de gerçekleşmeyeceğini belirten bir Boole değeri döndürür.  
  
- `entityCollectionChanged`-bağlama koleksiyonuna bir nesne eklendiğinde veya kaldırıldığında çağrılan bir yöntem. Bu <xref:System.Func%602> temsilci bir <xref:System.Data.Services.Client.EntityCollectionChangedParams> nesnesini kabul eder ve bir <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Add> eylemi için <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> veya <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> bir eylem için <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Remove> çağrısı yapılıp yapılmayacağını belirten bir Boole değeri döndürür , yine de gerçekleşmelidir.  
  
> [!NOTE]
> [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], bu Temsilcilerde uyguladığınız özel davranışlardan herhangi bir doğrulama gerçekleştirmediğini gerçekleştirir.  
  
 Aşağıdaki örnekte <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Remove> eylemi, silinen bir `Orders` varlığına ait `Orders_Details` varlıklarını kaldırmak için <xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A> ve <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> metodunu çağırmak üzere özelleştirilir. Bu özel eylem, üst varlık silindiği zaman bağımlı varlıklar otomatik olarak silinmediği için gerçekleştirilir.  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#customersordersdeleterelated)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#customersordersdeleterelated)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#customersordersdeleterelated)]  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: veri bağlama davranışlarını özelleştirme](how-to-customize-data-binding-behaviors-wcf-data-services.md).  
  
 Bir nesne <xref:System.Data.Services.Client.DataServiceCollection%601> <xref:System.Collections.ObjectModel.Collection%601.Remove%2A> yöntemi kullanılarak kaldırıldığında, nesnenin <xref:System.Data.Services.Client.DataServiceContext>silinmiş olarak da işaretlendiğine yönelik varsayılan davranış. Bu davranışı değiştirmek için, <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> olayı gerçekleştiğinde çağrılan `entityCollectionChanged` parametresinde bir yönteme temsilci belirtebilirsiniz.  
  
## <a name="data-binding-with-custom-client-data-classes"></a>Özel Istemci veri sınıflarıyla veri bağlama  
 Nesneleri bir <xref:System.Data.Services.Client.DataServiceCollection%601>yüklemek için nesnelerin kendisi <xref:System.ComponentModel.INotifyPropertyChanged> arabirimini uygulaması gerekir. Bu arabirimi uygulayan **hizmet başvurusu Ekle** iletişim kutusunu veya [DataSvcUtil. exe](wcf-data-service-client-utility-datasvcutil-exe.md) aracını kullandığınızda oluşturulan veri hizmeti istemci sınıfları. Kendi istemci veri sınıflarınızı sağlarsanız, veri bağlama için başka bir koleksiyon türü kullanmanız gerekir. Nesneler değiştiğinde, <xref:System.Data.Services.Client.DataServiceContext> sınıfının aşağıdaki yöntemlerini çağırmak için veri bağlantılı denetimlerindeki olayları işlemeniz gerekir:  
  
- <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A>-koleksiyona yeni bir nesne eklendiğinde.  
  
- <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A>-bir nesne koleksiyondan kaldırıldığında.  
  
- <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A>-koleksiyondaki bir nesne üzerinde bir özellik değiştirildiğinde.  
  
- <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>-bir nesne ilgili nesne koleksiyonuna eklendiğinde.  
  
- <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>-bir nesne ilgili nesneler koleksiyonuna eklendiğinde.  
  
 Daha fazla bilgi için bkz. [veri hizmetini güncelleştirme](updating-the-data-service-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: El İle İstemci Veri Hizmeti Sınıfları Oluşturma](how-to-manually-generate-client-data-service-classes-wcf-data-services.md)
- [Nasıl yapılır: Veri Hizmeti Başvurusu Ekleme](how-to-add-a-data-service-reference-wcf-data-services.md)
