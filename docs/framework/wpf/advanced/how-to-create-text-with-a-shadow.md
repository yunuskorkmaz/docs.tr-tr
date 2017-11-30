---
title: "Nasıl yapılır: Gölgeli Metin Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31bbc3da54c10304e52f93d38365a8d9ed005505
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-text-with-a-shadow"></a><span data-ttu-id="b55f0-102">Nasıl yapılır: Gölgeli Metin Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b55f0-102">How to: Create Text with a Shadow</span></span>
<span data-ttu-id="b55f0-103">Bu bölümdeki örnekleri görüntülenen metin gölge efekti oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b55f0-103">The examples in this section show how to create a shadow effect for displayed text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b55f0-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="b55f0-104">Example</span></span>  
 <span data-ttu-id="b55f0-105"><xref:System.Windows.Media.Effects.DropShadowEffect> Nesne açılan çeşitli gölge efektleri oluşturmanıza imkan tanır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b55f0-105">The <xref:System.Windows.Media.Effects.DropShadowEffect> object allows you to create a variety of drop shadow effects for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objects.</span></span> <span data-ttu-id="b55f0-106">Aşağıdaki örnek metne uygulanan bir gölge efekti gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b55f0-106">The following example shows a drop shadow effect applied to text.</span></span> <span data-ttu-id="b55f0-107">Bu durumda, gölge gölge rengini bulanıklıklaştırmalar anlamına gelir yumuşak gölge olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="b55f0-107">In this case, the shadow is a soft shadow, which means the shadow color blurs.</span></span>  
  
 <span data-ttu-id="b55f0-108">![Metin gölgesinin Yumuşaklık &#61; 0,25](../../../../docs/framework/wpf/advanced/media/shadowtext01.jpg "ShadowText01")</span><span class="sxs-lookup"><span data-stu-id="b55f0-108">![Text shadow with Softness &#61; 0.25](../../../../docs/framework/wpf/advanced/media/shadowtext01.jpg "ShadowText01")</span></span>  
<span data-ttu-id="b55f0-109">Yumuşak gölgeli metin örneği</span><span class="sxs-lookup"><span data-stu-id="b55f0-109">Example of text with a soft shadow</span></span>  
  
 <span data-ttu-id="b55f0-110">Ayarlayarak Gölge genişliğini kontrol edebilirsiniz <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b55f0-110">You can control the width of a shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> property.</span></span> <span data-ttu-id="b55f0-111">Değerini `4.0` 4 piksel Gölge genişliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b55f0-111">A value of `4.0` indicates a shadow width of 4 pixels.</span></span> <span data-ttu-id="b55f0-112">Yumuşaklık kontrol edebilirsiniz veya değiştirerek bir gölge Bulanıklığı <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b55f0-112">You can control the softness, or blur, of a shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property.</span></span> <span data-ttu-id="b55f0-113">Değerini `0.0` hiçbir bulanıklık belirtir.</span><span class="sxs-lookup"><span data-stu-id="b55f0-113">A value of `0.0` indicates no blurring.</span></span> <span data-ttu-id="b55f0-114">Aşağıdaki kod örneğinde yumuşak gölge oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b55f0-114">The following code example shows how to create a soft shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  <span data-ttu-id="b55f0-115">Bu gölge efektleri üzerinden geçmemektedir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] metin işleme ardışık düzeni.</span><span class="sxs-lookup"><span data-stu-id="b55f0-115">These shadow effects do not go through the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] text rendering pipeline.</span></span> <span data-ttu-id="b55f0-116">Sonuç olarak, ClearType bu etkilerle kullanırken devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="b55f0-116">As a result, ClearType is disabled when using these effects.</span></span>  
  
 <span data-ttu-id="b55f0-117">Aşağıdaki örnek metne uygulanan bir sabit gölge efekti gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b55f0-117">The following example shows a hard drop shadow effect applied to text.</span></span> <span data-ttu-id="b55f0-118">Bu durumda, gölge bulanık değildir.</span><span class="sxs-lookup"><span data-stu-id="b55f0-118">In this case, the shadow is not blurred.</span></span>  
  
 <span data-ttu-id="b55f0-119">![Metin gölgesinin Yumuşaklık &#61; 0](../../../../docs/framework/wpf/advanced/media/shadowtext02.jpg "ShadowText02")</span><span class="sxs-lookup"><span data-stu-id="b55f0-119">![Text shadow with Softness &#61; 0](../../../../docs/framework/wpf/advanced/media/shadowtext02.jpg "ShadowText02")</span></span>  
<span data-ttu-id="b55f0-120">Sabit gölgeli metin örneği</span><span class="sxs-lookup"><span data-stu-id="b55f0-120">Example of text with a hard shadow</span></span>  
  
 <span data-ttu-id="b55f0-121">Sabit gölge ayarlayarak oluşturabileceğiniz <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> özelliğine `0.0`, hiçbir bulanıklık olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b55f0-121">You can create a hard shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property to `0.0`, which indicates that no blurring is used.</span></span> <span data-ttu-id="b55f0-122">Gölge yönünü değiştirerek denetleyebilirsiniz <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b55f0-122">You can control the direction of the shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property.</span></span> <span data-ttu-id="b55f0-123">Bu özelliğin yönlü değerini arasında bir dereceye ayarlayın `0` ve `360`.</span><span class="sxs-lookup"><span data-stu-id="b55f0-123">Set the directional value of this property to a degree between `0` and `360`.</span></span> <span data-ttu-id="b55f0-124">Aşağıdaki çizimde yönlü değerlerini gösterir <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> özellik ayarı.</span><span class="sxs-lookup"><span data-stu-id="b55f0-124">The following illustration shows the directional values of the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property setting.</span></span>  
  
 <span data-ttu-id="b55f0-125">![Gölgenin DropShadow derece ayarı](../../../../docs/framework/wpf/advanced/media/shadowtext08.png "ShadowText08")</span><span class="sxs-lookup"><span data-stu-id="b55f0-125">![DropShadow degree setting of shadow](../../../../docs/framework/wpf/advanced/media/shadowtext08.png "ShadowText08")</span></span>  
<span data-ttu-id="b55f0-126">DropShadow yönü diyagramı</span><span class="sxs-lookup"><span data-stu-id="b55f0-126">DropShadow Direction diagram</span></span>  
  
 <span data-ttu-id="b55f0-127">Aşağıdaki kod örneğinde sabit gölge oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b55f0-127">The following code example shows how to create a hard shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a><span data-ttu-id="b55f0-128">Bir bulanıklaştırma efekti kullanma</span><span class="sxs-lookup"><span data-stu-id="b55f0-128">Using a Blur Effect</span></span>  
 <span data-ttu-id="b55f0-129">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> metin nesnenin arkasında yerleştirilebilecek bir gölge benzeri efekti oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b55f0-129">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> can be used to create a shadow-like effect that can be placed behind a text object.</span></span> <span data-ttu-id="b55f0-130">Metne uygulanan bulanık bit eşlem Efekt metnin her yöne eşit olarak bulanıklaştırır.</span><span class="sxs-lookup"><span data-stu-id="b55f0-130">A blur bitmap effect applied to text blurs the text evenly in all directions.</span></span>  
  
 <span data-ttu-id="b55f0-131">Aşağıdaki örnek metne uygulanan bir bulanıklaştırma efekti gösterir.</span><span class="sxs-lookup"><span data-stu-id="b55f0-131">The following example shows a blur effect applied to text.</span></span>  
  
 <span data-ttu-id="b55f0-132">![Metin gölgesinin BlurBitmapEffect kullanan](../../../../docs/framework/wpf/advanced/media/shadowtext06.jpg "ShadowText06")</span><span class="sxs-lookup"><span data-stu-id="b55f0-132">![Text shadow using a BlurBitmapEffect](../../../../docs/framework/wpf/advanced/media/shadowtext06.jpg "ShadowText06")</span></span>  
<span data-ttu-id="b55f0-133">Metin Bulanıklaştırma efekti örneği</span><span class="sxs-lookup"><span data-stu-id="b55f0-133">Example of text with a blur effect</span></span>  
  
 <span data-ttu-id="b55f0-134">Aşağıdaki kod örneğinde bir bulanıklaştırma efekti oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b55f0-134">The following code example shows how to create a blur effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a><span data-ttu-id="b55f0-135">Çeviri Dönüştürme kullanma</span><span class="sxs-lookup"><span data-stu-id="b55f0-135">Using a Translate Transform</span></span>  
 <span data-ttu-id="b55f0-136">A <xref:System.Windows.Media.TranslateTransform> metin nesnenin arkasında yerleştirilebilecek bir gölge benzeri efekti oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b55f0-136">A <xref:System.Windows.Media.TranslateTransform> can be used to create a shadow-like effect that can be placed behind a text object.</span></span>  
  
 <span data-ttu-id="b55f0-137">Aşağıdaki kod örneğinde bir <xref:System.Windows.Media.TranslateTransform> metni dengelemek için.</span><span class="sxs-lookup"><span data-stu-id="b55f0-137">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="b55f0-138">Bu örnekte, bir gölge etkisi birincil metin altındaki metin biraz uzaklık bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b55f0-138">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 <span data-ttu-id="b55f0-139">![Metin gölgesinin TranslateTransform kullanan](../../../../docs/framework/wpf/advanced/media/shadowtext07.jpg "ShadowText07")</span><span class="sxs-lookup"><span data-stu-id="b55f0-139">![Text shadow using a TranslateTransform](../../../../docs/framework/wpf/advanced/media/shadowtext07.jpg "ShadowText07")</span></span>  
<span data-ttu-id="b55f0-140">Dönüştürme için gölge efekti kullanarak metin örneği</span><span class="sxs-lookup"><span data-stu-id="b55f0-140">Example of text using a transform for a shadow effect</span></span>  
  
 <span data-ttu-id="b55f0-141">Aşağıdaki kod örneğinde gölge efekti dönüşümü oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b55f0-141">The following code example shows how to create a transform for a shadow effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
