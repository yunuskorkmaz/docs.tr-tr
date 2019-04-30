---
title: 'Nasıl yapılır: Gölgeli Metin Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: a2225e297dbc0b5f9d49799cb34eb5539746e62e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776846"
---
# <a name="how-to-create-text-with-a-shadow"></a><span data-ttu-id="afae6-102">Nasıl yapılır: Gölgeli Metin Oluşturma</span><span class="sxs-lookup"><span data-stu-id="afae6-102">How to: Create Text with a Shadow</span></span>
<span data-ttu-id="afae6-103">Bu bölümdeki örneklerde, bir gölge etkisi görüntülenen metin oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="afae6-103">The examples in this section show how to create a shadow effect for displayed text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afae6-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="afae6-104">Example</span></span>  
 <span data-ttu-id="afae6-105"><xref:System.Windows.Media.Effects.DropShadowEffect> Nesne gölge efektleri bırakma çeşitli oluşturmanıza imkan tanır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nesneleri.</span><span class="sxs-lookup"><span data-stu-id="afae6-105">The <xref:System.Windows.Media.Effects.DropShadowEffect> object allows you to create a variety of drop shadow effects for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objects.</span></span> <span data-ttu-id="afae6-106">Aşağıdaki örnek, metne uygulanacak gölge etkisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="afae6-106">The following example shows a drop shadow effect applied to text.</span></span> <span data-ttu-id="afae6-107">Bu durumda, gölge gölge rengi Bulanıklaştırma anlamına gelir. bir yazılım gölge olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="afae6-107">In this case, the shadow is a soft shadow, which means the shadow color blurs.</span></span>  
  
 ![Metin gölgesinin Yumuşaklık ile &#61; 0,25](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg) 
  
 <span data-ttu-id="afae6-109">Ayarlayarak Gölge genişliğini denetleyebilir <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="afae6-109">You can control the width of a shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> property.</span></span> <span data-ttu-id="afae6-110">Değerini `4.0` 4 piksel Gölge genişliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="afae6-110">A value of `4.0` indicates a shadow width of 4 pixels.</span></span> <span data-ttu-id="afae6-111">Yumuşaklık denetleyebilir veya değiştirerek bir gölge Bulanıklığı <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="afae6-111">You can control the softness, or blur, of a shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property.</span></span> <span data-ttu-id="afae6-112">Değerini `0.0` hiçbir Bulanıklaştırma gösterir.</span><span class="sxs-lookup"><span data-stu-id="afae6-112">A value of `0.0` indicates no blurring.</span></span> <span data-ttu-id="afae6-113">Aşağıdaki kod örneği, geçici bir gölge oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="afae6-113">The following code example shows how to create a soft shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  <span data-ttu-id="afae6-114">Bu gölge efektleri üzerinden geçmemektedir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] metin işleme zinciri.</span><span class="sxs-lookup"><span data-stu-id="afae6-114">These shadow effects do not go through the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] text rendering pipeline.</span></span> <span data-ttu-id="afae6-115">Sonuç olarak, ClearType bu etkileri kullanırken devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="afae6-115">As a result, ClearType is disabled when using these effects.</span></span>  
  
 <span data-ttu-id="afae6-116">Aşağıdaki örnek, metin için uygulanan sabit gölge etkisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="afae6-116">The following example shows a hard drop shadow effect applied to text.</span></span> <span data-ttu-id="afae6-117">Bu durumda, gölge bulanık değildir.</span><span class="sxs-lookup"><span data-stu-id="afae6-117">In this case, the shadow is not blurred.</span></span>  
  
 ![Metin gölgesinin Yumuşaklık ile &#61; 0](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg) 
  
 <span data-ttu-id="afae6-119">Sabit bir gölge ayarlayarak oluşturabileceğiniz <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> özelliğini `0.0`, hiçbir Bulanıklaştırma kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="afae6-119">You can create a hard shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property to `0.0`, which indicates that no blurring is used.</span></span> <span data-ttu-id="afae6-120">Gölge yönünü değiştirerek denetleyebilirsiniz <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="afae6-120">You can control the direction of the shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property.</span></span> <span data-ttu-id="afae6-121">Bu özelliğin yön değeri arasında bir dereceye ayarlayın `0` ve `360`.</span><span class="sxs-lookup"><span data-stu-id="afae6-121">Set the directional value of this property to a degree between `0` and `360`.</span></span> <span data-ttu-id="afae6-122">Tek yönlü değerlerini aşağıdaki çizimde <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> özellik ayarı.</span><span class="sxs-lookup"><span data-stu-id="afae6-122">The following illustration shows the directional values of the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property setting.</span></span>  
  
 ![Gölgenin DropShadow derece ayarı](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 <span data-ttu-id="afae6-124">Aşağıdaki kod örneği, sabit bir gölge oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="afae6-124">The following code example shows how to create a hard shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a><span data-ttu-id="afae6-125">Bulanıklaştırma efekt kullanma</span><span class="sxs-lookup"><span data-stu-id="afae6-125">Using a Blur Effect</span></span>  
 <span data-ttu-id="afae6-126">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> metin nesnesi yerleştirilebilir bir gölge benzeri etkisi oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="afae6-126">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> can be used to create a shadow-like effect that can be placed behind a text object.</span></span> <span data-ttu-id="afae6-127">Metnin her yöne eşit olarak metne uygulanan bir bulanıklaştırma bit eşlem etkisi bulanıklaştırır.</span><span class="sxs-lookup"><span data-stu-id="afae6-127">A blur bitmap effect applied to text blurs the text evenly in all directions.</span></span>  
  
 <span data-ttu-id="afae6-128">Aşağıdaki örnek metni uygulanan bir bulanıklaştırma etkisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="afae6-128">The following example shows a blur effect applied to text.</span></span>  
  
 ![Metin gölgesinin BlurBitmapEffect kullanma](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 <span data-ttu-id="afae6-130">Aşağıdaki kod örneği, Bulanıklaştırma efekti oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="afae6-130">The following code example shows how to create a blur effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a><span data-ttu-id="afae6-131">Çeviri dönüşümü kullanma</span><span class="sxs-lookup"><span data-stu-id="afae6-131">Using a Translate Transform</span></span>  
 <span data-ttu-id="afae6-132">A <xref:System.Windows.Media.TranslateTransform> metin nesnesi yerleştirilebilir bir gölge benzeri etkisi oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="afae6-132">A <xref:System.Windows.Media.TranslateTransform> can be used to create a shadow-like effect that can be placed behind a text object.</span></span>  
  
 <span data-ttu-id="afae6-133">Aşağıdaki kod örneğinde bir <xref:System.Windows.Media.TranslateTransform> metin uzaklık.</span><span class="sxs-lookup"><span data-stu-id="afae6-133">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="afae6-134">Bu örnekte, bir gölge etkisi birincil metin aşağıdaki metni biraz uzaklık bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="afae6-134">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 ![Metin gölgesinin TranslateTransform kullanma](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)    
  
 <span data-ttu-id="afae6-136">Aşağıdaki kod örneği, bir gölge etkisi dönüşümü oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="afae6-136">The following code example shows how to create a transform for a shadow effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
