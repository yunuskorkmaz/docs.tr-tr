---
title: 'Nasıl yapılır: Kod İçinde Bağlama Oluşturma'
description: Doğrudan SetBinding metodunu çağırarak Windows Presentation Foundation uygulamasında kodda bağlama oluşturmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: aa2a29f4c1262d8ac54641b856c297b284b23a38
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165810"
---
# <a name="how-to-create-a-binding-in-code"></a>Nasıl yapılır: Kod İçinde Bağlama Oluşturma
Bu örnek, bir kod içinde oluşturma ve ayarlama işlemlerinin nasıl yapılacağını gösterir <xref:System.Windows.Data.Binding> .  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.FrameworkElement>Sınıfı ve <xref:System.Windows.FrameworkContentElement> sınıfı her ikisi de bir yöntemi kullanıma sunar `SetBinding` . Bu sınıflardan birini devralan bir öğe bağlıyorsanız, <xref:System.Windows.FrameworkElement.SetBinding%2A> yöntemi doğrudan çağırabilirsiniz.  
  
 Aşağıdaki örnek adında bir özelliği içeren adlı bir sınıf oluşturur `MyData` `MyDataProperty` .  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 Aşağıdaki örnek, bağlamanın kaynağını ayarlamak için bağlama nesnesinin nasıl oluşturulacağını gösterir.  Örneği, <xref:System.Windows.FrameworkElement.SetBinding%2A> <xref:System.Windows.Controls.TextBlock.Text%2A> `myText` ' a bir denetim olan özelliğini bağlamak için kullanır <xref:System.Windows.Controls.TextBlock> `MyDataProperty` .  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Tam kod örneği için bkz. [yalnızca kod bağlama örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).  
  
 Çağırmak yerine <xref:System.Windows.FrameworkElement.SetBinding%2A> , <xref:System.Windows.Data.BindingOperations.SetBinding%2A> sınıfının statik yöntemini kullanabilirsiniz <xref:System.Windows.Data.BindingOperations> . Aşağıdaki örnek, <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> bağlamak için yerine çağırır <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> `myText` `myDataProperty` .  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
