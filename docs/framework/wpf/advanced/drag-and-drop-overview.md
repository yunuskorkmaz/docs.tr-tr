---
title: Sürükleme ve Bırakmaya Genel Bakış
description: Windows Presentation Foundation uygulamalarda sürükle ve bırak desteği hakkında bilgi edinin. Bu, kullanıcıların nesneleri kullanıcı arabirimindeki bir bölgeye sürükleyebilmenizi sağlar.
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
ms.openlocfilehash: 63384e79d8a198e4cc9507ca3266c484c0506e2c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168072"
---
# <a name="drag-and-drop-overview"></a>Sürükleme ve Bırakmaya Genel Bakış
Bu konu, uygulamalarda sürükle ve bırak desteğine genel bir bakış sağlar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] . Sürükleyip bırakma genellikle bir veya daha fazla nesne seçmek için fare (veya başka bir işaret aygıtı) kullanan bir veri aktarımı yöntemine başvurur ve bu nesneleri, içindeki belirli bir bırakma hedefi üzerine sürükleyip [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] bırakarak bunları bırakabilir.  

<a name="Drag_and_Drop_Support"></a>
## <a name="drag-and-drop-support-in-wpf"></a>WPF 'de sürükle ve bırak desteği  
 Sürükle ve bırak işlemleri genellikle iki taraf içerir: sürüklenen nesnenin kaynaklandığı Sürükle kaynağı ve bırakılan nesneyi alan bir bırakma hedefi.  Sürükle kaynağı ve bırakma hedefi, aynı uygulamadaki veya farklı bir uygulamadaki UI öğeleri olabilir.  
  
 Sürükle ve bırak ile işlenebilen nesnelerin türü ve sayısı tamamen rasgele olur. Örneğin, dosyalar, klasörler ve içerik seçimleri, sürükle ve bırak işlemleri aracılığıyla daha yaygın olarak kullanılan nesnelerden bazılarıdır.  
  
 Bir sürükle ve bırak işlemi sırasında gerçekleştirilen belirli eylemler uygulamaya özgüdür ve genellikle bağlam tarafından belirlenir.  Örneğin, aynı depolama cihazında bir klasörden diğerine dosya seçimini sürüklemek, dosyaları varsayılan olarak taşırken bir evrensel adlandırma kuralı (UNC) paylaşımından yerel bir klasöre sürüklemek dosyaları varsayılan olarak kopyalar.  
  
 Tarafından sunulan sürükle ve bırak olanakları, çok [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çeşitli sürükle ve bırak senaryolarını destekleyecek şekilde oldukça esnek ve özelleştirilebilir olacak şekilde tasarlanmıştır.  Sürükle ve bırak, nesneleri tek bir uygulama içinde veya farklı uygulamalar arasında düzenleme destekler. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Uygulamalar ve diğer Windows uygulamaları arasında sürükleme ve bırakma de tam olarak desteklenmektedir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]' De, herhangi bir <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement> sürükleyip bırakmaya katılabilir. Sürükle ve bırak işlemleri için gereken olaylar ve yöntemler <xref:System.Windows.DragDrop> sınıfında tanımlanır. <xref:System.Windows.UIElement>Ve <xref:System.Windows.ContentElement> sınıfları, <xref:System.Windows.DragDrop> bir <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement> temel öğe olarak Devralındığı zaman, olayların sınıf üyeleri listesinde görünmesi için, ekli olayların diğer adlarını içerir. Bu olaylara eklenen olay işleyicileri, temel alınan <xref:System.Windows.DragDrop> ekli olaya iliştirilir ve aynı olay veri örneğini alır. Daha fazla bilgi için, <xref:System.Windows.UIElement.Drop?displayProperty=nameWithType> olayına bakın.  
  
> [!IMPORTANT]
> OLE sürükle ve bırak Internet bölgesinde çalışırken çalışmaz.  
  
<a name="Data_Transfer"></a>
## <a name="data-transfer"></a>Veri Aktarımı  
 Sürükle ve bırak, veri aktarımının daha genel alanının bir parçasıdır. Veri aktarımı sürükle ve bırak ile kopyalama ve yapıştırma işlemlerini içerir. Bir sürükle ve bırak işlemi, sistem panosunu kullanarak bir nesneden veya uygulamadan diğerine veri aktarmak için kullanılan bir kopyalama ve yapıştırma ya da kesme ve yapıştırma işlemine benzer. Her iki tür işlem şunları gerektirir:  
  
