---
title: Sürükleme ve Bırakmaya Genel Bakış
ms.date: 03/30/2017
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
ms.openlocfilehash: 2b76c8fd3e2c6961b6ebdddc9b7ff9649f5196f4
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59301405"
---
# <a name="drag-and-drop-overview"></a>Sürükleme ve Bırakmaya Genel Bakış
Bu konu, sürükle ve bırak desteği'ne genel bakış sağlar. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalar. Sürükle ve bırak fare (veya başka bir işaretleme cihazı) bir veya birden çok nesne seçmek için bu nesneleri sürükleyerek üzerinden bazı istenen bırakma hedefi kullanılmasına veri aktarım yöntemi için yaygın olarak başvuruyor [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]ve onları bırakma.  

<a name="Drag_and_Drop_Support"></a>   
## <a name="drag-and-drop-support-in-wpf"></a>WPF sürükle ve bırak desteği  
 Sürükle ve bırak işlemleri genellikle iki taraf da içerir: sürükleme kaynağı, sürüklenen nesnenin kaynaklanan ve bir bırakma hedefi bırakılan nesnesini alır.  Sürükleme kaynağı ve bırakma hedefi, aynı veya farklı bir uygulama kullanıcı Arabirimi öğeleri olabilir.  
  
 Sürükle ve bırak ile yönetilebilir nesneleri sayısı ve türü tamamen isteğe bağlı. Örneğin, dosyaları, klasörleri ve içerik seçimleri sürükle ve bırak işlemleri aracılığıyla sık kullanılan nesnelerin bazıları.  
  
 Bir Sürükle ve bırak işlemi sırasında gerçekleştirilen belirli eylemler uygulamanın belirli ve bağlam tarafından belirlenen genellikle ' dir.  Örneğin, bir seçim dosyaların bir klasörden diğerine aynı depolama cihazında sürükleyerek dosyaları varsayılan olarak, dosyaları sürükleme taşır bir [!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)] paylaşımı yerel bir klasöre dosyalar varsayılan olarak kopyalar.  
  
 Tarafından sağlanan sürükle ve bırak özellikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yüksek oranda esnek ve çok çeşitli sürükle ve bırak senaryolarını desteklemek için özelleştirilebilir olacak şekilde tasarlanmıştır.  Düzenleme nesneleri tek bir uygulama içinde ya da farklı uygulamalar arasında sürükle ve bırak destekler. Sürükleme ve bırakma arasında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları ve diğer Windows uygulamaları de tam olarak desteklenir.  
  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement> sürükle ve bırak içinde yer alabilirler. Sürükle ve bırak işlemleri tanımlanan için gereken yöntemleri ve olayları <xref:System.Windows.DragDrop> sınıfı. <xref:System.Windows.UIElement> Ve <xref:System.Windows.ContentElement> sınıflar için diğer adlar bulunur <xref:System.Windows.DragDrop> olayları sınıfında görünecek biçimde ekli olaylar üye listesinde bir <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement> temel bir öğe devralınır. Bu olaylara bağlı olan olay işleyicileri, temel alınan iliştirilir <xref:System.Windows.DragDrop> ekli olay ve aynı olay verileri örneği alır. Daha fazla bilgi için <xref:System.Windows.UIElement.Drop?displayProperty=nameWithType> olay.  
  
> [!IMPORTANT]
>  OLE sürükle ve bırak Internet bölgesi sırasında çalışmaz.  
  
<a name="Data_Transfer"></a>   
## <a name="data-transfer"></a>Veri Aktarımı  
 Sürükle ve bırak daha genel alanı veri aktarımı'nın bir parçasıdır. Veri aktarımı, sürükle ve bırak ve kopyalama ve yapıştırma işlemlerini içerir. Bir Sürükle ve bırak işlemi, Sistem panosu kullanılarak bir nesne veya başka bir uygulamaya veri aktarımı için kullanılan bir kopyalama ve yapıştırma veya Kes ve Yapıştır işlemi benzerdir. Her iki tür işlemleri gerektirir:  
  
