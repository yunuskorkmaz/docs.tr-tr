---
title: 'Nasıl yapılır: Gölgeli Metin Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: c3e8135372ce4a092552c812cd971cb70bc49bf3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186844"
---
# <a name="how-to-create-text-with-a-shadow"></a><span data-ttu-id="acea7-102">Nasıl yapılır: Gölgeli Metin Oluşturma</span><span class="sxs-lookup"><span data-stu-id="acea7-102">How to: Create Text with a Shadow</span></span>
<span data-ttu-id="acea7-103">Bu bölümdeki örnekler, görüntülenen metin için gölge efektinin nasıl oluşturulabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="acea7-103">The examples in this section show how to create a shadow effect for displayed text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="acea7-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="acea7-104">Example</span></span>  
 <span data-ttu-id="acea7-105">Nesne, <xref:System.Windows.Media.Effects.DropShadowEffect> nesneler için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] çeşitli damla gölge efektleri oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="acea7-105">The <xref:System.Windows.Media.Effects.DropShadowEffect> object allows you to create a variety of drop shadow effects for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objects.</span></span> <span data-ttu-id="acea7-106">Aşağıdaki örnekte, metne uygulanan bir açılır gölge efekti gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="acea7-106">The following example shows a drop shadow effect applied to text.</span></span> <span data-ttu-id="acea7-107">Bu durumda, gölge yumuşak bir gölgedir, bu da gölge renginin bulanıkolduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="acea7-107">In this case, the shadow is a soft shadow, which means the shadow color blurs.</span></span>  
  
 ![Yumuşaklıklı metin gölgesi 0,25 &#61;](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg)
  
 <span data-ttu-id="acea7-109"><xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> Özelliği ayarlayarak gölgenin genişliğini denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acea7-109">You can control the width of a shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> property.</span></span> <span data-ttu-id="acea7-110">Değeri 4 `4.0` piksel lik bir gölge genişliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="acea7-110">A value of `4.0` indicates a shadow width of 4 pixels.</span></span> <span data-ttu-id="acea7-111"><xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> Özelliği değiştirerek gölgenin yumuşaklığını veya bulanıklığını denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acea7-111">You can control the softness, or blur, of a shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property.</span></span> <span data-ttu-id="acea7-112">Bir değer `0.0` bulanıklık gösterir.</span><span class="sxs-lookup"><span data-stu-id="acea7-112">A value of `0.0` indicates no blurring.</span></span> <span data-ttu-id="acea7-113">Aşağıdaki kod örneği, yumuşak bir gölgenin nasıl oluşturulabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="acea7-113">The following code example shows how to create a soft shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
> <span data-ttu-id="acea7-114">Bu gölge efektleri [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] metin işleme ardışık etki tarafından gitmez.</span><span class="sxs-lookup"><span data-stu-id="acea7-114">These shadow effects do not go through the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] text rendering pipeline.</span></span> <span data-ttu-id="acea7-115">Sonuç olarak, bu efektleri kullanırken ClearType devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="acea7-115">As a result, ClearType is disabled when using these effects.</span></span>  
  
 <span data-ttu-id="acea7-116">Aşağıdaki örnek, metne uygulanan sabit bir gölge efekti gösterir.</span><span class="sxs-lookup"><span data-stu-id="acea7-116">The following example shows a hard drop shadow effect applied to text.</span></span> <span data-ttu-id="acea7-117">Bu durumda, gölge bulanık değildir.</span><span class="sxs-lookup"><span data-stu-id="acea7-117">In this case, the shadow is not blurred.</span></span>  
  
 ![Yumuşaklık &#61; 0 ile metin gölgesi](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg)
  
 <span data-ttu-id="acea7-119"><xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> Özelliği `0.0`, bulanıklık kullanılmadığını gösteren şekilde ayarlayarak sabit bir gölge oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acea7-119">You can create a hard shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property to `0.0`, which indicates that no blurring is used.</span></span> <span data-ttu-id="acea7-120"><xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> Özelliği değiştirerek gölgenin yönünü denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acea7-120">You can control the direction of the shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property.</span></span> <span data-ttu-id="acea7-121">Bu özelliğin yön değerini bir `0` dereceye `360`kadar ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="acea7-121">Set the directional value of this property to a degree between `0` and `360`.</span></span> <span data-ttu-id="acea7-122">Aşağıdaki resimde <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> özellik ayarı yön değerlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="acea7-122">The following illustration shows the directional values of the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property setting.</span></span>  
  
 ![Gölgenin DropShadow derece ayarı](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 <span data-ttu-id="acea7-124">Aşağıdaki kod örneği, sabit bir gölgenin nasıl oluşturulabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="acea7-124">The following code example shows how to create a hard shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a><span data-ttu-id="acea7-125">Bulanıklaştırma Efekti Kullanma</span><span class="sxs-lookup"><span data-stu-id="acea7-125">Using a Blur Effect</span></span>  
 <span data-ttu-id="acea7-126">A, <xref:System.Windows.Media.Effects.BlurBitmapEffect> metin nesnesi arkasına yerleştirilebilir gölge benzeri bir efekt oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="acea7-126">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> can be used to create a shadow-like effect that can be placed behind a text object.</span></span> <span data-ttu-id="acea7-127">Metne uygulanan bulanıklık biteşefekti efekti metni tüm yönlerde eşit olarak bulanıklaştırır.</span><span class="sxs-lookup"><span data-stu-id="acea7-127">A blur bitmap effect applied to text blurs the text evenly in all directions.</span></span>  
  
 <span data-ttu-id="acea7-128">Aşağıdaki örnekte metne uygulanan bulanıklık efekti gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="acea7-128">The following example shows a blur effect applied to text.</span></span>  
  
 ![BlurBitmapEffect kullanarak metin gölgesi](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 <span data-ttu-id="acea7-130">Aşağıdaki kod örneği, bulanıklaştırma efektinin nasıl oluşturulabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="acea7-130">The following code example shows how to create a blur effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a><span data-ttu-id="acea7-131">Çevirme Dönüştürme'yi Kullanma</span><span class="sxs-lookup"><span data-stu-id="acea7-131">Using a Translate Transform</span></span>  
 <span data-ttu-id="acea7-132">A, <xref:System.Windows.Media.TranslateTransform> metin nesnesi arkasına yerleştirilebilir gölge benzeri bir efekt oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="acea7-132">A <xref:System.Windows.Media.TranslateTransform> can be used to create a shadow-like effect that can be placed behind a text object.</span></span>  
  
 <span data-ttu-id="acea7-133">Aşağıdaki kod örneği, <xref:System.Windows.Media.TranslateTransform> metni dengelemek için a kullanır.</span><span class="sxs-lookup"><span data-stu-id="acea7-133">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="acea7-134">Bu örnekte, birincil metnin altındaki metnin biraz ofset kopyası gölge efekti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="acea7-134">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 ![TranslateTransform kullanarak metin gölgesi](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)
  
 <span data-ttu-id="acea7-136">Aşağıdaki kod örneği, gölge efekti için dönüşümün nasıl oluşturulabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="acea7-136">The following code example shows how to create a transform for a shadow effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
