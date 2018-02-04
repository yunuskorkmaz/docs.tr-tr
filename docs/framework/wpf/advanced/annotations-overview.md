---
title: "Ek açıklamalara Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- highlights [WPF]
- documents [WPF], annotations
- sticky notes [WPF]
ms.assetid: 716bf474-29bd-4c74-84a4-8e0744bdad62
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1f3ac3ce66d944934724bef1b69307030ec813e2
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="annotations-overview"></a>Ek açıklamalara Genel Bakış
Not yazma veya kağıt belge açıklamalarını biz neredeyse sorgulamadan kabul ederiz, bir tür bir sıradan etkinlik değil. Bu notlar veya yorumlar "açıklamalardır" bilgilere bayrak ya da daha sonra başvurmak için ilgi vurgulamak için bir belgeye ekleriz. Kolay ve sıradan Yazdırılan belgeleri Not yazma olmasına karşın, elektronik belgelere kişisel açıklamalar ekleme yeteneği genellikle hiç varsa çok sınırlıdır.  
  
 Bu konu ortak çeşitli ek açıklamalarını, özellikle Yapışkan Notlar ve vurgular, gözden geçirir ve gösterilmektedir nasıl [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] bu tür uygulamalar aracılığıyla ek açıklamalar kolaylaştıran [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] belge görüntüleme denetimleri.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ek açıklamaları destekleyen belge görüntüleme denetimleri dahil <xref:System.Windows.Controls.FlowDocumentReader> ve <xref:System.Windows.Controls.FlowDocumentScrollViewer>, yanı sıra denetimleri türetilmiş <xref:System.Windows.Controls.Primitives.DocumentViewerBase> gibi <xref:System.Windows.Controls.DocumentViewer> ve <xref:System.Windows.Controls.FlowDocumentPageViewer>.  
  
  
<a name="caf1_type_stickynotes"></a>   
## <a name="sticky-notes"></a>Yapışkan Notlar  
 Tipik bir Yapışkan Not küçük bir sonra "belgeye takıldı" renkli kağıt üzerine yazılan bilgileri içerir. Dijital Yapışkan Not sağlamak benzer işlevselliği elektronik belgeleri, ancak birçok içerik türleri gibi eklemek için eklenen esnekliği yazılı metni, el yazısı notlar (örneğin, [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)] "mürekkep" vuruşları), Web bağlantıları veya.  
  
 Aşağıda bazı örnekler vurgulama, metin yapışkan not ve mürekkep yapışkan not ek açıklamaları gösterilmiştir.  
  
 ![Vurgu, metin ve mürekkep yapışkan ek açıklamaları unutmayın. ] (../../../../docs/framework/wpf/advanced/media/caf-stickynote.jpg "CAF_StickyNote")  
  
 Aşağıdaki örnek, uygulamanızdaki ek açıklama desteğini etkinleştirmek için kullanabileceğiniz yöntemi gösterilir.  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>   
## <a name="highlights"></a>Öne çıkan özellikleri  
 Kişiler, alt çizgi, vurgulama, tümcedeki sözcüklerin daire içine veya boşlukta çizim işaretleri veya gösterimler gibi bir kağıt belgeyi işaretlediğinizde ilgi öğelere dikkat çekmek için yaratıcı yöntemlerini kullanın.  Ek açıklamalar vurgulayın [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] benzer bir özellik olarak görüntülenen bilgiler işaretleme sağlar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] belge görüntüleme denetimleri.  
  
 Aşağıdaki çizimde vurgulama ek açıklama örneği gösterir.  
  
 ![Ek açıklama vurgulayın](../../../../docs/framework/wpf/advanced/media/caf-callouts.png "CAF_Callouts")  
  
 Kullanıcılar ilk bazı metin veya ilgi öğeyi seçerek ve görüntülemek için sağ tıklatıp ek açıklamaları genellikle oluşturma bir <xref:System.Windows.Controls.ContextMenu> ek açıklama seçenekleri.  Aşağıdaki örnekte gösterildiği [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] bildirmek için kullanabileceğiniz bir <xref:System.Windows.Controls.ContextMenu> yönlendirilmiş komutlarla oluşturmak ve ek açıklamaları yönetmek için kullanıcılar erişebilir.  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>   
## <a name="data-anchoring"></a>Veri bağlama  
 [!INCLUDE[TLA2#tla_caf](../../../../includes/tla2sharptla-caf-md.md)] Ek açıklamaları, kullanıcının seçtiği verileri, yalnızca görüntü görünümü konumuna bağlar. Bu nedenle, zaman kullanıcı kaydırdığında veya görüntü boyutlandırır gibi belge görünümü değişirse ek açıklama, bağlı olduğu veri seçimi ile kalır. Örneğin, aşağıdaki grafikte kullanıcının metin seçiminde yaptığı bir ek açıklamanın gösterilmektedir. Belgeyi görünümü değiştiğinde (kayarken, yeniden boyutlandırır, ölçekler veya başka bir hareket), özgün veri seçimiyle Vurgu ek açıklama taşır.  
  
 ![Ek açıklama veri bağlama](../../../../docs/framework/wpf/advanced/media/caf-dataanchoring.png "CAF_DataAnchoring")  
  
<a name="matching_annotations_with_annotated_objects"></a>   
## <a name="matching-annotations-with-annotated-objects"></a>Açıklanmış nesnelerle eşleşen ek açıklamaları  
 Ek açıklamaları karşılık gelen açıklanmış nesnelerle eşleştirebilirsiniz. Örneğin, açıklamalar bölmesi olan basit bir belge okuyucu uygulamasını göz önünde bulundurun. Açıklamalar bölmesi belgeye bağlantılı ek açıklamaları listesinden metni görüntüleyen bir liste kutusu olabilir. Kullanıcı liste kutusunda bir öğe seçerse, uygulama karşılık gelen ek açıklama nesnesinin sabitlenmiş olduğu belgedeki paragrafı görünüme getirir.  
  
 Aşağıdaki örnek, açıklamalar bölmesi olarak hizmet böyle bir liste kutusu olay işleyicisinin uygulanacak gösterilmiştir.  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 Başka bir örnek senaryo ek açıklamalar ve e-posta yoluyla belge okuyucular arasındaki Yapışkan Notlar alışverişini etkinleştirmek uygulamaları içerir. Bu özellik, okuyucu değiştirilen ek açıklamayı içeren sayfaya gitmek bu uygulamaları sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Primitives.DocumentViewerBase>  
 <xref:System.Windows.Controls.DocumentViewer>  
 <xref:System.Windows.Controls.FlowDocumentPageViewer>  
 <xref:System.Windows.Controls.FlowDocumentScrollViewer>  
 <xref:System.Windows.Controls.FlowDocumentReader>  
 <xref:System.Windows.Annotations.IAnchorInfo>  
 [Ek Açıklamalar Şeması](../../../../docs/framework/wpf/advanced/annotations-schema.md)  
 [ContextMenu Genel Bakış](../../../../docs/framework/wpf/controls/contextmenu-overview.md)  
 [Komut Vermeye Genel Bakış](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [Akış Belgesine Genel Bakış](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [Nasıl yapılır: bir MenuItem komut ekleme](http://msdn.microsoft.com/library/013d68a0-5373-4a68-bd91-5de574307370)
