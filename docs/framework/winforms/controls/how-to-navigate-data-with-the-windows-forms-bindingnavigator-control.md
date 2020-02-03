---
title: BindingNavigator denetimi ile verilerde gezinme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
ms.openlocfilehash: 10508cb447e70cc387f9d98effa3bc4b5ccbbaa9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736004"
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a>Nasıl yapılır: Windows Forms BindingNavigator Denetimi ile Verilerde Gezinme
Windows Forms ' deki <xref:System.Windows.Forms.BindingNavigator> denetiminin, geliştiricilerin oluşturdukları formlara basit bir veri gezintisi ve düzenleme kullanıcı arabirimi sağlamasına olanak sağlar.  
  
 <xref:System.Windows.Forms.BindingNavigator> denetimi, bir veri kümesindeki ilk, son, sonraki ve önceki kayda gezinti için önceden yapılandırılmış düğmelerin yanı sıra kayıt ekleme ve silme düğmelerine sahip bir <xref:System.Windows.Forms.ToolStrip> denetimidir. <xref:System.Windows.Forms.BindingNavigator> denetimine düğme eklemek kolaydır çünkü <xref:System.Windows.Forms.ToolStrip> bir denetim. Örnekler için bkz. [nasıl yapılır: Windows Forms BindingNavigator denetimine yükleme, kaydetme ve Iptal düğmeleri ekleme](load-save-and-cancel-bindingnavigator.md).  
  
 <xref:System.Windows.Forms.BindingNavigator> denetimindeki her düğme için, aynı işlevselliğe programlı olarak izin veren <xref:System.Windows.Forms.BindingSource> bileşeninin karşılık gelen bir üyesi vardır. Örneğin, <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> düğmesi <xref:System.Windows.Forms.BindingSource> bileşenin <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> yöntemine karşılık gelir, <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> düğmesi <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> yöntemine karşılık gelir ve bu şekilde devam eder. Sonuç olarak, veri kayıtlarında gezinmek için <xref:System.Windows.Forms.BindingNavigator> denetiminin etkinleştirilmesi, <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> özelliğini formdaki uygun <xref:System.Windows.Forms.BindingSource> bileşeni olarak ayarlamak kadar basittir.  
  
### <a name="to-set-up-the-bindingnavigator-control"></a>BindingNavigator denetimini ayarlamak için  
  
1. `bindingSource1` adlı ve `textBox1` ve `textBox2`adlı iki <xref:System.Windows.Forms.TextBox> denetim <xref:System.Windows.Forms.BindingSource> bileşen ekleyin.  
  
2. `bindingSource1` verilere ve metin kutusu denetimlerine `bindingSource1`. Bunu yapmak için, aşağıdaki kodu formunuza yapıştırın ve formun Oluşturucu veya <xref:System.Windows.Forms.Form.Load> olay işleme yönteminden `LoadData` çağırın.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3. Formunuza `bindingNavigator1` adlı <xref:System.Windows.Forms.BindingNavigator> bir denetim ekleyin.  
  
4. `bindingNavigator1` için <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> özelliğini `bindingSource1`olarak ayarlayın. Bunu tasarımcı veya kod içinde yapabilirsiniz.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, daha önce listelenen adımlar için tüm örnektir.  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System, System. Data, System. Drawing, System. Windows. Forms ve System. xml derlemelerine başvuru.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.BindingNavigator>
- [BindingNavigator Denetimi](bindingnavigator-control-windows-forms.md)
- [ToolStrip Denetimi](toolstrip-control-windows-forms.md)
