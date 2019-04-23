---
title: 'Nasıl yapılır: Bağlamaları Temizleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
ms.openlocfilehash: 8140928d44555e399ddf4ebd73407a251ad3cffe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101425"
---
# <a name="how-to-clear-bindings"></a>Nasıl yapılır: Bağlamaları Temizleme
Bu örnek, bir nesneden bağlamaları temizlemek gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Bir nesne üzerinde tek bir özellikten bağlamayı temizlemek için arama <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> aşağıdaki örnekte gösterildiği gibi. Aşağıdaki örnek bağlamayı kaldırır <xref:System.Windows.Controls.TextBlock.TextProperty> , *Metnim*, <xref:System.Windows.Controls.TextBlock> nesne.  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 Bağlama temizlenirken bağımlılık özelliğinin değeri, bağlama olmadan olması gereken şekilde değiştirilir. Bu değer, varsayılan değer, devralınan bir değer veya bir veri şablon bağlamayı arasında bir değer olabilir.  
  
 Bir nesne üzerinde olası tüm özelliklerinden bağlamaları temizlemek için kullanın <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.BindingOperations>
- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
