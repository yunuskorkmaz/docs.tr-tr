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
ms.openlocfilehash: 2d13650cb3e9a4e97a6642992b7211f323b9ea96
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502264"
---
# <a name="how-to-create-a-binding-in-code"></a>Nasıl yapılır: Kod İçinde Bağlama Oluşturma
Bu örnekte, oluşturma ve ayarlama işlemi gösterilmektedir bir <xref:System.Windows.Data.Binding> kod.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.FrameworkElement> Sınıfı ve <xref:System.Windows.FrameworkContentElement> hem de kullanıma sınıfı bir `SetBinding` yöntemi. Bu sınıfların ya da devralan bir öğe bağlanıyorsanız, çağırabilirsiniz <xref:System.Windows.FrameworkElement.SetBinding%2A> doğrudan yöntemi.  
  
 Aşağıdaki örnekte adlı bir sınıf oluşturur `MyData`, adlı bir özellik içeren `MyDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#DataObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 Aşağıdaki örnek, bağlama kaynağı ayarlamak için bir bağlama nesnesi oluşturma işlemi gösterilmektedir.  Örnekte <xref:System.Windows.FrameworkElement.SetBinding%2A> bağlamak için <xref:System.Windows.Controls.TextBlock.Text%2A> özelliği `myText`, olduğu bir <xref:System.Windows.Controls.TextBlock> çok denetimi `MyDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Tam kod örneği için bkz. [yalnızca kod bağlama örnek](https://msdn.microsoft.com/library/764aaf0b-2216-4941-9548-9c98da18d1a6).  
  
 Çağırmak yerine <xref:System.Windows.FrameworkElement.SetBinding%2A>, kullanabileceğiniz <xref:System.Windows.Data.BindingOperations.SetBinding%2A> statik yöntemi <xref:System.Windows.Data.BindingOperations> sınıfı. Aşağıdaki örnek, çağrıları <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> yerine <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> bağlamak için `myText` için `myDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
