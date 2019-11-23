---
title: Ek açıklamalara Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- highlights [WPF]
- documents [WPF], annotations
- sticky notes [WPF]
ms.assetid: 716bf474-29bd-4c74-84a4-8e0744bdad62
ms.openlocfilehash: dc9c4125f9ac3c44be41efe92b9e495599e5c130
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004040"
---
# <a name="annotations-overview"></a>Ek açıklamalara Genel Bakış
Yazılı belgelerde Not veya yorum yazmak, neredeyse kendisine verilmek üzere yaptığımız çok önemli bir etkinliktir. Bu notlar veya Yorumlar, bilgilere bayrak eklemek veya daha sonra başvurmak üzere ilgilendiğiniz öğeleri vurgulamak için bir belgeye eklediğimiz "ek açıklamalardır". Yazdırılmış belgelere not yazmak kolaydır ve çok daha kolay olsa da, elektronik belgelere kişisel açıklamalar ekleyebilme özelliği, genellikle çok sınırlı olur.  
  
 Bu konu başlığı altında, yaygın olarak yapışkan notlar ve önemli birçok ek açıklama türü incelenmiştir ve Microsoft ek açıklama çerçevesinin Windows Presentation Foundation aracılığıyla uygulamalarda bu ek açıklama türlerini nasıl kolaylaştırdığını gösterir (WPF ) belge görüntüleme denetimleri.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] belge görüntüleme denetimlerinin yanı sıra <xref:System.Windows.Controls.FlowDocumentReader> ve <xref:System.Windows.Controls.FlowDocumentScrollViewer>, <xref:System.Windows.Controls.DocumentViewer> ve <xref:System.Windows.Controls.FlowDocumentPageViewer>gibi <xref:System.Windows.Controls.Primitives.DocumentViewerBase> türetilen denetimleri içerir.  

<a name="caf1_type_stickynotes"></a>   
## <a name="sticky-notes"></a>Yapışkan Notlar  
 Tipik bir yapışkan notta, bir belgeye "takılmış" olan küçük bir renkli bir kağıda yazılan bilgiler yer alır. Dijital yapışkan notlar elektronik belgeler için benzer işlevler sağlar, ancak yazılı metin, el yazısı notları (örneğin, Tablet PC "mürekkep" vuruşları) veya Web bağlantıları gibi diğer birçok içerik türünü dahil etmek için eklenen esnekliğe sahiptir.  
  
 Aşağıdaki çizimde, bazı açıkton, metin Yapışkan Not ve mürekkep Yapışkan Not ek açıklamalarını gösteren bazı örnekler gösterilmektedir.  
  
 ![Vurgu, metin ve mürekkep Yapışkan Not ek açıklamaları.](./media/caf-stickynote.jpg "CAF_StickyNote")  
  
 Aşağıdaki örnek, uygulamanızda ek açıklama desteğini etkinleştirmek için kullanabileceğiniz yöntemi gösterir.  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>   
## <a name="highlights"></a>Lamaları  
 İnsanlar, bir kağıt belgeyi işaret eden alt çizgi, vurgulama, Circling kelimeleri veya kenar boşluğunda çizim işaretleri veya gösterimler gibi, ilgi çekici öğelere dikkat çekmek için yaratıcı yöntemler kullanır.  Microsoft ek açıklamaları çerçevesindeki ek açıklamaları Vurgula [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] belge görüntüleme denetimlerinde görüntülenen bilgileri işaretlemek için benzer bir özellik sağlar.  
  
 Aşağıdaki çizimde bir vurgulama ek açıklaması örneği gösterilmektedir.  
  
 ![Ek açıklama](./media/caf-callouts.png "CAF_Callouts") Vurgula  
  
 Kullanıcılar genellikle ilk olarak bir metin veya ilgilendiğiniz öğe seçerek ve ardından ek açıklama seçeneklerinin bir <xref:System.Windows.Controls.ContextMenu> görüntülenmesini sağlamak için sağ tıklanarak ek açıklamalar oluşturur.  Aşağıdaki örnek, kullanıcıların ek açıklamaları oluşturup yönetmek için erişebileceği yönlendirilmiş komutlarla bir <xref:System.Windows.Controls.ContextMenu> bildirmek için kullanabileceğiniz [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] gösterir.  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>   
## <a name="data-anchoring"></a>Veri sabitleme  
 Ek açıklamalar çerçevesi, ek açıklamaları yalnızca görüntü görünümündeki bir konuma değil kullanıcının seçtiği verilere bağlar. Bu nedenle, belge görünümü değişirse (örneğin, Kullanıcı görüntü penceresini kaydırdığında veya yeniden boyutlandırdığında), ek açıklama, bağlandığı veri seçimiyle kalır. Örneğin, aşağıdaki grafik, kullanıcının metin seçiminde yaptığı ek açıklamayı gösterir. Belge görünümü değiştiğinde (kaydırma, yeniden boyutlanıyor, ölçekler veya başka bir şekilde), vurgu ek açıklaması orijinal veri seçimiyle birlikte değişir.  
  
 ![Ek açıklama verileri sabitleme](./media/caf-dataanchoring.png "CAF_DataAnchoring")  
  
<a name="matching_annotations_with_annotated_objects"></a>   
## <a name="matching-annotations-with-annotated-objects"></a>Açıklamalı nesneler ile eşleşen ek açıklamalar  
 Ek açıklamaların karşılık gelen açıklamalı nesneleriyle eşleşmesini sağlayabilirsiniz. Örneğin, açıklamalar bölmesi olan basit bir belge okuyucu uygulaması düşünün. Açıklamalar bölmesi, bir belgeye sabitlenmiş bir ek açıklama listesinden metin görüntüleyen bir liste kutusu olabilir. Kullanıcı liste kutusunda bir öğe seçerse, uygulama, ilgili ek açıklama nesnesinin sabitlenmiş olduğu belgedeki paragrafı görüntüler.  
  
 Aşağıdaki örnek, açıklama bölmesi olarak hizmet veren böyle bir liste kutusunun olay işleyicisinin nasıl uygulanacağını gösterir.  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 Diğer bir örnek senaryo, e-posta aracılığıyla belge okuyucuları arasında ek açıklama ve yapışkan not alışverişi sağlayan uygulamalar içerir. Bu özellik, bu uygulamaların okuyucudaki değiş tokuş edilen ek açıklamanın bulunduğu sayfaya gitmesini sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Primitives.DocumentViewerBase>
- <xref:System.Windows.Controls.DocumentViewer>
- <xref:System.Windows.Controls.FlowDocumentPageViewer>
- <xref:System.Windows.Controls.FlowDocumentScrollViewer>
- <xref:System.Windows.Controls.FlowDocumentReader>
- <xref:System.Windows.Annotations.IAnchorInfo>
- [Ek Açıklamalar Şeması](annotations-schema.md)
- [ContextMenu Genel Bakış](../controls/contextmenu-overview.md)
- [Komut Vermeye Genel Bakış](commanding-overview.md)
- [Akış Belgesine Genel Bakış](flow-document-overview.md)
- [Nasıl yapılır: MenuItem 'a komut ekleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))
