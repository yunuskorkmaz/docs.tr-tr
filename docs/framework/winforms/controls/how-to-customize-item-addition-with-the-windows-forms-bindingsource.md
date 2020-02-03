---
title: BindingSource bileşeni ile öğe eklemeyi özelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], creating new items
- BindingSource component [Windows Forms], customizing item addition with
- examples [Windows Forms], BindingSource component
- BindingSource component [Windows Forms], examples
ms.assetid: 1aae11fc-6fb2-4cb9-b3d0-e0638fe77ef0
ms.openlocfilehash: 7d74fe6b4bbb1ddb94b359f5ba3ae32ed398d1dd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738323"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a>Nasıl yapılır: Windows Forms BindingSource ile Öğe Eklemeyi Özelleştirme
Bir Windows Forms denetimini bir veri kaynağına bağlamak için bir <xref:System.Windows.Forms.BindingSource> bileşeni kullandığınızda, yeni öğelerin oluşturulmasını özelleştirmek için gerekli olduğunu fark edebilirsiniz. <xref:System.Windows.Forms.BindingSource> bileşeni, genellikle, bağlantılı denetimin yeni bir öğe oluşturması gerektiğinde ortaya çıkarılan <xref:System.Windows.Forms.BindingSource.AddingNew> olayını sağlayarak bu işlemi doğrudan hale getirir. Olay işleyiciniz hangi özel davranışın gerekli olduğunu (örneğin, bir Web hizmetinde bir yöntemi çağırmak veya bir sınıf fabrikasından yeni bir nesne almak) sağlayabilir.  
  
> [!NOTE]
> <xref:System.Windows.Forms.BindingSource.AddingNew> olayı işlenerek bir öğe eklendiğinde ekleme işlemi iptal edilemez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir <xref:System.Windows.Forms.DataGridView> denetimini bir <xref:System.Windows.Forms.BindingSource> bileşeni kullanarak bir sınıf fabrikasına nasıl bağlayabileceğinizi gösterir. Kullanıcı <xref:System.Windows.Forms.DataGridView> denetiminin yeni satırına tıkladığında <xref:System.Windows.Forms.BindingSource.AddingNew> olay tetiklenir. Olay işleyicisi, <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> özelliğine atanan yeni bir `DemoCustomer` nesnesi oluşturur. Bu, yeni `DemoCustomer` nesnesinin <xref:System.Windows.Forms.BindingSource> bileşenin listesine eklenmesine ve <xref:System.Windows.Forms.DataGridView> denetiminin yeni satırında görüntülenmesine neden olur.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System, System. Data, System. Drawing ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingSource Bileşeni](bindingsource-component.md)
- [Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama](how-to-bind-a-windows-forms-control-to-a-type.md)
