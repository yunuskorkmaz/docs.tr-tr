---
title: "Nasıl yapılır: Bağımlı Hedef Özelliğinden Bağlama Nesnesi Alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 498849cc0205775f88c21d90d12b45c6b71a5dec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a>Nasıl yapılır: Bağımlı Hedef Özelliğinden Bağlama Nesnesi Alma
Bu örnek binding nesnesinin veri bağlama hedef özelliğinden elde etme gösterir.  
  
## <a name="example"></a>Örnek  
 Almak için aşağıdakileri yapabilirsiniz <xref:System.Windows.Data.Binding> nesnesi:  
  
 [!code-csharp[BindValidation#GetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
>  Hedef nesnenin birden fazla özellik veri bağlamayı kullanması mümkün olduğundan, istediğiniz bağlama için bağımlılık özelliği belirtmeniz gerekir.  
  
 Alternatif olarak, alabileceğiniz <xref:System.Windows.Data.BindingExpression> ve değerini alın <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> özelliği.  
  
 Tam bir örnek için bkz: [bağlama doğrulama örnek](http://go.microsoft.com/fwlink/?LinkID=159972).  
  
> [!NOTE]
>  Bağlama ise bir <xref:System.Windows.Data.MultiBinding>, kullanın <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>. Eğer öyleyse bir <xref:System.Windows.Data.PriorityBinding>, kullanın <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>. Target özelliği kullanılarak mı bağlı emin değilseniz bir <xref:System.Windows.Data.Binding>, <xref:System.Windows.Data.MultiBinding>, veya bir <xref:System.Windows.Data.PriorityBinding>, kullanabileceğiniz <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kod içinde bir bağlaması oluşturun](../../../../docs/framework/wpf/data/how-to-create-a-binding-in-code.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
