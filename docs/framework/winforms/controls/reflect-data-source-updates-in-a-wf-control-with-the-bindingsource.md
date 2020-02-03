---
title: BindingSource ile denetimdeki veri kaynağı güncelleştirmelerini yansıtma
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
ms.openlocfilehash: f98296b477dbb674cdbdbd8d03e291dd6ca0c8a3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742444"
---
# <a name="how-to-reflect-data-source-updates-in-a-windows-forms-control-with-the-bindingsource"></a>Nasıl yapılır: BindingSource ile Windows Forms Denetiminde Veri Kaynağı Güncelleştirmelerini Yansıtma
Veriye dayalı denetimler kullandığınızda, veri kaynağı liste değiştirme olaylarını yükseltmezse bazen veri kaynağındaki değişikliklere yanıt vermelisiniz. Veri kaynağınızı bir Windows Forms denetimine bağlamak için <xref:System.Windows.Forms.BindingSource> bileşenini kullandığınızda, <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> yöntemini çağırarak veri kaynağınızın değiştiği denetime bildirimde bulunabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, veri kaynağındaki bir güncelleştirmeyle ilgili bir denetim hakkında bildirim almak için <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> yöntemi kullanmayı gösterir.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingSource Bileşeni](bindingsource-component.md)
- [Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama](how-to-bind-a-windows-forms-control-to-a-type.md)
