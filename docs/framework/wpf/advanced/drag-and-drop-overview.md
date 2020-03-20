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
ms.openlocfilehash: dd42af77300a7a93bbcbfa4c8f1fc365fc3f5da1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185975"
---
# <a name="drag-and-drop-overview"></a>Sürükleme ve Bırakmaya Genel Bakış
Bu konu, uygulamalardaki [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sürükle ve bırak desteğine genel bir bakış sağlar. Sürükle ve bırak genellikle, bir veya daha fazla nesneyi seçmek için fare (veya başka bir işaretleme aygıtı) kullanarak, bu nesneleri [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]istenen bir bırakma hedefinin üzerine sürükleyerek ve bunları bırakarak içeren bir veri aktarım yöntemini ifade eder.  

<a name="Drag_and_Drop_Support"></a>
## <a name="drag-and-drop-support-in-wpf"></a>WPF'de Sürükle ve Bırak Desteği  
 Sürükle ve bırak işlemleri genellikle iki taraf içerir: sürüklenen nesnenin kaynağı olan bir sürükleme kaynağı ve bırakılan nesneyi alan bir bırakma hedefi.  Sürükle kaynağı ve bırak hedefi aynı uygulamada veya farklı bir uygulamada Kullanıcı Arabirimi öğeleri olabilir.  
  
 Sürükle ve bırak ile değiştirilebilen nesnelerin türü ve sayısı tamamen rasgeledir. Örneğin, dosya, klasör ve içerik seçimleri sürükle ve bırak işlemleri yle manipüle edilen daha yaygın nesnelerden bazılarıdır.  
  
 Sürükle ve bırak işlemi sırasında gerçekleştirilen belirli eylemler uygulamaya özgütür ve genellikle bağlam tarafından belirlenir.  Örneğin, aynı depolama aygıtında bir dosya seçimini bir klasörden diğerine sürüklemek dosyaları varsayılan olarak taşırken, dosyaları Evrensel Adlandırma Sözleşmesi (UNC) paylaşımından yerel bir klasöre sürüklemek dosyaları varsayılan olarak kopyalar.  
  
 Sürükle ve bırak tesisleri, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çok çeşitli sürükle ve bırak senaryolarını destekleyecek şekilde son derece esnek ve özelleştirilebilir olacak şekilde tasarlanmıştır.  Sürükle ve bırak, nesneleri tek bir uygulama içinde veya farklı uygulamalar arasında işlemeyi destekler. Uygulamalar ve diğer Windows [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları arasında sürükleme ve bırakma da tam olarak desteklenir.  
  
 Içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement> herhangi bir veya sürükle-ve-bırak katılabilir. Sürükle ve bırak işlemleri için gereken olaylar ve <xref:System.Windows.DragDrop> yöntemler sınıfta tanımlanır. Ve <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement> sınıflar, a <xref:System.Windows.DragDrop> <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement> temel öğe olarak devralınan olaylar sınıf üyeleri listesinde görünmesi için ekli olaylar için takma adlar içerir. Bu olaylara iliştirilen olay işleyicileri <xref:System.Windows.DragDrop> altta yatan bağlı olaya eklenir ve aynı olay veri örneğini alır. Daha fazla bilgi <xref:System.Windows.UIElement.Drop?displayProperty=nameWithType> için olaya bakın.  
  
> [!IMPORTANT]
> OLE sürükle ve bırak, Internet bölgesindeyken çalışmaz.  
  
<a name="Data_Transfer"></a>
## <a name="data-transfer"></a>Veri Aktarımı  
 Sürükle ve bırak, daha genel veri aktarım alanının bir parçasıdır. Veri aktarımı sürükle ve bırak ve kopyala ve yapıştır işlemlerini içerir. Sürükle ve bırak işlemi, sistem panosunu kullanarak bir nesneden veya uygulamadan diğerine veri aktarmak için kullanılan bir kopyala-yapıştır veya kes-yapıştır işlemiyle benzer. Her iki tür de şunları gerektirir:  
  
- Verileri sağlayan bir kaynak nesne.  
  
- Aktarılan verileri geçici olarak depolamanın bir yolu.  
  
- Verileri alan hedef nesne.  
  
 Bir kopyalama ve yapıştır işleminde, sistem panosu aktarılan verileri geçici olarak depolamak için kullanılır; bir sürükle ve bırak işleminde, verileri depolamak için a <xref:System.Windows.DataObject> kullanılır. Kavramsal olarak, bir veri nesnesi, gerçek <xref:System.Object> verileri içeren bir veya daha fazla çift ve karşılık gelen veri biçimi tanımlayıcısı oluşur.  
  
 Sürükleme kaynağı statik <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> yöntemi çağırarak ve aktarılan verileri ona aktararak sürükle ve bırak işlemini başlatır. Yöntem, <xref:System.Windows.DragDrop.DoDragDrop%2A> gerekirse verileri otomatik olarak <xref:System.Windows.DataObject> bir şekilde sarar. Veri biçimi üzerinde daha fazla denetim için, <xref:System.Windows.DataObject> yöntemi geçmeden <xref:System.Windows.DragDrop.DoDragDrop%2A> önce bir veri sarın. Bırakma hedefi, 'den veri ayıklama <xref:System.Windows.DataObject>sorumludur. Veri nesneleriyle çalışma hakkında daha fazla bilgi için [Bkz. Veri ve Veri Nesneleri.](data-and-data-objects.md)  
  
 Sürükle ve bırak işleminin kaynağı ve hedefi UI öğeleridir; ancak, gerçekte aktarılan verilerin genellikle görsel bir gösterimi yoktur. Windows Gezgini'nde dosyaları sürüklerken meydana gelen gibi sürüklenen verilerin görsel bir temsilini sağlamak için kod yazabilirsiniz. Varsayılan olarak, geribildirim, sürükle ve bırak işleminin veriler üzerinde sahip olacağı etkiyi (örneğin, verilerin taşınıp taşınmayacağı veya kopyalansın) temsil edecek şekilde imleci değiştirerek kullanıcıya sağlanır.  
  
### <a name="drag-and-drop-effects"></a>Sürükle ve Bırak Efektleri  
 Sürükle ve bırak işlemleri aktarılan veriler üzerinde farklı etkilere sahip olabilir. Örneğin, verileri kopyalayabilir veya verileri taşıyabilirsiniz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.DragDropEffects> sürükle ve bırak işleminin etkisini belirtmek için kullanabileceğiniz bir numaralandırma tanımlar. Sürükleme kaynağında, kaynağın <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemde izin verdiği efektleri belirtebilirsiniz. Bırakma hedefinde, hedefin <xref:System.Windows.DragEventArgs.Effects%2A> <xref:System.Windows.DragEventArgs> sınıfın özelliğinde amaçladığını belirtebilirsiniz. Açılan hedef <xref:System.Windows.DragDrop.DragOver> olaydaki amaçlanan etkisini belirttiğinde, bu bilgiler <xref:System.Windows.DragDrop.GiveFeedback> olaydaki sürükleme kaynağına geri aktarılır. Sürükleme kaynağı, bırakma hedefinin veriler üzerinde ne gibi bir etkiye sahip olmayı amaçlaları kullanıcıya bildirmek için bu bilgileri kullanır. Veriler bırakıldığında, bırakma hedefi <xref:System.Windows.DragDrop.Drop> olaydaki gerçek etkisini belirtir. Bu bilgiler, yöntemin geri dönüş değeri olarak <xref:System.Windows.DragDrop.DoDragDrop%2A> sürükleme kaynağına geri aktarılır. Açılan hedef sürükle kaynakları listesinde olmayan bir efekti `allowedEffects`döndürürse, sürükle ve bırak işlemi herhangi bir veri aktarımı oluşmadan iptal edilir.  
  
 Bu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.DragDropEffects> değerler, yalnızca sürükle kaynağı ve bırak hedefi arasında sürükleme ve bırak işleminin etkileri ile ilgili iletişim sağlamak için kullanılır hatırlamak önemlidir. Sürükle ve bırak işleminin gerçek etkisi, uygulamanızda uygun kodu yazmanıza bağlıdır.  
  
 Örneğin, bırakma hedefi, üzerinde veri bırakmanın etkisinin verileri taşımak olduğunu belirtebilir. Ancak, verileri taşımak için hem hedef öğeye eklenmesi ve kaynak öğesinden kaldırılması gerekir. Kaynak öğe, verilerin taşınmasına izin verdiğini gösterebilir, ancak verileri kaynak öğeden kaldırmak için kodu sağlamazsanız, sonuç olarak sonuç verilerin kopyalanması ve taşınmaması olacaktır.  
  
<a name="Drag_and_Drop_Events"></a>
## <a name="drag-and-drop-events"></a>Sürükle ve Bırak Etkinlikleri  
 Sürükle ve bırak işlemleri olay odaklı bir modeli destekler.  Hem sürükle kaynağı hem de bırak hedefi sürükle ve bırak işlemlerini işlemek için standart bir olay kümesi kullanır.  Aşağıdaki tablolar standart sürükle ve bırak olaylarını özetler. Bunlar sınıftaki <xref:System.Windows.DragDrop> eklenmiş olaylardır. Ekteki olaylar hakkında daha fazla bilgi için [bkz.](attached-events-overview.md)  
  
### <a name="drag-source-events"></a>Kaynak Olaylarını Sürükleyin  
  
|Olay|Özet|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.GiveFeedback>|Bu olay sürükle ve bırak işlemi sırasında sürekli olarak gerçekleşir ve bırakma kaynağının kullanıcıya geri bildirim bilgilerini vermesini sağlar. Bu geri bildirim genellikle, bırakma hedefitarafından izin verilen efektleri belirtmek için fare işaretçisinin görünümünü değiştirerek verilir.  Bu köpüren bir olay.|  
|<xref:System.Windows.DragDrop.QueryContinueDrag>|Bu olay, sürükle ve bırak işlemi sırasında klavye veya fare düğmesi durumlarında bir değişiklik olduğunda oluşur ve bırak kaynağının tuş/düğme durumlarına bağlı olarak sürükle ve bırak işlemini iptal etmesini sağlar. Bu köpüren bir olay.|  
|<xref:System.Windows.DragDrop.PreviewGiveFeedback>|Tünel sürümü <xref:System.Windows.DragDrop.GiveFeedback>.|  
|<xref:System.Windows.DragDrop.PreviewQueryContinueDrag>|Tünel sürümü <xref:System.Windows.DragDrop.QueryContinueDrag>.|  
  
### <a name="drop-target-events"></a>Hedef Olayları Bırak  
  
|Olay|Özet|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.DragEnter>|Bu olay, bir nesne bırakma hedefinin sınırına sürüklendiğinde oluşur. Bu köpüren bir olay.|  
|<xref:System.Windows.DragDrop.DragLeave>|Bu olay, bir nesne bırakma hedefinin sınırından çıkarıldığında oluşur.  Bu köpüren bir olay.|  
|<xref:System.Windows.DragDrop.DragOver>|Bu olay, bir nesne bırakma hedefinin sınırı içinde sürüklenirken (taşınırken) sürekli olarak oluşur. Bu köpüren bir olay.|  
|<xref:System.Windows.DragDrop.Drop>|Bu olay, bir nesne açılan hedefe bırakıldığında oluşur.  Bu köpüren bir olay.|  
|<xref:System.Windows.DragDrop.PreviewDragEnter>|Tünel sürümü <xref:System.Windows.DragDrop.DragEnter>.|  
|<xref:System.Windows.DragDrop.PreviewDragLeave>|Tünel sürümü <xref:System.Windows.DragDrop.DragLeave>.|  
|<xref:System.Windows.DragDrop.PreviewDragOver>|Tünel sürümü <xref:System.Windows.DragDrop.DragOver>.|  
|<xref:System.Windows.DragDrop.PreviewDrop>|Tünel sürümü <xref:System.Windows.DragDrop.Drop>.|  
  
 Bir nesnenin örnekleri için sürükle ve bırak olaylarını işlemek için, önceki tablolarda listelenen olaylar için işleyiciler ekleyin. Sürükle ve bırak olaylarını sınıf düzeyinde işlemek için, ilgili sanal\*On*Event ve PreviewEvent yöntemlerini geçersiz kılın. Daha fazla bilgi için [bkz.](marking-routed-events-as-handled-and-class-handling.md#Class_Handling_of_Routed_Events)  
  
<a name="Implementing_Drag_And_Drop"></a>
## <a name="implementing-drag-and-drop"></a>Sürükle ve Bırak'ı Uygulama  
 UI öğesi sürükle kaynağı, bırakma hedefi veya her ikisi olabilir. Temel sürükle ve bırak'ı uygulamak için sürükle ve bırak işlemini başlatmak ve bırakılan verileri işlemek için kod yazarsınız. İsteğe bağlı sürükle ve bırak olaylarını işleyerek sürükle ve bırak deneyimini geliştirebilirsiniz.  
  
 Temel sürükle ve bırak'ı uygulamak için aşağıdaki görevleri tamamlarsınız:  
  
- Sürükleme kaynağı olacak öğeyi tanımlayın. Sürükleme kaynağı bir <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement>.  
  
- Sürükle ve bırak işlemini başlatacak sürükleme kaynağında bir olay işleyicisi oluşturun. Olay genellikle <xref:System.Windows.UIElement.MouseMove> olaydır.  
  
- Sürükle kaynağı olay işleyicisinde, sürükle ve bırak işlemini başlatmak için <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemi çağırın. <xref:System.Windows.DragDrop.DoDragDrop%2A> Çağrıda, sürükle kaynağını, aktarılacak verileri ve izin verilen efektleri belirtin.  
  
- Bırakma hedefi olacak öğeyi tanımlayın. Bir bırakma hedefi <xref:System.Windows.UIElement> olabilir <xref:System.Windows.ContentElement>ya da .  
  
- Açılan hedefte, <xref:System.Windows.UIElement.AllowDrop%2A> özelliği . `true`  
  
- Açılan hedefte, bırakılan <xref:System.Windows.DragDrop.Drop> verileri işlemek için bir olay işleyicisi oluşturun.  
  
- Olay <xref:System.Windows.DragDrop.Drop> işleyicisi, ve <xref:System.Windows.DataObject.GetData%2A> yöntemleri <xref:System.Windows.DragEventArgs> kullanarak <xref:System.Windows.DataObject.GetDataPresent%2A> verileri ayıklayın.  
  
- Olay <xref:System.Windows.DragDrop.Drop> işleyicisi, istenen sürükle ve bırak işlemini gerçekleştirmek için verileri kullanın.  
  
 Özel <xref:System.Windows.DataObject> bir oluşturma ve aşağıdaki görevlerde gösterildiği gibi isteğe bağlı sürükle kaynağı ve bırak hedef olayları işleyerek sürükle ve bırak uygulamanızı geliştirebilirsiniz:  
  
- Özel veri veya birden çok veri <xref:System.Windows.DataObject> öğesi aktarmak <xref:System.Windows.DragDrop.DoDragDrop%2A> için yönteme geçmek için bir yöntem oluşturun.  
  
- Sürükleme sırasında ek eylemler gerçekleştirmek <xref:System.Windows.DragDrop.DragEnter>için, <xref:System.Windows.DragDrop.DragLeave> açılan hedefteki , ve <xref:System.Windows.DragDrop.DragOver>olayları işleyin.  
  
- Fare işaretçisinin görünümünü değiştirmek <xref:System.Windows.DragDrop.GiveFeedback> için, olayı sürükleme kaynağında işleyebilir.  
  
- Sürükle ve bırak işleminin nasıl iptal edildiğini <xref:System.Windows.DragDrop.QueryContinueDrag> değiştirmek için, olayı sürükleme kaynağında işleyebilir.  
  
<a name="Drag_And_Drop_Example"></a>
## <a name="drag-and-drop-example"></a>Sürükle ve Bırak Örneği  
 Bu bölümde, bir <xref:System.Windows.Shapes.Ellipse> öğe için sürükle ve bırak nasıl uygulanacağı açıklanmaktadır. Hem <xref:System.Windows.Shapes.Ellipse> bir sürükleme kaynağı hem de bir bırakma hedefidir. Aktarılan veriler, elipsin <xref:System.Windows.Shapes.Shape.Fill%2A> özelliğinin dize gösterimidir. Aşağıdaki XAML, <xref:System.Windows.Shapes.Ellipse> işlettiği öğeyi ve sürükle ve bırak ilgili olayları gösterir. Sürükle ve bırak'ın nasıl uygulanacağı yla ilgili tam adımlar için [Walkthrough: Sürükle ve Bırak'ı Kullanıcı Denetiminde Etkinleştirme'ye](walkthrough-enabling-drag-and-drop-on-a-user-control.md)bakın.  
  
 [!code-xaml[DragDropSnippets#EllipseXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#ellipsexaml)]  
  
### <a name="enabling-an-element-to-be-a-drag-source"></a>Öğenin Sürükle Kaynağı Olmasını Etkinleştirme  
 Sürükleme kaynağı olan bir nesne sorumludur:  
  
- Sürükleme ne zaman oluştuğunu tanımlama.  
  
- Sürükle ve bırak işlemini başlatılır.  
  
- Aktarılacak verilerin tanımlanması.  
  
- Sürükle ve bırak işleminin aktarılan veriler üzerinde sahip olması için izin verilen etkileri belirtilmesi.  
  
 Sürükleme kaynağı ayrıca kullanıcıya izin verilen eylemlerle ilgili geri bildirimde bulunabilir (taşıma, kopyalama, hiçbiri) ve sürükleme sırasında ESC tuşuna basmak gibi ek kullanıcı girişine dayalı sürükle ve bırak işlemini iptal edebilir.  
  
 Sürüklemenin ne zaman oluştuğunu belirlemek ve <xref:System.Windows.DragDrop.DoDragDrop%2A> ardından yöntemi arayarak sürükle ve bırak işlemini başlatmak uygulamanızın sorumluluğundadır. Genellikle, fare düğmesine <xref:System.Windows.UIElement.MouseMove> basıldığında sürülecek öğenin üzerinde bir olay oluşur. Aşağıdaki örnek, bir <xref:System.Windows.UIElement.MouseMove> <xref:System.Windows.Shapes.Ellipse> öğenin olay işleyicisinden sürükle ve bırak işlemini nasıl başlatırıcı hale getirin. Aktarılan veriler, elipsin <xref:System.Windows.Shapes.Shape.Fill%2A> özelliğinin dize gösterimidir.  
  
 [!code-csharp[DragDropSnippets#DoDragDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dodragdrop)]
 [!code-vb[DragDropSnippets#DoDragDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dodragdrop)]  
  
 Olay işleyicisinin <xref:System.Windows.UIElement.MouseMove> içinde sürükle ve bırak işlemini başlatmak için <xref:System.Windows.DragDrop.DoDragDrop%2A> yöntemi arayın. Yöntem <xref:System.Windows.DragDrop.DoDragDrop%2A> üç parametre alır:  
  
- `dragSource`– Aktarılan verilerin kaynağı olan bağımlılık nesnesine bir başvuru; bu genellikle <xref:System.Windows.UIElement.MouseMove> olayın kaynağıdır.  
  
- `data`- Aktarılan verileri içeren bir nesne, <xref:System.Windows.DataObject>bir .  
  
- `allowedEffects`- Sürükle <xref:System.Windows.DragDropEffects> ve bırak işleminin izin verilen etkilerini belirten numaralandırma değerlerinden biri.  
  
 Herhangi bir serileştirilebilir nesne `data` parametre geçirilebilir. Veriler zaten bir <xref:System.Windows.DataObject>sarılmış değilse, otomatik olarak yeni <xref:System.Windows.DataObject>bir . Birden çok veri öğesini geçirmek <xref:System.Windows.DataObject> için, kendinizi oluşturmanız ve yönteme aktarmanız <xref:System.Windows.DragDrop.DoDragDrop%2A> gerekir. Daha fazla bilgi için [Bkz. Veri ve Veri Nesneleri.](data-and-data-objects.md)  
  
 Parametre, `allowedEffects` sürükleme kaynağının damla hedefinin aktarılan verilerle ne yapmasına izin vereceğini belirtmek için kullanılır. Sürükleme kaynağının ortak değerleri <xref:System.Windows.DragDropEffects.Copy> <xref:System.Windows.DragDropEffects.Move>, <xref:System.Windows.DragDropEffects.All>ve .  
  
> [!NOTE]
> Bırakma hedefi, bırakılan verilere yanıt olarak hangi etkileri hedeflenebildiğini de belirtebilir. Örneğin, bırakma hedefi bırakılacak veri türünü tanımıyorsa, izin verilen efektleri <xref:System.Windows.DragDropEffects.None>. Genellikle olay işleyicisi <xref:System.Windows.DragDrop.DragOver> bunu yapar.  
  
 Sürükleme kaynağı isteğe bağlı <xref:System.Windows.DragDrop.GiveFeedback> <xref:System.Windows.DragDrop.QueryContinueDrag> olarak olayları ve olayları işleyebilir. Bu olaylar, işlenen olayları işaretlemediğiniz sürece kullanılan varsayılan işleyicileri vardır. Varsayılan davranışlarını değiştirmeniz gereken belirli bir gereksinim yoksa, genellikle bu olayları yoksayabilirsiniz.  
  
 Sürükleme <xref:System.Windows.DragDrop.GiveFeedback> kaynağı sürüklenirken olay sürekli olarak yükseltilir. Bu olay için varsayılan işleyici sürükle kaynağının geçerli bir bırakma hedefi üzerinde olup olmadığını denetler. Eğer varsa, bırakma hedefinin izin verilen etkilerini denetler. Daha sonra izin verilen bırakma efektleri ile ilgili olarak son kullanıcıya geribildirim verir. Bu genellikle fare imlecini bırakmaz, kopyalayarak veya imleciyi hareket ettirerek yapılır. Bu olayı yalnızca kullanıcıya geri bildirim sağlamak için özel imleçler kullanmanız gerekiyorsa işlemeniz gerekir. Bu olayı işlerseniz, varsayılan işleyicinin işleyicinizi geçersiz kılmaması için işlenir olarak işaretlediğinden emin olun.  
  
 Sürükleme <xref:System.Windows.DragDrop.QueryContinueDrag> kaynağı sürüklenirken olay sürekli olarak yükseltilir. ESC, SHIFT, CTRL ve ALT tuşlarının durumuna ve fare düğmelerinin durumuna göre sürükle ve bırak işlemini hangi eylemin sona erdirdiğini belirlemek için bu olayı işleyebilirsiniz. Bu olayın varsayılan işleyicisi, ESC tuşuna basıldığında sürükle ve bırak işlemini iptal eder ve fare düğmesi serbest bırakılırsa verileri düşürür.  
  
> [!CAUTION]
> Bu olaylar sürükle ve bırak işlemi sırasında sürekli olarak yükseltilir. Bu nedenle, olay işleyicileri kaynak yoğun görevleri kaçınmalısınız.  Örneğin, <xref:System.Windows.DragDrop.GiveFeedback> olay her yükseltilse yeni bir imleç oluşturmak yerine önbelleğe alınmış bir imleç kullanın.  
  
### <a name="enabling-an-element-to-be-a-drop-target"></a>Bir Öğenin Açılan Hedef Olmasını Etkinleştirme  
 Bırakma hedefi olan bir nesne sorumludur:  
  
- Geçerli bir bırakma hedefi olduğunu belirtme.  
  
- Hedefin üzerine sürüklendiğinde sürükleme kaynağına yanıt verir.  
  
- Aktarılan verilerin alabileceği bir biçimde olup olmadığını denetleme.  
  
- Bırakılan verileri işleme.  
  
 Bir öğenin bırakma hedefi olduğunu belirtmek <xref:System.Windows.UIElement.AllowDrop%2A> için, `true`özelliğini ' ye ayarlarsınız. Bırak hedef olayları daha sonra bunları işleyebilir böylece öğe üzerinde yükseltilir. Sürükle ve bırak işlemi sırasında, açılan hedefte aşağıdaki olaylar dizisi oluşur:  
  
1. <xref:System.Windows.DragDrop.DragEnter>  
  
2. <xref:System.Windows.DragDrop.DragOver>  
  
3. <xref:System.Windows.DragDrop.DragLeave> veya <xref:System.Windows.DragDrop.Drop>  
  
 Olay, <xref:System.Windows.DragDrop.DragEnter> veriler açılan hedefin sınırına sürüklendiğinde oluşur. Uygulamanız için uygunsa sürükle ve bırak işleminin etkilerinin önizlemesini sağlamak için genellikle bu olayı işlersiniz. Olay da <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> üzerine yazılacağına göre özelliği olaya göre ayarlamayın. <xref:System.Windows.DragDrop.DragOver> <xref:System.Windows.DragDrop.DragEnter>  
  
 Aşağıdaki örnek, <xref:System.Windows.DragDrop.DragEnter> bir <xref:System.Windows.Shapes.Ellipse> öğe için olay işleyicisi gösterir. Bu kod, geçerli <xref:System.Windows.Shapes.Shape.Fill%2A> fırçayı kaydederek sürükle ve bırak işleminin etkilerini önizler. Daha sonra <xref:System.Windows.DataObject.GetDataPresent%2A> elips üzerinde <xref:System.Windows.DataObject> sürüklenen bir dize veri seve mi kontrol <xref:System.Windows.Media.Brush>etmek için yöntemi kullanır . Bu nedenle, veriler <xref:System.Windows.DataObject.GetData%2A> yöntem kullanılarak ayıklanır. Daha sonra a <xref:System.Windows.Media.Brush> dönüştürülür ve elips uygulanır. Değişiklik olay işleyicisi <xref:System.Windows.DragDrop.DragLeave> olarak döndürüldü. Veriler bir <xref:System.Windows.Media.Brush>,'ye dönüştürülemiyorsa, hiçbir eylem gerçekleştirilir.  
  
 [!code-csharp[DragDropSnippets#DragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragenter)]
 [!code-vb[DragDropSnippets#DragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragenter)]  
  
 Veriler <xref:System.Windows.DragDrop.DragOver> bırakma hedefinin üzerine sürüklenirken olay sürekli olarak gerçekleşir. Bu olay sürükleme kaynağındaki <xref:System.Windows.DragDrop.GiveFeedback> olayla eşlenir. Olay <xref:System.Windows.DragDrop.DragOver> işleyicisi, genellikle aktarılan <xref:System.Windows.DataObject.GetDataPresent%2A> <xref:System.Windows.DataObject.GetData%2A> verilerin bırakma hedefinin işleyebilir biçiminde olup olmadığını denetlemek için ve yöntemleri kullanırsınız. Ayrıca, genellikle kullanıcının bir taşıma veya kopyalama eylemi isteyip istemediklerini gösteren herhangi bir değiştirici tuşa basılıp basıldığını da denetleyebilirsiniz. Bu denetimler yapıldıktan sonra, <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> özelliği sürükleme kaynağına veri bırakarak ne gibi bir etkiye sahip olacağını bildirmek üzere ayarlarsınız. Sürükleme kaynağı bu bilgileri <xref:System.Windows.DragDrop.GiveFeedback> args durumunda alır ve kullanıcıya geribildirim vermek için uygun bir imleç ayarlayabilirsiniz.  
  
 Aşağıdaki örnek, <xref:System.Windows.DragDrop.DragOver> bir <xref:System.Windows.Shapes.Ellipse> öğe için olay işleyicisi gösterir. Bu kod, elipsin üzerinde <xref:System.Windows.DataObject> sürüklenen bir dize verisi olup <xref:System.Windows.Media.Brush>olmadığını denetler. Bu nedenle, <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> özelliği . <xref:System.Windows.DragDropEffects.Copy> Bu, sürükleme kaynağına verilerin elipse kopyalanabileceğini gösterir. Veriler a <xref:System.Windows.Media.Brush>dönüştürülemiyorsa, <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> özellik . <xref:System.Windows.DragDropEffects.None> Bu, sürükleme kaynağına elipsin veriler için geçerli bir bırakma hedefi olmadığını gösterir.  
  
 [!code-csharp[DragDropSnippets#DragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragover)]
 [!code-vb[DragDropSnippets#DragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragover)]  
  
 Olay, <xref:System.Windows.DragDrop.DragLeave> veriler düşmeden hedefin sınırından çıkarıldığında oluşur. <xref:System.Windows.DragDrop.DragEnter> Olay işleyicisinde yaptığınız her şeyi geri almak için bu olayı işlersiniz.  
  
 Aşağıdaki örnek, <xref:System.Windows.DragDrop.DragLeave> bir <xref:System.Windows.Shapes.Ellipse> öğe için olay işleyicisi gösterir. Bu kod, kaydedilen <xref:System.Windows.DragDrop.DragEnter> <xref:System.Windows.Media.Brush> elipsi uygulayarak olay işleyicisinde gerçekleştirilen önizlemeyi geri almaz.  
  
 [!code-csharp[DragDropSnippets#DragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragleave)]
 [!code-vb[DragDropSnippets#DragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragleave)]  
  
 Olay, <xref:System.Windows.DragDrop.Drop> veriler bırakma hedefinin üzerine bırakıldığında oluşur; varsayılan olarak, fare düğmesi serbest bırakıldığında bu olur. <xref:System.Windows.DragDrop.Drop> Durumunda işleyici, aktarılan verileri <xref:System.Windows.DataObject.GetData%2A> ayıklamak <xref:System.Windows.DataObject> ve uygulamanızın gerektirdiği herhangi bir veri işleme gerçekleştirmek için yöntemi kullanırsınız. Olay <xref:System.Windows.DragDrop.Drop> sürükle ve bırak işlemini sona erdirer.  
  
 Aşağıdaki örnek, <xref:System.Windows.DragDrop.Drop> bir <xref:System.Windows.Shapes.Ellipse> öğe için olay işleyicisi gösterir. Bu kod sürükle ve bırak işleminin etkilerini uygular ve <xref:System.Windows.DragDrop.DragEnter> olay işleyicisindeki koda benzer. Elipsüzerinde <xref:System.Windows.DataObject> sürüklenen dize verilerinin bir <xref:System.Windows.Media.Brush>'e dönüştürülebilir olup olmadığını kontrol eder. Eğer öyleyse, <xref:System.Windows.Media.Brush> elips uygulanır. Veriler bir <xref:System.Windows.Media.Brush>,'ye dönüştürülemiyorsa, hiçbir eylem gerçekleştirilir.  
  
 [!code-csharp[DragDropSnippets#Drop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#drop)]
 [!code-vb[DragDropSnippets#Drop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#drop)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Clipboard>
- [İzlenecek yol: Kullanıcı Denetiminde Sürükleme ve Bırakmayı Etkinleştirme](walkthrough-enabling-drag-and-drop-on-a-user-control.md)
- [Nasıl Dır Konular](drag-and-drop-how-to-topics.md)
- [Sürükle ve Bırak](drag-and-drop.md)
