---
title: 'Nasıl yapılır: Veri Girişi İçin Yeniden Boyutlandırılabilir Windows Formu Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms], resizing
- forms [Windows Forms], creating resizable
- Windows Forms, resizable
ms.assetid: babdf198-404c-485d-a914-ed370c6ecd99
ms.openlocfilehash: 1b27c0e67aae1935c4216654d9f3ddf557719572
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588932"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a>Nasıl yapılır: Veri Girişi İçin Yeniden Boyutlandırılabilir Windows Formu Oluşturma
İyi bir düzen değişiklikleri kendi üst formunun boyutları için de yanıt verir. Kullanabileceğiniz <xref:System.Windows.Forms.TableLayoutPanel> yeniden boyutlandırabilir ve denetimleri tutarlı bir şekilde form denetiminin boyutlarını değiştikçe konumlandırmak için formun yerleşimini düzenlemeyi denetimi. <xref:System.Windows.Forms.TableLayoutPanel> Denetimidir de yararlıdır düzen değişiklikleri neden denetimlerinizi içeriğini değiştirir. Visual Studio ortamında bu yordamda bahsedilen işlem yapılabilir.  Ayrıca bkz: [izlenecek yol: Veri girişi için yeniden boyutlandırılabilir Windows formu oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Forms.TableLayoutPanel> zaman kullanıcı formu boyutlandırır iyi cevap veren bir düzen oluşturmak için denetimi. Ayrıca, yerelleştirmeye iyi cevap veren bir düzen gösterir.  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Nasıl yapılır: Sabitleme ve TableLayoutPanel denetiminde alt denetimleri yerleştirme](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Nasıl yapılır: Yerelleştirmeye iyi cevap veren bir Windows Forms düzeni tasarlama](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [Microsoft Windows kullanıcı deneyimi, kullanıcı arabirimi geliştiricileri ve tasarımcıları için resmi yönergeleri. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