- Verileri sağlayan kaynak nesne.  
  
- Aktarılan verileri geçici olarak depolamanın bir yolu.  
  
- Verileri alan bir hedef nesne.  
  
 Bir Kopyala ve Yapıştır işleminde, sistem panosu, aktarılan verileri geçici olarak depolamak için kullanılır; sürükle ve bırak işleminde, <xref:System.Windows.DataObject> verileri depolamak için kullanılır. Kavramsal olarak, bir veri nesnesi, gerçek verileri içeren bir veya daha fazla çiftinin <xref:System.Object> ve karşılık gelen bir veri biçimi tanımlayıcısını kapsar.  
  
 Sürükleme kaynağı, statik <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> yöntemi çağırarak ve aktarılan verileri buna geçirerek bir sürükle ve bırak işlemi başlatır. <xref:System.Windows.DragDrop.DoDragDrop%2A>Yöntemi, gerekirse verileri otomatik olarak bir halinde saracaktır <xref:System.Windows.DataObject> . Veri biçimi üzerinde daha fazla denetim için, verileri yöntemine geçirmeden önce bir içinde sardırabilirsiniz <xref:System.Windows.DataObject> <xref:System.Windows.DragDrop.DoDragDrop%2A> . Bırakma hedefi, öğesinden verilerin ayıklanmasından sorumludur <xref:System.Windows.DataObject> . Veri nesneleriyle çalışma hakkında daha fazla bilgi için bkz. [veri ve veri nesneleri](data-and-data-objects.md).  
  
 Bir sürükle ve bırak işleminin kaynağı ve hedefi Kullanıcı arabirimi öğeleridir; Ancak, gerçekten aktarılmakta olan verilerin genellikle görsel temsili yoktur. Windows Gezgini 'nde dosyaları sürüklerken oluşan gibi sürüklenen verilerin görsel bir gösterimini sağlamak için kod yazabilirsiniz. Varsayılan olarak, imleç sürükle ve bırak işleminin veriler üzerinde sahip olacağı etkiyi (verilerin taşınıp taşınacağını veya kopyalanmayacağı gibi) belirtecek şekilde değiştirerek kullanıcıya geri bildirim verilir.  
  
### <a name="drag-and-drop-effects"></a>Sürükle ve bırak efektleri  
 Sürükle ve bırak işlemlerinin, aktarılan veriler üzerinde farklı etkileri olabilir. Örneğin, verileri kopyalayabilir veya verileri taşıyabilirsiniz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.DragDropEffects>bir sürükle ve bırak işleminin etkisini belirtmek için kullanabileceğiniz bir sabit listesi tanımlar. Sürükleme kaynağında, kaynağın yöntemde izin verolacağı etkileri belirtebilirsiniz <xref:System.Windows.DragDrop.DoDragDrop%2A> . Bırakma hedefinde, hedefin sınıfının özelliğinde amaçladığı etkiyi belirtebilirsiniz <xref:System.Windows.DragEventArgs.Effects%2A> <xref:System.Windows.DragEventArgs> . Bırakma hedefi, olaydaki amaçlanan etkisini belirttiğinde <xref:System.Windows.DragDrop.DragOver> , bu bilgiler olaydaki sürükleme kaynağına geri geçirilir <xref:System.Windows.DragDrop.GiveFeedback> . Sürükleme kaynağı bu bilgileri kullanıcıya, bırakma hedefinin verileri ne kadar etkili olduğunu bildirmek için kullanır. Veriler bırakıldığında bırakma hedefi, olayda gerçek etkisini belirtir <xref:System.Windows.DragDrop.Drop> . Bu bilgiler, metodun dönüş değeri olarak sürükle kaynağına geçirilir <xref:System.Windows.DragDrop.DoDragDrop%2A> . Bırakma hedefi, sürükle kaynakları listesinde olmayan bir efekt döndürürse `allowedEffects` , sürükle ve bırak işlemi herhangi bir veri aktarımı yapılmaksızın iptal edilir.  
  
 ' De [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , <xref:System.Windows.DragDropEffects> değerleri yalnızca sürükle ve bırak işleminin etkileri ile ilgili sürükleme kaynağı ve bırakma hedefi arasında iletişim sağlamak için kullanıldığını unutmayın. Sürükle ve bırak işleminin gerçek etkisi, uygulamanıza uygun kodu yazmak için size bağlıdır.  
  
 Örneğin, bırakma hedefi, verileri bırakma efektinin verileri taşımakta olduğunu belirtebilir. Ancak, verileri taşımak için hem hedef öğeye eklenmeli hem de kaynak öğeden kaldırılacak olması gerekir. Kaynak öğe, verilerin taşınmasına izin verdiğini belirtebilir, ancak kaynak öğeden verileri kaldırmak için kod sağlamazsanız, nihai sonuç verilerin kopyalanmasının ve taşınmayacağı anlamına gelir.  
  
