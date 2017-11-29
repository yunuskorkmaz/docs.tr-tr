---
title: "(WCF Veri Hizmetleri) denetimlere veri bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- data binding, WCF Data Services
ms.assetid: b32e1d49-c214-4cb1-867e-88fbb3d08c8d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9e0d7ed9fdae7731fd4b023dcad656ebcdcf280f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="binding-data-to-controls-wcf-data-services"></a>(WCF Veri Hizmetleri) denetimlere veri bağlama
İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], denetimleri gibi bağlayabilirsiniz `ComboBox` ve `ListView` örneği denetimlere <xref:System.Data.Services.Client.DataServiceCollection%601> sınıfı. Öğesinden devralınan bu koleksiyonu <xref:System.Collections.ObjectModel.ObservableCollection%601> sınıfı, verileri içeren bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akış. Bu sınıf bildirimleri öğeleri eklendiğinde veya kaldırılan sağlayan dinamik veri koleksiyonunu temsil eder. Bir örneğini kullandığınızda <xref:System.Data.Services.Client.DataServiceCollection%601> veri bağlama için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplıkları tarafından izlenen nesneleri emin olmak için bu olayları işleme <xref:System.Data.Services.Client.DataServiceContext> ilişkili kullanıcı Arabirimi öğesi verilerle eşitlenmiş olarak kalır.  
  
 <xref:System.Data.Services.Client.DataServiceCollection%601> (Dolaylı olarak) uygulayan sınıf <xref:System.Collections.Specialized.INotifyCollectionChanged> arabirimi nesneleri için eklenemez veya koleksiyondan kaldırıldı olduğunda bağlamını uyarır. Veri hizmeti türü nesneleri ile kullanılan bir <xref:System.Data.Services.Client.DataServiceCollection%601> de uygulamalıdır <xref:System.ComponentModel.INotifyPropertyChanged> uyarı arabirimine <xref:System.Data.Services.Client.DataServiceCollection%601> bağlama koleksiyonundaki nesnelerin özelliklerini zaman değişti.  
  
