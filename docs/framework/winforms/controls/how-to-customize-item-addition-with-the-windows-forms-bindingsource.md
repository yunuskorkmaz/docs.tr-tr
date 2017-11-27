---
title: "Nasıl yapılır: Windows Forms BindingSource ile Öğe Eklemeyi Özelleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d1978d3b2cf8634d9222ee5278077dfbe437d04
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a>Nasıl yapılır: Windows Forms BindingSource ile Öğe Eklemeyi Özelleştirme
Kullandığınızda, bir <xref:System.Windows.Forms.BindingSource> bir Windows Forms denetimini bir veri kaynağına bağlama bileşeni yeni öğeler oluşturma özelleştirmek gerekli bulabilirsiniz. <xref:System.Windows.Forms.BindingSource> Bileşen yapar bu basit sağlayarak <xref:System.Windows.Forms.BindingSource.AddingNew> ilişkili denetim yeni bir öğe oluşturmak gerektiğinde genellikle oluşan olayı,. Olay işleyicinizi ne olursa olsun özel davranış (örneğin, bir Web hizmeti bir yöntemi çağırma veya yeni bir nesne bir sınıf fabrikası alma) gereklidir sağlayabilir.  
  
> [!NOTE]
>  İşleme göre bir öğe eklendiğinde <xref:System.Windows.Forms.BindingSource.AddingNew> olayı eklenmesi iptal edilemez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl bağlanacağını gösterir bir <xref:System.Windows.Forms.DataGridView> kullanarak bir üreteci denetimine bir <xref:System.Windows.Forms.BindingSource> bileşeni. Kullanıcı tıkladığında <xref:System.Windows.Forms.DataGridView> denetimin yeni satır <xref:System.Windows.Forms.BindingSource.AddingNew> olayı oluşturulur. Yeni bir olay işleyicisi oluşturur `DemoCustomer` atandığı nesne <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> özelliği. Bu yeni neden `DemoCustomer` eklenecek nesne <xref:System.Windows.Forms.BindingSource> bileşenin listesi ve yeni satırında görüntülenecek <xref:System.Windows.Forms.DataGridView> denetim.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Data, System.Drawing ve System.Windows.Forms derlemelerine başvurular.  
  
 Bu örnek için komut satırından oluşturma hakkında bilgi için [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [BindingSource bileşeni](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Nasıl yapılır: Windows Forms denetimini bir türe bağlama](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