<a name="Drag_and_Drop_Events"></a>
## <a name="drag-and-drop-events"></a>Sürükle ve bırak olayları  
 Sürükle ve bırak işlemleri olay temelli bir modeli destekler.  Sürükleme kaynağı ve bırakma hedefi, sürükle ve bırak işlemlerini işlemek için standart bir olay kümesi kullanır.  Aşağıdaki tablolar, standart Sürükle ve bırak olaylarını özetler. Bunlar, sınıfındaki ekli olaylardır <xref:System.Windows.DragDrop> . Ekli olaylar hakkında daha fazla bilgi için bkz. [ekli olaylara genel bakış](attached-events-overview.md).  
  
### <a name="drag-source-events"></a>Kaynak olaylarını sürükle  
  
|Olay|Özet|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.GiveFeedback>|Bu olay bir sürükle ve bırak işlemi sırasında sürekli gerçekleşir ve bırakma kaynağının kullanıcıya geri bildirim bilgileri vermesini sağlar. Bu geri bildirim genellikle, bırakma hedefinin izin verdiği etkileri göstermek üzere fare işaretçisinin görünümü değiştirilerek verilir.  Bu bir kabarcıklanma olayıdır.|  
|<xref:System.Windows.DragDrop.QueryContinueDrag>|Bu olay, sürükle ve bırak işlemi sırasında klavyede veya fare düğmesi durumunda olduğunda meydana gelir ve bırakma kaynağının anahtar/düğme durumlarına bağlı olarak sürükle ve bırak işlemini iptal etmesini sağlar. Bu bir kabarcıklanma olayıdır.|  
|<xref:System.Windows.DragDrop.PreviewGiveFeedback>|Tünel oluşturma sürümü <xref:System.Windows.DragDrop.GiveFeedback> .|  
|<xref:System.Windows.DragDrop.PreviewQueryContinueDrag>|Tünel oluşturma sürümü <xref:System.Windows.DragDrop.QueryContinueDrag> .|  
  
### <a name="drop-target-events"></a>Bırakma hedefi olayları  
  