-   Veri sağlayan bir kaynak nesne.  
  
-   Geçici olarak aktarılan verileri depolamak için bir yol.  
  
-   Verileri alan bir hedef nesne.  
  
 Kopyalama ve yapıştırma işleminde, sistem panosuna geçici olarak aktarılan verileri depolamak için kullanılır; bir Sürükle ve bırak işleminde bir <xref:System.Windows.DataObject> verileri depolamak için kullanılır. Kavramsal olarak, bir veri nesnesi, bir veya daha fazla çiftlerinden oluşan bir <xref:System.Object> gerçek veriler ve karşılık gelen bir veri biçimi tanımlayıcısı içeriyor.  
  
 Statik çağırarak bir Sürükle ve bırak işlemi sürükleme kaynağı başlatır <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> yöntemi ve aktarılan veriler için geçirme. <xref:System.Windows.DragDrop.DoDragDrop%2A> Yöntemi otomatik olarak verileri kaydırma bir <xref:System.Windows.DataObject> gerekirse. Veri biçimi üzerinde daha fazla denetim için verileri kaydırılabilir bir <xref:System.Windows.DataObject> öğesine iletmeden önce <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemi. Bırakma hedefi verilerden ayıklanmasına sorumludur <xref:System.Windows.DataObject>. Veri nesneleri ile çalışma hakkında daha fazla bilgi için bkz. [veri ve veri nesneleri](data-and-data-objects.md).  
  
 Kaynak ve hedef bir Sürükle ve bırak işleminin kullanıcı Arabirimi öğelerini olan; Ancak, gerçekte genellikle aktarıldığı veri görsel bir temsili yok. Sürüklenen, gibi Windows Gezgini'nde dosyaları sürüklendiğinde oluşur verilerin görsel bir temsili sağlamak için kod yazabilirsiniz. Varsayılan olarak, geri bildirim kullanıcıya sürükle ve bırak işlemi gibi veri olacak etkisini göstermek için imleç değiştirerek verileri taşınamaz veya kopyalanamaz sağlanır.  
  
### <a name="drag-and-drop-effects"></a>Sürükle ve bırak etkileri  
 Sürükle ve bırak işlemleri, aktarılan verileri farklı etkileri olabilir. Örneğin, veri kopyalayabilir veya verileri taşıyabilirsiniz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tanımlayan bir <xref:System.Windows.DragDropEffects> , bir Sürükle ve bırak işlemi etkisini belirlemek için kullanabileceğiniz sabit listesi. Sürükleme kaynağı içinde kaynak olarak tanıyacak etkileri belirtebilirsiniz <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemi. Bırakma hedefi, hedef düşünüyor etkisi belirtebilirsiniz <xref:System.Windows.DragEventArgs.Effects%2A> özelliği <xref:System.Windows.DragEventArgs> sınıfı. Ne zaman bırakma hedefi belirtir hedeflenen etkisini <xref:System.Windows.DragDrop.DragOver> bilgi sürükleme kaynağı geçirilir olay, <xref:System.Windows.DragDrop.GiveFeedback> olay. Sürükleme kaynağı bu bilgileri bırakma hedefi veri amaçlayan etkisini kullanıcıya bildirmek için kullanır. Veri bırakıldığında bırakma hedefi gerçek etkisini belirtir <xref:System.Windows.DragDrop.Drop> olay. Bilgi sürükleme kaynağı için geri dönüş değeri olarak geçirilir <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemi. Bırakma hedefi sürükleme kaynakları listesinde değil efekt döndürürse `allowedEffects`, gerçekleşen herhangi bir veri aktarımı sürükle ve bırak işlemi iptal edildi.  
  
 İçinde unutulmaması önemlidir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.DragDropEffects> değerler yalnızca ilgili sürükle ve bırak işlemi etkilerini bırakma hedefi sürükleme kaynağı arasındaki iletişimi sağlamak amacıyla kullanılır. Sürükle ve bırak işlemi gerçek etkisini, uygulamanıza uygun kod yazmanızı bağlıdır.  
  
 Örneğin, bırakma hedefi, verileri taşımak için veri bırakmadan etkisini olduğunu belirtebilir. Ancak, verileri taşımak için hem hedef öğesine eklenen ve gerekir kaynak öğeden kaldırılır. Kaynak öğesi, verilerin taşınması sağlar, ancak veri kaynağı öğesinden kaldırmak için kodu belirtmezseniz, sonuç verileri kopyalanır ve taşınmadı olduğunu olacaktır gösterebilir.  
  
