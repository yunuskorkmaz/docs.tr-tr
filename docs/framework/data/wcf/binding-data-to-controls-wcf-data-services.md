---
title: (WCF Veri Hizmetleri) denetimlere veri bağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- data binding, WCF Data Services
ms.assetid: b32e1d49-c214-4cb1-867e-88fbb3d08c8d
ms.openlocfilehash: fb2a7c8e1cf3fbae4c6417dab492343ead991204
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793457"
---
# <a name="binding-data-to-controls-wcf-data-services"></a>(WCF Veri Hizmetleri) denetimlere veri bağlama
İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], denetimleri gibi bağlayabilirsiniz `ComboBox` ve `ListView` örneğine denetimleri <xref:System.Data.Services.Client.DataServiceCollection%601> sınıfı. Öğesinden devralan bu koleksiyon <xref:System.Collections.ObjectModel.ObservableCollection%601> sınıfı, verileri içeren bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akış. Bu sınıf bildirimleri öğeleri eklendiğinde veya kaldırıldığında sağlayan bir dinamik veri koleksiyonunu temsil eder. Bir örneğini kullandığınızda, <xref:System.Data.Services.Client.DataServiceCollection%601> veri bağlama için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplıkları tarafından izlenen nesneleri emin olmak için bu olayları işleme <xref:System.Data.Services.Client.DataServiceContext> ilişkili kullanıcı Arabirimi öğesi verilerle eşitlenmiş olarak kalır.  
  
 <xref:System.Data.Services.Client.DataServiceCollection%601> (Dolaylı olarak) uygulayan sınıf <xref:System.Collections.Specialized.INotifyCollectionChanged> bağlamı nesneleri eklendiğinde veya koleksiyondan kaldırılır uyarmak için arabirim. Veri hizmeti türü nesneleri ile kullanılan bir <xref:System.Data.Services.Client.DataServiceCollection%601> de uygulamalıdır <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi uyarı <xref:System.Data.Services.Client.DataServiceCollection%601> bağlama koleksiyondaki nesnelerin özelliklerini, değişti.  
  
