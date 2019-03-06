---
title: 'Nasıl yapılır: Mantıksal Ağacı Geçersiz Kılma'
ms.date: 03/30/2017
helpviewer_keywords:
- overriding the logical tree [WPF]
- logical tree [WPF], overriding
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
ms.openlocfilehash: bf3459fff1a90326794d6713dd39c73596b0e960
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375235"
---
# <a name="how-to-override-the-logical-tree"></a><span data-ttu-id="8bfa1-102">Nasıl yapılır: Mantıksal Ağacı Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="8bfa1-102">How to: Override the Logical Tree</span></span>
<span data-ttu-id="8bfa1-103">Çoğu durumda gerekli olmamasına karşın, Gelişmiş denetim yazarlarının mantıksal ağacı geçersiz kılma seçeneği vardır.</span><span class="sxs-lookup"><span data-stu-id="8bfa1-103">Although it is not necessary in most cases, advanced control authors have the option to override the logical tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bfa1-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8bfa1-104">Example</span></span>  
 <span data-ttu-id="8bfa1-105">Bu örnek açıklar nasıl alt Sınıflama <xref:System.Windows.Controls.StackPanel> paneli yalnızca olabilir ve yalnızca tek bir alt öğe işleyecek bir davranışı zorlamak için mantıksal ağacı, bu durumda geçersiz kılma.</span><span class="sxs-lookup"><span data-stu-id="8bfa1-105">This example describes how to subclass <xref:System.Windows.Controls.StackPanel> to override the logical tree, in this case to enforce a behavior that the panel may only have and will only render a single child element.</span></span> <span data-ttu-id="8bfa1-106">Bu genellikle istenen bir davranış olmak zorunda değildir, ancak burada gösterilen öğenin normal mantıksal ağacı geçersiz kılma senaryoyu gösteren bir yolu olarak.</span><span class="sxs-lookup"><span data-stu-id="8bfa1-106">This isn't necessarily a practically desirable behavior, but is shown here as a means of illustrating the scenario for overriding an element's normal logical tree.</span></span>  
  
 [!code-csharp[LogicalOverride#SingletonPanel](~/samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 <span data-ttu-id="8bfa1-107">Mantıksal ağacı hakkında daha fazla bilgi için bkz. [WPF içinde ağaçlar](trees-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="8bfa1-107">For more information on the logical tree, see [Trees in WPF](trees-in-wpf.md).</span></span>
