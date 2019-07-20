---
title: 'Nasıl yapılır: ToolStripControlHost ile Bir Windows Forms Denetimini Kaydırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStrip control [Windows Forms], wrapping controls
- toolbars [Windows Forms], wrapping controls
- ToolStrip control [Windows Forms], hosting controls
ms.assetid: e2ce4990-661d-4882-a116-8a9eb575dc84
ms.openlocfilehash: 6335d09a89225ae1e202a781a73bfd149608f5fc
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364194"
---
# <a name="how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost"></a>Nasıl yapılır: ToolStripControlHost ile Bir Windows Forms Denetimini Kaydırma
<xref:System.Windows.Forms.ToolStripControlHost>, <xref:System.Windows.Forms.ToolStripControlHost> oluşturucuyu kullanarak veya kendisini genişleterek <xref:System.Windows.Forms.ToolStripControlHost> rastgele Windows Forms denetimlerinin barındırılmasına olanak tanımak üzere tasarlanmıştır. Denetimin sık kullanılan özelliklerini ve yöntemlerini sunan özellikleri ve <xref:System.Windows.Forms.ToolStripControlHost> yöntemleri genişleterek ve uygulayarak denetimi sarmayı daha kolay hale getirir. Ayrıca, denetimin <xref:System.Windows.Forms.ToolStripControlHost> olaylarını düzeyinde kullanıma sunabilirsiniz.  
  
### <a name="to-host-a-control-in-a-toolstripcontrolhost-by-derivation"></a>Türeerek bir ToolStripControlHost 'ta denetim barındırmak için  
  
1. Genişletin <xref:System.Windows.Forms.ToolStripControlHost>. İstenen denetimde geçen temel sınıf oluşturucusunu çağıran parametresiz bir Oluşturucu uygulayın.  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#10)]  
  
2. Sarmalanan denetimle aynı türde bir özellik bildirin ve özelliğin erişimcisinde doğru `Control` denetim türü olarak döndürün.  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#11)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#11)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#11)]  
  
3. Sarmalanan denetimin diğer sık kullanılan özelliklerini ve yöntemlerini genişletilmiş sınıftaki özellikler ve yöntemlerle kullanıma sunun.  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#12)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#12)]  
  
4. İsteğe bağlı olarak, <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A>ve <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> yöntemlerini geçersiz kılın ve göstermek istediğiniz denetim olaylarını ekleyin.  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#16)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#16)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#16)]  
  
5. Göstermek istediğiniz olaylar için gereken sarmayı sağlayın.  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#17)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#17)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#17)]  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#13)]
 [!code-csharp[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#13)]
 [!code-vb[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#13)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
Bu örnek şunları gerektirir:
  
- System ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStripControlHost>
- [ToolStrip Denetimine Genel Bakış](toolstrip-control-overview-windows-forms.md)
- [ToolStrip Denetim, Mimarisi](toolstrip-control-architecture.md)
- [ToolStrip Teknoloji Özeti](toolstrip-technology-summary.md)
