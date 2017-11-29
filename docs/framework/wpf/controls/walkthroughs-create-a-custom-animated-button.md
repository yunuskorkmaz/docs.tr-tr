---
title: "İzlenecek yollar: Özel Animasyonlu Düğme Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom animated buttons [WPF]
- buttons [WPF]
- animation [WPF], buttons [WPF]
ms.assetid: e9532c72-460f-4898-9332-613fa21d746a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bce1140ed11332b5bf30d487b2acacc644687d26
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="walkthroughs-create-a-custom-animated-button"></a><span data-ttu-id="4fe28-102">İzlenecek yollar: Özel Animasyonlu Düğme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4fe28-102">Walkthroughs: Create a Custom Animated Button</span></span>
<span data-ttu-id="4fe28-103">Adından da anlaşılacağı gibi [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] müşteriler için sunum deneyimlerini zenginleştirmek mükemmeldir.</span><span class="sxs-lookup"><span data-stu-id="4fe28-103">As its name suggests, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] is great for making rich presentation experiences for customers.</span></span> <span data-ttu-id="4fe28-104">Bu izlenecek yollar, Görünüm ve davranış (animasyon dahil) düğmesinin nasıl özelleştirileceği gösterir.</span><span class="sxs-lookup"><span data-stu-id="4fe28-104">These walkthroughs show you how to customize the look and behavior of a button (including animations).</span></span> <span data-ttu-id="4fe28-105">Bu özelleştirme yapılır, bu özel düğmeyi kolayca herhangi bir düğmeye uygulamanızda uygulayabileceğiniz bir stil ve şablon kullanarak.</span><span class="sxs-lookup"><span data-stu-id="4fe28-105">This customization is done using a style and template so that you can apply this custom button easily to any buttons in your application.</span></span> <span data-ttu-id="4fe28-106">Aşağıdaki çizimde, oluşturacağınız özelleştirilmiş düğmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4fe28-106">The following illustration shows the customized button that you will create.</span></span>  
  
 <span data-ttu-id="4fe28-107">![Oluşturacağınız özelleştirilmiş düğme](../../../../docs/framework/wpf/controls/media/custom-button-blend-intro.jpg "custom_button_blend_Intro")</span><span class="sxs-lookup"><span data-stu-id="4fe28-107">![The customized button that you will create](../../../../docs/framework/wpf/controls/media/custom-button-blend-intro.jpg "custom_button_blend_Intro")</span></span>  
  
 <span data-ttu-id="4fe28-108">Düğmenin görünümünü oluşturan vektör grafikleri kullanılarak oluşturulan [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4fe28-108">The vector graphics that make up the appearance of the button are created by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]<span data-ttu-id="4fe28-109">HTML olarak daha güçlü ve genişletilebilir olması dışında benzerdir.</span><span class="sxs-lookup"><span data-stu-id="4fe28-109"> is similar to HTML except it is more powerful and extensible.</span></span> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]<span data-ttu-id="4fe28-110">Microsoft Visual Studio veya Notepad kullanılarak el ile yazılabilir veya Microsoft Expression Blend gibi bir görsel tasarım aracını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fe28-110"> can be typed in manually using Microsoft Visual Studio or Notepad, or you can use a visual design tool such as Microsoft Expression Blend.</span></span> <span data-ttu-id="4fe28-111">Expression Blend çalışır temel oluşturarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kod yöntemlerin her ikisi de aynı grafikleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4fe28-111">Expression Blend works by creating underlying [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code, so both methods create the same graphics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4fe28-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4fe28-112">In This Section</span></span>  
 [<span data-ttu-id="4fe28-113">Microsoft Expression Blend kullanarak bir düğme oluşturma</span><span class="sxs-lookup"><span data-stu-id="4fe28-113">Create a Button by Using Microsoft Expression Blend</span></span>](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)  
 <span data-ttu-id="4fe28-114">Expression Blend tasarımcı özelliklerini kullanarak özel davranışa düğmeler oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4fe28-114">Demonstrates how to create buttons with custom behavior by using the designer features of Expression Blend.</span></span>  
  
 [<span data-ttu-id="4fe28-115">XAML kullanarak bir düğme oluşturma</span><span class="sxs-lookup"><span data-stu-id="4fe28-115">Create a Button by Using XAML</span></span>](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-xaml.md)  
 <span data-ttu-id="4fe28-116">Düğmeleri özel davranışlar ile kullanarak nasıl oluşturulacağını gösterir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4fe28-116">Demonstrates how to create buttons with custom behavior by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4fe28-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="4fe28-117">Related Sections</span></span>  
 [<span data-ttu-id="4fe28-118">Stil ve şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="4fe28-118">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 <span data-ttu-id="4fe28-119">Nasıl stilleri ve şablonları görünümünü ve davranışını denetim belirlemek için kullanılabilir açıklar.</span><span class="sxs-lookup"><span data-stu-id="4fe28-119">Describes how styles and templates can be used to determine the appearance and behavior of controls.</span></span>  
  
 [<span data-ttu-id="4fe28-120">Animasyon genel bakış</span><span class="sxs-lookup"><span data-stu-id="4fe28-120">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 <span data-ttu-id="4fe28-121">Nasıl nesneleri kullanarak animasyon uygulanabilir açıklar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] animasyon ve zamanlama sistemi.</span><span class="sxs-lookup"><span data-stu-id="4fe28-121">Describes how objects can be animated by using the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] animation and timing system.</span></span>  
  
 [<span data-ttu-id="4fe28-122">Boyama düz renklerle ve gradyan genel bakış</span><span class="sxs-lookup"><span data-stu-id="4fe28-122">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 <span data-ttu-id="4fe28-123">Düz renk, doğrusal gradyanlar ve radyal gradyanlar ile boyamak için fırça nesnelerin kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="4fe28-123">Describes how to use brush objects to paint with solid colors, linear gradients, and radial gradients.</span></span>  
  
 [<span data-ttu-id="4fe28-124">Bit eşlem efektleri genel bakış</span><span class="sxs-lookup"><span data-stu-id="4fe28-124">Bitmap Effects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)  
 <span data-ttu-id="4fe28-125">Tarafından desteklenen bit eşlem efektleri açıklar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ve bunların nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4fe28-125">Describes the bitmap effects supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] and explains how to apply them.</span></span>
