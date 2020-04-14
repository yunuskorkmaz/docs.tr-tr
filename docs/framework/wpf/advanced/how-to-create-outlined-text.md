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
ms.openlocfilehash: 86bfa396a2aa44eb511c014687501d60e170a396
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278931"
---
# <a name="how-to-create-outlined-text"></a><span data-ttu-id="f03e1-102">Nasıl yapılsın: Özetlenen metin oluşturma</span><span class="sxs-lookup"><span data-stu-id="f03e1-102">How to: Create outlined text</span></span>

<span data-ttu-id="f03e1-103">Çoğu durumda, uygulamanızdaki [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] metin dizelerine süsleme eklerken, metni ayrı karakterler veya glifler koleksiyonu açısından kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="f03e1-103">In most cases, when you're adding ornamentation to text strings in your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application, you are using text in terms of a collection of discrete characters, or glyphs.</span></span> <span data-ttu-id="f03e1-104">Örneğin, doğrusal bir degrade fırça sıcabilir <xref:System.Windows.Controls.Control.Foreground%2A> ve <xref:System.Windows.Controls.TextBox> bunu bir nesnenin özelliğine uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f03e1-104">For example, you could create a linear gradient brush and apply it to the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.TextBox> object.</span></span> <span data-ttu-id="f03e1-105">Metin kutusunu görüntülediğinizde veya yaptığınızda, doğrusal degrade fırçası metin dizesindeki geçerli karakter kümesine otomatik olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f03e1-105">When you display or edit the text box, the linear gradient brush is automatically applied to the current set of characters in the text string.</span></span>  
  
 ![Doğrusal degrade fırçasıyla görüntülenen metin](./media/how-to-create-outlined-text/text-linear-gradient.jpg)
  
 <span data-ttu-id="f03e1-107">Ancak, görsel açıdan zengin <xref:System.Windows.Media.Geometry> başka metin türleri oluşturmanıza olanak tanıyan metni nesnelere dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f03e1-107">However, you can also convert text into <xref:System.Windows.Media.Geometry> objects, allowing you to create other types of visually rich text.</span></span> <span data-ttu-id="f03e1-108">Örneğin, bir metin <xref:System.Windows.Media.Geometry> dizesinin anahatlarını temel alan bir nesne oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f03e1-108">For example, you could create a <xref:System.Windows.Media.Geometry> object based on the outline of a text string.</span></span>  
  
 ![Doğrusal degrade fırçası kullanarak metin anahattı](./media/how-to-create-outlined-text/text-outline-linear-gradient.jpg)  
  
 <span data-ttu-id="f03e1-110">Metin bir <xref:System.Windows.Media.Geometry> nesneye dönüştürüldüğünde, artık bir karakter topluluğu değildir—metin dizesindeki karakterleri değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="f03e1-110">When text is converted to a <xref:System.Windows.Media.Geometry> object, it is no longer a collection of characters—you cannot modify the characters in the text string.</span></span> <span data-ttu-id="f03e1-111">Ancak, kontur ve dolgu özelliklerini değiştirerek dönüştürülen metnin görünümünü etkileyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f03e1-111">However, you can affect the appearance of the converted text by modifying its stroke and fill properties.</span></span> <span data-ttu-id="f03e1-112">Kontur, dönüştürülen metnin anahatlarını ifade eder; dolgu, dönüştürülen metnin anahat içindeki alanı ifade eder.</span><span class="sxs-lookup"><span data-stu-id="f03e1-112">The stroke refers to the outline of the converted text; the fill refers to the area inside the outline of the converted text.</span></span>  
  
 <span data-ttu-id="f03e1-113">Aşağıdaki örnekler, dönüştürülen metnin konturunu ve dolgusunu değiştirerek görsel efekt oluşturmanın çeşitli yollarını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="f03e1-113">The following examples illustrate several ways of creating visual effects by modifying the stroke and fill of converted text.</span></span>  
  
 ![Dolgu ve kontur için farklı renklere sahip metin](./media/how-to-create-outlined-text/fill-stroke-text-effect.jpg)  
  
 ![Kontura uygulanan görüntü fırçası ile metin](./media/how-to-create-outlined-text/image-brush-application.jpg)
  
 <span data-ttu-id="f03e1-116">Dönüştürülen metnin sınırlayıcı kutusu dikdörtgenini veya vurgusunu değiştirmek de mümkündür.</span><span class="sxs-lookup"><span data-stu-id="f03e1-116">It is also possible to modify the bounding box rectangle, or highlight, of the converted text.</span></span> <span data-ttu-id="f03e1-117">Aşağıdaki örnek, dönüştürülen metnin konturunu ve vurgusunu değiştirerek görsel efekt oluşturmanın bir yolunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="f03e1-117">The following example illustrates a way to create visual effects by modifying the stroke and highlight of converted text.</span></span>  
  
 ![Kontur ve vurgulamaya uygulanan görüntü fırçası ile metin](./media/how-to-create-outlined-text/image-brush-text-application.jpg)

