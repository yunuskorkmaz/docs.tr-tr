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
ms.openlocfilehash: 433fee08d44720640d3f9d1bf2511a6a267eb58e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145468"
---
# <a name="annotations-overview"></a>Ek açıklamalara Genel Bakış
Kağıt belgelere not lar veya yorumlar yazmak o kadar yaygın bir faaliyettir ki neredeyse hafife alabiliriz. Bu notlar veya yorumlar, bilgileri işaretlemek veya daha sonra başvurmak üzere ilgi çekici öğeleri vurgulamak için belgeye eklediğimiz "ek açıklamalar"tır. Yazdırılan belgelere not yazmak kolay ve olağan olsa da, elektronik belgelere kişisel yorum ekleme yeteneği genellikle çok sınırlıdır, eğer varsa.  
  
 Bu konu, özellikle yapışkan notlar ve vurgular olmak üzere çeşitli ortak ek açıklama türlerini gözden geçirir ve Microsoft Ek Açıklamalar Çerçevesi'nin Windows Sunu Temeli (WPF) aracılığıyla uygulamalarda bu tür ek açıklamaları nasıl kolaylaştırdığını gösterir ) belge görüntüleme denetimleri.  Ek açıklamaları destekleyen WPF belge <xref:System.Windows.Controls.FlowDocumentReader> görüntüleme <xref:System.Windows.Controls.FlowDocumentScrollViewer>denetimleri, <xref:System.Windows.Controls.Primitives.DocumentViewerBase> bu tür <xref:System.Windows.Controls.DocumentViewer> ve <xref:System.Windows.Controls.FlowDocumentPageViewer>.  

<a name="caf1_type_stickynotes"></a>
## <a name="sticky-notes"></a>Yapışkan Notlar  
 Tipik yapışkan not, daha sonra bir belgeye "sıkışmış" renkli kağıt küçük bir parça üzerinde yazılmış bilgiler içerir. Dijital yapışkan notlar elektronik belgeler için benzer işlevsellik sağlar, ancak yazılmış metin, el yazısı notlar (örneğin, Tablet PC "mürekkep" konturları) veya Web bağlantıları gibi diğer birçok içerik türünü içerecek şekilde ek esneklik le birlikte.  
  
 Aşağıdaki resimde vurgu, metin yapışkan not ve mürekkep yapışkan not açıklamalarıbazı örnekler gösterilmektedir.  
  
 ![Vurgu, metin ve mürekkep yapışkan not ek açıklamaları.](./media/caf-stickynote.jpg "CAF_StickyNote")  
  
 Aşağıdaki örnek, uygulamanızda ek açıklama desteğini etkinleştirmek için kullanabileceğiniz yöntemi gösterir.  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>
## <a name="highlights"></a>Önemli Noktalar  
 İnsanlar, bir kağıt belgeyi işaretlediğinde, bir cümledeki sözcükleri çizme, işaret veya işaret çekme gibi ilgi çekici öğelere dikkat çekmek için yaratıcı yöntemler kullanır.  Microsoft Ek Açıklamalar Çerçevesi'ndeki vurgu ek açıklamaları, WPF belge görüntüleme denetimlerinde görüntülenen bilgileri işaretlemek için benzer bir özellik sağlar.  
  
 Aşağıdaki resimde vurgu ek açıklama bir örnek gösterilmektedir.  
  
 ![Ek Açıklamayı Vurgula](./media/caf-callouts.png "CAF_Callouts")  
  
 Kullanıcılar genellikle önce bir metin veya ilgi çekici bir öğe seçerek ve ardından ek <xref:System.Windows.Controls.ContextMenu> açıklama seçeneklerigörüntülemek için sağ tıklayarak ek açıklamalar oluşturur.  Aşağıdaki örnek, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kullanıcıların ek açıklamalar <xref:System.Windows.Controls.ContextMenu> oluşturmak ve yönetmek için erişebileceği yönlendirilmiş komutları bildirmek için kullanabileceğiniz leri gösterir.  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>
## <a name="data-anchoring"></a>Veri Bağlantı  
 Ek Açıklamalar Çerçevesi, ek açıklamaları yalnızca görüntü görünümündeki bir konuma değil, kullanıcının seçtiği verilere bağlar. Bu nedenle, kullanıcı ekran penceresini kaydırdığında veya yeniden boyutlandırdığında olduğu gibi belge görünümü değişirse, ek açıklama bağlı olduğu veri seçiminde kalır. Örneğin, aşağıdaki grafik, kullanıcının metin seçiminde yaptığı bir ek açıklamayı göstermektedir. Belge görünümü değiştiğinde (kaydırma, yeniden boyutlandırma, ölçeklendirme veya başka bir şekilde hareket ettiğinde), vurgu lama ek açıklama özgün veri seçimiyle birlikte hareket eder.  
  
 ![Ek Açıklama Veri Bağlantı](./media/caf-dataanchoring.png "CAF_DataAnchoring")  
  
<a name="matching_annotations_with_annotated_objects"></a>
## <a name="matching-annotations-with-annotated-objects"></a>Açıklamalı Nesnelerle Açıklama eşleştirme  
 Ek açıklamaları karşılık gelen ek açıklamalı nesnelerle eşleştirebilirsiniz. Örneğin, yorum bölmesi olan basit bir belge okuyucu uygulamasını düşünün. Açıklama bölmesi, belgeye bağlı ek açıklamalar listesinden metni görüntüleyen bir liste kutusu olabilir. Kullanıcı liste kutusunda bir öğe seçerse, uygulama ilgili ek açıklama nesnesinin bağlı olduğu belgedeki paragrafı görüntületir.  
  
 Aşağıdaki örnek, açıklama bölmesi olarak hizmet veren böyle bir liste kutusunun olay işleyicisinin nasıl uygulanacağını gösterir.  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 Başka bir örnek senaryo, e-posta yoluyla belge okuyucular arasında ek açıklamalar ve yapışkan notlar alışverişini sağlayan uygulamaları içerir. Bu özellik, bu uygulamaların okuyucuyu değiştirilmekte olan ek açıklamayı içeren sayfaya yönlendirmesini sağlar.  
  
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
- [Nasıl yapılsın: MenuItem'e Komut Ekleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))
