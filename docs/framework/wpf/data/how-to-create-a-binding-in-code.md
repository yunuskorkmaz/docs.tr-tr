---
title: "Nasıl yapılır: Kod İçinde Bağlama Oluşturma"
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
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d2ad9f855f1051ad6c0afac6bc813eecf87f7d36
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-binding-in-code"></a>Nasıl yapılır: Kod İçinde Bağlama Oluşturma
Bu örnek oluşturmak ve ayarlamak nasıl gösterir bir <xref:System.Windows.Data.Binding> kod.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.FrameworkElement> Sınıfı ve <xref:System.Windows.FrameworkContentElement> her ikisini kullanıma sınıfı bir `SetBinding` yöntemi. Bu sınıfların ya da devralan bir öğeyi bağlıyorsanız çağırabilirsiniz <xref:System.Windows.FrameworkElement.SetBinding%2A> doğrudan yöntemi.  
  
 Aşağıdaki örnek, adlandırılmış bir sınıf oluşturur `MyData`, adında bir özellik içeren `MyDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#DataObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 Aşağıdaki örnek, bağlama kaynağı ayarlamak için bir bağlama nesnesinin nasıl oluşturulacağını gösterir.  Örnek kullanır <xref:System.Windows.FrameworkElement.SetBinding%2A> bağlamak için <xref:System.Windows.Controls.TextBlock.Text%2A> özelliği `myText`, olduğu bir <xref:System.Windows.Controls.TextBlock> denetlemek, çok `MyDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Tam kod örneği için bkz: [yalnızca kod bağlama örnek](http://msdn.microsoft.com/library/764aaf0b-2216-4941-9548-9c98da18d1a6).  
  
 Çağırmak yerine <xref:System.Windows.FrameworkElement.SetBinding%2A>, kullanabileceğiniz <xref:System.Windows.Data.BindingOperations.SetBinding%2A> statik yöntemi <xref:System.Windows.Data.BindingOperations> sınıfı. Aşağıdaki örnek, çağrıları <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> yerine <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> bağlamak için `myText` için `myDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
