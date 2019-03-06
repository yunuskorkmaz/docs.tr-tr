---
title: 'Nasıl yapılır: Ad Kapsamı Tanımlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- name scope [WPF], defining
- Storyboards [WPF], animating in procedural code
- animation [WPF], Storyboards [WPF], in procedural code
ms.assetid: 4f361925-6a08-40dc-8231-a61111c6b28b
ms.openlocfilehash: 6afb59550d774109c62c283905495c76b0834b3d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370377"
---
# <a name="how-to-define-a-name-scope"></a><span data-ttu-id="7625d-102">Nasıl yapılır: Ad Kapsamı Tanımlama</span><span class="sxs-lookup"><span data-stu-id="7625d-102">How to: Define a Name Scope</span></span>
<span data-ttu-id="7625d-103">İle animasyon uygulamak için <xref:System.Windows.Media.Animation.Storyboard> kodda oluşturmalısınız bir <xref:System.Windows.NameScope> ve bu ad kapsamı sahip öğeyi hedef nesnelerin adlarını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="7625d-103">To animate with <xref:System.Windows.Media.Animation.Storyboard> in code, you must create a <xref:System.Windows.NameScope> and register the target objects' names with the element that owns that name scope.</span></span> <span data-ttu-id="7625d-104">Aşağıdaki örnekte, bir <xref:System.Windows.NameScope> için oluşturulan `myMainPanel`.</span><span class="sxs-lookup"><span data-stu-id="7625d-104">In the following example, a <xref:System.Windows.NameScope> is created for `myMainPanel`.</span></span> <span data-ttu-id="7625d-105">İki düğme `button1` ve `button2`, paneli ve kayıtlı adları eklenir.</span><span class="sxs-lookup"><span data-stu-id="7625d-105">Two buttons, `button1` and `button2`, are added to the panel, and their names registered.</span></span> <span data-ttu-id="7625d-106">Birkaç animasyon ve <xref:System.Windows.Media.Animation.Storyboard> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7625d-106">Several animations and a <xref:System.Windows.Media.Animation.Storyboard> are created.</span></span> <span data-ttu-id="7625d-107">Şeridinin <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi animasyonları başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7625d-107">The storyboard's <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method is used to start the animations.</span></span>  
  
 <span data-ttu-id="7625d-108">Çünkü `button1`, `button2`, ve `myMainPanel` aynı ad kapsamı herkes, bunları herhangi biri kullanılabilir <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> animasyonları başlatmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7625d-108">Because `button1`, `button2`, and `myMainPanel` all share the same name scope, any one of them can be used with the <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method to start the animations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7625d-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="7625d-109">Example</span></span>  
 [!code-csharp[StoryboardBeginAnimation_procedural_snip#NameScopeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/CSharp/ScopeExample.cs#namescopeexample)]
 [!code-vb[StoryboardBeginAnimation_procedural_snip#NameScopeExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/visualbasic/scopeexample.vb#namescopeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="7625d-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7625d-110">See also</span></span>
- [<span data-ttu-id="7625d-111">Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="7625d-111">Animate a Property by Using a Storyboard</span></span>](how-to-animate-a-property-by-using-a-storyboard.md)
- [<span data-ttu-id="7625d-112">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="7625d-112">Animation Overview</span></span>](animation-overview.md)
