---
title: Sürükleyip bırakmaya genel bakış
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
ms.openlocfilehash: 72dc443e5653b9871c3f67b003bd1af0536d5993
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291480"
---
# <a name="drag-and-drop-overview"></a>Sürükleyip bırakmaya genel bakış
Bu konu, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalarında sürükle ve bırak desteğine genel bir bakış sağlar. Sürükle ve bırak genellikle, bir veya daha fazla nesne seçmek, bu nesneleri [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ' da istenen bir bırakma hedefinin üzerinde sürüklemek ve onları bırakmak için fare (veya başka bir işaret aygıtı) kullanan bir veri aktarımı yöntemine başvurur.  

<a name="Drag_and_Drop_Support"></a>   
## <a name="drag-and-drop-support-in-wpf"></a>WPF 'de sürükle ve bırak desteği  
 Sürükle ve bırak işlemleri genellikle iki taraf içerir: sürüklenen nesnenin kaynaklandığı Sürükle kaynağı ve bırakılan nesneyi alan bir bırakma hedefi.  Sürükle kaynağı ve bırakma hedefi, aynı uygulamadaki veya farklı bir uygulamadaki UI öğeleri olabilir.  
  
 Sürükle ve bırak ile işlenebilen nesnelerin türü ve sayısı tamamen rasgele olur. Örneğin, dosyalar, klasörler ve içerik seçimleri, sürükle ve bırak işlemleri aracılığıyla daha yaygın olarak kullanılan nesnelerden bazılarıdır.  
  
 Bir sürükle ve bırak işlemi sırasında gerçekleştirilen belirli eylemler uygulamaya özgüdür ve genellikle bağlam tarafından belirlenir.  Örneğin, aynı depolama cihazında bir klasörden diğerine dosya seçimini sürüklemek, dosyaları varsayılan olarak taşırken bir evrensel adlandırma kuralı (UNC) paylaşımından yerel bir klasöre sürüklemek dosyaları varsayılan olarak kopyalar.  
  
 @No__t-0 tarafından sunulan sürükle ve bırak olanakları, çok çeşitli sürükle ve bırak senaryolarını destekleyecek şekilde oldukça esnek ve özelleştirilebilir olacak şekilde tasarlanmıştır.  Sürükle ve bırak, nesneleri tek bir uygulama içinde veya farklı uygulamalar arasında düzenleme destekler. @No__t-0 uygulamaları ve diğer Windows uygulamaları arasında sürükleme ve bırakma de tam olarak desteklenmektedir.  
  
 @No__t-0 ' da, herhangi bir <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement> ' nin sürükle ve bırak ile katılımını sağlayabilirsiniz. Sürükle ve bırak işlemleri için gereken olaylar ve Yöntemler <xref:System.Windows.DragDrop> sınıfında tanımlanır. @No__t-0 ve <xref:System.Windows.ContentElement> sınıfları, <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement> temel öğe olarak Devralındığı zaman, olayların sınıf üyeleri listesinde görünmesi için <xref:System.Windows.DragDrop> ekli olayları için diğer adlar içerir. Bu olaylara eklenen olay işleyicileri, temel alınan @no__t 0 ekli olaya iliştirilir ve aynı olay veri örneğini alır. Daha fazla bilgi için <xref:System.Windows.UIElement.Drop?displayProperty=nameWithType> olayına bakın.  
  
> [!IMPORTANT]
> OLE sürükle ve bırak Internet bölgesinde çalışırken çalışmaz.  
  
<a name="Data_Transfer"></a>   
## <a name="data-transfer"></a>Veri Aktarımı  
 Sürükle ve bırak, veri aktarımının daha genel alanının bir parçasıdır. Veri aktarımı sürükle ve bırak ile kopyalama ve yapıştırma işlemlerini içerir. Bir sürükle ve bırak işlemi, sistem panosunu kullanarak bir nesneden veya uygulamadan diğerine veri aktarmak için kullanılan bir kopyalama ve yapıştırma ya da kesme ve yapıştırma işlemine benzer. Her iki tür işlem şunları gerektirir:  
  
- Verileri sağlayan kaynak nesne.  
  
- Aktarılan verileri geçici olarak depolamanın bir yolu.  
  
- Verileri alan bir hedef nesne.  
  
 Bir Kopyala ve Yapıştır işleminde, sistem panosu, aktarılan verileri geçici olarak depolamak için kullanılır; bir sürükle ve bırak işleminde, verileri depolamak için bir <xref:System.Windows.DataObject> kullanılır. Kavramsal olarak, bir veri nesnesi gerçek verileri içeren bir veya daha fazla <xref:System.Object> çiftinden oluşur ve karşılık gelen bir veri biçimi tanımlayıcısı.  
  
 Sürükle kaynağı, statik <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> yöntemini çağırarak ve aktarılan verileri buna geçirerek bir sürükle ve bırak işlemi başlatır. @No__t-0 yöntemi, gerekirse verileri otomatik olarak bir <xref:System.Windows.DataObject> kaydırır. Veri biçimi üzerinde daha fazla denetim için, <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemine geçirmeden önce verileri bir @no__t sardırabilirsiniz. Bırakma hedefi <xref:System.Windows.DataObject> ' dan veri ayıklanmasından sorumludur. Veri nesneleriyle çalışma hakkında daha fazla bilgi için bkz. [veri ve veri nesneleri](data-and-data-objects.md).  
  
 Bir sürükle ve bırak işleminin kaynağı ve hedefi Kullanıcı arabirimi öğeleridir; Ancak, gerçekten aktarılmakta olan verilerin genellikle görsel temsili yoktur. Windows Gezgini 'nde dosyaları sürüklerken oluşan gibi sürüklenen verilerin görsel bir gösterimini sağlamak için kod yazabilirsiniz. Varsayılan olarak, imleç sürükle ve bırak işleminin veriler üzerinde sahip olacağı etkiyi (verilerin taşınıp taşınacağını veya kopyalanmayacağı gibi) belirtecek şekilde değiştirerek kullanıcıya geri bildirim verilir.  
  
### <a name="drag-and-drop-effects"></a>Sürükle ve bırak efektleri  
 Sürükle ve bırak işlemlerinin, aktarılan veriler üzerinde farklı etkileri olabilir. Örneğin, verileri kopyalayabilir veya verileri taşıyabilirsiniz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bir sürükle ve bırak işleminin etkisini belirtmek için kullanabileceğiniz bir <xref:System.Windows.DragDropEffects> numaralandırması tanımlar. Sürükleme kaynağında, kaynağın <xref:System.Windows.DragDrop.DoDragDrop%2A> yönteminde izin verolacağı etkileri belirtebilirsiniz. Bırakma hedefinde, hedefin <xref:System.Windows.DragEventArgs> sınıfının <xref:System.Windows.DragEventArgs.Effects%2A> özelliğinde amaçladığı etkiyi belirtebilirsiniz. Bırakma hedefi <xref:System.Windows.DragDrop.DragOver> olayında amaçlanan etkisini belirttiğinde, bu bilgiler <xref:System.Windows.DragDrop.GiveFeedback> olaydaki sürükleme kaynağına geri geçirilir. Sürükleme kaynağı bu bilgileri kullanıcıya, bırakma hedefinin verileri ne kadar etkili olduğunu bildirmek için kullanır. Veriler bırakıldığında bırakma hedefi, <xref:System.Windows.DragDrop.Drop> olayında gerçek etkisini belirtir. Bu bilgiler, <xref:System.Windows.DragDrop.DoDragDrop%2A> yönteminin dönüş değeri olarak sürükle kaynağına geçirilir. Bırakma hedefi `allowedEffects` ' ın sürükle kaynakları listesinde olmayan bir efekt döndürürse, sürükle ve bırak işlemi herhangi bir veri aktarımı yapılmadan iptal edilir.  
  
 @No__t-0 ' da, <xref:System.Windows.DragDropEffects> değerlerinin yalnızca sürükle ve bırak işleminin etkileri ile ilgili sürükleme kaynağı ve bırakma hedefi arasında iletişim sağlamak için kullanıldığını unutmamak önemlidir. Sürükle ve bırak işleminin gerçek etkisi, uygulamanıza uygun kodu yazmak için size bağlıdır.  
  
 Örneğin, bırakma hedefi, verileri bırakma efektinin verileri taşımakta olduğunu belirtebilir. Ancak, verileri taşımak için hem hedef öğeye eklenmeli hem de kaynak öğeden kaldırılacak olması gerekir. Kaynak öğe, verilerin taşınmasına izin verdiğini belirtebilir, ancak kaynak öğeden verileri kaldırmak için kod sağlamazsanız, nihai sonuç verilerin kopyalanmasının ve taşınmayacağı anlamına gelir.  
  
<a name="Drag_and_Drop_Events"></a>   
## <a name="drag-and-drop-events"></a>Sürükle ve bırak olayları  
 Sürükle ve bırak işlemleri olay temelli bir modeli destekler.  Sürükleme kaynağı ve bırakma hedefi, sürükle ve bırak işlemlerini işlemek için standart bir olay kümesi kullanır.  Aşağıdaki tablolar, standart Sürükle ve bırak olaylarını özetler. Bunlar <xref:System.Windows.DragDrop> sınıfındaki ekli olaylardır. Ekli olaylar hakkında daha fazla bilgi için bkz. [ekli olaylara genel bakış](attached-events-overview.md).  
  
### <a name="drag-source-events"></a>Kaynak olaylarını sürükle  
  
|Olay|Özet|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.GiveFeedback>|Bu olay bir sürükle ve bırak işlemi sırasında sürekli gerçekleşir ve bırakma kaynağının kullanıcıya geri bildirim bilgileri vermesini sağlar. Bu geri bildirim genellikle, bırakma hedefinin izin verdiği etkileri göstermek üzere fare işaretçisinin görünümü değiştirilerek verilir.  Bu bir kabarcıklanma olayıdır.|  
|<xref:System.Windows.DragDrop.QueryContinueDrag>|Bu olay, sürükle ve bırak işlemi sırasında klavyede veya fare düğmesi durumunda olduğunda meydana gelir ve bırakma kaynağının anahtar/düğme durumlarına bağlı olarak sürükle ve bırak işlemini iptal etmesini sağlar. Bu bir kabarcıklanma olayıdır.|  
|<xref:System.Windows.DragDrop.PreviewGiveFeedback>|@No__t-0 ' ın Tünel sürümü.|  
|<xref:System.Windows.DragDrop.PreviewQueryContinueDrag>|@No__t-0 ' ın Tünel sürümü.|  
  
### <a name="drop-target-events"></a>Bırakma hedefi olayları  
  
|Olay|Özet|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.DragEnter>|Bu olay, bir nesne bırakma hedefinin sınırına sürüklendiğinde oluşur. Bu bir kabarcıklanma olayıdır.|  
|<xref:System.Windows.DragDrop.DragLeave>|Bu olay, bir nesne bırakma hedefinin sınırının dışına sürüklendiğinde oluşur.  Bu bir kabarcıklanma olayıdır.|  
|<xref:System.Windows.DragDrop.DragOver>|Bu olay, bırakma hedefinin sınırının içinde bir nesne sürüklendiğinde (taşındığında) sürekli gerçekleşir. Bu bir kabarcıklanma olayıdır.|  
|<xref:System.Windows.DragDrop.Drop>|Bu olay bırakma hedefinde bir nesne bırakıldığında oluşur.  Bu bir kabarcıklanma olayıdır.|  
|<xref:System.Windows.DragDrop.PreviewDragEnter>|@No__t-0 ' ın Tünel sürümü.|  
|<xref:System.Windows.DragDrop.PreviewDragLeave>|@No__t-0 ' ın Tünel sürümü.|  
|<xref:System.Windows.DragDrop.PreviewDragOver>|@No__t-0 ' ın Tünel sürümü.|  
|<xref:System.Windows.DragDrop.PreviewDrop>|@No__t-0 ' ın Tünel sürümü.|  
  
 Bir nesnenin örnekleri için sürükle ve bırak olaylarını işlemek için, önceki tablolarda listelenen olaylara yönelik işleyiciler ekleyin. Sürükle ve bırak olaylarını sınıf düzeyinde işlemek için, karşılık gelen sanal on * olayını ve @ no__t-0PreviewEvent yöntemlerini geçersiz kılın. Daha fazla bilgi için bkz. [temel sınıfları denetim aracılığıyla yönlendirilmiş olayların sınıf işlemesi](marking-routed-events-as-handled-and-class-handling.md#Class_Handling_of_Routed_Events).  
  
<a name="Implementing_Drag_And_Drop"></a>   
## <a name="implementing-drag-and-drop"></a>Sürükle ve bırak uygulama  
 Bir kullanıcı arabirimi öğesi, bir Sürükle kaynağı, bir bırakma hedefi veya her ikisi olabilir. Temel sürükle ve bırak uygulamak için sürükle ve bırak işlemini başlatmak ve bırakılan verileri işlemek için kod yazarsınız. Sürükleme ve bırakma deneyimini, isteğe bağlı sürükle ve bırak olaylarını işleyerek geliştirebilirsiniz.  
  
 Temel sürükle ve bırak uygulamak için aşağıdaki görevleri tamamlayacaksınız:  
  
- Sürükle kaynağı olacak öğeyi belirler. Sürükle kaynağı bir <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement> olabilir.  
  
- Sürükleme kaynağında sürükle ve bırak işlemini başlatacak bir olay işleyicisi oluşturun. Olay genellikle <xref:System.Windows.UIElement.MouseMove> olayıdır.  
  
- Sürükle ve bırak işlemini başlatmak için kaynak olay işleyicide <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemini çağırın. @No__t-0 çağrısında, sürükleme kaynağını, aktarılacak verileri ve izin verilen etkileri belirtin.  
  
- Bırakma hedefi olacak öğeyi belirler. Bırakma hedefi <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement> olabilir.  
  
- Bırakma hedefinde <xref:System.Windows.UIElement.AllowDrop%2A> özelliğini `true` olarak ayarlayın.  
  
- Bırakma hedefinde, bırakılan verileri işlemek için bir <xref:System.Windows.DragDrop.Drop> olay işleyicisi oluşturun.  
  
- @No__t-0 olay işleyicisinde, <xref:System.Windows.DataObject.GetDataPresent%2A> ve <xref:System.Windows.DataObject.GetData%2A> yöntemlerini kullanarak verileri <xref:System.Windows.DragEventArgs> ' den ayıklayın.  
  
- @No__t-0 olay işleyicisinde, istenen sürükleme ve bırakma işlemini gerçekleştirmek için verileri kullanın.  
  
 Sürükle ve bırak uygulamanızı, aşağıdaki görevlerde gösterildiği gibi, özel bir <xref:System.Windows.DataObject> oluşturarak ve isteğe bağlı Sürükle kaynak ve bırakma hedefi olaylarını işleyerek geliştirebilirsiniz:  
  
- Özel verileri veya birden çok veri öğesini aktarmak için, <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemine geçirilecek <xref:System.Windows.DataObject> oluşturun.  
  
- Sürükleme sırasında ek eylemler gerçekleştirmek için, bırakma hedefinde <xref:System.Windows.DragDrop.DragEnter>, <xref:System.Windows.DragDrop.DragOver> ve <xref:System.Windows.DragDrop.DragLeave> olaylarını işleyin.  
  
- Fare işaretçisinin görünüşünü değiştirmek için sürükle kaynağında <xref:System.Windows.DragDrop.GiveFeedback> olayını işleyin.  
  
- Sürükle ve bırak işleminin nasıl iptal edildiğini değiştirmek için sürükle kaynağında <xref:System.Windows.DragDrop.QueryContinueDrag> olayını işleyin.  
  
<a name="Drag_And_Drop_Example"></a>   
## <a name="drag-and-drop-example"></a>Sürükle ve bırak örneği  
 Bu bölümde, <xref:System.Windows.Shapes.Ellipse> öğesi için sürükle ve bırak 'ın nasıl uygulanacağı açıklanmaktadır. @No__t-0 hem Sürükle kaynağı hem de bırakma hedefidir. Aktarılan veriler, elipsin <xref:System.Windows.Shapes.Shape.Fill%2A> özelliğinin dize gösterimidir. Aşağıdaki XAML <xref:System.Windows.Shapes.Ellipse> öğesini ve işlediği sürükle ve bırak ile ilgili olayları gösterir. Sürükleyip bırakmayı uygulama hakkında tam adımlar için bkz. [Izlenecek yol: Kullanıcı denetiminde sürükleme ve bırakmayı etkinleştirme](walkthrough-enabling-drag-and-drop-on-a-user-control.md).  
  
 [!code-xaml[DragDropSnippets#EllipseXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#ellipsexaml)]  
  
### <a name="enabling-an-element-to-be-a-drag-source"></a>Bir öğenin sürükle kaynağı olmasını sağlama  
 Sürükleme kaynağı olan bir nesne şu kaynaktan sorumludur:  
  
- Bir sürükleme işleminin ne zaman gerçekleşeceğini tanımlama.  
  
- Sürükle ve bırak işlemi başlatılıyor.  
  
- Aktarılacak verileri tanımlama.  
  
- Sürükle ve bırak işleminin aktarılan verilerde sahip olmasına izin verilen etkileri belirtme.  
  
 Sürükleme kaynağı, kullanıcıya izin verilen eylemlerle ilgili geri bildirimde bulunabilir (taşıma, kopyalama, yok) ve sürükleme sırasında ESC tuşuna basmak gibi, sürükle ve bırak işlemini ek kullanıcı girişine göre iptal edebilir.  
  
 Bu, bir sürükleme işleminin ne zaman gerçekleşeceğini tespit etmek ve sonra <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemini çağırarak Sürükle ve bırak işlemini başlatmak için uygulamanızın sorumluluğundadır. Genellikle, bu, fare düğmesine basıldığında sürüklediğiniz öğe üzerinde <xref:System.Windows.UIElement.MouseMove> olayı meydana geldi. Aşağıdaki örnek, bir sürükleme kaynağı yapmak için bir <xref:System.Windows.Shapes.Ellipse> öğesinin <xref:System.Windows.UIElement.MouseMove> olay işleyicisinden bir sürükle ve bırak işleminin nasıl başlatılacağı gösterilmektedir. Aktarılan veriler, elipsin <xref:System.Windows.Shapes.Shape.Fill%2A> özelliğinin dize gösterimidir.  
  
 [!code-csharp[DragDropSnippets#DoDragDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dodragdrop)]
 [!code-vb[DragDropSnippets#DoDragDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dodragdrop)]  
  
 @No__t-0 olay işleyicisinin içinde, sürükle ve bırak işlemini başlatmak için <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemini çağırın. @No__t-0 yöntemi üç parametre alır:  
  
- `dragSource` – aktarılan verilerin kaynağı olan Dependency nesnesine bir başvuru; Bu genellikle <xref:System.Windows.UIElement.MouseMove> olayının kaynağıdır.  
  
- `data`-<xref:System.Windows.DataObject> ' de kaydırılan, aktarılan verileri içeren bir nesne.  
  
- `allowedEffects`-sürükle ve bırak işleminin izin verilen efektlerini belirten <xref:System.Windows.DragDropEffects> sabit listesi değerlerinden biridir.  
  
 Herhangi bir serileştirilebilir nesne `data` parametresine geçirilebilir. Veriler zaten bir <xref:System.Windows.DataObject> ' a sarılmadığından, otomatik olarak yeni bir <xref:System.Windows.DataObject> ' i sarmalanır. Birden çok veri öğesi geçirmek için <xref:System.Windows.DataObject> ' ı oluşturmanız ve <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemine geçirmeniz gerekir. Daha fazla bilgi için bkz. [veri ve veri nesneleri](data-and-data-objects.md).  
  
 @No__t-0 parametresi, sürükleme kaynağının, aktarılan verilerle birlikte bırakma hedefinin ne izin verbileceklerini belirtmek için kullanılır. Bir sürükleme kaynağı için ortak değerler <xref:System.Windows.DragDropEffects.Copy>, <xref:System.Windows.DragDropEffects.Move> ve <xref:System.Windows.DragDropEffects.All> ' dir.  
  
> [!NOTE]
> Bırakma hedefi, bırakılan verilere yanıt olarak hangi etkileri amaçladığı de belirtebilir. Örneğin, bırakma hedefi bırakılacak veri türünü tanımazsa, izin verilen etkileri <xref:System.Windows.DragDropEffects.None> olarak ayarlayarak verileri reddedebilirler. Bu, genellikle <xref:System.Windows.DragDrop.DragOver> olay işleyicisinde bunu yapar.  
  
 Sürükleme kaynağı isteğe bağlı olarak <xref:System.Windows.DragDrop.GiveFeedback> ve <xref:System.Windows.DragDrop.QueryContinueDrag> olaylarını işleyebilir. Olayları işlenmiş olarak işaretlemediğiniz sürece bu olayların varsayılan işleyicileri kullanılır. Genellikle bu olayları, varsayılan davranışlarını değiştirmek için özel bir işlem yapmanız gerekmedikçe yoksayabilirsiniz.  
  
 Sürükleme kaynağı sürüklenirken <xref:System.Windows.DragDrop.GiveFeedback> olayı sürekli olarak oluşturulur. Bu olay için varsayılan işleyici, sürükleme kaynağının geçerli bir bırakma hedefi üzerinde olup olmadığını denetler. Varsa, bırakma hedefinin izin verilen efektlerini denetler. Daha sonra, izin verilen bırakma efektleriyle ilgili olarak son kullanıcıya geri bildirim sağlar. Bu, genellikle fare imlecini bırakma, kopyalama veya taşıma imlecine göre değiştirilerek yapılır. Yalnızca kullanıcıya geri bildirim sağlamak için özel imleçler kullanmanız gerekiyorsa bu olayı işlemeniz gerekir. Bu olayı idare ederseniz, varsayılan işleyicinin işleyicinizi geçersiz kılmaması için, onu işlenmiş olarak işaretlediğinizden emin olun.  
  
 Sürükleme kaynağı sürüklenirken <xref:System.Windows.DragDrop.QueryContinueDrag> olayı sürekli olarak oluşturulur. Bu olayı, sürükle ve bırak işlemini ESC, SHIFT, CTRL ve ALT tuşlarının yanı sıra fare düğmelerinin durumunu temel alarak hangi eylemin bittiğini belirlemek için işleyebilirsiniz. Bu olay için varsayılan işleyici, ESC tuşuna basıldığında sürükle ve bırak işlemini iptal eder ve fare düğmesi serbest bırakıldığında verileri bırakır.  
  
> [!CAUTION]
> Bu olaylar, sürükle ve bırak işlemi sırasında sürekli olarak oluşturulur. Bu nedenle, olay işleyicilerinde kaynakların yoğun görevlerinin olmaması gerekir.  Örneğin, <xref:System.Windows.DragDrop.GiveFeedback> olayı her başlatıldığında yeni bir imleç oluşturmak yerine önbelleğe alınmış bir imleç kullanın.  
  
### <a name="enabling-an-element-to-be-a-drop-target"></a>Bir öğeyi bırakma hedefi olarak etkinleştirme  
 Bırakma hedefi olan bir nesne, öğesinden sorumludur:  
  
- Bunun geçerli bir bırakma hedefi olduğunu belirtme.  
  
- Hedef üzerine sürüklendiğinde sürükle kaynağına yanıt verme.  
  
- Aktarılan verilerin alabileceği bir biçimde olup olmadığı denetleniyor.  
  
- Bırakılan veriler işleniyor.  
  
 Bir öğenin bırakma hedefi olduğunu belirtmek için, <xref:System.Windows.UIElement.AllowDrop%2A> özelliğini `true` olarak ayarlayın. Bırakma hedefi olayları, daha sonra işleyebilmeniz için öğesi üzerinde oluşturulur. Bir sürükle ve bırak işlemi sırasında, bırakma hedefinde aşağıdaki olay dizisi gerçekleşir:  
  
1. <xref:System.Windows.DragDrop.DragEnter>  
  
2. <xref:System.Windows.DragDrop.DragOver>  
  
3. <xref:System.Windows.DragDrop.DragLeave> veya <xref:System.Windows.DragDrop.Drop>  
  
 @No__t-0 olayı, veriler bırakma hedefinin sınırına sürüklendiğinde oluşur. Bu olayı genellikle, uygulamanız için uygunsa sürükle ve bırak işleminin etkilerinin önizlemesini sağlamak üzere işleyebilirsiniz. @No__t-2 olayında üzerine yazılacağı için <xref:System.Windows.DragDrop.DragEnter> olayında <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> özelliğini ayarlamayın.  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Ellipse> öğesi için <xref:System.Windows.DragDrop.DragEnter> olay işleyicisi gösterilmektedir. Bu kod, geçerli <xref:System.Windows.Shapes.Shape.Fill%2A> fırçasını kaydederek sürükle ve bırak işleminin etkilerini önizlemeler. Daha sonra, elips üzerine sürüklemekte olan <xref:System.Windows.DataObject> ' in <xref:System.Windows.Media.Brush> ' ye dönüştürülebilen dize verileri içerip içermediğini denetlemek için <xref:System.Windows.DataObject.GetDataPresent%2A> yöntemini kullanır. Bu durumda, veriler <xref:System.Windows.DataObject.GetData%2A> yöntemi kullanılarak ayıklanır. Daha sonra <xref:System.Windows.Media.Brush> ' a dönüştürülür ve elips 'e uygulanır. Değişiklik, <xref:System.Windows.DragDrop.DragLeave> olay işleyicisine geri döndürülür. Veriler <xref:System.Windows.Media.Brush> ' a dönüştürülemiyorsa hiçbir işlem yapılmaz.  
  
 [!code-csharp[DragDropSnippets#DragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragenter)]
 [!code-vb[DragDropSnippets#DragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragenter)]  
  
 @No__t-0 olayı, veriler bırakma hedefinin üzerine sürüklenirken sürekli gerçekleşir. Bu olay, sürükle kaynağında <xref:System.Windows.DragDrop.GiveFeedback> olayı ile eşleştirilmiş. @No__t-0 olay işleyicisinde, genellikle aktarılan verilerin bırakma hedefinin işleyebilip işlenemediğini denetlemek için <xref:System.Windows.DataObject.GetDataPresent%2A> ve <xref:System.Windows.DataObject.GetData%2A> yöntemlerini kullanırsınız. Ayrıca, bir değiştirici tuşuna basıldığında, genellikle kullanıcının bir taşıma veya kopyalama eylemi yapıp belirtmediğini de denetleyebilirsiniz. Bu denetimler gerçekleştirildikten sonra, sürükleme kaynağını, verilerin hangi etkilerden olacağını bildirmek için <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> özelliğini ayarlarsınız. Sürükleme kaynağı bu bilgileri <xref:System.Windows.DragDrop.GiveFeedback> olay bağımsız değişkenlerinin içinde alır ve kullanıcıya geri bildirim vermek için uygun bir imleç ayarlayabilir.  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Ellipse> öğesi için <xref:System.Windows.DragDrop.DragOver> olay işleyicisi gösterilmektedir. Bu kod, elips üzerinde sürüklenen @no__t, bir <xref:System.Windows.Media.Brush> ' e dönüştürülebilen dize verileri içerip içermediğini kontrol eder. Bu durumda, <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> özelliğini <xref:System.Windows.DragDropEffects.Copy> olarak ayarlar. Bu, sürükle kaynağına verilerin elips 'e kopyalanamayacağını gösterir. Veriler <xref:System.Windows.Media.Brush> ' a dönüştürülemiyorsa, <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> özelliği <xref:System.Windows.DragDropEffects.None> olarak ayarlanır. Bu, sürükle kaynağına, elipsin veri için geçerli bir bırakma hedefi olmadığını gösterir.  
  
 [!code-csharp[DragDropSnippets#DragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragover)]
 [!code-vb[DragDropSnippets#DragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragover)]  
  
 @No__t-0 olayı, veriler bırakılmadan hedefin sınırının dışına sürüklendiğinde oluşur. @No__t-0 olay işleyicisinde yaptığınız herhangi bir şeyi geri almak için bu olayı işleyebilirsiniz.  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Ellipse> öğesi için <xref:System.Windows.DragDrop.DragLeave> olay işleyicisi gösterilmektedir. Bu kod, <xref:System.Windows.DragDrop.DragEnter> olay işleyicisinde gerçekleştirilen önizlemeyi geri alır ve kayıtlı <xref:System.Windows.Media.Brush> ' i elips öğesine uygulayarak.  
  
 [!code-csharp[DragDropSnippets#DragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragleave)]
 [!code-vb[DragDropSnippets#DragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragleave)]  
  
 @No__t-0 olayı, veriler bırakma hedefinin üzerine bırakıldığında oluşur; Bu, varsayılan olarak fare düğmesi bırakıldığında gerçekleşir. @No__t-0 olay işleyicisinde, <xref:System.Windows.DataObject> ' den aktarılan verileri ayıklamak ve uygulamanızın gerektirdiği tüm veri işlemlerini gerçekleştirmek için <xref:System.Windows.DataObject.GetData%2A> yöntemini kullanırsınız. @No__t-0 olayı sürükle ve bırak işlemini sonlandırır.  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Ellipse> öğesi için <xref:System.Windows.DragDrop.Drop> olay işleyicisi gösterilmektedir. Bu kod, sürükle ve bırak işleminin etkilerini uygular ve <xref:System.Windows.DragDrop.DragEnter> olay işleyicisindeki koda benzerdir. Elips üzerinde sürüklenen @no__t, bir <xref:System.Windows.Media.Brush> ' e dönüştürülebilen dize verileri içerip içermediğini kontrol eder. Bu durumda, <xref:System.Windows.Media.Brush>, elips 'e uygulanır. Veriler <xref:System.Windows.Media.Brush> ' a dönüştürülemiyorsa hiçbir işlem yapılmaz.  
  
 [!code-csharp[DragDropSnippets#Drop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#drop)]
 [!code-vb[DragDropSnippets#Drop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#drop)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Clipboard>
- [İzlenecek yol: Kullanıcı denetiminde sürükleme ve bırakmayı etkinleştirme](walkthrough-enabling-drag-and-drop-on-a-user-control.md)
- [Nasıl yapılır konuları](drag-and-drop-how-to-topics.md)
- [Sürükleyip bırakma](drag-and-drop.md)
