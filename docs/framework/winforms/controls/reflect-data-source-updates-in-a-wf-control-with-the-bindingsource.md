---
title: 'Nasıl yapılır: BindingSource ile Windows Forms Denetiminde Veri Kaynağı Güncelleştirmelerini Yansıtma'
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
- cpp
helpviewer_keywords:
- data binding [Windows Forms], updating
- BindingSource component [Windows Forms], updating data binding
- examples [Windows Forms], BindingSource component
- data sources [Windows Forms], updating
- BindingSource component [Windows Forms], examples
ms.assetid: bd8bd9b2-af8a-4f11-a3d5-54eecbe2400b
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3efe2ee21b6e9073bc9046eae2537bcf8fd9aa1b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-reflect-data-source-updates-in-a-windows-forms-control-with-the-bindingsource"></a>Nasıl yapılır: BindingSource ile Windows Forms Denetiminde Veri Kaynağı Güncelleştirmelerini Yansıtma
Verilere bağlı denetimler kullandığınızda, bazen değişiklikler veri kaynağındaki veri kaynağı listesi değişti olayları oluşturmaz zaman yanıtlamak zorunda değilsiniz. Kullandığınızda <xref:System.Windows.Forms.BindingSource> veri kaynağınız bir Windows Forms denetimi bağlamak için bileşen veri kaynağınız çağırarak değişti denetim bildirebilir <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde kullanımı gösterilir <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> ilişkili bir denetim veri kaynağındaki bir güncelleştirme hakkında bilgilendirmek için yöntem.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetBindings#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetBindings#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetBindings#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [BindingSource Bileşeni](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
