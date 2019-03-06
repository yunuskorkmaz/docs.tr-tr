---
title: "Nasıl yapılır: Freezable'ın Dondurulmuş Olup Olmadığını Belirleme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], determining if frozen
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
ms.openlocfilehash: 005bb27803830a2e38a7b143d2c4cff669ad1da6
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362519"
---
# <a name="how-to-determine-whether-a-freezable-is-frozen"></a>Nasıl yapılır: Freezable'ın Dondurulmuş Olup Olmadığını Belirleme
Bu örnek nasıl belirleneceğini göstermektedir olup olmadığını bir <xref:System.Windows.Freezable> nesne donuktur. Dondurulmuş değiştirmeye çalışırsanız <xref:System.Windows.Freezable> nesnesi atar bir <xref:System.InvalidOperationException>. Bu özel durum önlemek için <xref:System.Windows.Freezable.IsFrozen%2A> özelliği <xref:System.Windows.Freezable> dondurulmuş olup olmadığını belirlemek için nesne.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek donuyor bir <xref:System.Windows.Media.SolidColorBrush> ve kullanılarak test <xref:System.Windows.Freezable.IsFrozen%2A> dondurulmuş olup olmadığını belirlemek için özellik.  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Freezable> nesneleri bkz [Freezable nesnelerine genel bakış](freezable-objects-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.IsFrozen%2A>
- [Freezable Nesnelerine Genel Bakış](freezable-objects-overview.md)
- [Nasıl Yapılır Konuları](base-elements-how-to-topics.md)
