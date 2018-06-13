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
# <a name="how-to-override-the-logical-tree"></a>Nasıl yapılır: Mantıksal Ağacı Geçersiz Kılma
Çoğu durumda gerekli olmamasına karşın, Gelişmiş denetim yazarlarının mantıksal ağacının geçersiz kılma seçeneği vardır.  
  
## <a name="example"></a>Örnek  
 Bu örnek açıklar alt sınıf yapma <xref:System.Windows.Controls.StackPanel> paneli yalnızca olabilir ve yalnızca tek bir alt öğe kılacak bir davranış zorlamak için mantıksal ağaç, bu durumda geçersiz kılmak için. Bu mutlaka pratikte istenen bir davranış değildir, ancak burada gösterilen senaryo, bir öğenin normal mantıksal ağacının geçersiz kılma için gösteren bir yolu olarak.  
  
 [!code-csharp[LogicalOverride#SingletonPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 Mantıksal ağacının hakkında daha fazla bilgi için bkz: [WPF ağaçlarında](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).