<a name="Drag_and_Drop_Events"></a>   
## <a name="drag-and-drop-events"></a>Sürükle ve bırak olayları  
 Sürükle ve bırak işlemleri, olay odaklı modeli destekler.  Sürükleme kaynağı hem de bırakma hedefi sürükle ve bırak işlemleri işlemek için standart bir etkinlik kümesi kullanın.  Aşağıdaki tablolarda, standart sürükle ve bırak olayları özetlenmektedir. Ekli olaylar üzerinde bunlar <xref:System.Windows.DragDrop> sınıfı. Ekli olaylar hakkında daha fazla bilgi için bkz. [iliştirilmiş olaylara genel bakış](attached-events-overview.md).  
  
### <a name="drag-source-events"></a>Sürükleme kaynağı olayları  
  
|Olay|Özet|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.GiveFeedback>|Bu olay, sürekli bir Sürükle ve bırak işlemi sırasında oluşur ve kullanıcıya geri bildirim bilgilerini vermek bırakma kaynağı sağlar. Bu geri bildirim genellikle fare işaretçisi görünümünü değiştirerek bırakma hedefi izin verilen efektleri belirtmek için verilir.  Tırmanma olay budur.|  
|<xref:System.Windows.DragDrop.QueryContinueDrag>|Bu olay bir değişiklik klavye veya fare düğmesi bir Sürükle ve bırak işlemi sırasında durumları ve anahtar/düğme durumları bağlı olarak sürükle ve bırak işlemini iptal etmek bırakma kaynağı sağlar oluşur. Tırmanma olay budur.|  
|<xref:System.Windows.DragDrop.PreviewGiveFeedback>|Tünel sürümünü <xref:System.Windows.DragDrop.GiveFeedback>.|  
|<xref:System.Windows.DragDrop.PreviewQueryContinueDrag>|Tünel sürümünü <xref:System.Windows.DragDrop.QueryContinueDrag>.|  
  
### <a name="drop-target-events"></a>Bırakma hedefi olayları  
  
