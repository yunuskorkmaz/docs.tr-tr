---
title: 'Nasıl yapılır: Anahatları Belirlenmiş Metin Oluşturma'
ms.date: 03/30/2017
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
ms.openlocfilehash: 237bdc097cd2a3fbfff6dd79bce401c2d091e211
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776768"
---
# <a name="how-to-create-outlined-text"></a><span data-ttu-id="39394-102">Nasıl yapılır: Anahatları Belirlenmiş Metin Oluşturma</span><span class="sxs-lookup"><span data-stu-id="39394-102">How to: Create Outlined Text</span></span>
<span data-ttu-id="39394-103">Çoğu durumda, metin dizelerini için eklediğiniz zaman, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulama, kullanmakta olduğunuz farklı karakter veya karakterler koleksiyonu açısından metin.</span><span class="sxs-lookup"><span data-stu-id="39394-103">In most cases, when you are adding ornamentation to text strings in your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application, you are using text in terms of a collection of discrete characters, or glyphs.</span></span> <span data-ttu-id="39394-104">Örneğin, doğrusal gradyan fırçası oluşturmak ve uygulamak <xref:System.Windows.Controls.Control.Foreground%2A> özelliği bir <xref:System.Windows.Controls.TextBox> nesne.</span><span class="sxs-lookup"><span data-stu-id="39394-104">For example, you could create a linear gradient brush and apply it to the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.TextBox> object.</span></span> <span data-ttu-id="39394-105">Görüntüleme veya düzenleme metin kutusu, doğrusal gradyan fırçası geçerli bir metin dizesindeki bir karakter kümesini otomatik olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="39394-105">When you display or edit the text box, the linear gradient brush is automatically applied to the current set of characters in the text string.</span></span>  
  
 ![Doğrusal gradyan fırçası ile bir metin](./media/how-to-create-outlined-text/text-linear-gradient.jpg)    
  
 <span data-ttu-id="39394-107">Ancak, aynı zamanda metne dönüştürebilirsiniz <xref:System.Windows.Media.Geometry> diğer türde bir görsel olarak zengin metin oluşturmanızı sağlayan nesneler.</span><span class="sxs-lookup"><span data-stu-id="39394-107">However, you can also convert text into <xref:System.Windows.Media.Geometry> objects, allowing you to create other types of visually rich text.</span></span> <span data-ttu-id="39394-108">Örneğin, aşağıdakileri oluşturabilirsiniz bir <xref:System.Windows.Media.Geometry> nesne tabanlı bir metin dizesinin çerçevesinde.</span><span class="sxs-lookup"><span data-stu-id="39394-108">For example, you could create a <xref:System.Windows.Media.Geometry> object based on the outline of a text string.</span></span>  
  
 ![Metin anahat doğrusal gradyan fırçası kullanma](./media/how-to-create-outlined-text/text-outline-linear-gradient.jpg)  
  
 <span data-ttu-id="39394-110">Ne zaman metin dönüştürülür bir <xref:System.Windows.Media.Geometry> nesnesi, artık bir derlemesidir karakter — metin dizesindeki karakterlerin değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="39394-110">When text is converted to a <xref:System.Windows.Media.Geometry> object, it is no longer a collection of characters—you cannot modify the characters in the text string.</span></span> <span data-ttu-id="39394-111">Ancak, çizme ve İşaretleme dolgu özelliklerini değiştirerek Dönüştürülen metin görünümünü etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="39394-111">However, you can affect the appearance of the converted text by modifying its stroke and fill properties.</span></span> <span data-ttu-id="39394-112">Fırça darbesi Dönüştürülen metin anahattına gösterir. Dolgu Dönüştürülen metin özetini içindeki alan ifade eder.</span><span class="sxs-lookup"><span data-stu-id="39394-112">The stroke refers to the outline of the converted text; the fill refers to the area inside the outline of the converted text.</span></span>  
  
 <span data-ttu-id="39394-113">Aşağıdaki örnekler, görsel efektler vuruş ve dönüştürülen metin dolgu değiştirerek oluşturmanın birkaç yolu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="39394-113">The following examples illustrate several ways of creating visual effects by modifying the stroke and fill of converted text.</span></span>  
  
 ![Farklı renklerde doldurup için metin](./media/how-to-create-outlined-text/fill-stroke-text-effect.jpg)  
  
 ![Resim fırçası uygulandığı metin](./media/how-to-create-outlined-text/image-brush-application.jpg)
  
 <span data-ttu-id="39394-116">Sınırlayıcı kutusunun dikdörtgen veya vurgulama, dönüştürülen metin değiştirmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="39394-116">It is also possible to modify the bounding box rectangle, or highlight, of the converted text.</span></span> <span data-ttu-id="39394-117">Aşağıdaki örnek, dönüştürülen metin vurgulama ve vuruş değiştirerek görsel efektler oluşturmanın bir yolu gösterir.</span><span class="sxs-lookup"><span data-stu-id="39394-117">The following example illustrates a way to creating visual effects by modifying the stroke and highlight of converted text.</span></span>  
  
 ![Resim fırçası vuruş yapmak ve vurgulamak için uygulanan metin](./media/how-to-create-outlined-text/image-brush-text-application.jpg)

