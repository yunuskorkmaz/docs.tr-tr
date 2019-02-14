---
title: 'Nasıl yapılır: BindingSource ile Windows Forms denetiminde veri kaynağı güncelleştirmelerini yansıtma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data binding [Windows Forms], updating
- BindingSource component [Windows Forms], updating data binding
- examples [Windows Forms], BindingSource component
- data sources [Windows Forms], updating
- BindingSource component [Windows Forms], examples
ms.assetid: bd8bd9b2-af8a-4f11-a3d5-54eecbe2400b
ms.openlocfilehash: fca356c258b482a9f4e4fd64f48801de428f8426
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56260835"
---
# <a name="how-to-reflect-data-source-updates-in-a-windows-forms-control-with-the-bindingsource"></a>Nasıl yapılır: BindingSource ile Windows Forms denetiminde veri kaynağı güncelleştirmelerini yansıtma
Verilere bağlı denetimler kullandığınızda, bazen veri kaynağındaki değişiklikleri veri kaynağına listesi değişti olayları oluşturmaz, yanıtlamak zorunda değilsiniz. Kullandığınızda, <xref:System.Windows.Forms.BindingSource> bileşen veri kaynağınızın bir Windows Forms denetimine bağlamak için veri kaynağınızın çağırarak değişti denetim bildirebilir <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği kullanmayı gösterir <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> ilişkili bir denetimi veri kaynağında bir güncelleştirme hakkında bilgilendirmek için yöntemi.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetBindings#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetBindings#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetBindings#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingSource Bileşeni](../../../../docs/framework/winforms/controls/bindingsource-component.md)
- [Nasıl yapılır: Bir Windows Forms denetimini bir türe bağlama](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
