---
title: Denetimi bir fabrika nesnesine bağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], binding
- factory objects [Windows Forms], binding to
- BindingSource component [Windows Forms], binding to a factory object
- BindingSource component [Windows Forms], examples
ms.assetid: 7d59af89-ff82-41d8-a48a-f1fbae788b0d
ms.openlocfilehash: 2b4d9aca3345a0cb1e7e995f66a8982dee983ca8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745085"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a>Nasıl yapılır: Windows Forms Denetimini Bir Fabrika Nesnesine Bağlama
Verilerle etkileşime geçen denetimleri oluştururken, bazen başka nesneler üreten bir nesne veya yönteme denetim bağlamayı gerekli bulabilirsiniz. Bu tür bir nesne veya yöntem fabrika olarak adlandırılır. Veri kaynağınız, örneğin, bellek veya tür bir nesne yerine bir yöntem çağrısından dönüş değeri olabilir. Kaynak bir koleksiyon döndürdüğü sürece bu tür veri kaynağına bir denetim bağlayabilirsiniz.  
  
 <xref:System.Windows.Forms.BindingSource> denetimini kullanarak bir denetimi bir fabrika nesnesine kolayca bağlayabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir <xref:System.Windows.Forms.DataGridView> denetiminin bir <xref:System.Windows.Forms.BindingSource> denetimi kullanılarak bir fabrika yöntemine nasıl bağlanacağını gösterir. Fabrika yöntemine `GetOrdersByCustomerId`adı verilir ve Northwind veritabanındaki belirli bir müşteri için tüm siparişler döndürülür.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System, System. Data, System. Drawing ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingSource Bileşeni](bindingsource-component.md)
- [Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama](how-to-bind-a-windows-forms-control-to-a-type.md)
