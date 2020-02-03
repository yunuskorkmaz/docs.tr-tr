---
title: Denetimi bir türe bağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 94faeebb-d2bc-45d6-86d7-96a42661b43d
ms.openlocfilehash: 0bc1f92ee8922990bd0e461655168f5618ba39a6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744993"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type"></a>Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama
Verilerle etkileşime geçen denetimleri oluştururken, bazen bir denetimi bir nesne yerine bir türe bağlamayı gerekli bulacaktır. Bu durum özellikle tasarım zamanında, verilerin kullanılamadığı durumlarda ortaya çıkar, ancak veri bağlantılı denetimleriniz, bir türün ortak arabiriminden bilgi görüntülemeye hala gerek duyar. Örneğin, bir Web hizmeti tarafından kullanıma sunulan bir nesneye <xref:System.Windows.Forms.DataGridView> denetimi bağlayabilir ve <xref:System.Windows.Forms.DataGridView> denetiminin sütunlarını tasarım zamanında özel bir türün üye adlarıyla etiketlemesini sağlayabilirsiniz.  
  
 <xref:System.Windows.Forms.BindingSource> bileşeniyle bir denetimi kolayca bir türe bağlayabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, bir <xref:System.Windows.Forms.DataGridView> denetiminin bir <xref:System.Windows.Forms.BindingSource> bileşeni kullanılarak özel bir türe nasıl bağlanacağı gösterilmektedir. Örneği çalıştırdığınızda <xref:System.Windows.Forms.DataGridView>, denetimin verilerle doldurulmadan önce, bir `Customer` nesnesinin özelliklerini yansıtan sütunlar etiketli olduğunu fark edeceksiniz. Örneğin, <xref:System.Windows.Forms.DataGridView> denetimine veri eklemek için bir müşteri Ekle düğmesi vardır. Düğmeye tıkladığınızda, <xref:System.Windows.Forms.BindingSource>yeni bir `Customer` nesnesi eklenir. Gerçek dünyada bir senaryoda veriler, bir Web hizmeti veya başka bir veri kaynağı çağrısıyla elde edilebilir.  
  
 [!code-csharp[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingSource Bileşeni](bindingsource-component.md)
