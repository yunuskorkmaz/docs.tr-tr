---
title: 'Nasıl yapılır: Bağımlı Hedef Özelliğinden Bağlama Nesnesi Alma'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: c7aacc2145ffe98ec7b58afb3b2e3dca151ef0ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965430"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a>Nasıl yapılır: Bağımlı Hedef Özelliğinden Bağlama Nesnesi Alma
Bu örnek, bağlama nesnesinin bir veri bağlantılı hedef özelliğinden nasıl alınacağını gösterir.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Data.Binding> Nesneyi almak için aşağıdakileri yapabilirsiniz:  
  
 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
> Hedef nesnenin birden fazla özelliğinin veri bağlamayı kullanıyor olması mümkün olduğundan, istediğiniz bağlama için bağımlılık özelliğini belirtmelisiniz.  
  
 Alternatif olarak, <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> ve daha sonra özelliğin değerini alabilir. <xref:System.Windows.Data.BindingExpression>  
  
 Tüm örnek için bkz. [bağlama doğrulama örneği](https://go.microsoft.com/fwlink/?LinkID=159972).  
  
> [!NOTE]
> Bağlamanız bir <xref:System.Windows.Data.MultiBinding>ise, kullanın <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>.. Bir <xref:System.Windows.Data.PriorityBinding>ise, kullanın <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>.. <xref:System.Windows.Data.Binding>Hedef özelliğin bir<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A> <xref:System.Windows.Data.BindingOperations>,, veya a <xref:System.Windows.Data.PriorityBinding>kullanarak bağlanıp bağlanmadığından emin değilseniz, kullanabilirsiniz... <xref:System.Windows.Data.MultiBinding>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kod İçinde Bağlama Oluşturma](how-to-create-a-binding-in-code.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
