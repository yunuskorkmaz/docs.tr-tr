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
# <a name="annotations-overview"></a><span data-ttu-id="eee7c-102">Ek açıklamalara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="eee7c-102">Annotations Overview</span></span>
<span data-ttu-id="eee7c-103">Kağıt belgelere not lar veya yorumlar yazmak o kadar yaygın bir faaliyettir ki neredeyse hafife alabiliriz.</span><span class="sxs-lookup"><span data-stu-id="eee7c-103">Writing notes or comments on paper documents is such a commonplace activity that we almost take it for granted.</span></span> <span data-ttu-id="eee7c-104">Bu notlar veya yorumlar, bilgileri işaretlemek veya daha sonra başvurmak üzere ilgi çekici öğeleri vurgulamak için belgeye eklediğimiz "ek açıklamalar"tır.</span><span class="sxs-lookup"><span data-stu-id="eee7c-104">These notes or comments are "annotations" that we add to a document to flag information or to highlight items of interest for later reference.</span></span> <span data-ttu-id="eee7c-105">Yazdırılan belgelere not yazmak kolay ve olağan olsa da, elektronik belgelere kişisel yorum ekleme yeteneği genellikle çok sınırlıdır, eğer varsa.</span><span class="sxs-lookup"><span data-stu-id="eee7c-105">Although writing notes on printed documents is easy and commonplace, the ability to add personal comments to electronic documents is typically very limited, if available at all.</span></span>  
  
 <span data-ttu-id="eee7c-106">Bu konu, özellikle yapışkan notlar ve vurgular olmak üzere çeşitli ortak ek açıklama türlerini gözden geçirir ve Microsoft Ek Açıklamalar Çerçevesi'nin Windows Sunu Temeli (WPF) aracılığıyla uygulamalarda bu tür ek açıklamaları nasıl kolaylaştırdığını gösterir ) belge görüntüleme denetimleri.</span><span class="sxs-lookup"><span data-stu-id="eee7c-106">This topic reviews several common types of annotations, specifically sticky notes and highlights, and illustrates how the Microsoft Annotations Framework facilitates these types of annotations in applications through the Windows Presentation Foundation (WPF) document viewing controls.</span></span>  <span data-ttu-id="eee7c-107">Ek açıklamaları destekleyen WPF belge <xref:System.Windows.Controls.FlowDocumentReader> görüntüleme <xref:System.Windows.Controls.FlowDocumentScrollViewer>denetimleri, <xref:System.Windows.Controls.Primitives.DocumentViewerBase> bu tür <xref:System.Windows.Controls.DocumentViewer> ve <xref:System.Windows.Controls.FlowDocumentPageViewer>.</span><span class="sxs-lookup"><span data-stu-id="eee7c-107">WPF document viewing controls that support annotations include <xref:System.Windows.Controls.FlowDocumentReader> and <xref:System.Windows.Controls.FlowDocumentScrollViewer>, as well as controls derived from <xref:System.Windows.Controls.Primitives.DocumentViewerBase> such as <xref:System.Windows.Controls.DocumentViewer> and <xref:System.Windows.Controls.FlowDocumentPageViewer>.</span></span>  

<a name="caf1_type_stickynotes"></a>
## <a name="sticky-notes"></a><span data-ttu-id="eee7c-108">Yapışkan Notlar</span><span class="sxs-lookup"><span data-stu-id="eee7c-108">Sticky Notes</span></span>  
 <span data-ttu-id="eee7c-109">Tipik yapışkan not, daha sonra bir belgeye "sıkışmış" renkli kağıt küçük bir parça üzerinde yazılmış bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="eee7c-109">A typical sticky note contains information written on a small piece of colored paper that is then "stuck" to a document.</span></span> <span data-ttu-id="eee7c-110">Dijital yapışkan notlar elektronik belgeler için benzer işlevsellik sağlar, ancak yazılmış metin, el yazısı notlar (örneğin, Tablet PC "mürekkep" konturları) veya Web bağlantıları gibi diğer birçok içerik türünü içerecek şekilde ek esneklik le birlikte.</span><span class="sxs-lookup"><span data-stu-id="eee7c-110">Digital sticky notes provide similar functionality for electronic documents, but with the added flexibility to include many other types of content such as typed text, handwritten notes (for example, Tablet PC "ink" strokes), or Web links.</span></span>  
  
 <span data-ttu-id="eee7c-111">Aşağıdaki resimde vurgu, metin yapışkan not ve mürekkep yapışkan not açıklamalarıbazı örnekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="eee7c-111">The following illustration shows some examples of highlight, text sticky note, and ink sticky note annotations.</span></span>  
  
 <span data-ttu-id="eee7c-112">![Vurgu, metin ve mürekkep yapışkan not ek açıklamaları.](./media/caf-stickynote.jpg "CAF_StickyNote")</span><span class="sxs-lookup"><span data-stu-id="eee7c-112">![Highlight, text and ink sticky note annotations.](./media/caf-stickynote.jpg "CAF_StickyNote")</span></span>  
  
 <span data-ttu-id="eee7c-113">Aşağıdaki örnek, uygulamanızda ek açıklama desteğini etkinleştirmek için kullanabileceğiniz yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="eee7c-113">The following example shows the method that you can use to enable annotation support in your application.</span></span>  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>