> [!NOTE]
>  Kullanırken **hizmet Başvurusu Ekle** iletişim veya [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) ile aracı `/dataservicecollection` istemci veri hizmeti sınıfları oluşturma seçeneği, oluşturulan veri sınıfları uygulayın<xref:System.ComponentModel.INotifyPropertyChanged> arabirimi. Daha fazla bilgi için [nasıl yapılır: El ile istemci veri hizmeti sınıfları oluşturma](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
## <a name="creating-the-binding-collection"></a>Bağlama koleksiyonu oluşturuluyor  
 Yeni bir örneğini oluşturma <xref:System.Data.Services.Client.DataServiceCollection%601> sınıfı ile sağlanan sınıfı Oluşturucu yöntemi çağırarak <xref:System.Data.Services.Client.DataServiceContext> örneği ve isteğe bağlı olarak bir <xref:System.Data.Services.Client.DataServiceQuery%601> veya yürütüldüğünde, döndürür, LINQ sorgusu bir <xref:System.Collections.Generic.IEnumerable%601> örneği. Bu <xref:System.Collections.Generic.IEnumerable%601> gelen gerçekleştirilmiş bağlama koleksiyonu nesnelerin kaynak sağlayan bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış. Daha fazla bilgi için [nesne gerçekleştirme](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md). Varsayılan olarak, bağlı nesnelere yapılan değişiklikleri ve koleksiyonuna eklediğiniz öğeleri otomatik olarak tarafından izlenen <xref:System.Data.Services.Client.DataServiceContext>. Bu değişiklikler el ile izlemek ihtiyacınız varsa, alan oluşturucu yöntemlerden birini çağırma bir `trackingMode` parametre ve bir değer belirleyebilirsiniz <xref:System.Data.Services.Client.TrackingMode.None>.  
  
 Aşağıdaki örnek, bir örneğini oluşturma işlemi gösterilmektedir <xref:System.Data.Services.Client.DataServiceCollection%601> sağlanan üzerinde temel <xref:System.Data.Services.Client.DataServiceContext> ve <xref:System.Data.Services.Client.DataServiceQuery%601> olan tüm müşterilerle ilgili Siparişler döndürür:  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrders2Binding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders2.cs#customersorders2binding)]
 [!code-vb[Astoria Northwind Client#CustomersOrders2Binding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders2.vb#customersorders2binding)]  
  
## <a name="binding-data-to-windows-presentation-foundation-elements"></a>Windows Presentation Foundation öğelerine veri bağlama  
 Çünkü <xref:System.Data.Services.Client.DataServiceCollection%601> sınıfının devraldığı <xref:System.Collections.ObjectModel.ObservableCollection%601> sınıfı kullanırken yaptığınız gibi bir öğe ya da denetimi, bir Windows Presentation Foundation (WPF) uygulamasındaki nesneleri bağlayabilirsiniz <xref:System.Collections.ObjectModel.ObservableCollection%601> bağlama için sınıf. Daha fazla bilgi için [veri bağlama (Windows Presentation Foundation)](../../../../docs/framework/wpf/data/data-binding-wpf.md). Veri hizmetinin veri bağlama WPF denetimleri yollarından biri açıklanmıştır ayarlanacak `DataContext` örneğine öğesinin özelliği <xref:System.Data.Services.Client.DataServiceCollection%601> sorgu sonucunu içeren sınıf. Bu durumda, kullandığınız <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> nesne kaynak denetimi için ayarlanacak özellik. Kullanım <xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A> özelliği görüntülenecek ilişkili nesnenin hangi özelliğinin belirtin. Bir gezinti özelliği tarafından döndürülen bir ilişkili nesne için bir öğe bağlıyorsanız yol için tanımlı bağlama dahil <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği. Bu set kök nesnesinin göreli yoludur <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği üst denetim. Aşağıdaki örnek kümeleri <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği bir <xref:System.Windows.Controls.StackPanel> üst denetime bağlanacak öğeyi bir <xref:System.Data.Services.Client.DataServiceCollection%601> müşteri nesnesi:  
  
 [!code-csharp[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#masterdetailbinding)]
 [!code-csharp[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#masterdetailbinding)]  
  
 Aşağıdaki örnek bir alt XAML bağlama tanımı gösterilmektedir <xref:System.Windows.Controls.DataGrid> ve <xref:System.Windows.Controls.ComboBox> denetimler:  
  
 [!code-xaml[Astoria Northwind Client#MasterDetailXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#masterdetailxaml)]  
  
 Daha fazla bilgi için [nasıl yapılır: Windows Presentation Foundation öğelerine veri bağlama](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md).  
  
 Ne zaman bir bire-çok bir varlığın katıldığı veya çoktan çoğa ilişki, ilişkinin gezinme özelliğini ilgili nesnelerin bir koleksiyonunu döndürür. Kullanırken **hizmet Başvurusu Ekle** gezinme özelliği iletişim kutusu veya istemci veri hizmeti sınıfları oluşturmak için DataSvcUtil.exe aracı, bir örneğini döndürür <xref:System.Data.Services.Client.DataServiceCollection%601>. Bu, ilgili nesneleri bir denetime bağlama ve ortak WPF bağlama için ilgili varlıkları ana öğe-ayrıntı bağlama deseni gibi senaryoları desteği sağlar. Önceki XAML örnekte XAML kodu ana bağlar <xref:System.Data.Services.Client.DataServiceCollection%601> kök veri öğesi için. Sipariş <xref:System.Windows.Controls.DataGrid> siparişlere sonra bağlı <xref:System.Data.Services.Client.DataServiceCollection%601> sırayla kök veri öğesi için bağlı seçili müşteriler nesne öğesinden döndürülen <xref:System.Windows.Window>.  
  
## <a name="binding-data-to-windows-forms-controls"></a>Veri bağlama için bir Windows Forms denetimleri  
 Nesneleri bir Windows formu denetimine bağlamak için ayarlanmış `DataSource` örneğini denetimin özellik <xref:System.Data.Services.Client.DataServiceCollection%601> sorgu sonucunu içeren sınıf.  
  
> [!NOTE]
>  Veri bağlama uygulayarak değişiklik olayları dinler denetimleri için yalnızca desteklenen <xref:System.Collections.Specialized.INotifyCollectionChanged> ve <xref:System.ComponentModel.INotifyPropertyChanged> arabirimleri. Ne zaman bir denetim desteklemiyor bu tür bir değişiklik bildirimi, temel alınan yapılan değişiklikleri <xref:System.Data.Services.Client.DataServiceCollection%601> ilişkili denetiminde yansıtılmaz.  
  
 Aşağıdaki örnek bağlayan bir <xref:System.Data.Services.Client.DataServiceCollection%601> için bir <xref:System.Windows.Forms.ComboBox> denetimi:  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdatabindingspecific)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdatabindingspecific)]  
  
 Kullanırken **hizmet Başvurusu Ekle** istemci veri hizmeti sınıfları, veri kaynağı da oluşturulduğu diğer bir deyişle bir proje oluşturmak için iletişim tabanlı oluşturulan <xref:System.Data.Services.Client.DataServiceContext>. Bu veri kaynağı ile UI öğelerine veya öğeleri sürükleyerek veri hizmetinden alınan verileri görüntüleyen denetimler oluşturabilirsiniz **veri kaynakları** tasarımcıya penceresi. Bu öğeler, veri kaynağına bağlı uygulama kullanıcı Arabirimi öğelerinde haline gelir. Daha fazla bilgi için [nasıl yapılır: Bir proje veri kaynağı kullanarak veri bağlama](../../../../docs/framework/data/wcf/how-to-bind-data-using-a-project-data-source-wcf-data-services.md).  
  
## <a name="binding-paged-data"></a>Veri bağlama disk belleği  
 Bir veri hizmeti, bir tek yanıt iletisinde döndürülür sorgulanan veri miktarını sınırlamak için yapılandırılabilir. Daha fazla bilgi için [veri hizmeti yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md). Veri hizmeti yanıt verileri disk belleği, her yanıt sonraki sonuç sayfasını döndürmek için kullanılan bir bağlantı içerir. Daha fazla bilgi için [ertelenmiş içerik yükleme](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md). Bu durumda, açıkça sayfaları çağırarak yüklemelisiniz <xref:System.Data.Services.Client.DataServiceCollection%601.Load%2A> metodunda <xref:System.Data.Services.Client.DataServiceCollection%601> alınan URI geçirerek <xref:System.Data.Services.Client.DataServiceQueryContinuation.NextLinkUri%2A> özelliği aşağıdaki örnekteki gibi:  
  
 [!code-csharp[Astoria Northwind Client#BindPagedDataSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddataspecific)]
 [!code-vb[Astoria Northwind Client#BindPagedDataSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddataspecific)]  
  
 İlgili nesneler benzer bir şekilde yüklenir. Daha fazla bilgi için [nasıl yapılır: Windows Presentation Foundation öğelerine veri bağlama](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md).  
  
## <a name="customizing-data-binding-behaviors"></a>Veri bağlama davranışlarını özelleştirme  
 <xref:System.Data.Services.Client.DataServiceCollection%601> Sınıfı gibi bir nesne eklenmiş veya kaldırılmasını ve bir koleksiyondaki nesnenin özelliklerini değişiklik yapıldığında, koleksiyona değişiklik yapıldığında tetiklenen olayları müdahale etmenizi sağlar. Aşağıdaki kısıtlamaları içeren varsayılan davranışı geçersiz kılmak için veri bağlama olaylarını değiştirebilirsiniz:  
  
- Temsilcileri içinde doğrulama yapılmaz.  
  
- Varlık otomatik olarak ekleme, ilgili varlıkları ekler.  
  
- Bir varlığı silme ilgili varlıkları silmez.  
  
 Yeni bir örneğini oluştururken <xref:System.Data.Services.Client.DataServiceCollection%601>, ilişkili nesneleri değiştiğinde harekete geçirilen olayları işleyen yöntemler için temsilciler tanımlamak aşağıdaki parametreleri belirtmeniz seçeneğiniz vardır:  
  
- `entityChanged` -bir bağımlı nesne özelliği değiştiğinde çağrılan yöntem. Bu <xref:System.Func%602> temsilci kabul bir <xref:System.Data.Services.Client.EntityChangedParams> nesne ve gösteren bir Boole değeri döndürür olmadığını çağırmak için varsayılan davranışı, <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> üzerinde <xref:System.Data.Services.Client.DataServiceContext>, hala gerçekleşmelidir.  
  
- `entityCollectionChanged` -bir nesne eklendiğinde veya bağlama koleksiyondan kaldırılır çağrılan yöntem. Bu <xref:System.Func%602> temsilci kabul bir <xref:System.Data.Services.Client.EntityCollectionChangedParams> nesne ve gösteren bir Boole değeri döndürür olmadığını çağırmak için varsayılan davranışı, <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> için bir <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Add> eylem veya <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> için bir <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Remove> Eylem<xref:System.Data.Services.Client.DataServiceContext>, hala gerçekleşmelidir.  
  
> [!NOTE]
>  [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Bu temsilcileri uygulayan özel davranış doğrulama gerçekleştirir.  
  
 Aşağıdaki örnekte, <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Remove> eylem çağırmak için özelleştirilmiş <xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A> ve <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> kaldırmak için yöntemi `Orders_Details` silinmiş bir ait varlıkları `Orders` varlık. Üst varlık silindiğinde bağımlı varlıkları otomatik olarak silinmez çünkü bu özel eylem gerçekleştirilir.  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#customersordersdeleterelated)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#customersordersdeleterelated)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#customersordersdeleterelated)]  
  
 Daha fazla bilgi için [nasıl yapılır: Veri bağlama davranışlarını özelleştirme](../../../../docs/framework/data/wcf/how-to-customize-data-binding-behaviors-wcf-data-services.md).  
  
 Bir nesne kaldırılır kullanırken varsayılan davranış bir <xref:System.Data.Services.Client.DataServiceCollection%601> kullanarak <xref:System.Collections.ObjectModel.Collection%601.Remove%2A> yöntemi olan nesne de silinmiş olarak işaretlenmiş <xref:System.Data.Services.Client.DataServiceContext>. Bu davranışı değiştirmek için bir yöntem temsilciye belirtebilirsiniz `entityCollectionChanged` aldığında çağrılan parametresi <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> olayı oluşur.  
  
## <a name="data-binding-with-custom-client-data-classes"></a>Veri bağlama ile özel istemci veri sınıfları  
 Nesneleri yüklemek için bir <xref:System.Data.Services.Client.DataServiceCollection%601>, nesnelerinin kendileri uygulamalıdır <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi. Veri Hizmeti kullandığınızda, oluşturulan istemci sınıfları **hizmet Başvurusu Ekle** iletişim kutusu veya [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) aracı bu arabirimi uygulayın. Veri sınıfları kendi istemci sağlarsanız, veri bağlama için başka türde bir koleksiyonu kullanmanız gerekir. Nesneleri değiştirdiğinizde, aşağıdaki yöntemleri çağırmak için veri bağlama denetimleri olayları işlemesi <xref:System.Data.Services.Client.DataServiceContext> sınıfı:  
  
- <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> -Yeni bir nesne koleksiyona eklendiğinde.  
  
- <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> -bir nesne koleksiyondan kaldırıldığında.  
  
- <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> -ne zaman bir özelliği değiştirildiğinde koleksiyondaki bir nesne üzerinde.  
  
- <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> -ilgili nesne koleksiyonu için bir nesne eklendiğinde.  
  
- <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> -ilgili nesnelerden oluşan bir koleksiyon için bir nesne eklendiğinde.  
  
 Daha fazla bilgi için [veri hizmetini güncelleştirme](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: El ile istemci veri hizmeti sınıfları oluşturma](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)
- [Nasıl yapılır: Bir veri hizmeti başvurusu ekleme](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
