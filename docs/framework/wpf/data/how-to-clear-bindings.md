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
ms.openlocfilehash: f66477fc857a9e7a065e01b8cddf43789042b59c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555863"
---
# <a name="how-to-clear-bindings"></a>Nasıl yapılır: Bağlamaları Temizleme
Bu örnek, bir nesneden bağlamaları temizlemek gösterilmiştir.  
  
## <a name="example"></a>Örnek  
 Bir nesne üzerinde tek bir özellikten bağlamayı temizlemek için arama <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> aşağıdaki örnekte gösterildiği gibi. Aşağıdaki örnek bağlamayı kaldırır <xref:System.Windows.Controls.TextBlock.TextProperty> , *mytext*, <xref:System.Windows.Controls.TextBlock> nesnesi.  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 Bağlama temizlenirken bağımlılık özelliğinin değeri bağlama yokken olması gereken şekilde değiştirilir. Bu değer, varsayılan değer, devralınan değerinin ya da bir veri şablonu bağlama arasında bir değer olabilir.  
  
 Bir nesne üzerinde tüm olası özelliklerinden bağlamaları temizlemek için kullanın <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Data.BindingOperations>  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
