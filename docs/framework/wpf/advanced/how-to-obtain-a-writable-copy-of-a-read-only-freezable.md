---
title: "Nasıl yapılır: Salt Okunur Freezable'ın Yazılabilir Kopyasını Edinme"
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
- cloning Freezable objects [WPF]
- Freezable objects [WPF], modifiable clones
ms.assetid: d028de61-bbe9-4d62-b656-8fe3b1b2ca24
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6925e9322063d68d0d7f8c8e048eed254cd14ed7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-a-writable-copy-of-a-read-only-freezable"></a>Nasıl yapılır: Salt Okunur Freezable'ın Yazılabilir Kopyasını Edinme
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Freezable.Clone%2A> salt okunur yazılabilir bir kopyasını oluşturmak için yöntemi <xref:System.Windows.Freezable>.  
  
 Sonra bir <xref:System.Windows.Freezable> nesne işaretlenmiş salt okunur ("dondurulmuş"), onu değiştiremezsiniz. Ancak, kullanabileceğiniz <xref:System.Windows.Freezable.Clone%2A> dondurulmuş nesne değiştirilebilir bir kopyasını oluşturmak için yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dondurulmuş değiştirilebilir kopyasını oluşturur <xref:System.Windows.Media.SolidColorBrush> nesnesi.  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Freezable> nesneleri bkz [Freezable nesnelere genel bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.CloneCurrentValue%2A>  
 [Freezable nesnelere genel bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
