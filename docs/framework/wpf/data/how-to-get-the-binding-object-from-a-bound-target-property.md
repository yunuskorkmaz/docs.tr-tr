---
title: 'Nasıl yapılır: Bağımlı Hedef Özelliğinden Bağlama Nesnesi Alma'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: c528515124898c7deb6114e620ce21766123ab3c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453058"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a>Nasıl yapılır: Bağımlı Hedef Özelliğinden Bağlama Nesnesi Alma
Bu örnek, bağlama nesnesinin bir veri bağlantılı hedef özelliğinden nasıl alınacağını gösterir.

## <a name="example"></a>Örnek
 <xref:System.Windows.Data.Binding> nesnesini almak için aşağıdakileri yapabilirsiniz:

 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]

> [!NOTE]
> Hedef nesnenin birden fazla özelliğinin veri bağlamayı kullanıyor olması mümkün olduğundan, istediğiniz bağlama için bağımlılık özelliğini belirtmelisiniz.

 Alternatif olarak, <xref:System.Windows.Data.BindingExpression> alabilir ve sonra <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> özelliğinin değerini alabilirsiniz.

 Tüm örnek için bkz. [bağlama doğrulama örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).

> [!NOTE]
> Bağlamanız bir <xref:System.Windows.Data.MultiBinding>ise, <xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A?displayProperty=nameWithType>kullanın. <xref:System.Windows.Data.PriorityBinding>, <xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A?displayProperty=nameWithType>kullanın. Hedef özelliğin <xref:System.Windows.Data.Binding>, bir <xref:System.Windows.Data.MultiBinding>veya <xref:System.Windows.Data.PriorityBinding>kullanarak bağlanıp bağlanmadığından emin değilseniz, <xref:System.Windows.Data.BindingOperations.GetBindingBase%2A?displayProperty=nameWithType>kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod İçinde Bağlama Oluşturma](how-to-create-a-binding-in-code.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
