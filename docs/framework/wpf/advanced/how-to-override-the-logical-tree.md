---
title: 'Nasıl yapılır: Mantıksal Ağacı Geçersiz Kılma'
ms.date: 03/30/2017
helpviewer_keywords:
- overriding the logical tree [WPF]
- logical tree [WPF], overriding
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
ms.openlocfilehash: 0c7269b9ea052019e2e4f6def23b063903cbb5e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542896"
---
# <a name="how-to-override-the-logical-tree"></a><span data-ttu-id="0be9e-102">Nasıl yapılır: Mantıksal Ağacı Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="0be9e-102">How to: Override the Logical Tree</span></span>
<span data-ttu-id="0be9e-103">Çoğu durumda gerekli olmamasına karşın, Gelişmiş denetim yazarlarının mantıksal ağacının geçersiz kılma seçeneği vardır.</span><span class="sxs-lookup"><span data-stu-id="0be9e-103">Although it is not necessary in most cases, advanced control authors have the option to override the logical tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0be9e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0be9e-104">Example</span></span>  
 <span data-ttu-id="0be9e-105">Bu örnek açıklar alt sınıf yapma <xref:System.Windows.Controls.StackPanel> paneli yalnızca olabilir ve yalnızca tek bir alt öğe kılacak bir davranış zorlamak için mantıksal ağaç, bu durumda geçersiz kılmak için.</span><span class="sxs-lookup"><span data-stu-id="0be9e-105">This example describes how to subclass <xref:System.Windows.Controls.StackPanel> to override the logical tree, in this case to enforce a behavior that the panel may only have and will only render a single child element.</span></span> <span data-ttu-id="0be9e-106">Bu mutlaka pratikte istenen bir davranış değildir, ancak burada gösterilen senaryo, bir öğenin normal mantıksal ağacının geçersiz kılma için gösteren bir yolu olarak.</span><span class="sxs-lookup"><span data-stu-id="0be9e-106">This isn't necessarily a practically desirable behavior, but is shown here as a means of illustrating the scenario for overriding an element's normal logical tree.</span></span>  
  
 [!code-csharp[LogicalOverride#SingletonPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 <span data-ttu-id="0be9e-107">Mantıksal ağacının hakkında daha fazla bilgi için bkz: [WPF ağaçlarında](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="0be9e-107">For more information on the logical tree, see [Trees in WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).</span></span>
