---
title: "Nasıl yapılır: Bağlamaları Temizleme"
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
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9f8e009d00960f40abcd3c3913a15fa51f1be4f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
