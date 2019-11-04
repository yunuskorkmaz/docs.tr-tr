---
title: "Nasıl yapılır: Freezable'ı Salt Okunur Yapma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: 4185966d864be425bc631953461f6f27ab983bee
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460075"
---
# <a name="how-to-make-a-freezable-read-only"></a>Nasıl yapılır: Freezable'ı Salt Okunur Yapma
Bu örnek, <xref:System.Windows.Freezable.Freeze%2A> metodunu çağırarak <xref:System.Windows.Freezable> salt okunurdur.  
  
 Aşağıdaki koşullardan herhangi biri nesne hakkında `true` ise <xref:System.Windows.Freezable> nesnesini donduramazsınız:  
  
- Animasyonlu veya veri bağlantılı özelliklere sahiptir.  
  
- Dinamik bir kaynak tarafından ayarlanan özelliklere sahiptir. Dinamik kaynaklar hakkında daha fazla bilgi için bkz. [xaml kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
- Dondurulamayan <xref:System.Windows.Freezable> alt nesneler içerir.  
  
 Bu koşullar <xref:System.Windows.Freezable> nesneniz için `false` ve değiştirmek istemiyorsanız, performans avantajları elde etmek için bunu dondurmayı göz önünde bulundurun.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir tür <xref:System.Windows.Freezable> nesnesi olan bir <xref:System.Windows.Media.SolidColorBrush>dondurur.  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 <xref:System.Windows.Freezable> nesneler hakkında daha fazla bilgi için bkz. [Freezable nesnelerine genel bakış](freezable-objects-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [Freezable Nesnelerine Genel Bakış](freezable-objects-overview.md)
- [Nasıl Yapılır Konuları](base-elements-how-to-topics.md)
