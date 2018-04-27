---
title: 'Nasıl yapılır: Windows Forms BindingNavigator Denetimi ile Verilerde Gezinme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 99ed6b7232dd80733fea3c9f36722b0722dc1525
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a>Nasıl yapılır: Windows Forms BindingNavigator Denetimi ile Verilerde Gezinme
Geliştirilirken <xref:System.Windows.Forms.BindingNavigator> Windows Forms denetiminde oluşturdukları formlarında basit veri gezinme ve düzenleme kullanıcı arabirimi ile son kullanıcılar sağlamak için geliştiriciler sağlar.  
  
 <xref:System.Windows.Forms.BindingNavigator> Denetimi bir <xref:System.Windows.Forms.ToolStrip> denetimi düğmeleri ile önceden yapılandırılmış ilk gezinme için son olarak, bir veri kümesi olarak ekleyin ve kayıt silme düğmeleri, önceki ve sonraki kayıt. Düğmelere ekleme <xref:System.Windows.Forms.BindingNavigator> denetim kolaydır, çünkü bir <xref:System.Windows.Forms.ToolStrip> denetim.  Ayrıca bkz. [nasıl yapılır: yükleme, kaydetme ve ekleme İptal düğmeleri Windows Forms BindingNavigator denetimi](http://msdn.microsoft.com/library/safa4957\(v=vs.110\)).  
  
 Her düğme için <xref:System.Windows.Forms.BindingNavigator> denetlemek, karşılık gelen bir üyesi <xref:System.Windows.Forms.BindingSource> program aracılığıyla aynı işlevselliği sağlayan bileşeni. Örneğin, <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> düğmesi karşılık gelen <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> yöntemi <xref:System.Windows.Forms.BindingSource> bileşeni <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> düğmesi karşılık gelen <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> yöntemi ve benzeri. Sonuç olarak, etkinleştirme <xref:System.Windows.Forms.BindingNavigator> veri kayıtlarını gitmek için denetimidir basit bir ayarı olarak kendi <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> özelliğine uygun <xref:System.Windows.Forms.BindingSource> formdaki bileşen.  
  
### <a name="to-set-up-the-bindingnavigator-control"></a>BindingNavigator denetimi ayarlamak için  
  
1.  Ekleme bir <xref:System.Windows.Forms.BindingSource> adlı bileşeni `bindingSource1` ve iki <xref:System.Windows.Forms.TextBox> adlı denetimleri `textBox1` ve `textBox2`.  
  
2.  Bağlama `bindingSource1` veri ve textbox denetimleri `bindingSource1`. Bunu yapmak için aşağıdaki kodu form ve çağrı yapıştırın `LoadData` formun oluşturucusundan veya <xref:System.Windows.Forms.Form.Load> olay işleme yöntemi.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3.  Ekleme bir <xref:System.Windows.Forms.BindingNavigator> adlı Denetim `bindingNavigator1` formunuza.  
  
4.  Ayarlama <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> özelliği için `bindingNavigator1` için `bindingSource1`. Tasarımcı ile veya kod bunu yapabilirsiniz.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, daha önce listelenen adımları için tam örnektir.  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Data, System.Drawing, System.Windows.Forms ve System.Xml derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.BindingNavigator>  
 [BindingNavigator Denetimi](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [ToolStrip Denetimi](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
