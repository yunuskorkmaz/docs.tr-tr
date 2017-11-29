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
# <a name="how-to-override-the-logical-tree"></a>Nasıl yapılır: Mantıksal Ağacı Geçersiz Kılma
Çoğu durumda gerekli olmamasına karşın, Gelişmiş denetim yazarlarının mantıksal ağacının geçersiz kılma seçeneği vardır.  
  
## <a name="example"></a>Örnek  
 Bu örnek açıklar alt sınıf yapma <xref:System.Windows.Controls.StackPanel> paneli yalnızca olabilir ve yalnızca tek bir alt öğe kılacak bir davranış zorlamak için mantıksal ağaç, bu durumda geçersiz kılmak için. Bu mutlaka pratikte istenen bir davranış değildir, ancak burada gösterilen senaryo, bir öğenin normal mantıksal ağacının geçersiz kılma için gösteren bir yolu olarak.  
  
 [!code-csharp[LogicalOverride#SingletonPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 Mantıksal ağacının hakkında daha fazla bilgi için bkz: [WPF ağaçlarında](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).