|Olay|Özet|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.DragEnter>|Bu olay, bir nesne bırakma hedefinin sınırına sürüklendiğinde oluşur. Bu bir kabarcıklanma olayıdır.|  
|<xref:System.Windows.DragDrop.DragLeave>|Bu olay, bir nesne bırakma hedefinin sınırının dışına sürüklendiğinde oluşur.  Bu bir kabarcıklanma olayıdır.|  
|<xref:System.Windows.DragDrop.DragOver>|Bu olay, bırakma hedefinin sınırının içinde bir nesne sürüklendiğinde (taşındığında) sürekli gerçekleşir. Bu bir kabarcıklanma olayıdır.|  
|<xref:System.Windows.DragDrop.Drop>|Bu olay bırakma hedefinde bir nesne bırakıldığında oluşur.  Bu bir kabarcıklanma olayıdır.|  
|<xref:System.Windows.DragDrop.PreviewDragEnter>|Tünel oluşturma sürümü <xref:System.Windows.DragDrop.DragEnter> .|  
|<xref:System.Windows.DragDrop.PreviewDragLeave>|Tünel oluşturma sürümü <xref:System.Windows.DragDrop.DragLeave> .|  
|<xref:System.Windows.DragDrop.PreviewDragOver>|Tünel oluşturma sürümü <xref:System.Windows.DragDrop.DragOver> .|  
|<xref:System.Windows.DragDrop.PreviewDrop>|Tünel oluşturma sürümü <xref:System.Windows.DragDrop.Drop> .|  
  
 Bir nesnenin örnekleri için sürükle ve bırak olaylarını işlemek için, önceki tablolarda listelenen olaylara yönelik işleyiciler ekleyin. Sürükle ve bırak olaylarını sınıf düzeyinde işlemek için, karşılık gelen sanal on * olayını ve \* PreviewEvent yöntemlerini geçersiz kılın. Daha fazla bilgi için bkz. [temel sınıfları denetim aracılığıyla yönlendirilmiş olayların sınıf işlemesi](marking-routed-events-as-handled-and-class-handling.md#Class_Handling_of_Routed_Events).  
  
<a name="Implementing_Drag_And_Drop"></a>
## <a name="implementing-drag-and-drop"></a>Sürükle ve bırak uygulama  
 Bir kullanıcı arabirimi öğesi, bir Sürükle kaynağı, bir bırakma hedefi veya her ikisi olabilir. Temel sürükle ve bırak uygulamak için sürükle ve bırak işlemini başlatmak ve bırakılan verileri işlemek için kod yazarsınız. Sürükleme ve bırakma deneyimini, isteğe bağlı sürükle ve bırak olaylarını işleyerek geliştirebilirsiniz.  
  
 Temel sürükle ve bırak uygulamak için aşağıdaki görevleri tamamlayacaksınız:  
  
- Sürükle kaynağı olacak öğeyi belirler. Sürükle kaynağı bir <xref:System.Windows.UIElement> veya bir olabilir <xref:System.Windows.ContentElement> .  
  
- Sürükleme kaynağında sürükle ve bırak işlemini başlatacak bir olay işleyicisi oluşturun. Olay genellikle <xref:System.Windows.UIElement.MouseMove> olaydır.  
  
- Sürükle <xref:System.Windows.DragDrop.DoDragDrop%2A> ve bırak işlemini başlatmak için kaynak olay işleyicisindeki yöntemi çağırın. Çağrıda, <xref:System.Windows.DragDrop.DoDragDrop%2A> Sürükle kaynağını, aktarılacak verileri ve izin verilen etkileri belirtin.  
  
- Bırakma hedefi olacak öğeyi belirler. Bırakma hedefi <xref:System.Windows.UIElement> veya olabilir <xref:System.Windows.ContentElement> .  
  
- Bırakma hedefinde <xref:System.Windows.UIElement.AllowDrop%2A> özelliğini olarak ayarlayın `true` .  
  
- Bırakma hedefinde, <xref:System.Windows.DragDrop.Drop> bırakılan verileri işlemek için bir olay işleyicisi oluşturun.  
  
- <xref:System.Windows.DragDrop.Drop>Olay işleyicisinde, <xref:System.Windows.DragEventArgs> ve yöntemlerini kullanarak içindeki verileri ayıklayın <xref:System.Windows.DataObject.GetDataPresent%2A> <xref:System.Windows.DataObject.GetData%2A> .  
  
- <xref:System.Windows.DragDrop.Drop>Olay işleyicisinde, istenen sürükleme ve bırakma işlemini gerçekleştirmek için verileri kullanın.  
  
 Sürükle ve bırak uygulamanızı, <xref:System.Windows.DataObject> aşağıdaki görevlerde gösterildiği gibi isteğe bağlı Sürükle kaynak ve bırakma hedefi olaylarını işleyerek bir özel oluşturarak geliştirebilirsiniz:  
  
- Özel verileri veya birden çok veri öğesini aktarmak için, <xref:System.Windows.DataObject> yöntemine geçirilecek bir oluşturun <xref:System.Windows.DragDrop.DoDragDrop%2A> .  
  
- Sürükleme sırasında ek eylemler gerçekleştirmek için <xref:System.Windows.DragDrop.DragEnter> <xref:System.Windows.DragDrop.DragOver> <xref:System.Windows.DragDrop.DragLeave> bırakma hedefinin, ve olaylarını işleyin.  
  
- Fare işaretçisinin görünüşünü değiştirmek için <xref:System.Windows.DragDrop.GiveFeedback> Sürükle kaynağındaki olayı işleyin.  
  
- Sürükle ve bırak işleminin nasıl iptal edildiğini değiştirmek için <xref:System.Windows.DragDrop.QueryContinueDrag> Sürükle kaynağında olayı işleyin.  
  
<a name="Drag_And_Drop_Example"></a>
## <a name="drag-and-drop-example"></a>Sürükle ve bırak örneği  
 Bu bölümde bir öğesi için sürükle ve bırak 'ın nasıl uygulanacağı açıklanmaktadır <xref:System.Windows.Shapes.Ellipse> . , <xref:System.Windows.Shapes.Ellipse> Bir Sürükle kaynağı ve bırakma hedefidir. Aktarılan veriler, elips özelliğinin dize gösterimidir <xref:System.Windows.Shapes.Shape.Fill%2A> . Aşağıdaki XAML, <xref:System.Windows.Shapes.Ellipse> öğesini ve işlediği, sürükle ve bırak ile ilgili olayları gösterir. Sürükleyip bırakmayı uygulama hakkında tam adımlar için bkz. [Izlenecek yol: Kullanıcı denetiminde sürükleme ve bırakmayı etkinleştirme](walkthrough-enabling-drag-and-drop-on-a-user-control.md).  
  
 [!code-xaml[DragDropSnippets#EllipseXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#ellipsexaml)]  
  
### <a name="enabling-an-element-to-be-a-drag-source"></a>Bir öğenin sürükle kaynağı olmasını sağlama  
 Sürükleme kaynağı olan bir nesne şu kaynaktan sorumludur:  
  
- Bir sürükleme işleminin ne zaman gerçekleşeceğini tanımlama.  
  
- Sürükle ve bırak işlemi başlatılıyor.  
  
- Aktarılacak verileri tanımlama.  
  
- Sürükle ve bırak işleminin aktarılan verilerde sahip olmasına izin verilen etkileri belirtme.  
  
 Sürükleme kaynağı, kullanıcıya izin verilen eylemlerle ilgili geri bildirimde bulunabilir (taşıma, kopyalama, yok) ve sürükleme sırasında ESC tuşuna basmak gibi, sürükle ve bırak işlemini ek kullanıcı girişine göre iptal edebilir.  
  
 Bu, bir sürükleme işleminin ne zaman gerçekleşeceğini tespit etmek ve sonra yöntemi çağırarak Sürükle ve bırak işlemini başlatmak için uygulamanızın sorumluluğundadır <xref:System.Windows.DragDrop.DoDragDrop%2A> . Genellikle, bu, <xref:System.Windows.UIElement.MouseMove> fare düğmesine basıldığında sürüklediğiniz öğe üzerinde bir olay meydana geldi. Aşağıdaki örnek, <xref:System.Windows.UIElement.MouseMove> bir <xref:System.Windows.Shapes.Ellipse> sürükleme kaynağı yapmak için bir öğenin olay işleyicisinden bir sürükle ve bırak işleminin nasıl başlatılacağı gösterilmektedir. Aktarılan veriler, elips özelliğinin dize gösterimidir <xref:System.Windows.Shapes.Shape.Fill%2A> .  
  
 [!code-csharp[DragDropSnippets#DoDragDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dodragdrop)]
 [!code-vb[DragDropSnippets#DoDragDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dodragdrop)]  
  
 <xref:System.Windows.UIElement.MouseMove>Olay işleyicisinin içinde, <xref:System.Windows.DragDrop.DoDragDrop%2A> sürükle ve bırak işlemini başlatmak için yöntemini çağırın. <xref:System.Windows.DragDrop.DoDragDrop%2A>Yöntemi üç parametre alır:  
  
- `dragSource`– Aktarılan verilerin kaynağı olan Dependency nesnesine bir başvuru; Bu genellikle <xref:System.Windows.UIElement.MouseMove> olayın kaynağıdır.  
  
- `data`-İçinde kaydırılan, aktarılan verileri içeren bir nesne <xref:System.Windows.DataObject> .  
  
- `allowedEffects`- <xref:System.Windows.DragDropEffects> Sürükle ve bırak işleminin izin verilen etkilerini belirten sabit listesi değerlerinden biri.  
  
 Seri hale getirilebilir herhangi bir nesne parametreye geçirilebilir `data` . Veriler henüz bir içinde <xref:System.Windows.DataObject> sarmalanmamış ise, otomatik olarak yeni bir ile sarmalanır <xref:System.Windows.DataObject> . Birden çok veri öğesi geçirmek için <xref:System.Windows.DataObject> kendiniz oluşturmanız ve yöntemine geçirmeniz gerekir <xref:System.Windows.DragDrop.DoDragDrop%2A> . Daha fazla bilgi için bkz. [veri ve veri nesneleri](data-and-data-objects.md).  
  
 Bu `allowedEffects` parametre, sürükleme kaynağının, aktarılan verilerle birlikte bırakma hedefinin ne izin verbileceklerini belirtmek için kullanılır. Bir sürükleme kaynağı için ortak değerler <xref:System.Windows.DragDropEffects.Copy> , ve ' dir <xref:System.Windows.DragDropEffects.Move> <xref:System.Windows.DragDropEffects.All> .  
  
> [!NOTE]
> Bırakma hedefi, bırakılan verilere yanıt olarak hangi etkileri amaçladığı de belirtebilir. Örneğin, bırakma hedefi bırakılacak veri türünü tanımazsa, izin verilen etkileri olarak ayarlayarak verileri reddedebilirler <xref:System.Windows.DragDropEffects.None> . Genellikle bunu <xref:System.Windows.DragDrop.DragOver> olay işleyicide yapar.  
  
 Sürükleme kaynağı isteğe bağlı olarak <xref:System.Windows.DragDrop.GiveFeedback> ve olaylarını işleyebilir <xref:System.Windows.DragDrop.QueryContinueDrag> . Olayları işlenmiş olarak işaretlemediğiniz sürece bu olayların varsayılan işleyicileri kullanılır. Genellikle bu olayları, varsayılan davranışlarını değiştirmek için özel bir işlem yapmanız gerekmedikçe yoksayabilirsiniz.  
  
 <xref:System.Windows.DragDrop.GiveFeedback>Sürükleme kaynağı sürüklenirken olay sürekli olarak getirilir. Bu olay için varsayılan işleyici, sürükleme kaynağının geçerli bir bırakma hedefi üzerinde olup olmadığını denetler. Varsa, bırakma hedefinin izin verilen efektlerini denetler. Daha sonra, izin verilen bırakma efektleriyle ilgili olarak son kullanıcıya geri bildirim sağlar. Bu, genellikle fare imlecini bırakma, kopyalama veya taşıma imlecine göre değiştirilerek yapılır. Yalnızca kullanıcıya geri bildirim sağlamak için özel imleçler kullanmanız gerekiyorsa bu olayı işlemeniz gerekir. Bu olayı idare ederseniz, varsayılan işleyicinin işleyicinizi geçersiz kılmaması için, onu işlenmiş olarak işaretlediğinizden emin olun.  
  
 <xref:System.Windows.DragDrop.QueryContinueDrag>Sürükleme kaynağı sürüklenirken olay sürekli olarak getirilir. Bu olayı, sürükle ve bırak işlemini ESC, SHIFT, CTRL ve ALT tuşlarının yanı sıra fare düğmelerinin durumunu temel alarak hangi eylemin bittiğini belirlemek için işleyebilirsiniz. Bu olay için varsayılan işleyici, ESC tuşuna basıldığında sürükle ve bırak işlemini iptal eder ve fare düğmesi serbest bırakıldığında verileri bırakır.  
  
> [!CAUTION]
> Bu olaylar, sürükle ve bırak işlemi sırasında sürekli olarak oluşturulur. Bu nedenle, olay işleyicilerinde kaynakların yoğun görevlerinin olmaması gerekir.  Örneğin, olay her oluşturulduğunda yeni bir imleç oluşturmak yerine önbelleğe alınmış bir imleç kullanın <xref:System.Windows.DragDrop.GiveFeedback> .  
  
### <a name="enabling-an-element-to-be-a-drop-target"></a>Bir öğeyi bırakma hedefi olarak etkinleştirme  
 Bırakma hedefi olan bir nesne, öğesinden sorumludur:  
  
- Bunun geçerli bir bırakma hedefi olduğunu belirtme.  
  
- Hedef üzerine sürüklendiğinde sürükle kaynağına yanıt verme.  
  
- Aktarılan verilerin alabileceği bir biçimde olup olmadığı denetleniyor.  
  
- Bırakılan veriler işleniyor.  
  
 Bir öğenin bırakma hedefi olduğunu belirtmek için <xref:System.Windows.UIElement.AllowDrop%2A> özelliğini olarak ayarlayın `true` . Bırakma hedefi olayları, daha sonra işleyebilmeniz için öğesi üzerinde oluşturulur. Bir sürükle ve bırak işlemi sırasında, bırakma hedefinde aşağıdaki olay dizisi gerçekleşir:  
  
1. <xref:System.Windows.DragDrop.DragEnter>  
  
2. <xref:System.Windows.DragDrop.DragOver>  
  
3. <xref:System.Windows.DragDrop.DragLeave> veya <xref:System.Windows.DragDrop.Drop>  
  
 Bu <xref:System.Windows.DragDrop.DragEnter> olay, veriler bırakma hedefinin sınırına sürüklendiğinde oluşur. Bu olayı genellikle, uygulamanız için uygunsa sürükle ve bırak işleminin etkilerinin önizlemesini sağlamak üzere işleyebilirsiniz. Olayda <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> <xref:System.Windows.DragDrop.DragEnter> üzerine yazılacak şekilde, özelliği olayda ayarlamayın <xref:System.Windows.DragDrop.DragOver> .  
  
 Aşağıdaki örnekte <xref:System.Windows.DragDrop.DragEnter> bir öğesi için olay işleyicisi gösterilmektedir <xref:System.Windows.Shapes.Ellipse> . Bu kod, geçerli fırçayı kaydederek sürükle ve bırak işleminin etkilerini önizlemeler <xref:System.Windows.Shapes.Shape.Fill%2A> . Ardından, <xref:System.Windows.DataObject.GetDataPresent%2A> <xref:System.Windows.DataObject> elips üzerine sürüklenemekte olan dize verileri içerip içermediğini denetlemek için yöntemini kullanır <xref:System.Windows.Media.Brush> . Öyleyse, veriler yöntemi kullanılarak ayıklanır <xref:System.Windows.DataObject.GetData%2A> . Daha sonra bir öğesine dönüştürülür <xref:System.Windows.Media.Brush> ve elips 'e uygulanır. Değişiklik <xref:System.Windows.DragDrop.DragLeave> olay işleyicisine geri döndürülür. Veriler bir öğesine dönüştürülemiyorsa <xref:System.Windows.Media.Brush> hiçbir işlem yapılmaz.  
  
 [!code-csharp[DragDropSnippets#DragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragenter)]
 [!code-vb[DragDropSnippets#DragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragenter)]  
  
 <xref:System.Windows.DragDrop.DragOver>Veriler bırakma hedefinin üzerine sürüklenirken olay sürekli gerçekleşir. Bu olay, <xref:System.Windows.DragDrop.GiveFeedback> sürükleme kaynağındaki olayla eşleştirilir. <xref:System.Windows.DragDrop.DragOver>Olay işleyicisinde, genellikle, <xref:System.Windows.DataObject.GetDataPresent%2A> <xref:System.Windows.DataObject.GetData%2A> aktarılan verilerin bırakma hedefinin işleyebilip işlenemediğini denetlemek için ve yöntemlerini kullanırsınız. Ayrıca, bir değiştirici tuşuna basıldığında, genellikle kullanıcının bir taşıma veya kopyalama eylemi yapıp belirtmediğini de denetleyebilirsiniz. Bu denetimler gerçekleştirildikten sonra, <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> Sürükle kaynağına verilerin hangi etkilerden hangilerinin sahip olacağını bildirmek için özelliğini ayarlayın. Sürükle kaynağı bu bilgileri <xref:System.Windows.DragDrop.GiveFeedback> olay bağımsız değişkenlerinin içinde alır ve kullanıcıya geri bildirim vermek için uygun bir imleç ayarlayabilir.  
  
 Aşağıdaki örnekte <xref:System.Windows.DragDrop.DragOver> bir öğesi için olay işleyicisi gösterilmektedir <xref:System.Windows.Shapes.Ellipse> . Bu kod, <xref:System.Windows.DataObject> elips üzerine sürüklenemekte olan dize verilerini içerip içermediğini kontrol eder <xref:System.Windows.Media.Brush> . Varsa, <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> özelliğini olarak ayarlar <xref:System.Windows.DragDropEffects.Copy> . Bu, sürükle kaynağına verilerin elips 'e kopyalanamayacağını gösterir. Veriler bir öğesine dönüştürülemiyorsa <xref:System.Windows.Media.Brush> , <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> özelliği olarak ayarlanır <xref:System.Windows.DragDropEffects.None> . Bu, sürükle kaynağına, elipsin veri için geçerli bir bırakma hedefi olmadığını gösterir.  
  
 [!code-csharp[DragDropSnippets#DragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragover)]
 [!code-vb[DragDropSnippets#DragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragover)]  
  
 <xref:System.Windows.DragDrop.DragLeave>Veriler, verilerin bırakılmadan önce hedef sınırın dışına sürüklenmesi durumunda meydana gelir. Olay işleyicisinde yaptığınız herhangi bir şeyi geri almak için bu olayı işleyebilirsiniz <xref:System.Windows.DragDrop.DragEnter> .  
  
 Aşağıdaki örnekte <xref:System.Windows.DragDrop.DragLeave> bir öğesi için olay işleyicisi gösterilmektedir <xref:System.Windows.Shapes.Ellipse> . Bu kod, <xref:System.Windows.DragDrop.DragEnter> kayıt, elips 'e kaydedilmiş şekilde uygulanarak olay işleyicisinde gerçekleştirilen önizlemeyi geri alır <xref:System.Windows.Media.Brush> .  
  
 [!code-csharp[DragDropSnippets#DragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragleave)]
 [!code-vb[DragDropSnippets#DragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragleave)]  
  
 <xref:System.Windows.DragDrop.Drop>Bu olay, veriler bırakma hedefinin üzerine bırakıldığında oluşur; Varsayılan olarak, fare düğmesi bırakıldığında gerçekleşir. <xref:System.Windows.DragDrop.Drop>Olay işleyicisinde, <xref:System.Windows.DataObject.GetData%2A> öğesinden aktarılan verileri ayıklamak <xref:System.Windows.DataObject> ve uygulamanızın gerektirdiği tüm veri işlemlerini gerçekleştirmek için yöntemini kullanırsınız. <xref:System.Windows.DragDrop.Drop>Olay sürükle ve bırak işlemini sonlandırır.  
  
 Aşağıdaki örnekte <xref:System.Windows.DragDrop.Drop> bir öğesi için olay işleyicisi gösterilmektedir <xref:System.Windows.Shapes.Ellipse> . Bu kod, sürükle ve bırak işleminin etkilerini uygular ve <xref:System.Windows.DragDrop.DragEnter> olay işleyicisindeki koda benzerdir. <xref:System.Windows.DataObject>Elips üzerine sürüklenemekte olup olmadığını kontrol eder <xref:System.Windows.Media.Brush> . Varsa, bu, <xref:System.Windows.Media.Brush> elips 'e uygulanır. Veriler bir öğesine dönüştürülemiyorsa <xref:System.Windows.Media.Brush> hiçbir işlem yapılmaz.  
  
 [!code-csharp[DragDropSnippets#Drop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#drop)]
 [!code-vb[DragDropSnippets#Drop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#drop)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Clipboard>
- [İzlenecek yol: Kullanıcı Denetiminde Sürükleme ve Bırakmayı Etkinleştirme](walkthrough-enabling-drag-and-drop-on-a-user-control.md)
- [Nasıl Yapılır Konuları](drag-and-drop-how-to-topics.md)
- [Sürükleme ve Bırakma](drag-and-drop.md)
