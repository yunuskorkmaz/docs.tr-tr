---
title: 'Nasıl yapılır: Gölgeli Metin Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: 0fe64e4e9e7aadbd30a38743647251f9fa49ba95
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960437"
---
# <a name="how-to-create-text-with-a-shadow"></a><span data-ttu-id="e8545-102">Nasıl yapılır: Gölgeli Metin Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e8545-102">How to: Create Text with a Shadow</span></span>
<span data-ttu-id="e8545-103">Bu bölümdeki örneklerde, görüntülenecek metin için bir gölge efektinin nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e8545-103">The examples in this section show how to create a shadow effect for displayed text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8545-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e8545-104">Example</span></span>  
 <span data-ttu-id="e8545-105">Nesnesi <xref:System.Windows.Media.Effects.DropShadowEffect> , nesneler için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] çeşitli gölge efektler oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8545-105">The <xref:System.Windows.Media.Effects.DropShadowEffect> object allows you to create a variety of drop shadow effects for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objects.</span></span> <span data-ttu-id="e8545-106">Aşağıdaki örnek, metne uygulanan bir gölge efekti gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8545-106">The following example shows a drop shadow effect applied to text.</span></span> <span data-ttu-id="e8545-107">Bu durumda, gölge bir gölgedir, bu da gölge rengin bulanıklaştırmasıdır.</span><span class="sxs-lookup"><span data-stu-id="e8545-107">In this case, the shadow is a soft shadow, which means the shadow color blurs.</span></span>  
  
 ![Soflük &#61; 0,25 ile metin gölgesi](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg) 
  
 <span data-ttu-id="e8545-109"><xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> Özelliği ayarlayarak bir gölgenin genişliğini kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8545-109">You can control the width of a shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> property.</span></span> <span data-ttu-id="e8545-110">Değeri 4 piksellik `4.0` bir gölge genişliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8545-110">A value of `4.0` indicates a shadow width of 4 pixels.</span></span> <span data-ttu-id="e8545-111"><xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> Özelliği değiştirerek, bir gölgenin yumuşaklığını veya bulanıklaştırarak denetim yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8545-111">You can control the softness, or blur, of a shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property.</span></span> <span data-ttu-id="e8545-112">Değeri, `0.0` bulanıklık olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8545-112">A value of `0.0` indicates no blurring.</span></span> <span data-ttu-id="e8545-113">Aşağıdaki kod örneği, nasıl yumuşak bir gölge oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="e8545-113">The following code example shows how to create a soft shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
> <span data-ttu-id="e8545-114">Bu gölge etkileri [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] metin işleme ardışık düzeninde ilerleyemez.</span><span class="sxs-lookup"><span data-stu-id="e8545-114">These shadow effects do not go through the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] text rendering pipeline.</span></span> <span data-ttu-id="e8545-115">Sonuç olarak, bu efektler kullanılırken ClearType devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="e8545-115">As a result, ClearType is disabled when using these effects.</span></span>  
  
 <span data-ttu-id="e8545-116">Aşağıdaki örnekte, metne uygulanan bir sabit gölge efekti gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e8545-116">The following example shows a hard drop shadow effect applied to text.</span></span> <span data-ttu-id="e8545-117">Bu durumda, gölge bulanık değildir.</span><span class="sxs-lookup"><span data-stu-id="e8545-117">In this case, the shadow is not blurred.</span></span>  
  
 ![Soflük &#61; 0 ile metin gölgesi](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg) 
  
 <span data-ttu-id="e8545-119"><xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> Özelliğini olarak`0.0`ayarlayarak sabit bir gölge oluşturabilirsiniz. Bu, bir bulanıklık kullanılmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8545-119">You can create a hard shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property to `0.0`, which indicates that no blurring is used.</span></span> <span data-ttu-id="e8545-120"><xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> Özelliği değiştirerek Gölgenin yönünü kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8545-120">You can control the direction of the shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property.</span></span> <span data-ttu-id="e8545-121">Bu özelliğin yönlü değerini ve `0` `360`arasında bir dereceye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e8545-121">Set the directional value of this property to a degree between `0` and `360`.</span></span> <span data-ttu-id="e8545-122">Aşağıdaki çizim, <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> özellik ayarının yönlü değerlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8545-122">The following illustration shows the directional values of the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property setting.</span></span>  
  
 ![Gölgenin DropShadow derecesi ayarı](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 <span data-ttu-id="e8545-124">Aşağıdaki kod örneği, sabit gölge oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8545-124">The following code example shows how to create a hard shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a><span data-ttu-id="e8545-125">Bulanıklaştırma efekti kullanma</span><span class="sxs-lookup"><span data-stu-id="e8545-125">Using a Blur Effect</span></span>  
 <span data-ttu-id="e8545-126">Bir <xref:System.Windows.Media.Effects.BlurBitmapEffect> metin nesnesinin arkasına yerleştirilebilecek bir gölge benzeri efekt oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e8545-126">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> can be used to create a shadow-like effect that can be placed behind a text object.</span></span> <span data-ttu-id="e8545-127">Metne uygulanan bir bulanıklaştırma bit eşlem efekti, metni her yönden eşit şekilde bulanıklaştırır.</span><span class="sxs-lookup"><span data-stu-id="e8545-127">A blur bitmap effect applied to text blurs the text evenly in all directions.</span></span>  
  
 <span data-ttu-id="e8545-128">Aşağıdaki örnek, metne uygulanan bir bulanıklaştırma efektini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8545-128">The following example shows a blur effect applied to text.</span></span>  
  
 ![Bir BlurBitmapEffect kullanarak metin gölgesi](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 <span data-ttu-id="e8545-130">Aşağıdaki kod örneği, bir bulanıklaştırma efektinin nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="e8545-130">The following code example shows how to create a blur effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a><span data-ttu-id="e8545-131">Çeviri dönüştürmesi kullanma</span><span class="sxs-lookup"><span data-stu-id="e8545-131">Using a Translate Transform</span></span>  
 <span data-ttu-id="e8545-132">Bir <xref:System.Windows.Media.TranslateTransform> metin nesnesinin arkasına yerleştirilebilecek bir gölge benzeri efekt oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e8545-132">A <xref:System.Windows.Media.TranslateTransform> can be used to create a shadow-like effect that can be placed behind a text object.</span></span>  
  
 <span data-ttu-id="e8545-133">Aşağıdaki kod örneği, metin kaydırmak <xref:System.Windows.Media.TranslateTransform> için bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="e8545-133">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="e8545-134">Bu örnekte, birincil metnin altındaki metnin biraz bir konum kopyası bir gölge efekti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e8545-134">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 ![TranslateTransform kullanarak metin gölgesi](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)    
  
 <span data-ttu-id="e8545-136">Aşağıdaki kod örneği, bir gölge efekti için dönüşümün nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="e8545-136">The following code example shows how to create a transform for a shadow effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
