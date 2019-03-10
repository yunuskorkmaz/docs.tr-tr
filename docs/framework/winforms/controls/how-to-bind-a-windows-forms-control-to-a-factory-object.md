---
title: 'Nasıl yapılır: Bir Windows Forms denetimini bir Fabrika nesnesine bağlama'
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
ms.openlocfilehash: 57fab57896c4b122f96cea72a5af637c5f5d268a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717329"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a>Nasıl yapılır: Bir Windows Forms denetimini bir Fabrika nesnesine bağlama
Verilerle etkileşimde bulunmak denetimleri oluştururken, bazı durumlarda, bir denetim için bir nesne veya diğer nesneleri oluşturan yöntemi bağlamak gerekli bulacaksınız. Böyle bir nesne veya yöntem bir Fabrika adı verilir. Veri kaynağı, örneğin, bellek veya bir türü bir nesne yerine bir yöntem çağrısının dönüş değeri olabilir. Kaynak koleksiyonu döndürdüğü sürece bu tür bir veri kaynağı için bir denetim bağlayabilirsiniz.  
  
 Kullanarak bir denetimi bir Fabrika nesnesine kolayca bağlayabilirsiniz <xref:System.Windows.Forms.BindingSource> denetimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl bağlanacağını gösterir. bir <xref:System.Windows.Forms.DataGridView> denetlemek için bir Üreteç yöntemi kullanarak bir <xref:System.Windows.Forms.BindingSource> denetimi. Üreteç yöntemi adlı `GetOrdersByCustomerId`, Northwind veritabanında belirli bir müşteri için tüm siparişleri döndürür.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingSource Bileşeni](bindingsource-component.md)
- [Nasıl yapılır: Bir Windows Forms denetimini bir türe bağlama](how-to-bind-a-windows-forms-control-to-a-type.md)
