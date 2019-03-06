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
ms.openlocfilehash: a0c6260eee10487034655b5e4abbfa1f1a7bce71
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355187"
---
# <a name="annotations-overview"></a>Ek açıklamalara Genel Bakış
Not yazma veya kağıt belge açıklamalarını biz neredeyse sorgulamadan kabul ederiz, bir tür bir sıradan etkinlik olduğundan. Bu Notlar ya da yorumlarınız "ek açıklamalar", bir belgeye bilgi bayrağı veya daha sonra başvurmak için ilgi öğelerini vurgulamak için ekleriz. Kolay ve sıradan Yazdırılan belgeleri Not yazma olmasına karşın, elektronik belgeleri kişisel açıklamalar ekleme yeteneği genellikle kullanılabilir olsa çok sınırlıdır.  
  
 Bu konu, ek açıklamalarını, özellikle Yapışkan Notlar ve vurgular, çeşitli genel türleri inceler ve gösterir nasıl [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] bu uygulamalar Windows Presentation Foundation (WPF) belgenin aracılığıyla ek açıklamalarda tür kolaylaştırır görüntüleme denetimleri.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ek açıklamaları destekleyen belge görüntüleme denetimleri dahil <xref:System.Windows.Controls.FlowDocumentReader> ve <xref:System.Windows.Controls.FlowDocumentScrollViewer>, yanı sıra denetimleri türetilen <xref:System.Windows.Controls.Primitives.DocumentViewerBase> gibi <xref:System.Windows.Controls.DocumentViewer> ve <xref:System.Windows.Controls.FlowDocumentPageViewer>.  
  
  
<a name="caf1_type_stickynotes"></a>   
## <a name="sticky-notes"></a>Yapışkan Notlar  
 Tipik bir Yapışkan Not, bir küçük kağıda ardından "belgeye takılmış" renkli yazılan bilgileri içerir. Dijital Yapışkan Notlar benzer bir işlevsellik elektronik belgeleri, ancak diğer birçok içerik türleri gibi eklemek için eklenen esnekliğiyle yazılı metni, el yazısı notları sağlayın (örneğin, [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)] "mürekkep" strokes), veya Web bağlantıları.  
  
 Aşağıdaki çizimde, Yapışkan Not Vurgu, metin yapışkan not ve mürekkep bazı örnekler gösterilmektedir.  
  
 ![Ek açıklamalar, Vurgu, metin ve mürekkep yapışkan unutmayın. ](./media/caf-stickynote.jpg "CAF_StickyNote")  
  
 Aşağıdaki örnek, uygulamanızda ek açıklama desteğini etkinleştirmek için kullanabileceğiniz yöntemi gösterir.  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>   
## <a name="highlights"></a>Öne çıkan özellikleri  
 Kişiler, alt çizgi, vurgulama, daire içine bir cümle sözcükleri veya işaretleri veya gösterimler çizim gibi bir inceleme belgeyi işaretlediğinizde ilgi öğelere dikkat çekmek yaratıcı yöntemler kullanır.  Ek açıklamalarda vurgulayın [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] görüntülenen bilgileri işaretlemek için benzer bir özellik sağlar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] belge görüntüleme denetimleri.  
  
 Aşağıdaki çizimde örnek olarak bir Vurgu ek açıklama gösterir.  
  
 ![Ek açıklama vurgulayın](./media/caf-callouts.png "CAF_Callouts")  
  
 Kullanıcıların ilk metin ya da bir öğe bulduğunuzda seçip ardından görüntülemek için sağ tıklayarak ek açıklamalar genellikle oluşturma bir <xref:System.Windows.Controls.ContextMenu> ek açıklama seçenekleri.  Aşağıdaki örnekte gösterildiği [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] bildirmek için kullanabileceğiniz bir <xref:System.Windows.Controls.ContextMenu> yönlendirilmiş komutlarla oluşturmak ve ek açıklamalar yönetmek için kullanıcılar erişebilir.  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>   
## <a name="data-anchoring"></a>Veri bağlama  
 [!INCLUDE[TLA2#tla_caf](../../../../includes/tla2sharptla-caf-md.md)] Ek açıklamaları, kullanıcının seçtiği verileri, yalnızca bir görüntü görünümü konumuna bağlar. Bu nedenle kullanıcı kayan veya görüntü boyutlandırır gibi belge görünümü değişirse, bağlı olduğu veri seçimi ile ek açıklama kalır. Örneğin, aşağıdaki grafikte üzerinde metin seçimi kullanıcı tarafından yapılan bir ek açıklama gösterilmektedir. Belge (kayarken, yeniden boyutlandırır, Ölçek veya başka bir hareket) değişiklikleri görüntülediğinizde vurgulama ek açıklaması ile özgün veri seçimi taşır.  
  
 ![Veri ek açıklama sabitleme](./media/caf-dataanchoring.png "CAF_DataAnchoring")  
  
<a name="matching_annotations_with_annotated_objects"></a>   
## <a name="matching-annotations-with-annotated-objects"></a>Ek açıklamalı nesnelerle eşleşen ek açıklamaları  
 Ek açıklamalar açıklanmış karşılık gelen nesnelerle eşleşebilir. Örneğin, bir açıklama bölmesi olan basit bir belge bir okuyucu uygulama göz önünde bulundurun. Açıklamalar bölmesinde, bir belgeye metni sabitlenmiş bir ek açıklamaların listesini görüntüleyen bir liste kutusu olabilir. Kullanıcı bir öğeyi liste kutusunda seçerse uygulama ilgili ek açıklama nesnesinin sabitlendiği belge paragrafta görünümde gösterir.  
  
 Aşağıdaki örnekte olay işleyicisi yorumlar bölmesinin hizmet böyle bir liste kutusu uygulamak nasıl gösterir.  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 Başka bir örnek senaryo, exchange e-posta ile belge okuyucular arasında Yapışkan Notlar ve ek açıklamalar sağlayan uygulamaları içerir. Bu özellik okuyucu ek açıklama, değiştirilen içeren sayfasına gitmek bu uygulamalar sağlar.  
  
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
- [Nasıl yapılır: MenuItem için bir komut ekleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))
