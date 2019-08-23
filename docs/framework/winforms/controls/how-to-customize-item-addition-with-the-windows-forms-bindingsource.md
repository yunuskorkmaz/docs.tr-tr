---
title: 'Nasıl yapılır: Windows Forms BindingSource ile Öğe Eklemeyi Özelleştirme'
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
ms.openlocfilehash: 59522791408eb9c8cabf97a62be2049aeb17f864
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935357"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a>Nasıl yapılır: Windows Forms BindingSource ile Öğe Eklemeyi Özelleştirme
Bir Windows Forms denetimini bir <xref:System.Windows.Forms.BindingSource> veri kaynağına bağlamak için bir bileşeni kullandığınızda, yeni öğelerin oluşturulmasını özelleştirmek için gerekli olduğunu fark edebilirsiniz. Bileşen bunu, genellikle, bağlantılı denetimin yeni <xref:System.Windows.Forms.BindingSource.AddingNew> bir öğe oluşturması gerektiğinde ortaya çıkarılan olayını sağlayarak basittir. <xref:System.Windows.Forms.BindingSource> Olay işleyiciniz hangi özel davranışın gerekli olduğunu (örneğin, bir Web hizmetinde bir yöntemi çağırmak veya bir sınıf fabrikasından yeni bir nesne almak) sağlayabilir.  
  
> [!NOTE]
> <xref:System.Windows.Forms.BindingSource.AddingNew> Olay işlenerek bir öğe eklendiğinde ekleme işlemi iptal edilemez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.BindingSource> bileşeni kullanarak bir denetimin bir sınıf fabrikasına nasıl bağlanacağını göstermektedir. Kullanıcı <xref:System.Windows.Forms.DataGridView> denetimin yeni satırına <xref:System.Windows.Forms.BindingSource.AddingNew> tıkladığında olay tetiklenir. Olay işleyicisi, <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> özelliğine atanan yeni `DemoCustomer` bir nesne oluşturur. Bu, yeni `DemoCustomer` nesnenin <xref:System.Windows.Forms.BindingSource> bileşenin listesine eklenmesine ve <xref:System.Windows.Forms.DataGridView> denetimin yeni satırında görüntülenmesine neden olur.  
  
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
- [Nasıl yapılır: Windows Forms denetimini bir türe bağlama](how-to-bind-a-windows-forms-control-to-a-type.md)