## <a name="example"></a><span data-ttu-id="39394-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="39394-119">Example</span></span>  
 <span data-ttu-id="39394-120">Metin dönüştürmenin anahtarı bir <xref:System.Windows.Media.Geometry> kullanılacak nesnedir <xref:System.Windows.Media.FormattedText> nesne.</span><span class="sxs-lookup"><span data-stu-id="39394-120">The key to converting text to a <xref:System.Windows.Media.Geometry> object is to use the <xref:System.Windows.Media.FormattedText> object.</span></span> <span data-ttu-id="39394-121">Bu nesne oluşturulduktan sonra kullanabileceğiniz <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> ve <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> metne dönüştürme yöntemleri <xref:System.Windows.Media.Geometry> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="39394-121">Once you have created this object, you can use the <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> and <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> methods to convert the text to <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="39394-122">İlk yöntem, geometri biçimlendirilmiş metin döndürür; İkinci yöntem, biçimlendirilmiş metnin geometrisini sınırlayıcı kutusunun döndürür.</span><span class="sxs-lookup"><span data-stu-id="39394-122">The first method returns the geometry of the formatted text; the second method returns the geometry of the formatted text's bounding box.</span></span> <span data-ttu-id="39394-123">Aşağıdaki kod örneğinde nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Media.FormattedText> nesne ve biçimlendirilmiş metnin ve sınırlayıcı kutusunun geometriler alınacak.</span><span class="sxs-lookup"><span data-stu-id="39394-123">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and to retrieve the geometries of the formatted text and its bounding box.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 <span data-ttu-id="39394-124">Alınan görüntülemek için <xref:System.Windows.Media.Geometry> nesnelerini erişmek için gereksinim duyduğunuz <xref:System.Windows.Media.DrawingContext> Dönüştürülen metin görüntüleme nesnesi.</span><span class="sxs-lookup"><span data-stu-id="39394-124">In order to display the retrieved the <xref:System.Windows.Media.Geometry> objects, you need to access the <xref:System.Windows.Media.DrawingContext> of the object that is displaying the converted text.</span></span> <span data-ttu-id="39394-125">Bu kod örnekleri, bu kullanıcı tanımlı işlemeyi destekleyen bir sınıftan türetilmiş bir özel denetim nesnesi oluşturarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="39394-125">In these code examples, this is done by creating a custom control object that is derived from a class that supports user-defined rendering.</span></span>  
  
 <span data-ttu-id="39394-126">Görüntülenecek <xref:System.Windows.Media.Geometry> özel denetimindeki nesnelere sağlamak için bir geçersiz kılma <xref:System.Windows.UIElement.OnRender%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="39394-126">To display <xref:System.Windows.Media.Geometry> objects in the custom control, provide an override for the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span> <span data-ttu-id="39394-127">Geçersiz kılınan yönteminizi kullanması gereken <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> çizmek için yöntemi <xref:System.Windows.Media.Geometry> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="39394-127">Your overridden method should use the <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> method to draw the <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  <span data-ttu-id="39394-128">Örnek özel kullanıcı denetimi nesnesinin kaynağını görmek [için OutlineTextControl.cs C# ](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) ve [Visual Basic için OutlineTextControl.vb](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).</span><span class="sxs-lookup"><span data-stu-id="39394-128">For the source of the example custom user control object, see [OutlineTextControl.cs for C#](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) and [OutlineTextControl.vb for Visual Basic](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="39394-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39394-129">See also</span></span>

- [<span data-ttu-id="39394-130">Biçimlendirilmiş Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="39394-130">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
