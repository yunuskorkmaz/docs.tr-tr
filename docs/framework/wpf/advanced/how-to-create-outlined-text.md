---
title: "Nasıl yapılır: Anahatları Belirlenmiş Metin Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], linear gradient brush
- outlined text [WPF]
- gradient brush [WPF]
- linear gradient brush [WPF]
- typography [WPF], outline effects
ms.assetid: 4aa3cf6e-1953-4f26-8230-7c1409e5f28d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 41254d8f93174c896923b1c070e6bf9b5b7c863c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-outlined-text"></a><span data-ttu-id="b27ef-102">Nasıl yapılır: Anahatları Belirlenmiş Metin Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b27ef-102">How to: Create Outlined Text</span></span>
<span data-ttu-id="b27ef-103">Çoğu durumda, metin dizelerini için eklediğiniz zaman, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulama, kullanmakta olduğunuz farklı karakter ya da karakterlerin koleksiyonu bakımından metin.</span><span class="sxs-lookup"><span data-stu-id="b27ef-103">In most cases, when you are adding ornamentation to text strings in your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application, you are using text in terms of a collection of discrete characters, or glyphs.</span></span> <span data-ttu-id="b27ef-104">Örneğin, doğrusal gradyan fırçası oluşturabilir ve uygulayan <xref:System.Windows.Controls.Control.Foreground%2A> özelliği bir <xref:System.Windows.Controls.TextBox> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b27ef-104">For example, you could create a linear gradient brush and apply it to the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.TextBox> object.</span></span> <span data-ttu-id="b27ef-105">Görüntüleme veya düzenleme metin kutusu, doğrusal gradyan fırçası metin dizesindeki karakterlerin geçerli kümesini otomatik olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b27ef-105">When you display or edit the text box, the linear gradient brush is automatically applied to the current set of characters in the text string.</span></span>  
  
 <span data-ttu-id="b27ef-106">![Doğrusal gradyan fırçası ile görüntülenen metin](../../../../docs/framework/wpf/advanced/media/outlinedtext01.jpg "OutlinedText01")</span><span class="sxs-lookup"><span data-stu-id="b27ef-106">![Text displayed with a linear gradient brush](../../../../docs/framework/wpf/advanced/media/outlinedtext01.jpg "OutlinedText01")</span></span>  
<span data-ttu-id="b27ef-107">Bir metin kutusuna uygulanan doğrusal gradyan fırçası örneği</span><span class="sxs-lookup"><span data-stu-id="b27ef-107">Example of a linear gradient brush applied to a text box</span></span>  
  
 <span data-ttu-id="b27ef-108">Ancak, aynı zamanda metne dönüştürebilirsiniz <xref:System.Windows.Media.Geometry> nesneleri, sizin görsel olarak zengin metin diğer türleri oluşturmanıza izin verir.</span><span class="sxs-lookup"><span data-stu-id="b27ef-108">However, you can also convert text into <xref:System.Windows.Media.Geometry> objects, allowing you to create other types of visually rich text.</span></span> <span data-ttu-id="b27ef-109">Örneğin, oluşturabilirsiniz bir <xref:System.Windows.Media.Geometry> nesne tabanlı bir metin dizesinin anahattına.</span><span class="sxs-lookup"><span data-stu-id="b27ef-109">For example, you could create a <xref:System.Windows.Media.Geometry> object based on the outline of a text string.</span></span>  
  
 <span data-ttu-id="b27ef-110">![Doğrusal gradyan fırçası kullanarak metin anahattı](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")</span><span class="sxs-lookup"><span data-stu-id="b27ef-110">![Text outline using a linear gradient brush](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")</span></span>  
<span data-ttu-id="b27ef-111">Metin anahat geometriye uygulanan doğrusal gradyan fırçası örneği</span><span class="sxs-lookup"><span data-stu-id="b27ef-111">Example of a linear gradient brush applied to the outline geometry of text</span></span>  
  
 <span data-ttu-id="b27ef-112">Ne zaman metin dönüştürülür için bir <xref:System.Windows.Media.Geometry> nesne olduğu artık karakterler koleksiyonu — metin dizesindeki karakterleri değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="b27ef-112">When text is converted to a <xref:System.Windows.Media.Geometry> object, it is no longer a collection of characters—you cannot modify the characters in the text string.</span></span> <span data-ttu-id="b27ef-113">Ancak, vuruş ve dolgu özelliklerini değiştirerek Dönüştürülen metin görünümünü etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="b27ef-113">However, you can affect the appearance of the converted text by modifying its stroke and fill properties.</span></span> <span data-ttu-id="b27ef-114">Vuruşun Dönüştürülen metin anahattına gösterir; Dolgu alanının içini Dönüştürülen metin anahat ifade eder.</span><span class="sxs-lookup"><span data-stu-id="b27ef-114">The stroke refers to the outline of the converted text; the fill refers to the area inside the outline of the converted text.</span></span>  
  
 <span data-ttu-id="b27ef-115">Aşağıdaki örneklerde vuruş ve dönüştürülen metin dolgusunu değiştirerek görsel efektler oluşturmanın birkaç yolu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b27ef-115">The following examples illustrate several ways of creating visual effects by modifying the stroke and fill of converted text.</span></span>  
  
 <span data-ttu-id="b27ef-116">![Doldurma ve vuruş yapmak için farklı renkler metinle](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")</span><span class="sxs-lookup"><span data-stu-id="b27ef-116">![Text with different colors for fill and stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")</span></span>  
