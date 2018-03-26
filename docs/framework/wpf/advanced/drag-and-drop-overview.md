---
title: Sürükleme ve Bırakmaya Genel Bakış
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], implementing
- drag sources [WPF], drag-and-drop
- data transfer [WPF], drag-and-drop
- drag-and-drop [WPF], about
- drag-and-drop [WPF], events
- drop targets [WPF], drag-and-drop
ms.assetid: 1a5b27b0-0ac5-4cdf-86c0-86ac0271fa64
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b7a69a4dcd5fc39b700bf9c3404e70d581509ebc
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="drag-and-drop-overview"></a>Sürükleme ve Bırakmaya Genel Bakış
Bu konu, sürükle ve bırak desteği'ne genel bakış sağlar. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalar. Sürükle ve bırak fare (veya başka bir işaretleme aygıtı) bir veya daha fazla nesne seçmek için bu nesneleri sürükleyerek bazı istenilen bırakma hedefi üzerinden kullanılmasına veri aktarım yöntemi için yaygın olarak başvuruyor [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]ve bunları bırakma.  
  
  
<a name="Drag_and_Drop_Support"></a>   
## <a name="drag-and-drop-support-in-wpf"></a>WPF sürükle ve bırak desteği  
 Sürükle ve bırak işlemleri genellikle iki taraf içerir: sürükleme kaynağından hangi sürüklenen nesnenin kaynaklanan ve bırakılan nesneyi alan bir bırakma hedefi.  Sürükleme kaynağı ve bırakma hedefi aynı uygulama ya da farklı bir uygulama kullanıcı Arabirimi öğeleri olabilir.  
  
 Sürükle ve bırak ile yönetilebilir nesnelerinin sayısı ve türü tamamen rastgele. Örneğin, dosyaları, klasörleri ve içerik seçimleri sürükle ve bırak işlemleri aracılığıyla daha yaygın nesnelerin bazılarıdır.  
  
 Bir Sürükle ve bırak işlemi sırasında belirli eylemlerin uygulama belirli ve genellikle bağlam tarafından belirlenen var.  Örneğin, seçim dosyalarını bir klasöründen diğerine aynı depolama aygıtında sürükleme dosyaları varsayılan olarak, dosyaları sürükleme taşınırken bir [!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)] bir yerel klasör paylaşımına varsayılan olarak dosyalarını kopyalar.  
  
 Tarafından sağlanan sürükle ve bırak özellikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oldukça esnek ve çok çeşitli sürükle ve bırak senaryolarını desteklemek üzere özelleştirilebilir olacak şekilde tasarlanmıştır.  Düzenleme nesneleri, tek bir uygulama içinde ya da farklı uygulamalar arasında sürükle ve bırak destekler. Sürükleme ve bırakma arasında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları ve diğer [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)] uygulamaları tam olarak desteklenir.  
  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], her türlü <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement> sürükle ve bırak içinde katılabilirsiniz. Olayları ve içinde tanımlanan sürükle ve bırak işlemleri için gereken yöntemleri <xref:System.Windows.DragDrop> sınıfı. <xref:System.Windows.UIElement> Ve <xref:System.Windows.ContentElement> sınıfları için diğer adlar içeren <xref:System.Windows.DragDrop> sınıfında olayları görünmesini sağlayacak şekilde ekli olaylar üyeleri listeler bir <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement> temel bir öğe devralınır. Bu olaylara bağlı olan olay işleyicileri için temel bağlı <xref:System.Windows.DragDrop> ekli olayı ve aynı olay veri örneğini alır. Daha fazla bilgi için bkz: <xref:System.Windows.UIElement.Drop?displayProperty=nameWithType> olay.  
  
> [!IMPORTANT]
>  OLE sürükle ve bırak Internet bölgesinde durumdayken çalışmaz.  
  
