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
ms.openlocfilehash: e8e8b294e05579a91a4557b23be6c65f4d619167
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940875"
---
# <a name="drag-and-drop-overview"></a>Sürükleme ve Bırakmaya Genel Bakış
Bu konu, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalarda sürükle ve bırak desteğine genel bir bakış sağlar. Sürükleyip bırakma genellikle bir veya daha fazla nesne seçmek için fare (veya başka bir işaret aygıtı) kullanan bir veri aktarımı yöntemine başvurur ve bu nesneleri, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]içindeki belirli bir bırakma hedefi üzerine sürükleyip bırakarak bunları bırakabilir.  

<a name="Drag_and_Drop_Support"></a>   
## <a name="drag-and-drop-support-in-wpf"></a>WPF 'de sürükle ve bırak desteği  
 Sürükle ve bırak işlemleri genellikle iki taraf içerir: sürüklenen nesnenin kaynaklandığı Sürükle kaynağı ve bırakılan nesneyi alan bir bırakma hedefi.  Sürükle kaynağı ve bırakma hedefi, aynı uygulamadaki veya farklı bir uygulamadaki UI öğeleri olabilir.  
  
 Sürükle ve bırak ile işlenebilen nesnelerin türü ve sayısı tamamen rasgele olur. Örneğin, dosyalar, klasörler ve içerik seçimleri, sürükle ve bırak işlemleri aracılığıyla daha yaygın olarak kullanılan nesnelerden bazılarıdır.  
  
 Bir sürükle ve bırak işlemi sırasında gerçekleştirilen belirli eylemler uygulamaya özgüdür ve genellikle bağlam tarafından belirlenir.  Örneğin, aynı depolama cihazında bir klasörden diğerine dosya seçimini sürüklemek, dosyaları varsayılan olarak taşırken, dosyaları bir [!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)] paylaşımdan yerel bir klasöre sürüklemek, dosyaları varsayılan olarak kopyalar.  
  
 Tarafından [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sunulan sürükle ve bırak olanakları, çok çeşitli sürükle ve bırak senaryolarını destekleyecek şekilde oldukça esnek ve özelleştirilebilir olacak şekilde tasarlanmıştır.  Sürükle ve bırak, nesneleri tek bir uygulama içinde veya farklı uygulamalar arasında düzenleme destekler. Uygulamalar ve diğer Windows uygulamaları arasında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sürükleme ve bırakma de tam olarak desteklenmektedir.  
  
 ' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]De, <xref:System.Windows.UIElement> herhangi <xref:System.Windows.ContentElement> bir veya sürükleyip bırakmaya katılabilir. Sürükle ve bırak işlemleri için gereken olaylar ve yöntemler <xref:System.Windows.DragDrop> sınıfında tanımlanır. Ve <xref:System.Windows.UIElement> sınıfları,<xref:System.Windows.UIElement> bir veya temelöğeolarakDevralındığızaman,olaylarınsınıfüyelerilistesindegörünmesiiçin,ekliolaylarındiğeradlarınıiçerir.<xref:System.Windows.ContentElement> <xref:System.Windows.DragDrop> <xref:System.Windows.ContentElement> Bu olaylara eklenen olay işleyicileri, temel alınan <xref:System.Windows.DragDrop> ekli olaya iliştirilir ve aynı olay veri örneğini alır. Daha fazla bilgi için, <xref:System.Windows.UIElement.Drop?displayProperty=nameWithType> olayına bakın.  
  
> [!IMPORTANT]
> OLE sürükle ve bırak Internet bölgesinde çalışırken çalışmaz.  
  
<a name="Data_Transfer"></a>   
## <a name="data-transfer"></a>Veri Aktarımı  
 Sürükle ve bırak, veri aktarımının daha genel alanının bir parçasıdır. Veri aktarımı sürükle ve bırak ile kopyalama ve yapıştırma işlemlerini içerir. Bir sürükle ve bırak işlemi, sistem panosunu kullanarak bir nesneden veya uygulamadan diğerine veri aktarmak için kullanılan bir kopyalama ve yapıştırma ya da kesme ve yapıştırma işlemine benzer. Her iki tür işlem şunları gerektirir:  
  
- Verileri sağlayan kaynak nesne.  
  
- Aktarılan verileri geçici olarak depolamanın bir yolu.  
  
- Verileri alan bir hedef nesne.  
  
 Bir Kopyala ve Yapıştır işleminde, sistem panosu, aktarılan verileri geçici olarak depolamak için kullanılır; sürükle ve bırak işleminde, <xref:System.Windows.DataObject> verileri depolamak için kullanılır. Kavramsal olarak, bir veri nesnesi, gerçek verileri içeren bir veya daha <xref:System.Object> fazla çiftinin ve karşılık gelen bir veri biçimi tanımlayıcısını kapsar.  
  
 Sürükleme kaynağı, statik <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> yöntemi çağırarak ve aktarılan verileri buna geçirerek bir sürükle ve bırak işlemi başlatır. Yöntemi, gerekirse verileri otomatik olarak bir <xref:System.Windows.DataObject> halinde saracaktır. <xref:System.Windows.DragDrop.DoDragDrop%2A> Veri biçimi üzerinde daha fazla denetim için, verileri <xref:System.Windows.DataObject> <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemine geçirmeden önce bir içinde sardırabilirsiniz. Bırakma hedefi, <xref:System.Windows.DataObject>öğesinden verilerin ayıklanmasından sorumludur. Veri nesneleriyle çalışma hakkında daha fazla bilgi için bkz. [veri ve veri nesneleri](data-and-data-objects.md).  
  
 Bir sürükle ve bırak işleminin kaynağı ve hedefi Kullanıcı arabirimi öğeleridir; Ancak, gerçekten aktarılmakta olan verilerin genellikle görsel temsili yoktur. Windows Gezgini 'nde dosyaları sürüklerken oluşan gibi sürüklenen verilerin görsel bir gösterimini sağlamak için kod yazabilirsiniz. Varsayılan olarak, imleç sürükle ve bırak işleminin veriler üzerinde sahip olacağı etkiyi (verilerin taşınıp taşınacağını veya kopyalanmayacağı gibi) belirtecek şekilde değiştirerek kullanıcıya geri bildirim verilir.  
  
### <a name="drag-and-drop-effects"></a>Sürükle ve bırak efektleri  
 Sürükle ve bırak işlemlerinin, aktarılan veriler üzerinde farklı etkileri olabilir. Örneğin, verileri kopyalayabilir veya verileri taşıyabilirsiniz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]bir sürükle <xref:System.Windows.DragDropEffects> ve bırak işleminin etkisini belirtmek için kullanabileceğiniz bir sabit listesi tanımlar. Sürükleme kaynağında, kaynağın <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemde izin verolacağı etkileri belirtebilirsiniz. Bırakma hedefinde, hedefin <xref:System.Windows.DragEventArgs.Effects%2A> <xref:System.Windows.DragEventArgs> sınıfının özelliğinde amaçladığı etkiyi belirtebilirsiniz. Bırakma hedefi, <xref:System.Windows.DragDrop.DragOver> olaydaki amaçlanan etkisini belirttiğinde, bu bilgiler <xref:System.Windows.DragDrop.GiveFeedback> olaydaki sürükleme kaynağına geri geçirilir. Sürükleme kaynağı bu bilgileri kullanıcıya, bırakma hedefinin verileri ne kadar etkili olduğunu bildirmek için kullanır. Veriler bırakıldığında bırakma hedefi, <xref:System.Windows.DragDrop.Drop> olayda gerçek etkisini belirtir. Bu bilgiler, <xref:System.Windows.DragDrop.DoDragDrop%2A> metodun dönüş değeri olarak sürükle kaynağına geçirilir. Bırakma hedefi, sürükle kaynakları listesinde `allowedEffects`olmayan bir efekt döndürürse, sürükle ve bırak işlemi herhangi bir veri aktarımı yapılmaksızın iptal edilir.  
  
 ' De [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.DragDropEffects> , değerleri yalnızca sürükle ve bırak işleminin etkileri ile ilgili sürükleme kaynağı ve bırakma hedefi arasında iletişim sağlamak için kullanıldığını unutmayın. Sürükle ve bırak işleminin gerçek etkisi, uygulamanıza uygun kodu yazmak için size bağlıdır.  
  
 Örneğin, bırakma hedefi, verileri bırakma efektinin verileri taşımakta olduğunu belirtebilir. Ancak, verileri taşımak için hem hedef öğeye eklenmeli hem de kaynak öğeden kaldırılacak olması gerekir. Kaynak öğe, verilerin taşınmasına izin verdiğini belirtebilir, ancak kaynak öğeden verileri kaldırmak için kod sağlamazsanız, nihai sonuç verilerin kopyalanmasının ve taşınmayacağı anlamına gelir.  
  
