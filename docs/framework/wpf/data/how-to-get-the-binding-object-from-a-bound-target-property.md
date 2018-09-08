---
title: 'Nasıl yapılır: Bağımlı Hedef Özelliğinden Bağlama Nesnesi Alma'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: 7cebaf1077fb66420d77d656db32f444dd932b85
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210873"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a>Nasıl yapılır: Bağımlı Hedef Özelliğinden Bağlama Nesnesi Alma
Bu örnek veri bağımlı hedef özelliğinden bağlama nesnesi elde etme gösterir.  
  
## <a name="example"></a>Örnek  
 Almak için aşağıdakileri yapabilirsiniz <xref:System.Windows.Data.Binding> nesnesi:  
  
 [!code-csharp[BindValidation#GetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
>  Bağımlılık özelliği için birden fazla özellik hedef nesnenin veri bağlama kullanması mümkün olduğundan, istediğiniz bağlama belirtmeniz gerekir.  
  
 Alternatif olarak, alabilirsiniz <xref:System.Windows.Data.BindingExpression> ve ardından değerini almak <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> özelliği.  
  
 Tam bir örnek için bkz. [bağlama doğrulaması örnek](https://go.microsoft.com/fwlink/?LinkID=159972).  
  
> [!NOTE]
>  Bağlamanız ise bir <xref:System.Windows.Data.MultiBinding>, kullanın <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>. Eğer öyleyse bir <xref:System.Windows.Data.PriorityBinding>, kullanın <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>. Hedef özelliği kullanarak mı bağlı emin değilseniz bir <xref:System.Windows.Data.Binding>, <xref:System.Windows.Data.MultiBinding>, veya bir <xref:System.Windows.Data.PriorityBinding>, kullanabileceğiniz <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kod İçinde Bağlama Oluşturma](../../../../docs/framework/wpf/data/how-to-create-a-binding-in-code.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
