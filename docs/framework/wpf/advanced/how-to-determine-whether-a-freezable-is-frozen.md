---
title: "Nasıl yapılır: Freezable'ın Dondurulmuş Olup Olmadığını Belirleme"
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
helpviewer_keywords: Freezable objects [WPF], determining if frozen
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47fb0a871c3792450386c440629ead1ee3fbecdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-whether-a-freezable-is-frozen"></a>Nasıl yapılır: Freezable'ın Dondurulmuş Olup Olmadığını Belirleme
Bu örnek nasıl belirleneceğini göstermektedir olup bir <xref:System.Windows.Freezable> nesnesinin dondurulmuş. Dondurulmuş değiştirmeye çalışırsanız, <xref:System.Windows.Freezable> nesnesi, onu oluşturur bir <xref:System.InvalidOperationException>. Bu özel durum atma önlemek için <xref:System.Windows.Freezable.IsFrozen%2A> özelliği <xref:System.Windows.Freezable> dondurulmuş olup olmadığını belirlemek için nesne.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek donuyor bir <xref:System.Windows.Media.SolidColorBrush> ve kullanılarak test <xref:System.Windows.Freezable.IsFrozen%2A> dondurulmuş olup olmadığını belirlemek için özellik.  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Freezable> nesneleri bkz [Freezable nesnelere genel bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.IsFrozen%2A>  
 [Freezable nesnelere genel bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