|Olay|Özet|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.DragEnter>|Bu olay, bir nesne açılan hedefinin sınırları içine sürüklendiğinde oluşur. Tırmanma olay budur.|  
|<xref:System.Windows.DragDrop.DragLeave>|Bu olay, bir nesne dışında bırakma hedefinin sınır sürüklendiğinde oluşur.  Tırmanma olay budur.|  
|<xref:System.Windows.DragDrop.DragOver>|Bu olay, sürekli olarak bir nesne (taşınan) bırakma hedefinin sınırları içinde sürüklediğiniz sırada gerçekleşir. Tırmanma olay budur.|  
|<xref:System.Windows.DragDrop.Drop>|Bu olay, bir nesne üzerinde bırakma hedefi bırakıldığında gerçekleşir.  Tırmanma olay budur.|  
|<xref:System.Windows.DragDrop.PreviewDragEnter>|Tünel sürümünü <xref:System.Windows.DragDrop.DragEnter>.|  
|<xref:System.Windows.DragDrop.PreviewDragLeave>|Tünel sürümünü <xref:System.Windows.DragDrop.DragLeave>.|  
|<xref:System.Windows.DragDrop.PreviewDragOver>|Tünel sürümünü <xref:System.Windows.DragDrop.DragOver>.|  
|<xref:System.Windows.DragDrop.PreviewDrop>|Tünel sürümünü <xref:System.Windows.DragDrop.Drop>.|  
  
 Sürükle ve bırak olayları işlemek için bir nesnenin örneklerini eklemek için yukarıdaki tablolarda listelenen olayları için işleyiciler. Üzerinde sanal karşılık gelen Sınıf düzeyinde sürükle ve bırak olayları işlemek için geçersiz kılma * olay ve\*PreviewEvent yöntemleri. Daha fazla bilgi için [sınıfı işleme yönlendirilmiş olay denetim temel sınıfları tarafından](marking-routed-events-as-handled-and-class-handling.md#Class_Handling_of_Routed_Events).  
  
<a name="Implementing_Drag_And_Drop"></a>   
## <a name="implementing-drag-and-drop"></a>Sürükle ve bırak uygulama  
 Bir kullanıcı Arabirimi öğesi sürükleme kaynağı, bir bırakma hedefi veya her ikisi de olabilir. Basit sürükle ve bırak uygulamak için sürükle ve bırak işlemi başlatmak için ve bırakılan veri işlemek için kod yazın. İsteğe bağlı sürükle ve bırak olayları işleme tarafından sürükle ve bırak deneyimini geliştirebilir.  
  
 Basit sürükle ve bırak uygulamak için aşağıdaki görevleri tamamlar:  
  
-   Bir sürükleme kaynağı olacak öğe belirleyin. Bir sürükleme kaynağı olabilir bir <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement>.  
  
-   Bir olay işleyicisi, sürükle ve bırak işlemi başlatacak sürükleme kaynağı oluşturun. Genellikle olaydır <xref:System.Windows.UIElement.MouseMove> olay.  
  
-   Sürükleme kaynağı olay işleyicisi çağırma <xref:System.Windows.DragDrop.DoDragDrop%2A> sürükle ve bırak işlemi başlatmak için yöntem. İçinde <xref:System.Windows.DragDrop.DoDragDrop%2A> çağrı, sürükleme kaynağı, aktarılacak veriler ve izin verilen efektleri belirtin.  
  
-   Bir bırakma hedefi olacak öğesini belirleyin. Bir bırakma hedefi olarak <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement>.  
  
-   Bırakma hedefi üzerinde ayarlanmış <xref:System.Windows.UIElement.AllowDrop%2A> özelliğini `true`.  
  
-   Bırakma hedefi oluşturma bir <xref:System.Windows.DragDrop.Drop> bırakılan veri işlemek için olay işleyicisi.  
  
-   İçinde <xref:System.Windows.DragDrop.Drop> olay işleyicisi, verileri ayıklamayı <xref:System.Windows.DragEventArgs> kullanarak <xref:System.Windows.DataObject.GetDataPresent%2A> ve <xref:System.Windows.DataObject.GetData%2A> yöntemleri.  
  
-   İçinde <xref:System.Windows.DragDrop.Drop> olay işleyicisi, istenen sürükle ve bırak işlemi gerçekleştirmek için verileri kullanın.  
  
 Sürükle ve bırak uygulamanıza özel bir oluşturarak artırabileceğinizi <xref:System.Windows.DataObject> ve işleme isteğe bağlı kaynak ve bırakma hedefi olayları, aşağıdaki görevleri gösterildiği sürükleyin:  
  
-   Özel veri veya birden çok veri öğeleri aktarmak için oluşturun bir <xref:System.Windows.DataObject> geçirilecek <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemi.  
  
-   Bir sürükleme sırasında ek işlemleri gerçekleştirmek için tanıtıcı <xref:System.Windows.DragDrop.DragEnter>, <xref:System.Windows.DragDrop.DragOver>, ve <xref:System.Windows.DragDrop.DragLeave> bırakma hedefi olayları.  
  
-   Fare işaretçisi görünümünü değiştirmek için tanıtıcı <xref:System.Windows.DragDrop.GiveFeedback> sürükleme kaynağı olayı.  
  
-   Sürükle ve bırak işleminin iptal nasıl değiştirileceğini işlemek <xref:System.Windows.DragDrop.QueryContinueDrag> sürükleme kaynağı olayı.  
  
<a name="Drag_And_Drop_Example"></a>   
## <a name="drag-and-drop-example"></a>Sürükle ve bırak örnek  
 Bu bölümde, sürükle ve bırak için uygulanacak açıklar bir <xref:System.Windows.Shapes.Ellipse> öğesi. <xref:System.Windows.Shapes.Ellipse> Sürükleme kaynağı hem de bir bırakma hedefi. Elips'ın dize gösterimini aktarılan verileri olduğu <xref:System.Windows.Shapes.Shape.Fill%2A> özelliği. Aşağıdaki XAML gösterildiği <xref:System.Windows.Shapes.Ellipse> öğesini ve bunu işleyen sürükle ve bırak ilgili olaylar. Sürükle ve bırak uygulama konusunda tam adımlar için bkz: [izlenecek yol: Etkinleştirme sürükle ve bırak kullanıcı denetiminde](walkthrough-enabling-drag-and-drop-on-a-user-control.md).  
  
 [!code-xaml[DragDropSnippets#EllipseXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#ellipsexaml)]  
  
### <a name="enabling-an-element-to-be-a-drag-source"></a>Bir sürükleme kaynağı olarak bir öğeyi etkinleştirme  
 Bir sürükleme kaynağı olan bir nesne için sorumludur:  
  
-   Bir sürükleme oluştuğunda tanımlayıcı.  
  
-   Sürükle ve bırak işlemi başlatılıyor.  
  
-   Verilerin aktarılması için tanımlayıcı.  
  
-   Sürükle ve bırak işlemi aktarılan veriler için izin verilen efektleri belirtme.  
  
 Sürükleme kaynağı, kullanıcıya izin verilen eylemleri ile ilgili geri bildirim de verebilir (taşıyın, kopyalayın, none) ve sürükleme sırasında ESC tuşuna basarak gibi ek kullanıcı girişini dayalı sürükle ve bırak işlemini iptal edebilirsiniz.  
  
 Bir sürükleme ne zaman gerçekleştiğini belirlemek için uygulamanızı ve başlatma sürükle ve bırak işlemi çağırarak sorumluluğundadır <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemi. Bu ne zaman genellikle bir <xref:System.Windows.UIElement.MouseMove> olay öğenin fare düğmesini basılı durumdayken sürüklenmesi için gerçekleşir. Aşağıdaki örnek, bir Sürükle ve bırak işlemi başlatmak gösterilmektedir <xref:System.Windows.UIElement.MouseMove> olay işleyicisinde bir <xref:System.Windows.Shapes.Ellipse> sürükleme kaynağı yapmak için öğesi. Elips'ın dize gösterimini aktarılan verileri olduğu <xref:System.Windows.Shapes.Shape.Fill%2A> özelliği.  
  
 [!code-csharp[DragDropSnippets#DoDragDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dodragdrop)]
 [!code-vb[DragDropSnippets#DoDragDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dodragdrop)]  
  
 İçine <xref:System.Windows.UIElement.MouseMove> olay işleyicisi, çağrı <xref:System.Windows.DragDrop.DoDragDrop%2A> sürükle ve bırak işlemi başlatmak için yöntem. <xref:System.Windows.DragDrop.DoDragDrop%2A> Yöntemi üç parametreleri alır:  
  
-   `dragSource` – Aktarılan verileri kaynak bağımlılık nesnesi bir başvuru; Bu genellikle kaynağıdır <xref:System.Windows.UIElement.MouseMove> olay.  
  
-   `data` -İçinde sarmalanmış aktarılan verileri içeren bir nesne bir <xref:System.Windows.DataObject>.  
  
-   `allowedEffects` -Biri <xref:System.Windows.DragDropEffects> sürükle ve bırak işlemi izin verilen etkilerini belirten numaralandırma değerlerinden.  
  
 Herhangi bir seri hale getirilebilir nesne geçirilebilir `data` parametresi. Varsa, verileri önceden sarmalanmamış bir <xref:System.Windows.DataObject>, bunu otomatik olarak yeni bir sarmalanır <xref:System.Windows.DataObject>. Birden çok veri öğelerini geçirmek için oluşturmalısınız <xref:System.Windows.DataObject> kendiniz ve geçirin <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemi. Daha fazla bilgi için [veri ve veri nesneleri](data-and-data-objects.md).  
  
 `allowedEffects` Parametresi ne bırakma hedefi, aktarılan verileri ile yapmak sürükleme kaynağı sağlayacak belirtmek için kullanılır. Bir sürükleme kaynağı ortak değerleri <xref:System.Windows.DragDropEffects.Copy>, <xref:System.Windows.DragDropEffects.Move>, ve <xref:System.Windows.DragDropEffects.All>.  
  
> [!NOTE]
>  Bırakma hedefi, düşünüyor hangi etkileri yanıt bırakılan veri olarak belirtebilirsiniz. Bırakma hedefi bırakılan veri türünü tanımıyor, örneğin, bu veri, izin verilen efektleri ayarlayarak reddedebilir <xref:System.Windows.DragDropEffects.None>. Genellikle bunu yapar kendi <xref:System.Windows.DragDrop.DragOver> olay işleyicisi.  
  
 Bir sürükleme kaynağı isteğe bağlı olarak işleyebilir <xref:System.Windows.DragDrop.GiveFeedback> ve <xref:System.Windows.DragDrop.QueryContinueDrag> olayları. Bu olaylar, olayları işlenmiş olarak işaretleme sürece kullanılan varsayılan işleyicileri vardır. Kendi varsayılan davranışı değiştirmek için belirli bir gereksiniminiz olmadığı sürece genellikle bu olayları göz ardı eder.  
  
 <xref:System.Windows.DragDrop.GiveFeedback> Sürükleme kaynağı sürekli olarak sürüklenen sırada olayı oluşturulur. Bu olay için varsayılan işleyici sürükleme kaynağı üzerinde geçerli bırakma hedefi olup olmadığını denetler. Bu durumda, izin verilen bir bırakma hedefi etkilerini denetler. Ardından son kullanıcılara doğrudan izin verilen efektleri ile ilgili geri bildirim sağlar. Bu, genellikle bir bırakma için kopyalama, fare imlecini değiştirerek gerçekleştirilir veya imleci taşıma. Kullanıcıya geri bildirim sağlamak için özel işaretçiler kullanmanız gerekiyorsa yalnızca bu olay işlemesi gerekir. Bu olayı işleyin, böylece varsayılan işleyici işleyicinizi kılmaz işlenmiş olarak işaretleme emin olun.  
  
 <xref:System.Windows.DragDrop.QueryContinueDrag> Sürükleme kaynağı sürekli olarak sürüklenen sırada olayı oluşturulur. Hangi eylemin ESC, kaydırma, CTRL ve ALT anahtarları durumunu hem de farenin düğme durumunu dayalı sürükle ve bırak işlemi sonlandırır belirlemek için bu olay işleyebilir. ESC tuşuna basıldığında ve veri fare düğmesini serbest bıraktığı varsayılan işleyicisi bu olayı için sürükle ve bırak işleminin iptal eder.  
  
> [!CAUTION]
>  Bu olaylar sürükle ve bırak işlemi sırasında sürekli olarak oluşturulur. Bu nedenle, olay işleyicilerinde kaynak kullanımlı görevler kaçınmanız gerekir.  Örneğin, her seferinde yeni bir imleç oluşturmak yerine önbelleğe alınmış bir imleç kullanır <xref:System.Windows.DragDrop.GiveFeedback> olayı oluşturulur.  
  
### <a name="enabling-an-element-to-be-a-drop-target"></a>Bir bırakma hedefi olarak bir öğeyi etkinleştirme  
 Bir bırakma hedefi olan nesne için sorumludur:  
  
-   Geçerli bırakma hedefi olduğunu belirleme.  
  
-   Hedef sürüklediğinde Sürükle kaynağına yanıt.  
  
-   Aktarılan veriler alabileceği bir biçimde olup olmadığını denetleyerek.  
  
-   Bırakılan veri işleme.  
  
 Bir bırakma hedefi bir öğedir, ayarladığınız belirtmek için kendi <xref:System.Windows.UIElement.AllowDrop%2A> özelliğini `true`. Bırakma hedefi olayları, sonra bunları işleyebilmesi öğede gerçekleştirilecektir. Bir Sürükle ve bırak işlemi sırasında bırakma hedefi üzerinde aşağıdaki olaylar dizisi gerçekleşir:  
  
1. <xref:System.Windows.DragDrop.DragEnter>  
  
2. <xref:System.Windows.DragDrop.DragOver>  
  
3. <xref:System.Windows.DragDrop.DragLeave> veya <xref:System.Windows.DragDrop.Drop>  
  
 <xref:System.Windows.DragDrop.DragEnter> Olay verileri bırakma hedefinin sınırları içine sürüklendiğinde oluşur. Uygulamanız için uygunsa genellikle sürükle ve bırak işleminin etkilerini önizlemesini sağlamak için bu olayı işleyin. Ayarlı değil <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> özelliğinde <xref:System.Windows.DragDrop.DragEnter> haliyle bir olay yazılır <xref:System.Windows.DragDrop.DragOver> olay.  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Windows.DragDrop.DragEnter> için olay işleyicisi bir <xref:System.Windows.Shapes.Ellipse> öğesi. Bu kod, geçerli kaydederek sürükle ve bırak işlemi etkilerini önizleme <xref:System.Windows.Shapes.Shape.Fill%2A> fırça. Ardından kullanır <xref:System.Windows.DataObject.GetDataPresent%2A> denetlenecek yöntemi olup olmadığını <xref:System.Windows.DataObject> elipsin sürüklenen dönüştürülebilir dize verileri içeren bir <xref:System.Windows.Media.Brush>. Bu nedenle, verileri kullanarak ayıklanan, <xref:System.Windows.DataObject.GetData%2A> yöntemi. Ardından dönüştürülür bir <xref:System.Windows.Media.Brush> ve üç nokta için uygulanır. Değişikliği de geri <xref:System.Windows.DragDrop.DragLeave> olay işleyicisi. Veriler için döndürülemezse bir <xref:System.Windows.Media.Brush>, hiçbir eylem gerçekleştirilmedi.  
  
 [!code-csharp[DragDropSnippets#DragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragenter)]
 [!code-vb[DragDropSnippets#DragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragenter)]  
  
 <xref:System.Windows.DragDrop.DragOver> Olay verileri bırakma hedefi üzerinde sürekli olarak sürüklediğiniz sırada gerçekleşir. Bu olay ile eşleştirilmiş <xref:System.Windows.DragDrop.GiveFeedback> sürükleme kaynağı olayı. İçinde <xref:System.Windows.DragDrop.DragOver> olay işleyicisi, genellikle kullandığınız <xref:System.Windows.DataObject.GetDataPresent%2A> ve <xref:System.Windows.DataObject.GetData%2A> aktarılan verileri bırakma hedefi işleyebilen bir biçimde olup olmadığını denetlemek için yöntemleri. Ayrıca, tüm değiştirici tuşları, hangi kullanıcının bir kopyalama veya taşıma eylemi düşünüyor olmadığını genellikle gösterecektir basıldığında olup olmadığını kontrol edebilirsiniz. Bu denetimleri yapıldıktan sonra ayarladığınız <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> source özelliği sürükleme bildirmek için veri bırakma hangi etkisi olmaz. Bu bilgileri sürükleme kaynağı alır <xref:System.Windows.DragDrop.GiveFeedback> event args ve kullanıcıya geri bildirim sağlamak için uygun bir imleç ayarlayabilirsiniz.  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Windows.DragDrop.DragOver> için olay işleyicisi bir <xref:System.Windows.Shapes.Ellipse> öğesi. Bu kod olup olmadığını denetler. <xref:System.Windows.DataObject> elipsin sürüklenen dönüştürülebilir dize verileri içeren bir <xref:System.Windows.Media.Brush>. Bu nedenle, bunu ayarlarsa <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> özelliğini <xref:System.Windows.DragDropEffects.Copy>. Bu veriler için üç nokta kopyalanabilir için sürükleme kaynağı belirtir. Veriler için döndürülemezse bir <xref:System.Windows.Media.Brush>, <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> özelliği <xref:System.Windows.DragDropEffects.None>. Bu işlem için sürükleme kaynağı elips verileri geçerli bırakma hedefi değil gösterir.  
  
 [!code-csharp[DragDropSnippets#DragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragover)]
 [!code-vb[DragDropSnippets#DragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragover)]  
  
 <xref:System.Windows.DragDrop.DragLeave> Olay verileri hedefin sınırları dışında bırakılan olmadan sürüklendiğinde oluşur. Yaptığınız herhangi bir şeyi geri almak için bu olayı işleyin <xref:System.Windows.DragDrop.DragEnter> olay işleyicisi.  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Windows.DragDrop.DragLeave> için olay işleyicisi bir <xref:System.Windows.Shapes.Ellipse> öğesi. Bu kod önizlemeyi gerçekleştirilen alır <xref:System.Windows.DragDrop.DragEnter> kaydedilen uygulayarak olay işleyicisi <xref:System.Windows.Media.Brush> elipsin için.  
  
 [!code-csharp[DragDropSnippets#DragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragleave)]
 [!code-vb[DragDropSnippets#DragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragleave)]  
  
 <xref:System.Windows.DragDrop.Drop> Olay verileri bırakma hedefi üzerinde bırakıldığında gerçekleşir; varsayılan olarak, bu fare düğmesi bırakıldığında gerçekleşir. İçinde <xref:System.Windows.DragDrop.Drop> olay işleyicisi, kullandığınız <xref:System.Windows.DataObject.GetData%2A> aktarılan verilerin ayıklanacağı yöntemi <xref:System.Windows.DataObject> ve uygulamanızın gerektirdiği herhangi bir veri işlemi gerçekleştirin. <xref:System.Windows.DragDrop.Drop> Olayı, sürükle ve bırak işlemi sonlandırır.  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Windows.DragDrop.Drop> için olay işleyicisi bir <xref:System.Windows.Shapes.Ellipse> öğesi. Bu kod, sürükle ve bırak işlemi etkilerini uygular ve kodda benzer <xref:System.Windows.DragDrop.DragEnter> olay işleyicisi. Olup olmadığını denetler <xref:System.Windows.DataObject> elipsin sürüklenen dönüştürülebilir dize verileri içeren bir <xref:System.Windows.Media.Brush>. Bu durumda, <xref:System.Windows.Media.Brush> elipsin için uygulanır. Veriler için döndürülemezse bir <xref:System.Windows.Media.Brush>, hiçbir eylem gerçekleştirilmedi.  
  
 [!code-csharp[DragDropSnippets#Drop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#drop)]
 [!code-vb[DragDropSnippets#Drop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#drop)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Clipboard>
- [İzlenecek yol: Kullanıcı Denetiminde Sürükleme ve Bırakmayı Etkinleştirme](walkthrough-enabling-drag-and-drop-on-a-user-control.md)
- [Nasıl Yapılır Konuları](drag-and-drop-how-to-topics.md)
- [Sürükleme ve Bırakma](drag-and-drop.md)