<a name="Data_Transfer"></a>   
## <a name="data-transfer"></a>Veri aktarımı  
 Sürükle ve bırak daha genel alan veri aktarımı'nın bir parçasıdır. Veri Aktarımı Sürükle ve bırak ve kopyalama ve yapıştırma işlemlerini içerir. Sürükle ve bırak işlemi, verileri bir nesne ya da başka bir uygulama Sistem panosu kullanarak aktarmak için kullanılan bir kopyalama ve yapıştırma veya kesme ve yapıştırma işlemi benzer. Her iki tür işlemler gerektirir:  
  
-   Veri sağlayan bir kaynak nesnesi.  
  
-   Geçici olarak aktarılan verileri depolamak için bir yol.  
  
-   Verileri alan bir hedef nesnesi.  
  
 Bir kopyalama ve yapıştırma işlemi Sistem panosu, geçici olarak aktarılan verileri depolamak için kullanılır; Sürükle ve bırak işlemi içinde bir <xref:System.Windows.DataObject> verileri depolamak için kullanılır. Kavramsal olarak, bir veri nesnesi, bir veya daha fazla çiftlerinden oluşur bir <xref:System.Object> gerçek veri ve karşılık gelen bir veri biçimi tanımlayıcısı içeriyor.  
  
 Statik çağırarak sürükleme kaynağı sürükle ve bırak işlemi başlatan <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> yöntemi ve aktarılan veri için geçirme. <xref:System.Windows.DragDrop.DoDragDrop%2A> Yöntemi otomatik olarak verilerde sarmalamak bir <xref:System.Windows.DataObject> gerekiyorsa. Veri biçimi üzerinde daha fazla denetim için verileri kayabilir bir <xref:System.Windows.DataObject> kendisine geçirmeden önce <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemi. Bırakma hedefi verilerden ayıklanmasına sorumludur <xref:System.Windows.DataObject>. Veri nesneleri ile çalışma hakkında daha fazla bilgi için bkz: [veri ve veri nesneleri](../../../../docs/framework/wpf/advanced/data-and-data-objects.md).  
  
 Kaynak ve hedef bir Sürükle ve bırak işlemi, kullanıcı Arabirimi öğeleri olan; Ancak, aslında genellikle aktarıldığı veri görsel gösterimi yok. Sürüklenen, Windows Gezgini'ndeki dosyaları sürükleme gibi oluşur verileri görsel gösterimi sağlamak üzere kod yazabilirsiniz. Varsayılan olarak, geri bildirim kullanıcıya sürükle ve bırak işlemi verileri üzerinde gibi olacaktır etkisi temsil etmek için imleci değiştirerek verileri taşınamaz veya kopyalanamaz sağlanır.  
  
