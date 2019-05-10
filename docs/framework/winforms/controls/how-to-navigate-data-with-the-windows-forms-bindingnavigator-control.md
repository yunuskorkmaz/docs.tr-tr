---
title: 'Nasıl yapılır: Windows Forms BindingNavigator Denetimi ile Verilerde Gezinme'
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
ms.openlocfilehash: 0702532627fe4425a7c5e3ade5530939c8df5500
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649239"
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a>Nasıl yapılır: Windows Forms BindingNavigator Denetimi ile Verilerde Gezinme
Gelişinden <xref:System.Windows.Forms.BindingNavigator> denetimini Windows Forms içinde son kullanıcılar oluşturdukları formlarında basit veri gezinti ve düzenleme kullanıcı arabirimi ile sağlamak geliştiricilerin sağlar.  
  
 <xref:System.Windows.Forms.BindingNavigator> Denetimi bir <xref:System.Windows.Forms.ToolStrip> denetimi düğmeleri ile önceden yapılandırılmış, ilk gezinme için son olarak, bir veri kümesinin yanı sıra ekleme ve silme kayıtlarını düğmeleri sonraki ve önceki kayıt. Düğmeleri ekleme <xref:System.Windows.Forms.BindingNavigator> denetim kolaydır, çünkü bu bir <xref:System.Windows.Forms.ToolStrip> denetimi. Örnekler için bkz [nasıl yapılır: Yükleme, kaydetme ve ekleme İptal düğmeleri Windows Forms BindingNavigator denetimi](load-save-and-cancel-bindingnavigator.md).  
  
 Her düğme için <xref:System.Windows.Forms.BindingNavigator> karşılık gelen bir üyesi olduğunda, Denetim <xref:System.Windows.Forms.BindingSource> programlı olarak aynı işlevselliği sağlayan bileşeni. Örneğin, <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> düğmesi karşılık gelen <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> yöntemi <xref:System.Windows.Forms.BindingSource> bileşeni <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> düğmesi karşılık gelen <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> yöntemi ve benzeri. Sonuç olarak, etkinleştirme <xref:System.Windows.Forms.BindingNavigator> denetimi veri Kayıtlarda gezinmek için basit bir ayarı olarak kendi <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> özelliğini uygun <xref:System.Windows.Forms.BindingSource> formdaki bileşen.  
  
### <a name="to-set-up-the-bindingnavigator-control"></a>BindingNavigator denetimi ayarlamak için  
  
1. Ekleme bir <xref:System.Windows.Forms.BindingSource> bileşeninizin `bindingSource1` ve iki <xref:System.Windows.Forms.TextBox> adlarında `textBox1` ve `textBox2`.  
  
2. Bağlama `bindingSource1` veri ve metin denetimlerine `bindingSource1`. Bunu yapmak için aşağıdaki kodu, form ve çağrı yapıştırın `LoadData` formun oluşturucudan veya <xref:System.Windows.Forms.Form.Load> olay işleme yöntemi.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3. Ekleme bir <xref:System.Windows.Forms.BindingNavigator> adlı Denetim `bindingNavigator1` formunuza.  
  
4. Ayarlama <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> özelliği `bindingNavigator1` için `bindingSource1`. Tasarımcı ile veya kod bunu yapabilirsiniz.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, tam bir örnek daha önce listelenen adımları için ' dir.  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- Sistem, System.Data System.Drawing, System.Windows.Forms ve System.Xml derlemesine ilişkin başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.BindingNavigator>
- [BindingNavigator Denetimi](bindingnavigator-control-windows-forms.md)
- [ToolStrip Denetimi](toolstrip-control-windows-forms.md)