<span data-ttu-id="b27ef-117">Farklı renk vuruş ve dolgu ayarlama örneği</span><span class="sxs-lookup"><span data-stu-id="b27ef-117">Example of setting stroke and fill to different colors</span></span>  
  
 <span data-ttu-id="b27ef-118">![Görüntü fırça uygulandığı metinle](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")</span><span class="sxs-lookup"><span data-stu-id="b27ef-118">![Text with image brush applied to stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")</span></span>  
<span data-ttu-id="b27ef-119">Uygulandığı bir resim fırçası örneği</span><span class="sxs-lookup"><span data-stu-id="b27ef-119">Example of an image brush applied to the stroke</span></span>  
  
 <span data-ttu-id="b27ef-120">Sınırlama kutusu dikdörtgen veya dönüştürülen metni vurgulama değiştirmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="b27ef-120">It is also possible to modify the bounding box rectangle, or highlight, of the converted text.</span></span> <span data-ttu-id="b27ef-121">Aşağıdaki örnek, vuruş ve dönüştürülen metin Vurgusu değiştirerek görsel efektler oluşturmanın bir şekilde gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b27ef-121">The following example illustrates a way to creating visual effects by modifying the stroke and highlight of converted text.</span></span>  
  
 <span data-ttu-id="b27ef-122">![Görüntü fırça uygulandığı metinle](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")</span><span class="sxs-lookup"><span data-stu-id="b27ef-122">![Text with image brush applied to stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")</span></span>  
<span data-ttu-id="b27ef-123">Vuruş ve vurgulamaya uygulanan resim fırçası örneği</span><span class="sxs-lookup"><span data-stu-id="b27ef-123">Example of an image brush applied to the stroke and highlight</span></span>  
  
## <a name="example"></a><span data-ttu-id="b27ef-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="b27ef-124">Example</span></span>  
 <span data-ttu-id="b27ef-125">Metne dönüştürme anahtarını bir <xref:System.Windows.Media.Geometry> nesnesi kullanmaktır <xref:System.Windows.Media.FormattedText> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b27ef-125">The key to converting text to a <xref:System.Windows.Media.Geometry> object is to use the <xref:System.Windows.Media.FormattedText> object.</span></span> <span data-ttu-id="b27ef-126">Bu nesne oluşturduktan sonra kullanabileceğiniz <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> ve <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> metne dönüştürmek için yöntemleri <xref:System.Windows.Media.Geometry> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b27ef-126">Once you have created this object, you can use the <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> and <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> methods to convert the text to <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="b27ef-127">İlk yöntem geometri biçimlendirilmiş metin döndürür; İkinci yöntem, geometri biçimlendirilmiş metin kutusu sınırlayıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="b27ef-127">The first method returns the geometry of the formatted text; the second method returns the geometry of the formatted text's bounding box.</span></span> <span data-ttu-id="b27ef-128">Aşağıdaki kod örneğinde nasıl oluşturulacağını gösterir bir <xref:System.Windows.Media.FormattedText> nesne ve biçimlendirilmiş metin ve kendi sınırlama kutusu geometri alınamadı.</span><span class="sxs-lookup"><span data-stu-id="b27ef-128">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and to retrieve the geometries of the formatted text and its bounding box.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 <span data-ttu-id="b27ef-129">Alınan görüntülemek için <xref:System.Windows.Media.Geometry> nesneleri erişmek gereken <xref:System.Windows.Media.DrawingContext> Dönüştürülen metin görüntüleme nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b27ef-129">In order to display the retrieved the <xref:System.Windows.Media.Geometry> objects, you need to access the <xref:System.Windows.Media.DrawingContext> of the object that is displaying the converted text.</span></span> <span data-ttu-id="b27ef-130">Bu kod örneklerinde, kullanıcı tanımlı işlemeyi destekleyen bir sınıfından türetilen özel bir denetim nesnesi oluşturarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="b27ef-130">In these code examples, this is done by creating a custom control object that is derived from a class that supports user-defined rendering.</span></span>  
  
 <span data-ttu-id="b27ef-131">Görüntülenecek <xref:System.Windows.Media.Geometry> özel denetim nesneleri sağlamak için bir geçersiz kılma <xref:System.Windows.UIElement.OnRender%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b27ef-131">To display <xref:System.Windows.Media.Geometry> objects in the custom control, provide an override for the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span> <span data-ttu-id="b27ef-132">Geçersiz kılınan yönteminizi kullanması gereken <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> çizmek için yöntemi <xref:System.Windows.Media.Geometry> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b27ef-132">Your overridden method should use the <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> method to draw the <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
## <a name="see-also"></a><span data-ttu-id="b27ef-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b27ef-133">See Also</span></span>  
 [<span data-ttu-id="b27ef-134">Biçimlendirilmiş Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="b27ef-134">Drawing Formatted Text</span></span>](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
