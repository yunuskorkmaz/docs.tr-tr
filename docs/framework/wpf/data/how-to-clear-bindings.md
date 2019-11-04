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
ms.openlocfilehash: 66f7eb0209d23660b9c7351ca793f509b2f4bb8d
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458871"
---
# <a name="how-to-clear-bindings"></a>Nasıl yapılır: Bağlamaları Temizleme
Bu örnek, bir nesneden bağlamaların nasıl temizyükleneceğini gösterir.  
  
## <a name="example"></a>Örnek  
 Bir nesne üzerindeki tek bir özellikten bağlamayı temizlemek için aşağıdaki örnekte gösterildiği gibi <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> çağırın. Aşağıdaki örnek, bir <xref:System.Windows.Controls.TextBlock> nesnesi olan *myText*<xref:System.Windows.Controls.TextBlock.TextProperty> bağlamayı kaldırır.  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 Bağlamayı Temizleme, bağımlılık özelliğinin değeri bağlama olmadan olacak şekilde değiştirildikten şekilde bağlamayı kaldırır. Bu değer bir varsayılan değer, devralınan bir değer veya bir veri şablonu bağlamasındaki bir değer olabilir.  
  
 Bir nesnedeki tüm olası özelliklerden bağlamaları temizlemek için <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.BindingOperations>
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