### <a name="drag-and-drop-effects"></a>Sürükle ve bırak etkileri  
 Sürükle ve bırak işlemleri aktarılan verileri farklı etkileri olabilir. Örneğin, veri kopyalayabilir veya veri taşıyabilirsiniz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tanımlayan bir <xref:System.Windows.DragDropEffects> sürükle ve bırak işlemi etkisini belirlemek için kullanabileceğiniz numaralandırması. Sürükleme kaynağında kaynak izin veren etkilerini belirtebilirsiniz <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemi. Bırakma hedefi, hedef oranla etkisi belirtebilirsiniz <xref:System.Windows.DragEventArgs.Effects%2A> özelliği <xref:System.Windows.DragEventArgs> sınıfı. Bırakma hedefi hedeflenen etkisini belirttiğinde <xref:System.Windows.DragDrop.DragOver> bilgi geri sürükleyin kaynağında geçirilen olay <xref:System.Windows.DragDrop.GiveFeedback> olay. Sürükleme kaynağı bu bilgileri bırakma hedefi verilere sahip amaçlayan hangi etkisi kullanıcıyı bilgilendirmek üzere kullanır. Veri bırakıldığında bırakma hedefi gerçek etkisini belirtir <xref:System.Windows.DragDrop.Drop> olay. Bilgi sürükleme kaynağına geri dönüş değeri olarak geçirilir <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemi. Bırakma hedefi Sürükle kaynakları listesinde değil efekt döndürürse `allowedEffects`, oluşan herhangi bir veri aktarımı sürükle ve bırak işlemi iptal edildi.  
  
 Sisteminde unutulmaması önemlidir; [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.DragDropEffects> değerleri yalnızca sürükleme kaynağı sürükle ve bırak işlemi etkilerini ilgili bırakma hedefi arasındaki iletişimi sağlamak için kullanılır. Sürükle ve bırak işlemi gerçek etkisi, uygun kodu, uygulamanızda yazmanızı bağlıdır.  
  
 Örneğin, bırakma hedefi verileri taşımak için veri bırakmadan etkisini olduğunu belirtebilir. Ancak, verileri taşımak için hem hedef öğesine eklendi ve gerekir kaynağı öğesinden kaldırıldı. Source öğesi, verilerin taşınmasını sağlar, ancak veri kaynağı öğesinden kaldırmak için kodu belirtmezseniz, sonuç verileri kopyalanır ve taşınmaz olduğunu olacak gösterebilir.  
  
<a name="Drag_and_Drop_Events"></a>   
## <a name="drag-and-drop-events"></a>Sürükle ve bırak olayları  
 Sürükle ve bırak işlemleri kullanımlı olay modelini destekler.  Sürükleme kaynağı ve bırakma hedefi sürükle ve bırak işlemleri işlemek için standart olaylar kümesi kullanır.  Aşağıdaki tablolarda, standart sürükle ve bırak olayları özetlenmektedir. Ekli olaylar üzerinde bunlar <xref:System.Windows.DragDrop> sınıfı. Ekli olaylar hakkında daha fazla bilgi için bkz: [bağlı olaylara genel bakış](../../../../docs/framework/wpf/advanced/attached-events-overview.md).  
  
### <a name="drag-source-events"></a>Sürükleme kaynağı olayları  
  
|Olay|Özet|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.GiveFeedback>|Bu olay, sürekli bir Sürükle ve bırak işlemi sırasında oluşur ve kullanıcıya geri bildirim bilgi vermek açılan kaynak sağlar. Bu geri bildirim genellikle fare işaretçisini görünümünü değiştirerek bırakma hedefi tarafından izin verilen etkileri belirtmek için verilir.  Bu kabarcıklanma bir olaydır.|  
|<xref:System.Windows.DragDrop.QueryContinueDrag>|Bu olay bir değişiklik klavye veya fare düğmesini bir Sürükle ve bırak işlemi sırasında durumları ve anahtar/düğme durumlarına bağlı olarak sürükle ve bırak işlemi iptal etmek bırakma kaynağını etkinleştirir oluşur. Bu kabarcıklanma bir olaydır.|  
|<xref:System.Windows.DragDrop.PreviewGiveFeedback>|Tünel sürümü <xref:System.Windows.DragDrop.GiveFeedback>.|  
|<xref:System.Windows.DragDrop.PreviewQueryContinueDrag>|Tünel sürümü <xref:System.Windows.DragDrop.QueryContinueDrag>.|  
  
### <a name="drop-target-events"></a>Bırakma hedefi olayları  
  
|Olay|Özet|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.DragEnter>|Bu olay, bir nesne bırakma hedefinin sınırları içine sürüklendiğinde gerçekleşir. Bu kabarcıklanma bir olaydır.|  
|<xref:System.Windows.DragDrop.DragLeave>|Bu olay, bir nesne bırakma hedefinin sınırları dışında sürüklendiğinde oluşur.  Bu kabarcıklanma bir olaydır.|  
|<xref:System.Windows.DragDrop.DragOver>|Bu olay, sürekli bir nesne (taşınan) bırakma hedefinin sınırları içinde sürüklenen sırada gerçekleşir. Bu kabarcıklanma bir olaydır.|  
|<xref:System.Windows.DragDrop.Drop>|Bu olay, bir nesne üzerinde bırakma hedefi bırakılan oluşur.  Bu kabarcıklanma bir olaydır.|  
|<xref:System.Windows.DragDrop.PreviewDragEnter>|Tünel sürümü <xref:System.Windows.DragDrop.DragEnter>.|  
|<xref:System.Windows.DragDrop.PreviewDragLeave>|Tünel sürümü <xref:System.Windows.DragDrop.DragLeave>.|  
|<xref:System.Windows.DragDrop.PreviewDragOver>|Tünel sürümü <xref:System.Windows.DragDrop.DragOver>.|  
|<xref:System.Windows.DragDrop.PreviewDrop>|Tünel sürümü <xref:System.Windows.DragDrop.Drop>.|  
  
 Sürükle ve bırak olayları işlemek için bir nesne örneklerini eklemek için yukarıdaki tablolarda listelenen olaylar için işleyiciler. Sınıf düzeyinde sürükle ve bırak olayları işlemek için üzerinde sanal karşılık gelen geçersiz kılma * olay ve\*PreviewEvent yöntemleri. Daha fazla bilgi için bkz: [sınıf işleme, yönlendirilmiş olayları denetim taban sınıfları tarafından](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md#Class_Handling_of_Routed_Events).  
  
<a name="Implementing_Drag_And_Drop"></a>   
## <a name="implementing-drag-and-drop"></a>Sürükle ve bırak uygulama  
 Bir kullanıcı Arabirimi öğesi sürükleme kaynağı, bir bırakma hedefi veya her ikisi de olabilir. Temel sürükle ve bırak uygulamak için sürükle ve bırak işlemi başlatmak için bırakılan verileri işlemek için bir kod yazın. İsteğe bağlı sürükle ve bırak olayları işleme tarafından sürükle ve bırak deneyimini geliştirebilirsiniz.  
  
 Temel sürükle ve bırak uygulamak için aşağıdaki görevleri tamamlayacaktır:  
  
-   Sürükleme kaynağı olacaktır öğesi tanımlayın. Sürükleme kaynağı olabilir bir <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement>.  
  
-   Olay işleyici sürükle ve bırak işlemi başlatır sürükleme kaynağı oluşturun. Genellikle olaydır <xref:System.Windows.UIElement.MouseMove> olay.  
  
-   Sürükleme kaynağı olay işleyicisi çağırma <xref:System.Windows.DragDrop.DoDragDrop%2A> sürükle ve bırak işlemi başlatmak için yöntem. İçinde <xref:System.Windows.DragDrop.DoDragDrop%2A> çağrısı, sürükleme kaynağı, aktarılacak veri ve izin verilen etkileri belirtin.  
  
-   Bırakma hedefi olacak öğesi tanımlayın. Bırakma hedefi olabilir <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement>.  
  
-   Bırakma hedefi üzerindeki ayarlamak <xref:System.Windows.UIElement.AllowDrop%2A> özelliğine `true`.  
  
-   Bırakma hedefi oluşturma bir <xref:System.Windows.DragDrop.Drop> bırakılan verileri işlemek için olay işleyicisi.  
  
-   İçinde <xref:System.Windows.DragDrop.Drop> olay işleyicisi çağırmanız <xref:System.Windows.DragEventArgs> kullanarak <xref:System.Windows.DataObject.GetDataPresent%2A> ve <xref:System.Windows.DataObject.GetData%2A> yöntemleri.  
  
-   İçinde <xref:System.Windows.DragDrop.Drop> olay işleyicisi verileri istenen sürükle ve bırak işlemi gerçekleştirmek için kullanabilirsiniz.  
  
 Özel bir oluşturarak sürükle ve bırak uygulamanızı geliştirebilirsiniz <xref:System.Windows.DataObject> ve aşağıdaki görevleri gösterildiği gibi isteğe bağlı işleyerek kaynağı ve bırakma hedefi olayları sürükleyin:  
  
-   Özel veri veya birden çok veri öğeleri aktarmak için Oluştur bir <xref:System.Windows.DataObject> geçirilecek <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemi.  
  
-   Sürükleme sırasında ek eylemleri gerçekleştirmek için tanıtıcı <xref:System.Windows.DragDrop.DragEnter>, <xref:System.Windows.DragDrop.DragOver>, ve <xref:System.Windows.DragDrop.DragLeave> bırakma hedefi olayları.  
  
-   Fare işaretçisini görünümünü değiştirmek için tanıtıcı <xref:System.Windows.DragDrop.GiveFeedback> sürükleme kaynağı olayı.  
  
-   Sürükle ve bırak işlemi nasıl iptal değiştirmek için tanıtıcı <xref:System.Windows.DragDrop.QueryContinueDrag> sürükleme kaynağı olayı.  
  
<a name="Drag_And_Drop_Example"></a>   
## <a name="drag-and-drop-example"></a>Sürükle ve bırak örneği  
 Bu bölümde, sürükle ve bırak için uygulanacak açıklar bir <xref:System.Windows.Shapes.Ellipse> öğesi. <xref:System.Windows.Shapes.Ellipse> Hem sürükleme kaynağı, hem de bir bırakma hedefi. Aktarılan veri elips 's dize gösterimidir <xref:System.Windows.Shapes.Shape.Fill%2A> özelliği. Aşağıdaki XAML gösterildiği <xref:System.Windows.Shapes.Ellipse> öğesi ve bunu işleyen sürükle ve bırak ilgili olaylar. Sürükle ve bırak uygulamak nasıl tam adımlar için bkz: [izlenecek yol: etkinleştirme sürükleme ve bırakma bir kullanıcı denetimi üzerinde](../../../../docs/framework/wpf/advanced/walkthrough-enabling-drag-and-drop-on-a-user-control.md).  
  
 [!code-xaml[DragDropSnippets#EllipseXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#ellipsexaml)]  
  
### <a name="enabling-an-element-to-be-a-drag-source"></a>Sürükleme kaynağı olarak bir öğeyi etkinleştirme  
 Sürükleme kaynağı olan bir nesneyi sorumludur:  
  
-   Bir Sürükle oluştuğunda tanımlama.  
  
-   Sürükle ve bırak işlemi başlatılıyor.  
  
-   Verilerin aktarılması için tanımlayıcı.  
  
-   Sürükle ve bırak işlemi aktarılan verilerin üzerinde izin veriliyor etkilerini belirtme.  
  
 Sürükleme kaynağı da kullanıcıya izin verilen eylemleri ile ilgili geri bildirim verebilir (taşıma, kopyalama, hiçbiri) ve sürükleme sırasında ESC tuşuna basarak gibi ek kullanıcı girişi, temel sürükle ve bırak işlemini iptal edebilirsiniz.  
  
 Bunu bir Sürükle oluştuğunda belirlemek için uygulamanızı ve başlatma sürükle ve bırak işlemi çağırarak sorumluluğundadır <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemi. Genellikle, bu olduğunda bir <xref:System.Windows.UIElement.MouseMove> olayı, fare düğmesini basılı durumdayken sürüklenen öğenin üzerine oluşur. Aşağıdaki örnek, bir Sürükle ve bırak işlemi başlatmak gösterilmiştir <xref:System.Windows.UIElement.MouseMove> olay işleyicisine bir <xref:System.Windows.Shapes.Ellipse> sürükleme kaynağı yapmak için öğesi. Aktarılan veri elips 's dize gösterimidir <xref:System.Windows.Shapes.Shape.Fill%2A> özelliği.  
  
 [!code-csharp[DragDropSnippets#DoDragDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dodragdrop)]
 [!code-vb[DragDropSnippets#DoDragDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dodragdrop)]  
  
 İçinde <xref:System.Windows.UIElement.MouseMove> olay işleyicisi, çağrı <xref:System.Windows.DragDrop.DoDragDrop%2A> sürükle ve bırak işlemi başlatmak için yöntem. <xref:System.Windows.DragDrop.DoDragDrop%2A> Yöntemi üç parametreleri alır:  
  
-   `dragSource` – Aktarılan veri kaynağı bağımlılık nesnesi bir başvuru; Bu genellikle kaynağıdır <xref:System.Windows.UIElement.MouseMove> olay.  
  
-   `data` -Sarmalanmış aktarılan verileri içeren bir nesne bir <xref:System.Windows.DataObject>.  
  
-   `allowedEffects` -Biri <xref:System.Windows.DragDropEffects> sürükle ve bırak işlemi izin verilen etkilerini belirten numaralandırma değerlerinin.  
  
 Herhangi bir seri hale getirilebilir nesnesi geçirilebilir `data` parametresi. Veri içinde zaten sarmalanmamış varsa bir <xref:System.Windows.DataObject>, onu otomatik olarak yeni bir sarılır <xref:System.Windows.DataObject>. Birden çok veri öğeleri geçirmek için oluşturmalısınız <xref:System.Windows.DataObject> kendiniz ve ona geçirin <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemi. Daha fazla bilgi için bkz: [veri ve veri nesneleri](../../../../docs/framework/wpf/advanced/data-and-data-objects.md).  
  
 `allowedEffects` Parametresi ne sürükleme kaynağı aktarılan verilerle yapmak bırakma hedefi sağlayacak belirtmek için kullanılır. Sürükleme kaynağı için ortak değerler <xref:System.Windows.DragDropEffects.Copy>, <xref:System.Windows.DragDropEffects.Move>, ve <xref:System.Windows.DragDropEffects.All>.  
  
> [!NOTE]
>  Bırakma hedefi ayrıca yanıt bırakılan veri olarak bunu oranla hangi etkileri belirtebilirsiniz. Bırakma hedefi bırakılmasına veri türü tanımazsa, örneğin, bu verileri izin verilen etkileri ayarlayarak reddedebilir <xref:System.Windows.DragDropEffects.None>. Genellikle bu yaptığı da kendi <xref:System.Windows.DragDrop.DragOver> olay işleyicisi.  
  
 Sürükleme kaynağı isteğe bağlı olarak işleyebilir <xref:System.Windows.DragDrop.GiveFeedback> ve <xref:System.Windows.DragDrop.QueryContinueDrag> olaylar. Bu olaylar olayları işlenmiş olarak işaretlemezseniz, kullanılan varsayılan işleyicileri sahiptir. Kendi varsayılan davranışı değiştirmek için belirli bir gereksiniminiz yoksa bu olaylar genelde göz ardı eder.  
  
 <xref:System.Windows.DragDrop.GiveFeedback> Sürekli sürükleme kaynağı sürüklenen sırada olayı oluşturulur. Bu olay için varsayılan işleyici sürükleme kaynağı geçerli bırakma hedefi olup olmadığını denetler. İse, izin verilen bırakma hedefi etkilerini denetler. Sonra son kullanıcının izin verilen açılan efektleri ile ilgili geri bildirim sağlar. Bu genellikle bir Hayır bırak için kopyalama, fare imlecini değiştirilerek yapılır veya imleç taşıyın. Kullanıcıya geri bildirim sağlamak için özel imleçler kullanmanız gerekiyorsa bu olay yalnızca işlemelidir. Bu olayı işlemek, böylece varsayılan işleyici işleyicinizi kılmaz işlenmiş olarak işaretlemek emin olun.  
  
 <xref:System.Windows.DragDrop.QueryContinueDrag> Sürekli sürükleme kaynağı sürüklenen sırada olayı oluşturulur. Hangi eylemini ESC, SHIFT, CTRL ve ALT anahtarları durumunun yanı sıra üzerinde fare düğmelerinin durumunu dayalı sürükle ve bırak işlemi sonlandırır belirlemek için bu olay işleyebilir. ESC tuşuna basılana ve fare düğmesini yayımlanırsa verileri bırakır, bu olay için varsayılan işleyici sürükle ve bırak işlemi iptal eder.  
  
> [!CAUTION]
>  Bu olaylar sürükle ve bırak işlemi sırasında sürekli olarak oluşturulur. Bu nedenle, olay işleyicileri yoğun bir kaynak görevlerinde kaçınmalısınız.  Örneğin, her seferinde yeni imleç yerine önbelleğe alınmış bir imleç kullanın <xref:System.Windows.DragDrop.GiveFeedback> olayı oluşturulur.  
  
### <a name="enabling-an-element-to-be-a-drop-target"></a>Bırakma hedefi olarak bir öğeyi etkinleştirme  
 Bırakma hedefi bir nesne sorumludur:  
  
-   Geçerli bırakma hedefi olup olmadığını belirleme.  
  
-   Hedef sürüklendiğinde sürükleyin kaynağına yanıt.  
  
-   Aktarılan veri alabileceği bir biçimde olup olmadığı denetleniyor.  
  
-   Bırakılan veri işliyor.  
  
 Bırakma hedefi bir öğe ise, ayarladığınız belirtmek için kendi <xref:System.Windows.UIElement.AllowDrop%2A> özelliğine `true`. Böylece bunları işleyebilir bırakma hedefi olayları sonra öğede gerçekleştirilecektir. Bir Sürükle ve bırak işlemi sırasında açılan hedef sunucuda aşağıdaki olaylar dizisi gerçekleşir:  
  
1.  <xref:System.Windows.DragDrop.DragEnter>  
  
2.  <xref:System.Windows.DragDrop.DragOver>  
  
3.  <xref:System.Windows.DragDrop.DragLeave> Veya <xref:System.Windows.DragDrop.Drop>  
  
 <xref:System.Windows.DragDrop.DragEnter> Veri bırakma hedefinin sınırları içine sürüklendiğinde olayı oluşur. Uygulamanız için uygun şekilde, genellikle bir Sürükle ve bırak işlemi etkilerini önizlemesini sağlamak için bu olayı işleyin. Ayarlamayın <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> özelliğinde <xref:System.Windows.DragDrop.DragEnter> şekliyle olay yazılır <xref:System.Windows.DragDrop.DragOver> olay.  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Windows.DragDrop.DragEnter> olay işleyicisi için bir <xref:System.Windows.Shapes.Ellipse> öğesi. Bu kod, geçerli kaydederek sürükle ve bırak işlemi etkilerini önizlemeleri sağlanır <xref:System.Windows.Shapes.Shape.Fill%2A> Fırçası. Daha sonra kullanır <xref:System.Windows.DataObject.GetDataPresent%2A> denetlemek için yöntemi olup olmadığını <xref:System.Windows.DataObject> elips sürüklenen dönüştürülebilir dize verilerini içeren bir <xref:System.Windows.Media.Brush>. Bu nedenle, verileri kullanarak ayıklanan varsa <xref:System.Windows.DataObject.GetData%2A> yöntemi. Ardından dönüştürülmeden bir <xref:System.Windows.Media.Brush> ve elips uygulanır. İçinde değişiklik geri <xref:System.Windows.DragDrop.DragLeave> olay işleyicisi. Verileri için dönüştürülemiyorsa bir <xref:System.Windows.Media.Brush>, hiçbir eylem gerçekleştirilir.  
  
 [!code-csharp[DragDropSnippets#DragEnter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragenter)]
 [!code-vb[DragDropSnippets#DragEnter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragenter)]  
  
 <xref:System.Windows.DragDrop.DragOver> Olayı, veri bırakma hedefi sürekli sürüklenen sırasında oluşur. Bu olay ile eşleştirilmiş <xref:System.Windows.DragDrop.GiveFeedback> sürükleme kaynağı olayı. İçinde <xref:System.Windows.DragDrop.DragOver> olay işleyicisi, genellikle kullandığınız <xref:System.Windows.DataObject.GetDataPresent%2A> ve <xref:System.Windows.DataObject.GetData%2A> aktarılan verileri bırakma hedefi işleyebilir bir biçimde olup olmadığını denetlemek için yöntemler. Ayrıca, tüm değiştirici tuşları, hangi genellikle kullanıcı taşıma veya kopyalama eylem oranla olup olmadığını gösterir basıldığında olup olmadığını kontrol edebilirsiniz. Bu denetimler yapıldıktan sonra ayarladığınız <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> source özelliği Sürükle bildirmek için veri bırakma hangi etkisi olmaz. Bu bilgileri sürükleme kaynağı alır <xref:System.Windows.DragDrop.GiveFeedback> olay bağımsız değişken ve kullanıcıya geribildirim vermek için uygun bir imleç ayarlayabilirsiniz.  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Windows.DragDrop.DragOver> olay işleyicisi için bir <xref:System.Windows.Shapes.Ellipse> öğesi. Bu kod olup olmadığını denetler. <xref:System.Windows.DataObject> elips sürüklenen dönüştürülebilir dize verilerini içeren bir <xref:System.Windows.Media.Brush>. Bu nedenle, bunu ayarlarsa <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> özelliğine <xref:System.Windows.DragDropEffects.Copy>. Bu veriler için üç nokta kopyalanabilir sürükleme kaynağına gösterir. Verileri için dönüştürülemiyorsa bir <xref:System.Windows.Media.Brush>, <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> özelliği ayarlanmış <xref:System.Windows.DragDropEffects.None>. Bu, sürükleme kaynağına elips veriler için geçerli bırakma hedefi olmadığını gösterir.  
  
 [!code-csharp[DragDropSnippets#DragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragover)]
 [!code-vb[DragDropSnippets#DragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragover)]  
  
 <xref:System.Windows.DragDrop.DragLeave> Olay verileri hedefin sınırları dışında bırakılan olmadan sürüklendiğinde oluşur. Yaptığınız herhangi bir şeyi geri almak için bu olayı işlemek <xref:System.Windows.DragDrop.DragEnter> olay işleyicisi.  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Windows.DragDrop.DragLeave> olay işleyicisi için bir <xref:System.Windows.Shapes.Ellipse> öğesi. Bu kod başlığında gerçekleştirilen Önizleme alır <xref:System.Windows.DragDrop.DragEnter> kaydedilen uygulayarak olay işleyicisi <xref:System.Windows.Media.Brush> elips için.  
  
 [!code-csharp[DragDropSnippets#DragLeave](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragleave)]
 [!code-vb[DragDropSnippets#DragLeave](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragleave)]  
  
 <xref:System.Windows.DragDrop.Drop> Olay verileri bırakma hedefi bırakılan oluşur; fare düğmesini serbest bırakıldığında varsayılan olarak, bu gerçekleşir. İçinde <xref:System.Windows.DragDrop.Drop> olay işleyicisi kullandığınız <xref:System.Windows.DataObject.GetData%2A> aktarılan verileri ayıklamak için yöntemi <xref:System.Windows.DataObject> ve uygulamanızın gerektirdiği herhangi bir veri işlem gerçekleştirin. <xref:System.Windows.DragDrop.Drop> Olay sürükle ve bırak işlemi sonlandırır.  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Windows.DragDrop.Drop> olay işleyicisi için bir <xref:System.Windows.Shapes.Ellipse> öğesi. Bu kod sürükle ve bırak işlemi etkilerini uygular ve kodda benzer <xref:System.Windows.DragDrop.DragEnter> olay işleyicisi. Olup olmadığını denetler <xref:System.Windows.DataObject> elips sürüklenen dönüştürülebilir dize verilerini içeren bir <xref:System.Windows.Media.Brush>. Bu durumda, <xref:System.Windows.Media.Brush> elips uygulanır. Verileri için dönüştürülemiyorsa bir <xref:System.Windows.Media.Brush>, hiçbir eylem gerçekleştirilir.  
  
 [!code-csharp[DragDropSnippets#Drop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#drop)]
 [!code-vb[DragDropSnippets#Drop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#drop)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Clipboard>  
 [İzlenecek yol: Kullanıcı Denetiminde Sürükleme ve Bırakmayı Etkinleştirme](../../../../docs/framework/wpf/advanced/walkthrough-enabling-drag-and-drop-on-a-user-control.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/advanced/drag-and-drop-how-to-topics.md)  
 [Sürükleme ve Bırakma](../../../../docs/framework/wpf/advanced/drag-and-drop.md)
