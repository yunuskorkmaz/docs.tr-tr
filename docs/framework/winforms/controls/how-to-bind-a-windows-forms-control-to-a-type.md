---
title: 'Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 94faeebb-d2bc-45d6-86d7-96a42661b43d
ms.openlocfilehash: 1130eba7b92ecb5adeba2df9601a31637823754e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530100"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type"></a>Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama
Verilerle etkileşimli denetimleri oluştururken, bazen, bir nesne yerine bir tür bir denetimi bağlamak gerekli bulacaksınız. Ne zaman veri kullanılamayabilir, ancak bir türün ortak arabirim bilgilerini görüntülemek, veri bağlama denetimleri hala gerekir özellikle tasarım zamanında, bu durum ortaya çıkar. Örneğin, bağlayabilirsiniz bir <xref:System.Windows.Forms.DataGridView> denetlemek için bir Web hizmeti tarafından sunulan bir nesne ve istediğiniz <xref:System.Windows.Forms.DataGridView> sütunlarını tasarım zamanında üyeyi içeren özel bir tür adlarını etiketlemek için denetim.  
  
 Bir denetim türü ile kolayca bağlayabilirsiniz <xref:System.Windows.Forms.BindingSource> bileşeni.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde nasıl bağlanacağını gösterir bir <xref:System.Windows.Forms.DataGridView> kullanarak özel bir tür denetimi bir <xref:System.Windows.Forms.BindingSource> bileşeni. Örnek çalıştırdığınızda, fark edeceksiniz <xref:System.Windows.Forms.DataGridView> özelliklerini yansıtan sütunları etiketli bir `Customer` denetimi verilerle doldurulur önce nesne. Örnek veri eklemek için bir müşteri Ekle düğmesi bulunur <xref:System.Windows.Forms.DataGridView> denetim. Düğmeye tıkladığınızda yeni bir `Customer` nesne eklenmiş olup <xref:System.Windows.Forms.BindingSource>. Gerçek hayattaki bir senaryoda, verileri bir Web hizmeti veya diğer veri kaynağı için bir çağrı tarafından alınabilir.  
  
 [!code-csharp[System.Windows.Forms.DataConnector.BindingToType#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindingToType#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem ve System.Windows.Forms derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [BindingSource Bileşeni](../../../../docs/framework/winforms/controls/bindingsource-component.md)