## <a name="example"></a><span data-ttu-id="f03e1-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="f03e1-119">Example</span></span>  
 <span data-ttu-id="f03e1-120">Metni bir <xref:System.Windows.Media.Geometry> nesneye dönüştürmenin anahtarı nesneyi <xref:System.Windows.Media.FormattedText> kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="f03e1-120">The key to converting text to a <xref:System.Windows.Media.Geometry> object is to use the <xref:System.Windows.Media.FormattedText> object.</span></span> <span data-ttu-id="f03e1-121">Bu nesneyi oluşturduktan sonra, <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> metni <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> nesnelere dönüştürmek <xref:System.Windows.Media.Geometry> için bu ve yöntemleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f03e1-121">Once you have created this object, you can use the <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> and <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> methods to convert the text to <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="f03e1-122">İlk yöntem biçimlendirilmiş metnin geometrisini döndürür; ikinci yöntem biçimlendirilmiş metnin sınırlayıcı kutusunun geometrisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f03e1-122">The first method returns the geometry of the formatted text; the second method returns the geometry of the formatted text's bounding box.</span></span> <span data-ttu-id="f03e1-123">Aşağıdaki kod örneği, bir <xref:System.Windows.Media.FormattedText> nesnenin nasıl oluşturulup biçimlendirilmiş metnin ve sınırlayıcı kutusunun geometrilerini nasıl alınca gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f03e1-123">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and to retrieve the geometries of the formatted text and its bounding box.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 <span data-ttu-id="f03e1-124">Alınan <xref:System.Windows.Media.Geometry> nesneleri görüntülemek için dönüştürülen metni görüntüleyen <xref:System.Windows.Media.DrawingContext> nesnenin erişimine erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f03e1-124">In order to display the retrieved the <xref:System.Windows.Media.Geometry> objects, you need to access the <xref:System.Windows.Media.DrawingContext> of the object that's displaying the converted text.</span></span> <span data-ttu-id="f03e1-125">Bu kod örneklerinde, bu erişim, kullanıcı tanımlı işlemeyi destekleyen bir sınıftan türetilen özel bir denetim nesnesi oluşturularak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="f03e1-125">In these code examples, this access is achieved by creating a custom control object that's derived from a class that supports user-defined rendering.</span></span>  
  
 <span data-ttu-id="f03e1-126">Nesneleri <xref:System.Windows.Media.Geometry> özel denetimde görüntülemek için <xref:System.Windows.UIElement.OnRender%2A> yöntem için bir geçersiz kılma sağlayın.</span><span class="sxs-lookup"><span data-stu-id="f03e1-126">To display <xref:System.Windows.Media.Geometry> objects in the custom control, provide an override for the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span> <span data-ttu-id="f03e1-127">Geçersiz kılınan yöntem, <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> <xref:System.Windows.Media.Geometry> nesneleri çizmek için yöntemi kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f03e1-127">Your overridden method should use the <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> method to draw the <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  <span data-ttu-id="f03e1-128">Örnek özel kullanıcı denetim nesnesinin kaynağı için, Visual Basic [için C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) için OutlineTextControl.cs ve [OutlineTextControl.vb bölümüne](https://github.com/dotnet/docs/blob/master/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb)bakın.</span><span class="sxs-lookup"><span data-stu-id="f03e1-128">For the source of the example custom user control object, see [OutlineTextControl.cs for C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) and [OutlineTextControl.vb for Visual Basic](https://github.com/dotnet/docs/blob/master/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f03e1-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f03e1-129">See also</span></span>

- [<span data-ttu-id="f03e1-130">Biçimlendirilmiş Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="f03e1-130">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