<a name="Drag_and_Drop_Events"></a>   
## <a name="drag-and-drop-events"></a>Sürükle ve bırak olayları  
 Sürükle ve bırak işlemleri olay temelli bir modeli destekler.  Sürükleme kaynağı ve bırakma hedefi, sürükle ve bırak işlemlerini işlemek için standart bir olay kümesi kullanır.  Aşağıdaki tablolar, standart Sürükle ve bırak olaylarını özetler. Bunlar, <xref:System.Windows.DragDrop> sınıfındaki ekli olaylardır. Ekli olaylar hakkında daha fazla bilgi için bkz. [ekli olaylara genel bakış](attached-events-overview.md).  
  
### <a name="drag-source-events"></a>Kaynak olaylarını sürükle  
  
|Olay|Özet|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.GiveFeedback>|Bu olay bir sürükle ve bırak işlemi sırasında sürekli gerçekleşir ve bırakma kaynağının kullanıcıya geri bildirim bilgileri vermesini sağlar. Bu geri bildirim genellikle, bırakma hedefinin izin verdiği etkileri göstermek üzere fare işaretçisinin görünümü değiştirilerek verilir.  Bu bir kabarcıklanma olayıdır.|  
|<xref:System.Windows.DragDrop.QueryContinueDrag>|Bu olay, sürükle ve bırak işlemi sırasında klavyede veya fare düğmesi durumunda olduğunda meydana gelir ve bırakma kaynağının anahtar/düğme durumlarına bağlı olarak sürükle ve bırak işlemini iptal etmesini sağlar. Bu bir kabarcıklanma olayıdır.|  
|<xref:System.Windows.DragDrop.PreviewGiveFeedback>|Tünel oluşturma sürümü <xref:System.Windows.DragDrop.GiveFeedback>.|  
|<xref:System.Windows.DragDrop.PreviewQueryContinueDrag>|Tünel oluşturma sürümü <xref:System.Windows.DragDrop.QueryContinueDrag>.|  
  
