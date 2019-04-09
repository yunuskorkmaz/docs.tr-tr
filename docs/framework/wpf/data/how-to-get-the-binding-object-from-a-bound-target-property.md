---
title: 'Nasıl yapılır: Bağımlı Hedef Özelliğinden Bağlama Nesnesi Alma'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: 7c7392bc11af57b2e9f27e2302f36efb59d40e9d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083120"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a>Nasıl yapılır: Bağımlı Hedef Özelliğinden Bağlama Nesnesi Alma
Bu örnek veri bağımlı hedef özelliğinden bağlama nesnesi elde etme gösterir.  
  
## <a name="example"></a>Örnek  
 Almak için aşağıdakileri yapabilirsiniz <xref:System.Windows.Data.Binding> nesnesi:  
  
 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
>  Bağımlılık özelliği için birden fazla özellik hedef nesnenin veri bağlama kullanması mümkün olduğundan, istediğiniz bağlama belirtmeniz gerekir.  
  
 Alternatif olarak, alabilirsiniz <xref:System.Windows.Data.BindingExpression> ve ardından değerini almak <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> özelliği.  
  
 Tam bir örnek için bkz. [bağlama doğrulaması örnek](https://go.microsoft.com/fwlink/?LinkID=159972).  
  
> [!NOTE]
>  Bağlamanız ise bir <xref:System.Windows.Data.MultiBinding>, kullanın <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>. Eğer öyleyse bir <xref:System.Windows.Data.PriorityBinding>, kullanın <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>. Hedef özelliği kullanarak mı bağlı emin değilseniz bir <xref:System.Windows.Data.Binding>, <xref:System.Windows.Data.MultiBinding>, veya bir <xref:System.Windows.Data.PriorityBinding>, kullanabileceğiniz <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kod İçinde Bağlama Oluşturma](how-to-create-a-binding-in-code.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