## <a name="highlights"></a><span data-ttu-id="eee7c-114">Önemli Noktalar</span><span class="sxs-lookup"><span data-stu-id="eee7c-114">Highlights</span></span>  
 <span data-ttu-id="eee7c-115">İnsanlar, bir kağıt belgeyi işaretlediğinde, bir cümledeki sözcükleri çizme, işaret veya işaret çekme gibi ilgi çekici öğelere dikkat çekmek için yaratıcı yöntemler kullanır.</span><span class="sxs-lookup"><span data-stu-id="eee7c-115">People use creative methods to draw attention to items of interest when they mark up a paper document, such as underlining, highlighting, circling words in a sentence, or drawing marks or notations in the margin.</span></span>  <span data-ttu-id="eee7c-116">Microsoft Ek Açıklamalar Çerçevesi'ndeki vurgu ek açıklamaları, WPF belge görüntüleme denetimlerinde görüntülenen bilgileri işaretlemek için benzer bir özellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="eee7c-116">Highlight annotations in Microsoft Annotations Framework provide a similar feature for marking up information displayed in WPF document viewing controls.</span></span>  
  
 <span data-ttu-id="eee7c-117">Aşağıdaki resimde vurgu ek açıklama bir örnek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="eee7c-117">The following illustration shows an example of a highlight annotation.</span></span>  
  
 <span data-ttu-id="eee7c-118">![Ek Açıklamayı Vurgula](./media/caf-callouts.png "CAF_Callouts")</span><span class="sxs-lookup"><span data-stu-id="eee7c-118">![Highlight Annotation](./media/caf-callouts.png "CAF_Callouts")</span></span>  
  
 <span data-ttu-id="eee7c-119">Kullanıcılar genellikle önce bir metin veya ilgi çekici bir öğe seçerek ve ardından ek <xref:System.Windows.Controls.ContextMenu> açıklama seçeneklerigörüntülemek için sağ tıklayarak ek açıklamalar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eee7c-119">Users typically create annotations by first selecting some text or an item of interest, and then right-clicking to display a <xref:System.Windows.Controls.ContextMenu> of annotation options.</span></span>  <span data-ttu-id="eee7c-120">Aşağıdaki örnek, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kullanıcıların ek açıklamalar <xref:System.Windows.Controls.ContextMenu> oluşturmak ve yönetmek için erişebileceği yönlendirilmiş komutları bildirmek için kullanabileceğiniz leri gösterir.</span><span class="sxs-lookup"><span data-stu-id="eee7c-120">The following example shows the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] you can use to declare a <xref:System.Windows.Controls.ContextMenu> with routed commands that users can access to create and manage annotations.</span></span>  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>
## <a name="data-anchoring"></a><span data-ttu-id="eee7c-121">Veri Bağlantı</span><span class="sxs-lookup"><span data-stu-id="eee7c-121">Data Anchoring</span></span>  
 <span data-ttu-id="eee7c-122">Ek Açıklamalar Çerçevesi, ek açıklamaları yalnızca görüntü görünümündeki bir konuma değil, kullanıcının seçtiği verilere bağlar.</span><span class="sxs-lookup"><span data-stu-id="eee7c-122">The Annotations Framework binds annotations to the data that the user selects, not just to a position on the display view.</span></span> <span data-ttu-id="eee7c-123">Bu nedenle, kullanıcı ekran penceresini kaydırdığında veya yeniden boyutlandırdığında olduğu gibi belge görünümü değişirse, ek açıklama bağlı olduğu veri seçiminde kalır.</span><span class="sxs-lookup"><span data-stu-id="eee7c-123">Therefore, if the document view changes, such as when the user scrolls or resizes the display window, the annotation stays with the data selection to which it is bound.</span></span> <span data-ttu-id="eee7c-124">Örneğin, aşağıdaki grafik, kullanıcının metin seçiminde yaptığı bir ek açıklamayı göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="eee7c-124">For example, the following graphic illustrates an annotation that the user has made on a text selection.</span></span> <span data-ttu-id="eee7c-125">Belge görünümü değiştiğinde (kaydırma, yeniden boyutlandırma, ölçeklendirme veya başka bir şekilde hareket ettiğinde), vurgu lama ek açıklama özgün veri seçimiyle birlikte hareket eder.</span><span class="sxs-lookup"><span data-stu-id="eee7c-125">When the document view changes (scrolls, resizes, scales, or otherwise moves), the highlight annotation moves with the original data selection.</span></span>  
  
 <span data-ttu-id="eee7c-126">![Ek Açıklama Veri Bağlantı](./media/caf-dataanchoring.png "CAF_DataAnchoring")</span><span class="sxs-lookup"><span data-stu-id="eee7c-126">![Annotation Data Anchoring](./media/caf-dataanchoring.png "CAF_DataAnchoring")</span></span>  
  
