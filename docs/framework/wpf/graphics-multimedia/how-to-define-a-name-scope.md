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
# <a name="how-to-define-a-name-scope"></a>Nasıl yapılır: Ad Kapsamı Tanımlama
İle animasyon uygulamak için <xref:System.Windows.Media.Animation.Storyboard> kodda oluşturmalısınız bir <xref:System.Windows.NameScope> ve bu ad kapsamı sahip öğeyi hedef nesnelerin adlarını kaydedin. Aşağıdaki örnekte, bir <xref:System.Windows.NameScope> için oluşturulan `myMainPanel`. İki düğme `button1` ve `button2`, paneli ve kayıtlı adları eklenir. Birkaç animasyon ve <xref:System.Windows.Media.Animation.Storyboard> oluşturulur. Şeridinin <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi animasyonları başlatmak için kullanılır.  
  
 Çünkü `button1`, `button2`, ve `myMainPanel` aynı ad kapsamı herkes, bunları herhangi biri kullanılabilir <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> animasyonları başlatmak için yöntemi.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[StoryboardBeginAnimation_procedural_snip#NameScopeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/CSharp/ScopeExample.cs#namescopeexample)]
 [!code-vb[StoryboardBeginAnimation_procedural_snip#NameScopeExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/visualbasic/scopeexample.vb#namescopeexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme](how-to-animate-a-property-by-using-a-storyboard.md)
- [Animasyona Genel bakış](animation-overview.md)
