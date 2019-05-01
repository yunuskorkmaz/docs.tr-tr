---
title: 'İzlenecek yollar: Özel Animasyonlu Düğme Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- custom animated buttons [WPF]
- buttons [WPF]
- animation [WPF], buttons [WPF]
ms.assetid: e9532c72-460f-4898-9332-613fa21d746a
ms.openlocfilehash: 3c601641a0eb1024722b4f449f0ab23e54fe93dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024475"
---
# <a name="walkthroughs-create-a-custom-animated-button"></a><span data-ttu-id="73c4e-102">İzlenecek yollar: Özel Animasyonlu Düğme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="73c4e-102">Walkthroughs: Create a Custom Animated Button</span></span>
<span data-ttu-id="73c4e-103">Adından da anlaşılacağı gibi Windows Presentation Foundation (WPF) müşteriler için sunum deneyimlerini zenginleştirmek idealdir.</span><span class="sxs-lookup"><span data-stu-id="73c4e-103">As its name suggests, Windows Presentation Foundation (WPF) is great for making rich presentation experiences for customers.</span></span> <span data-ttu-id="73c4e-104">Bu izlenecek yollar (animasyonları dahil) bir düğme davranışını ve görünümünü özelleştirmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="73c4e-104">These walkthroughs show you how to customize the look and behavior of a button (including animations).</span></span> <span data-ttu-id="73c4e-105">Bu özelleştirme bitti bu özel düğme kolayca herhangi bir düğmeye uygulamanızda uygulayabilirsiniz böylece stil ve şablon kullanarak.</span><span class="sxs-lookup"><span data-stu-id="73c4e-105">This customization is done using a style and template so that you can apply this custom button easily to any buttons in your application.</span></span> <span data-ttu-id="73c4e-106">Aşağıdaki çizimde özelleştirilmiş bir düğme, oluşturacağınız gösterilir.</span><span class="sxs-lookup"><span data-stu-id="73c4e-106">The following illustration shows the customized button that you will create.</span></span>  
  
 <span data-ttu-id="73c4e-107">![Oluşturacağınız özelleştirilmiş bir düğme](./media/custom-button-blend-intro.jpg "custom_button_blend_Intro")</span><span class="sxs-lookup"><span data-stu-id="73c4e-107">![The customized button that you will create](./media/custom-button-blend-intro.jpg "custom_button_blend_Intro")</span></span>  
  
 <span data-ttu-id="73c4e-108">Düğmenin görünümünü oluşturan vektör grafik, kullanılarak oluşturulan [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="73c4e-108">The vector graphics that make up the appearance of the button are created by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <span data-ttu-id="73c4e-109">HTML için daha güçlü ve Genişletilebilir dışında benzerdir.</span><span class="sxs-lookup"><span data-stu-id="73c4e-109">is similar to HTML except it is more powerful and extensible.</span></span> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <span data-ttu-id="73c4e-110">Microsoft Visual Studio veya not defteri kullanılarak el ile yazılan veya Microsoft Expression Blend gibi bir görsel tasarım aracını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73c4e-110">can be typed in manually using Microsoft Visual Studio or Notepad, or you can use a visual design tool such as Microsoft Expression Blend.</span></span> <span data-ttu-id="73c4e-111">Expression Blend çalıştığı temel oluşturarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kodu her iki yöntem de aynı grafik oluşturur.</span><span class="sxs-lookup"><span data-stu-id="73c4e-111">Expression Blend works by creating underlying [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code, so both methods create the same graphics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="73c4e-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="73c4e-112">In This Section</span></span>  
 [<span data-ttu-id="73c4e-113">Microsoft Expression Blend Kullanarak Düğme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="73c4e-113">Create a Button by Using Microsoft Expression Blend</span></span>](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)  
 <span data-ttu-id="73c4e-114">Expression Blend tasarımcı özelliklerini kullanarak düğmeleri ile özel davranışlar oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="73c4e-114">Demonstrates how to create buttons with custom behavior by using the designer features of Expression Blend.</span></span>  
  
 [<span data-ttu-id="73c4e-115">XAML Kullanarak bir Düğme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="73c4e-115">Create a Button by Using XAML</span></span>](walkthrough-create-a-button-by-using-xaml.md)  
 <span data-ttu-id="73c4e-116">Düğmeleri kullanarak ile özel davranışlar oluşturma işlemini gösterir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="73c4e-116">Demonstrates how to create buttons with custom behavior by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and Visual Studio.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="73c4e-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="73c4e-117">Related Sections</span></span>  
 [<span data-ttu-id="73c4e-118">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="73c4e-118">Styling and Templating</span></span>](styling-and-templating.md)  
 <span data-ttu-id="73c4e-119">Nasıl stilleri ve şablonları görünümünü ve davranışını denetim belirlemek için kullanılabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="73c4e-119">Describes how styles and templates can be used to determine the appearance and behavior of controls.</span></span>  
  
 [<span data-ttu-id="73c4e-120">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="73c4e-120">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)  
 <span data-ttu-id="73c4e-121">Nasıl nesneleri kullanarak animasyonu oluşturulabilen açıklar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] animasyon ve zamanlama sistemi.</span><span class="sxs-lookup"><span data-stu-id="73c4e-121">Describes how objects can be animated by using the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] animation and timing system.</span></span>  
  
 [<span data-ttu-id="73c4e-122">Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="73c4e-122">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 <span data-ttu-id="73c4e-123">Düz renkler, doğrusal gradyanlar ve radyal gradyanlar ile Boyama fırça nesneleri kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="73c4e-123">Describes how to use brush objects to paint with solid colors, linear gradients, and radial gradients.</span></span>  
  
 [<span data-ttu-id="73c4e-124">Bit Eşlem Etkilerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="73c4e-124">Bitmap Effects Overview</span></span>](../graphics-multimedia/bitmap-effects-overview.md)  
 <span data-ttu-id="73c4e-125">Tarafından desteklenen bir bit eşlem efektleri açıklar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ve bunların nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="73c4e-125">Describes the bitmap effects supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] and explains how to apply them.</span></span>