> [!NOTE]
>  Kullandığınızda **hizmet Başvurusu Ekle** iletişim veya[DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) ile aracı `/dataservicecollection` istemci veri hizmeti sınıfları oluşturmak için seçeneği, oluşturulanverisınıflarınıuygulama<xref:System.ComponentModel.INotifyPropertyChanged> arabirimi. Daha fazla bilgi için bkz: [nasıl yapılır: el ile oluşturmak istemci veri hizmeti sınıfları](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
## <a name="creating-the-binding-collection"></a>Bağlama koleksiyonu oluşturma  
 Yeni bir örneğini oluşturmak <xref:System.Data.Services.Client.DataServiceCollection%601> sınıfı oluşturucusu sağlanan yöntemleriyle birini çağırarak sınıfı <xref:System.Data.Services.Client.DataServiceContext> örneği ve isteğe bağlı olarak bir <xref:System.Data.Services.Client.DataServiceQuery%601> veya döndüren, yürütüldüğünde, LINQ sorgusu bir <xref:System.Collections.Generic.IEnumerable%601> örneği. Bu <xref:System.Collections.Generic.IEnumerable%601> gelen gerçekleştirilip bağlama koleksiyonu nesnelerin kaynak sağlayan bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış. Daha fazla bilgi için bkz: [nesne Materialization](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md). Varsayılan olarak, bağlı nesnelere yapılan değişiklikleri ve koleksiyona eklenen öğelerin otomatik olarak tarafından izlenen <xref:System.Data.Services.Client.DataServiceContext>. Bu değişiklikleri el ile izlemeniz gerekiyorsa, alan oluşturucu yöntemlerden birini çağrısı bir `trackingMode` parametresi ve değeri belirtin <xref:System.Data.Services.Client.TrackingMode.None>.  
  
 Aşağıdaki örnek bir örneğini oluşturmak nasıl gösterir <xref:System.Data.Services.Client.DataServiceCollection%601> sağlanan üzerinde temel <xref:System.Data.Services.Client.DataServiceContext> ve <xref:System.Data.Services.Client.DataServiceQuery%601> ilgili emirleriyle tüm müşteriler döndürür:  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrders2Binding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders2.cs#customersorders2binding)]
 [!code-vb[Astoria Northwind Client#CustomersOrders2Binding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders2.vb#customersorders2binding)]  
  
## <a name="binding-data-to-windows-presentation-foundation-elements"></a>Windows Presentation Foundation öğelerine veri bağlama  
 Çünkü <xref:System.Data.Services.Client.DataServiceCollection%601> sınıfının devraldığı <xref:System.Collections.ObjectModel.ObservableCollection%601> sınıfı, kullanırken yaptığınız gibi nesneleri bir öğe veya bir Windows Presentation Foundation (WPF) uygulamasında denetim bağlayabilirsiniz <xref:System.Collections.ObjectModel.ObservableCollection%601> bağlama için sınıf. Daha fazla bilgi için bkz: [veri bağlama (Windows Presentation Foundation)](../../../../docs/framework/wpf/data/data-binding-wpf.md). Veri hizmeti verilerini WPF denetimleri bağlama için bir yoldur ayarlamak için `DataContext` örneğine öğesi özelliği <xref:System.Data.Services.Client.DataServiceCollection%601> sorgu sonucu içeren sınıf. Bu durumda, kullandığınız <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> nesne kaynak denetimi için ayarlamak için özellik. Kullanım <xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A> özelliği görüntülenecek ilişkili nesnenin hangi özelliğinin belirtin. Bir gezinti özelliği tarafından döndürülen bir ilişkili nesne için bir öğe bağlıyorsanız için tanımlanan bağlama yolunu dahil <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği. Tarafından belirlenen kök nesnesi bu yol görelidir <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği üst denetim. Aşağıdaki örnek kümeleri <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği bir <xref:System.Windows.Controls.StackPanel> öğesinin üst denetimi bağlamak için bir <xref:System.Data.Services.Client.DataServiceCollection%601> müşteri nesnelerin:  
  
 [!code-csharp[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderscustom.xaml.cs#masterdetailbinding)]
 [!code-csharp[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf.xaml.cs#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom.xaml.vb#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf.xaml.vb#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom2.xaml.vb#masterdetailbinding)]  
  
 Aşağıdaki örnek alt XAML bağlama tanımını gösterir <xref:System.Windows.Controls.DataGrid> ve <xref:System.Windows.Controls.ComboBox> denetimleri:  
  
 [!code-xaml[Astoria Northwind Client#MasterDetailXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf.xaml#masterdetailxaml)]  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: Windows Presentation Foundation öğelerine bağlama verileri](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md).  
  
 Ne zaman bir bir-çok bir varlığın katıldığı veya çok-çok ilişkisi, ilişki için gezinme özelliği ilişkili nesneleri topluluğunu döndürür. Kullandığınızda **hizmet Başvurusu Ekle** iletişim kutusunda veya istemci veri hizmeti sınıfları oluşturmak için DataSvcUtil.exe aracını, gezinti özelliği döndürür örneği <xref:System.Data.Services.Client.DataServiceCollection%601>. Bu, bir denetimi ilişkili nesneleri bağlamak ve ilgili varlıklar için ana-ayrıntı bağlama düzeni gibi senaryoları bağlama ortak WPF destek sağlar. Önceki XAML örnekte XAML kodu asıl bağlar <xref:System.Data.Services.Client.DataServiceCollection%601> kök veri öğesi için. Sipariş <xref:System.Windows.Controls.DataGrid> sonra siparişe bağlı <xref:System.Data.Services.Client.DataServiceCollection%601> sırayla kök veri öğesi için bağlı seçili müşteriler nesnesi döndürülen <xref:System.Windows.Window>.  
  
## <a name="binding-data-to-windows-forms-controls"></a>Veri bağlama Windows Forms denetimleri  
 Bir Windows Forms denetimi nesneleri bağlamak için ayarlanmış `DataSource` örneğine denetiminin özelliğini <xref:System.Data.Services.Client.DataServiceCollection%601> sorgu sonucu içeren sınıf.  
  
> [!NOTE]
>  Veri bağlama uygulayarak değişiklik olaylarını dinler denetimleri için yalnızca desteklenen <xref:System.Collections.Specialized.INotifyCollectionChanged> ve <xref:System.ComponentModel.INotifyPropertyChanged> arabirimleri. Ne zaman bir denetim desteklemiyor bu tür bir değişiklik bildirimi, arka plandaki için yapılan değişiklikleri <xref:System.Data.Services.Client.DataServiceCollection%601> ilişkili denetiminde yansıtılmaz.  
  
 Aşağıdaki örnek bağlar bir <xref:System.Data.Services.Client.DataServiceCollection%601> için bir <xref:System.Windows.Forms.ComboBox> denetimi:  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersdatabindingspecific)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersdatabindingspecific)]  
  
 Kullandığınızda **hizmet Başvurusu Ekle** istemci veri hizmeti sınıfları, veri kaynağı da oluşturuldu. diğer bir deyişle bir proje oluşturmak için iletişim oluşturulan üzerinde temel <xref:System.Data.Services.Client.DataServiceContext>. Bu veri kaynağı ile kullanıcı Arabirimi öğeleri veya konumundan öğeleri sürükleyerek veri hizmetinden veri görüntüleme denetimleri oluşturabilirsiniz **veri kaynakları** tasarımcıya penceresi. Bu öğeler, veri kaynağına bağlı uygulama kullanıcı Arabirimi öğeleri haline gelir. Daha fazla bilgi için bkz: [nasıl yapılır: Proje veri kaynağı kullanarak veri bağlama](../../../../docs/framework/data/wcf/how-to-bind-data-using-a-project-data-source-wcf-data-services.md).  
  
## <a name="binding-paged-data"></a>Veri bağlama disk belleği  
 Veri Hizmeti, bir tek yanıt iletisinde döndürülür sorgulanan veri miktarını sınırlamak için yapılandırılabilir. Daha fazla bilgi için bkz: [veri hizmeti yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md). Veri hizmeti yanıt verilerini disk belleği, her yanıtı sonraki sonuç sayfasını döndürmek için kullanılan bir bağlantı içerir. Daha fazla bilgi için bkz: [ertelenmiş içerik yüklenirken](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md). Bu durumda, açıkça sayfaları çağırarak yüklemelisiniz <xref:System.Data.Services.Client.DataServiceCollection%601.Load%2A> yöntemi <xref:System.Data.Services.Client.DataServiceCollection%601> alınan URI geçirerek <xref:System.Data.Services.Client.DataServiceQueryContinuation.NextLinkUri%2A> aşağıdaki örnekteki gibi özelliği:  
  
 [!code-csharp[Astoria Northwind Client#BindPagedDataSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf3.xaml.cs#bindpageddataspecific)]
 [!code-vb[Astoria Northwind Client#BindPagedDataSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf3.xaml.vb#bindpageddataspecific)]  
  
 İlişkili nesneleri benzer bir şekilde yüklenir. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Presentation Foundation öğelerine bağlama verileri](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md).  
  
## <a name="customizing-data-binding-behaviors"></a>Veri bağlama davranışları özelleştirme  
 <xref:System.Data.Services.Client.DataServiceCollection%601> Sınıfı gibi bir nesne eklenmiş veya kaldırılmasını ve nesnesinin bir koleksiyondaki özellikleri için değişiklik yapıldığında koleksiyona değişiklik yapıldığında tetiklenen olayları müdahale olanak sağlar. Veri bağlama olayları aşağıdaki kısıtlamaları içeren varsayılan davranışı geçersiz kılma değiştirebilirsiniz:  
  
-   Temsilcileri içinde bir doğrulama yapılmaz.  
  
-   Varlık otomatik olarak ekleme ilgili varlıklar ekler.  
  
-   Bir varlık silindiğinde ilgili varlıkları silinmez.  
  
 Yeni bir örneğini oluştururken <xref:System.Data.Services.Client.DataServiceCollection%601>, ilişkili nesneleri değiştirildiğinde başlatılan olayları işlemek yöntemleri temsilciler tanımlamak aşağıdaki parametreleri belirtmeniz seçeneğiniz vardır:  
  
-   `entityChanged`-bir ilişkili nesne özelliği değiştiğinde çağrılan bir yöntem. Bu <xref:System.Func%602> temsilci kabul bir <xref:System.Data.Services.Client.EntityChangedParams> nesne ve gösteren bir Boole değeri döndürür olup olmadığını çağırmak için varsayılan davranış, <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> üzerinde <xref:System.Data.Services.Client.DataServiceContext>, oluşmaya.  
  
-   `entityCollectionChanged`-bir nesne eklendiğinde veya bağlama koleksiyondan kaldırıldı çağrılan bir yöntem. Bu <xref:System.Func%602> temsilci kabul bir <xref:System.Data.Services.Client.EntityCollectionChangedParams> nesne ve gösteren bir Boole değeri döndürür olup olmadığını çağırmak için varsayılan davranış, <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> için bir <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Add> eylem veya <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> için bir <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Remove> eylemini<xref:System.Data.Services.Client.DataServiceContext>, oluşmaya.  
  
> [!NOTE]
>  [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Bu temsilci uygulayan özel davranışları hiçbir doğrulama gerçekleştirir.  
  
 Aşağıdaki örnekte, <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Remove> çağrılacak eylem özelleştirilmiş <xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A> ve <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> kaldırmak için yöntemi `Orders_Details` silinmiş bir ait varlıklar `Orders` varlık. Üst varlık silindiğinde bağımlı varlıkları otomatik olarak silinmez çünkü bu özel eylem gerçekleştirilir.  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderscustom.xaml.cs#customersordersdeleterelated)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom.xaml.vb#customersordersdeleterelated)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom2.xaml.vb#customersordersdeleterelated)]  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: veri bağlama davranışları özelleştirme](../../../../docs/framework/data/wcf/how-to-customize-data-binding-behaviors-wcf-data-services.md).  
  
 Bir nesne kaldırılır varsayılan davranış bir <xref:System.Data.Services.Client.DataServiceCollection%601> kullanarak <xref:System.Collections.ObjectModel.Collection%601.Remove%2A> yöntemdir nesne da silinmiş olarak işaretlenmiş <xref:System.Data.Services.Client.DataServiceContext>. Bu davranışı değiştirmek için bir yöntem için temsilci belirleyebilirsiniz `entityCollectionChanged` aldığında çağrılan parametresi <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> olayı oluşur.  
  
## <a name="data-binding-with-custom-client-data-classes"></a>Veri bağlama ile özel istemci veri sınıfları  
 Nesneleri yüklemek için bir <xref:System.Data.Services.Client.DataServiceCollection%601>, nesnelerinin kendilerini uygulamalıdır <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi. Veri Hizmeti kullandığınızda, oluşturulan istemci sınıfları **hizmet Başvurusu Ekle** iletişim kutusu veya [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) aracı bu arabirim uygulama. Kendi istemci veri sınıfları sağlarsanız, veri bağlama için başka türde bir koleksiyonu kullanmanız gerekir. Nesneleri değiştirdiğinizde, aşağıdaki yöntemleri çağırmak için veri bağlama denetimleri olayları işlemelidir <xref:System.Data.Services.Client.DataServiceContext> sınıfı:  
  
-   <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A>-Yeni bir nesne koleksiyona eklendiğinde.  
  
-   <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A>-bir nesne koleksiyondan kaldırıldığında.  
  
-   <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A>-ne zaman bir özelliği değiştirildiğinde koleksiyondaki bir nesne üzerinde.  
  
-   <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>-ilgili nesne koleksiyonu için bir nesne eklendiğinde.  
  
-   <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>-ilgili nesneleri bir koleksiyon için bir nesne eklendiğinde.  
  
 Daha fazla bilgi için bkz: [veri hizmeti güncelleştirme](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: el ile istemci veri hizmeti sınıfları oluşturma](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)  
 [Nasıl yapılır: bir veri hizmet Başvurusu Ekle](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