### <a name="drop-target-events"></a>Bırakma hedefi olayları  
  
|Olay|Özet|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.DragEnter>|Bu olay, bir nesne bırakma hedefinin sınırına sürüklendiğinde oluşur. Bu bir kabarcıklanma olayıdır.|  
|<xref:System.Windows.DragDrop.DragLeave>|Bu olay, bir nesne bırakma hedefinin sınırının dışına sürüklendiğinde oluşur.  Bu bir kabarcıklanma olayıdır.|  
|<xref:System.Windows.DragDrop.DragOver>|Bu olay, bırakma hedefinin sınırının içinde bir nesne sürüklendiğinde (taşındığında) sürekli gerçekleşir. Bu bir kabarcıklanma olayıdır.|  
|<xref:System.Windows.DragDrop.Drop>|Bu olay bırakma hedefinde bir nesne bırakıldığında oluşur.  Bu bir kabarcıklanma olayıdır.|  
|<xref:System.Windows.DragDrop.PreviewDragEnter>|Tünel oluşturma sürümü <xref:System.Windows.DragDrop.DragEnter>.|  
|<xref:System.Windows.DragDrop.PreviewDragLeave>|Tünel oluşturma sürümü <xref:System.Windows.DragDrop.DragLeave>.|  
|<xref:System.Windows.DragDrop.PreviewDragOver>|Tünel oluşturma sürümü <xref:System.Windows.DragDrop.DragOver>.|  
|<xref:System.Windows.DragDrop.PreviewDrop>|Tünel oluşturma sürümü <xref:System.Windows.DragDrop.Drop>.|  
  
 Bir nesnenin örnekleri için sürükle ve bırak olaylarını işlemek için, önceki tablolarda listelenen olaylara yönelik işleyiciler ekleyin. Sürükle ve bırak olaylarını sınıf düzeyinde işlemek için, karşılık gelen sanal on * olayını ve\*PreviewEvent yöntemlerini geçersiz kılın. Daha fazla bilgi için bkz. [temel sınıfları denetim aracılığıyla yönlendirilmiş olayların sınıf işlemesi](marking-routed-events-as-handled-and-class-handling.md#Class_Handling_of_Routed_Events).  
  
<a name="Implementing_Drag_And_Drop"></a>   
## <a name="implementing-drag-and-drop"></a>Sürükle ve bırak uygulama  
 Bir kullanıcı arabirimi öğesi, bir Sürükle kaynağı, bir bırakma hedefi veya her ikisi olabilir. Temel sürükle ve bırak uygulamak için sürükle ve bırak işlemini başlatmak ve bırakılan verileri işlemek için kod yazarsınız. Sürükleme ve bırakma deneyimini, isteğe bağlı sürükle ve bırak olaylarını işleyerek geliştirebilirsiniz.  
  
 Temel sürükle ve bırak uygulamak için aşağıdaki görevleri tamamlayacaksınız:  
  
- Sürükle kaynağı olacak öğeyi belirler. Sürükle kaynağı bir <xref:System.Windows.UIElement> veya bir <xref:System.Windows.ContentElement>olabilir.  
  
- Sürükleme kaynağında sürükle ve bırak işlemini başlatacak bir olay işleyicisi oluşturun. Olay genellikle <xref:System.Windows.UIElement.MouseMove> olaydır.  
  
- Sürükle ve bırak işlemini başlatmak için kaynak olay işleyicisindeki <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemi çağırın. <xref:System.Windows.DragDrop.DoDragDrop%2A> Çağrıda, Sürükle kaynağını, aktarılacak verileri ve izin verilen etkileri belirtin.  
  
- Bırakma hedefi olacak öğeyi belirler. Bırakma hedefi <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement>veya olabilir.  
  
- Bırakma hedefinde <xref:System.Windows.UIElement.AllowDrop%2A> özelliğini olarak `true`ayarlayın.  
  
- Bırakma hedefinde, bırakılan verileri işlemek için <xref:System.Windows.DragDrop.Drop> bir olay işleyicisi oluşturun.  
  
- Olay işleyicisinde, <xref:System.Windows.DataObject.GetDataPresent%2A> ve <xref:System.Windows.DragEventArgs> yöntemlerini<xref:System.Windows.DataObject.GetData%2A> kullanarak içindeki verileri ayıklayın. <xref:System.Windows.DragDrop.Drop>  
  
- <xref:System.Windows.DragDrop.Drop> Olay işleyicisinde, istenen sürükleme ve bırakma işlemini gerçekleştirmek için verileri kullanın.  
  
 Sürükle ve bırak uygulamanızı, aşağıdaki görevlerde gösterildiği gibi isteğe bağlı Sürükle kaynak ve <xref:System.Windows.DataObject> bırakma hedefi olaylarını işleyerek bir özel oluşturarak geliştirebilirsiniz:  
  
- Özel verileri veya birden çok veri öğesini aktarmak için, <xref:System.Windows.DataObject> <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemine geçirilecek bir oluşturun.  
  
- Sürükleme sırasında ek eylemler gerçekleştirmek için bırakma hedefinin <xref:System.Windows.DragDrop.DragEnter>, <xref:System.Windows.DragDrop.DragOver>ve <xref:System.Windows.DragDrop.DragLeave> olaylarını işleyin.  
  
- Fare işaretçisinin görünüşünü değiştirmek için sürükle kaynağındaki <xref:System.Windows.DragDrop.GiveFeedback> olayı işleyin.  
  
- Sürükle ve bırak işleminin nasıl iptal edildiğini değiştirmek için sürükle kaynağında <xref:System.Windows.DragDrop.QueryContinueDrag> olayı işleyin.  
  
<a name="Drag_And_Drop_Example"></a>   
## <a name="drag-and-drop-example"></a>Sürükle ve bırak örneği  
 Bu bölümde bir <xref:System.Windows.Shapes.Ellipse> öğesi için sürükle ve bırak 'ın nasıl uygulanacağı açıklanmaktadır. , <xref:System.Windows.Shapes.Ellipse> Bir Sürükle kaynağı ve bırakma hedefidir. Aktarılan veriler, elips <xref:System.Windows.Shapes.Shape.Fill%2A> özelliğinin dize gösterimidir. Aşağıdaki XAML, <xref:System.Windows.Shapes.Ellipse> öğesini ve işlediği, sürükle ve bırak ile ilgili olayları gösterir. Sürükleyip bırakmayı uygulama hakkında tam adımlar için bkz [. İzlenecek yol: Kullanıcı denetiminde](walkthrough-enabling-drag-and-drop-on-a-user-control.md)sürükle ve bırak etkinleştiriliyor.  
  
 [!code-xaml[DragDropSnippets#EllipseXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#ellipsexaml)]  
  
### <a name="enabling-an-element-to-be-a-drag-source"></a>Bir öğenin sürükle kaynağı olmasını sağlama  
 Sürükleme kaynağı olan bir nesne şu kaynaktan sorumludur:  
  
- Bir sürükleme işleminin ne zaman gerçekleşeceğini tanımlama.  
  
- Sürükle ve bırak işlemi başlatılıyor.  
  
- Aktarılacak verileri tanımlama.  
  
- Sürükle ve bırak işleminin aktarılan verilerde sahip olmasına izin verilen etkileri belirtme.  
  
 Sürükleme kaynağı, kullanıcıya izin verilen eylemlerle ilgili geri bildirimde bulunabilir (taşıma, kopyalama, yok) ve sürükleme sırasında ESC tuşuna basmak gibi, sürükle ve bırak işlemini ek kullanıcı girişine göre iptal edebilir.  
  
 Bu, bir sürükleme işleminin ne zaman gerçekleşeceğini tespit etmek ve sonra <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemi çağırarak Sürükle ve bırak işlemini başlatmak için uygulamanızın sorumluluğundadır. Genellikle, bu, fare düğmesine <xref:System.Windows.UIElement.MouseMove> basıldığında sürüklediğiniz öğe üzerinde bir olay meydana geldi. Aşağıdaki örnek, bir sürükleme kaynağı yapmak için bir <xref:System.Windows.UIElement.MouseMove> <xref:System.Windows.Shapes.Ellipse> öğenin olay işleyicisinden bir sürükle ve bırak işleminin nasıl başlatılacağı gösterilmektedir. Aktarılan veriler, elips <xref:System.Windows.Shapes.Shape.Fill%2A> özelliğinin dize gösterimidir.  
  
 [!code-csharp[DragDropSnippets#DoDragDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dodragdrop)]
 [!code-vb[DragDropSnippets#DoDragDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dodragdrop)]  
  
 Olay işleyicisinin içinde, sürükle ve bırak işlemini <xref:System.Windows.DragDrop.DoDragDrop%2A> başlatmak için yöntemini çağırın. <xref:System.Windows.UIElement.MouseMove> <xref:System.Windows.DragDrop.DoDragDrop%2A> Yöntemi üç parametre alır:  
  
- `dragSource`– Aktarılan verilerin kaynağı olan Dependency nesnesine bir başvuru; Bu genellikle <xref:System.Windows.UIElement.MouseMove> olayın kaynağıdır.  
  
- `data`-İçinde <xref:System.Windows.DataObject>kaydırılan, aktarılan verileri içeren bir nesne.  
  
- `allowedEffects`-Sürükle ve bırak <xref:System.Windows.DragDropEffects> işleminin izin verilen etkilerini belirten sabit listesi değerlerinden biri.  
  
 Seri hale getirilebilir herhangi bir nesne `data` parametreye geçirilebilir. Veriler henüz bir <xref:System.Windows.DataObject>içinde sarmalanmamış ise, otomatik olarak yeni <xref:System.Windows.DataObject>bir ile sarmalanır. Birden çok veri öğesi geçirmek için <xref:System.Windows.DataObject> kendiniz oluşturmanız ve <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemine geçirmeniz gerekir. Daha fazla bilgi için bkz. [veri ve veri nesneleri](data-and-data-objects.md).  
  
 Bu `allowedEffects` parametre, sürükleme kaynağının, aktarılan verilerle birlikte bırakma hedefinin ne izin verbileceklerini belirtmek için kullanılır. Bir sürükleme kaynağı için ortak değerler, <xref:System.Windows.DragDropEffects.Copy> <xref:System.Windows.DragDropEffects.Move>ve <xref:System.Windows.DragDropEffects.All>' dir.  
  
> [!NOTE]
> Bırakma hedefi, bırakılan verilere yanıt olarak hangi etkileri amaçladığı de belirtebilir. Örneğin, bırakma hedefi bırakılacak veri türünü tanımazsa, izin verilen etkileri olarak <xref:System.Windows.DragDropEffects.None>ayarlayarak verileri reddedebilirler. Genellikle bunu <xref:System.Windows.DragDrop.DragOver> olay işleyicide yapar.  
  
 Sürükleme kaynağı isteğe bağlı olarak <xref:System.Windows.DragDrop.GiveFeedback> ve <xref:System.Windows.DragDrop.QueryContinueDrag> olaylarını işleyebilir. Olayları işlenmiş olarak işaretlemediğiniz sürece bu olayların varsayılan işleyicileri kullanılır. Genellikle bu olayları, varsayılan davranışlarını değiştirmek için özel bir işlem yapmanız gerekmedikçe yoksayabilirsiniz.  
  
 Sürükleme kaynağı sürüklenirken olay sürekli olarak getirilir. <xref:System.Windows.DragDrop.GiveFeedback> Bu olay için varsayılan işleyici, sürükleme kaynağının geçerli bir bırakma hedefi üzerinde olup olmadığını denetler. Varsa, bırakma hedefinin izin verilen efektlerini denetler. Daha sonra, izin verilen bırakma efektleriyle ilgili olarak son kullanıcıya geri bildirim sağlar. Bu, genellikle fare imlecini bırakma, kopyalama veya taşıma imlecine göre değiştirilerek yapılır. Yalnızca kullanıcıya geri bildirim sağlamak için özel imleçler kullanmanız gerekiyorsa bu olayı işlemeniz gerekir. Bu olayı idare ederseniz, varsayılan işleyicinin işleyicinizi geçersiz kılmaması için, onu işlenmiş olarak işaretlediğinizden emin olun.  
  
 Sürükleme kaynağı sürüklenirken olay sürekli olarak getirilir. <xref:System.Windows.DragDrop.QueryContinueDrag> Bu olayı, sürükle ve bırak işlemini ESC, SHIFT, CTRL ve ALT tuşlarının yanı sıra fare düğmelerinin durumunu temel alarak hangi eylemin bittiğini belirlemek için işleyebilirsiniz. Bu olay için varsayılan işleyici, ESC tuşuna basıldığında sürükle ve bırak işlemini iptal eder ve fare düğmesi serbest bırakıldığında verileri bırakır.  
  
> [!CAUTION]
>  Bu olaylar, sürükle ve bırak işlemi sırasında sürekli olarak oluşturulur. Bu nedenle, olay işleyicilerinde kaynakların yoğun görevlerinin olmaması gerekir.  Örneğin, <xref:System.Windows.DragDrop.GiveFeedback> olay her oluşturulduğunda yeni bir imleç oluşturmak yerine önbelleğe alınmış bir imleç kullanın.  
  
### <a name="enabling-an-element-to-be-a-drop-target"></a>Bir öğeyi bırakma hedefi olarak etkinleştirme  
 Bırakma hedefi olan bir nesne, öğesinden sorumludur:  
  
- Bunun geçerli bir bırakma hedefi olduğunu belirtme.  
  
- Hedef üzerine sürüklendiğinde sürükle kaynağına yanıt verme.  
  
- Aktarılan verilerin alabileceği bir biçimde olup olmadığı denetleniyor.  
  
- Bırakılan veriler işleniyor.  
  
 Bir öğenin bırakma hedefi olduğunu belirtmek için <xref:System.Windows.UIElement.AllowDrop%2A> özelliğini olarak `true`ayarlayın. Bırakma hedefi olayları, daha sonra işleyebilmeniz için öğesi üzerinde oluşturulur. Bir sürükle ve bırak işlemi sırasında, bırakma hedefinde aşağıdaki olay dizisi gerçekleşir:  
  
1. <xref:System.Windows.DragDrop.DragEnter>  
  
2. <xref:System.Windows.DragDrop.DragOver>  
  
3. <xref:System.Windows.DragDrop.DragLeave> veya <xref:System.Windows.DragDrop.Drop>  
  
 Bu <xref:System.Windows.DragDrop.DragEnter> olay, veriler bırakma hedefinin sınırına sürüklendiğinde oluşur. Bu olayı genellikle, uygulamanız için uygunsa sürükle ve bırak işleminin etkilerinin önizlemesini sağlamak üzere işleyebilirsiniz. Olayda üzerine yazılacak <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> <xref:System.Windows.DragDrop.DragEnter> şekilde,özelliğiolaydaayarlamayın<xref:System.Windows.DragDrop.DragOver> .  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Shapes.Ellipse> öğesi için <xref:System.Windows.DragDrop.DragEnter> olay işleyicisi gösterilmektedir. Bu kod, geçerli <xref:System.Windows.Shapes.Shape.Fill%2A> fırçayı kaydederek sürükle ve bırak işleminin etkilerini önizlemeler. Ardından, elips üzerine <xref:System.Windows.DataObject.GetDataPresent%2A> <xref:System.Windows.DataObject> sürüklenemekte olan <xref:System.Windows.Media.Brush>dize verileri içerip içermediğini denetlemek için yöntemini kullanır. Öyleyse, veriler <xref:System.Windows.DataObject.GetData%2A> yöntemi kullanılarak ayıklanır. Daha sonra bir <xref:System.Windows.Media.Brush> öğesine dönüştürülür ve elips 'e uygulanır. Değişiklik <xref:System.Windows.DragDrop.DragLeave> olay işleyicisine geri döndürülür. Veriler bir <xref:System.Windows.Media.Brush>öğesine dönüştürülemiyorsa hiçbir işlem yapılmaz.  
  
 [!code-csharp[DragDropSnippets#DragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragenter)]
 [!code-vb[DragDropSnippets#DragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragenter)]  
  
 Veriler bırakma hedefinin üzerine sürüklenirken olaysürekligerçekleşir.<xref:System.Windows.DragDrop.DragOver> Bu olay <xref:System.Windows.DragDrop.GiveFeedback> , sürükleme kaynağındaki olayla eşleştirilir. Olay işleyicisinde, genellikle, <xref:System.Windows.DataObject.GetDataPresent%2A> aktarılan verilerin bırakma hedefinin işleyebilip işlenemediğini denetlemek için ve <xref:System.Windows.DataObject.GetData%2A> yöntemlerini kullanırsınız. <xref:System.Windows.DragDrop.DragOver> Ayrıca, bir değiştirici tuşuna basıldığında, genellikle kullanıcının bir taşıma veya kopyalama eylemi yapıp belirtmediğini de denetleyebilirsiniz. Bu denetimler gerçekleştirildikten sonra, sürükle kaynağına verilerin hangi <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> etkilerden hangilerinin sahip olacağını bildirmek için özelliğini ayarlayın. Sürükle kaynağı bu bilgileri <xref:System.Windows.DragDrop.GiveFeedback> olay bağımsız değişkenlerinin içinde alır ve kullanıcıya geri bildirim vermek için uygun bir imleç ayarlayabilir.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Shapes.Ellipse> öğesi için <xref:System.Windows.DragDrop.DragOver> olay işleyicisi gösterilmektedir. Bu kod, <xref:System.Windows.DataObject> elips üzerine sürüklenemekte olan dize verilerini <xref:System.Windows.Media.Brush>içerip içermediğini kontrol eder. Varsa, <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> özelliğini olarak <xref:System.Windows.DragDropEffects.Copy>ayarlar. Bu, sürükle kaynağına verilerin elips 'e kopyalanamayacağını gösterir. Veriler bir <xref:System.Windows.Media.Brush>öğesine dönüştürülemiyorsa <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> , özelliği olarak <xref:System.Windows.DragDropEffects.None>ayarlanır. Bu, sürükle kaynağına, elipsin veri için geçerli bir bırakma hedefi olmadığını gösterir.  
  
 [!code-csharp[DragDropSnippets#DragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragover)]
 [!code-vb[DragDropSnippets#DragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragover)]  
  
 <xref:System.Windows.DragDrop.DragLeave> Veriler, verilerin bırakılmadan önce hedef sınırın dışına sürüklenmesi durumunda meydana gelir. <xref:System.Windows.DragDrop.DragEnter> Olay işleyicisinde yaptığınız herhangi bir şeyi geri almak için bu olayı işleyebilirsiniz.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Shapes.Ellipse> öğesi için <xref:System.Windows.DragDrop.DragLeave> olay işleyicisi gösterilmektedir. Bu kod, kayıt, elips 'e kaydedilmiş <xref:System.Windows.DragDrop.DragEnter> <xref:System.Windows.Media.Brush> şekilde uygulanarak olay işleyicisinde gerçekleştirilen önizlemeyi geri alır.  
  
 [!code-csharp[DragDropSnippets#DragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragleave)]
 [!code-vb[DragDropSnippets#DragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragleave)]  
  
 Bu <xref:System.Windows.DragDrop.Drop> olay, veriler bırakma hedefinin üzerine bırakıldığında oluşur; Varsayılan olarak, fare düğmesi bırakıldığında gerçekleşir. Olay işleyicisinde, öğesinden <xref:System.Windows.DataObject.GetData%2A> <xref:System.Windows.DataObject> aktarılan verileri ayıklamak ve uygulamanızın gerektirdiği tüm veri işlemlerini gerçekleştirmek için yöntemini kullanırsınız. <xref:System.Windows.DragDrop.Drop> <xref:System.Windows.DragDrop.Drop> Olay sürükle ve bırak işlemini sonlandırır.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Shapes.Ellipse> öğesi için <xref:System.Windows.DragDrop.Drop> olay işleyicisi gösterilmektedir. Bu kod, sürükle ve bırak işleminin etkilerini uygular ve <xref:System.Windows.DragDrop.DragEnter> olay işleyicisindeki koda benzerdir. <xref:System.Windows.DataObject> Elips<xref:System.Windows.Media.Brush>üzerine sürüklenemekte olup olmadığını kontrol eder. <xref:System.Windows.Media.Brush> Varsa, bu, elips 'e uygulanır. Veriler bir <xref:System.Windows.Media.Brush>öğesine dönüştürülemiyorsa hiçbir işlem yapılmaz.  
  
 [!code-csharp[DragDropSnippets#Drop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#drop)]
 [!code-vb[DragDropSnippets#Drop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#drop)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Clipboard>
- [İzlenecek yol: Kullanıcı denetiminde sürükleme ve bırakmayı etkinleştirme](walkthrough-enabling-drag-and-drop-on-a-user-control.md)
- [Nasıl Yapılır Konuları](drag-and-drop-how-to-topics.md)
- [Sürükleme ve Bırakma](drag-and-drop.md)
