---
title: "Nasıl yapılır: Salt Okunur Freezable'ın Yazılabilir Kopyasını Edinme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cloning Freezable objects [WPF]
- Freezable objects [WPF], modifiable clones
ms.assetid: d028de61-bbe9-4d62-b656-8fe3b1b2ca24
ms.openlocfilehash: 894a2e42ca3f5cbb159c3129227f4b03e71fc4ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543627"
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
 [Freezable Nesnelerine Genel Bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