<a name="matching_annotations_with_annotated_objects"></a>
## <a name="matching-annotations-with-annotated-objects"></a><span data-ttu-id="eee7c-127">Açıklamalı Nesnelerle Açıklama eşleştirme</span><span class="sxs-lookup"><span data-stu-id="eee7c-127">Matching Annotations with Annotated Objects</span></span>  
 <span data-ttu-id="eee7c-128">Ek açıklamaları karşılık gelen ek açıklamalı nesnelerle eşleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eee7c-128">You can match annotations with the corresponding annotated objects.</span></span> <span data-ttu-id="eee7c-129">Örneğin, yorum bölmesi olan basit bir belge okuyucu uygulamasını düşünün.</span><span class="sxs-lookup"><span data-stu-id="eee7c-129">For example, consider a simple document reader application that has a comments pane.</span></span> <span data-ttu-id="eee7c-130">Açıklama bölmesi, belgeye bağlı ek açıklamalar listesinden metni görüntüleyen bir liste kutusu olabilir.</span><span class="sxs-lookup"><span data-stu-id="eee7c-130">The comments pane might be a list box that displays the text from a list of annotations that are anchored to a document.</span></span> <span data-ttu-id="eee7c-131">Kullanıcı liste kutusunda bir öğe seçerse, uygulama ilgili ek açıklama nesnesinin bağlı olduğu belgedeki paragrafı görüntületir.</span><span class="sxs-lookup"><span data-stu-id="eee7c-131">If the user selects an item in the list box, then the application brings into view the paragraph in the document that the corresponding annotation object is anchored to.</span></span>  
  
 <span data-ttu-id="eee7c-132">Aşağıdaki örnek, açıklama bölmesi olarak hizmet veren böyle bir liste kutusunun olay işleyicisinin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="eee7c-132">The following example demonstrates how to implement the event handler of such a list box that serves as the comments pane.</span></span>  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 <span data-ttu-id="eee7c-133">Başka bir örnek senaryo, e-posta yoluyla belge okuyucular arasında ek açıklamalar ve yapışkan notlar alışverişini sağlayan uygulamaları içerir.</span><span class="sxs-lookup"><span data-stu-id="eee7c-133">Another example scenario involves applications that enable the exchange of annotations and sticky notes between document readers through email.</span></span> <span data-ttu-id="eee7c-134">Bu özellik, bu uygulamaların okuyucuyu değiştirilmekte olan ek açıklamayı içeren sayfaya yönlendirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="eee7c-134">This feature enables these applications to navigate the reader to the page that contains the annotation that is being exchanged.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eee7c-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eee7c-135">See also</span></span>

- <xref:System.Windows.Controls.Primitives.DocumentViewerBase>
- <xref:System.Windows.Controls.DocumentViewer>
- <xref:System.Windows.Controls.FlowDocumentPageViewer>
- <xref:System.Windows.Controls.FlowDocumentScrollViewer>
- <xref:System.Windows.Controls.FlowDocumentReader>
- <xref:System.Windows.Annotations.IAnchorInfo>
- [<span data-ttu-id="eee7c-136">Ek Açıklamalar Şeması</span><span class="sxs-lookup"><span data-stu-id="eee7c-136">Annotations Schema</span></span>](annotations-schema.md)
- [<span data-ttu-id="eee7c-137">ContextMenu Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="eee7c-137">ContextMenu Overview</span></span>](../controls/contextmenu-overview.md)
- [<span data-ttu-id="eee7c-138">Komut Vermeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="eee7c-138">Commanding Overview</span></span>](commanding-overview.md)
- [<span data-ttu-id="eee7c-139">Akış Belgesine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="eee7c-139">Flow Document Overview</span></span>](flow-document-overview.md)
- <span data-ttu-id="eee7c-140">[Nasıl yapılsın: MenuItem'e Komut Ekleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="eee7c-140">[How to: Add a Command to a MenuItem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))</span></span>
