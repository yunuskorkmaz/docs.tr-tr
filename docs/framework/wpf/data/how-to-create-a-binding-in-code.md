---
title: 'Nasıl yapılır: Kod İçinde Bağlama Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: 616487a16ebbe6e23fe067fb7ce72644aa3f919f
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458849"
---
# <a name="how-to-create-a-binding-in-code"></a>Nasıl yapılır: Kod İçinde Bağlama Oluşturma
Bu örnek, kodda <xref:System.Windows.Data.Binding> oluşturma ve ayarlama işlemlerinin nasıl yapılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.FrameworkElement> sınıfı ve <xref:System.Windows.FrameworkContentElement> sınıfı her ikisi de bir `SetBinding` yöntemi sunar. Bu sınıflardan birini devralan bir öğe bağlıyorsanız, <xref:System.Windows.FrameworkElement.SetBinding%2A> yöntemini doğrudan çağırabilirsiniz.  
  
 Aşağıdaki örnek, `MyDataProperty`adlı bir özelliği içeren `MyData`adlı bir sınıf oluşturur.  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 Aşağıdaki örnek, bağlamanın kaynağını ayarlamak için bağlama nesnesinin nasıl oluşturulacağını gösterir.  Örnek, `MyDataProperty`için <xref:System.Windows.Controls.TextBlock> denetimi olan `myText`<xref:System.Windows.Controls.TextBlock.Text%2A> özelliğini bağlamak için <xref:System.Windows.FrameworkElement.SetBinding%2A> kullanır.  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Tam kod örneği için bkz. [yalnızca kod bağlama örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).  
  
 <xref:System.Windows.FrameworkElement.SetBinding%2A>çağırmak yerine <xref:System.Windows.Data.BindingOperations> sınıfının <xref:System.Windows.Data.BindingOperations.SetBinding%2A> static yöntemini kullanabilirsiniz. Aşağıdaki örnek, `myText` `myDataProperty`bağlamak için <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> yerine <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> çağırır.  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
