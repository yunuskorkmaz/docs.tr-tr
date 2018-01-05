---
title: "Nasıl yapılır: Ad Kapsamı Tanımlama"
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
- name scope [WPF], defining
- Storyboards [WPF], animating in procedural code
- animation [WPF], Storyboards [WPF], in procedural code
ms.assetid: 4f361925-6a08-40dc-8231-a61111c6b28b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3007088f849f40e4e9b4f1846c19c98c33e95c17
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-name-scope"></a><span data-ttu-id="7cdde-102">Nasıl yapılır: Ad Kapsamı Tanımlama</span><span class="sxs-lookup"><span data-stu-id="7cdde-102">How to: Define a Name Scope</span></span>
<span data-ttu-id="7cdde-103">İle animasyon eklemek için <xref:System.Windows.Media.Animation.Storyboard> kodda, oluşturmalısınız bir <xref:System.Windows.NameScope> ve bu adı kapsama sahip olan öğeye hedef nesnelerin adlarını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="7cdde-103">To animate with <xref:System.Windows.Media.Animation.Storyboard> in code, you must create a <xref:System.Windows.NameScope> and register the target objects' names with the element that owns that name scope.</span></span> <span data-ttu-id="7cdde-104">Aşağıdaki örnekte, bir <xref:System.Windows.NameScope> için oluşturulan `myMainPanel`.</span><span class="sxs-lookup"><span data-stu-id="7cdde-104">In the following example, a <xref:System.Windows.NameScope> is created for `myMainPanel`.</span></span> <span data-ttu-id="7cdde-105">İki düğme `button1` ve `button2`, bölmenin ve kayıtlı adları eklenir.</span><span class="sxs-lookup"><span data-stu-id="7cdde-105">Two buttons, `button1` and `button2`, are added to the panel, and their names registered.</span></span> <span data-ttu-id="7cdde-106">Birkaç animasyon ve <xref:System.Windows.Media.Animation.Storyboard> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7cdde-106">Several animations and a <xref:System.Windows.Media.Animation.Storyboard> are created.</span></span> <span data-ttu-id="7cdde-107">Film şeridi 's <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi animasyonları başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7cdde-107">The storyboard's <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method is used to start the animations.</span></span>  
  
 <span data-ttu-id="7cdde-108">Çünkü `button1`, `button2`, ve `myMainPanel` tümü aynı ad kapsamını paylaştığından, bunları herhangi biri ile birlikte kullanılabilir <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> animasyonları başlatmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="7cdde-108">Because `button1`, `button2`, and `myMainPanel` all share the same name scope, any one of them can be used with the <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method to start the animations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cdde-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="7cdde-109">Example</span></span>  
 [!code-csharp[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/CSharp/ScopeExample.cs#namescopeexample)]
 [!code-vb[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/visualbasic/scopeexample.vb#namescopeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="7cdde-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7cdde-110">See Also</span></span>  
 [<span data-ttu-id="7cdde-111">Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="7cdde-111">Animate a Property by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [<span data-ttu-id="7cdde-112">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="7cdde-112">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
