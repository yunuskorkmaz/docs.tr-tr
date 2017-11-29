---
title: "Nasıl yapılır: Mantıksal Ağacı Geçersiz Kılma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- overriding the logical tree [WPF]
- logical tree [WPF], overriding
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4cc6045d3505981d93f07347ebd49d57cd759774
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-override-the-logical-tree"></a><span data-ttu-id="0bd5f-102">Nasıl yapılır: Mantıksal Ağacı Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="0bd5f-102">How to: Override the Logical Tree</span></span>
<span data-ttu-id="0bd5f-103">Çoğu durumda gerekli olmamasına karşın, Gelişmiş denetim yazarlarının mantıksal ağacının geçersiz kılma seçeneği vardır.</span><span class="sxs-lookup"><span data-stu-id="0bd5f-103">Although it is not necessary in most cases, advanced control authors have the option to override the logical tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bd5f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0bd5f-104">Example</span></span>  
 <span data-ttu-id="0bd5f-105">Bu örnek açıklar alt sınıf yapma <xref:System.Windows.Controls.StackPanel> paneli yalnızca olabilir ve yalnızca tek bir alt öğe kılacak bir davranış zorlamak için mantıksal ağaç, bu durumda geçersiz kılmak için.</span><span class="sxs-lookup"><span data-stu-id="0bd5f-105">This example describes how to subclass <xref:System.Windows.Controls.StackPanel> to override the logical tree, in this case to enforce a behavior that the panel may only have and will only render a single child element.</span></span> <span data-ttu-id="0bd5f-106">Bu mutlaka pratikte istenen bir davranış değildir, ancak burada gösterilen senaryo, bir öğenin normal mantıksal ağacının geçersiz kılma için gösteren bir yolu olarak.</span><span class="sxs-lookup"><span data-stu-id="0bd5f-106">This isn't necessarily a practically desirable behavior, but is shown here as a means of illustrating the scenario for overriding an element's normal logical tree.</span></span>  
  
 [!code-csharp[LogicalOverride#SingletonPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 <span data-ttu-id="0bd5f-107">Mantıksal ağacının hakkında daha fazla bilgi için bkz: [WPF ağaçlarında](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="0bd5f-107">For more information on the logical tree, see [Trees in WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).</span></span>
