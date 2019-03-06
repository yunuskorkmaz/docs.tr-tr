---
title: "Nasıl yapılır: Freezable'ı Salt Okunur Yapma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: 874724584b44c17ff6c01331295cfa1a60978d54
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360361"
---
# <a name="how-to-make-a-freezable-read-only"></a>Nasıl yapılır: Freezable'ı Salt Okunur Yapma
Bu örnek nasıl yapılacağını gösteren bir <xref:System.Windows.Freezable> salt okunur çağırarak kendi <xref:System.Windows.Freezable.Freeze%2A> yöntemi.  
  
 Freeze edilemez bir <xref:System.Windows.Freezable> aşağıdaki koşullardan herhangi biri doğru ise, nesne `true` nesneyle ilgili:  
  
-   Animasyonlu veya veri ilişkili özellikleri.  
  
-   Dinamik bir kaynak tarafından ayarlanan özellikler var. Dinamik kaynaklar hakkında daha fazla bilgi için bkz. [XAML kaynakları](xaml-resources.md).  
  
-   İçerdiği <xref:System.Windows.Freezable> nelze zmrazit alt nesneler.  
  
 Bu koşullar varsa `false` için <xref:System.Windows.Freezable> nesne ve düşünmüyorsanız onu değiştirmek için performans avantajı için dondurmayı göz önünde bulundurun.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek donuyor bir <xref:System.Windows.Media.SolidColorBrush>, bir tür olduğu <xref:System.Windows.Freezable> nesne.  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Freezable> nesneleri bkz [Freezable nesnelerine genel bakış](freezable-objects-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [Freezable Nesnelerine Genel Bakış](freezable-objects-overview.md)
- [Nasıl Yapılır Konuları](base-elements-how-to-topics.md)
