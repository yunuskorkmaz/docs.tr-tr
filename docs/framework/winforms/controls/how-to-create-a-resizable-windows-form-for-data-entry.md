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
ms.openlocfilehash: aeab1b506b9ded4c3c2ab527f07a8655a44cad2b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72396022"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a>Nasıl yapılır: Veri Girişi İçin Yeniden Boyutlandırılabilir Windows Formu Oluşturma
İyi bir düzen, üst form boyutlarındaki değişikliklere iyi yanıt verir. Form boyutları değiştikçe, denetimlerinizi yeniden boyutlandırmak ve düzenli bir şekilde konumlandırmak üzere formunuzun yerleşimini düzenlemek için <xref:System.Windows.Forms.TableLayoutPanel> denetimini kullanabilirsiniz. @No__t-0 denetimi, denetimlerinizin içeriklerinde yapılan değişiklikler düzende değişikliklere neden olduğunda da yararlıdır. Bu yordamda ele alınan işlem, Visual Studio ortamı içinde yapılabilir.  Ayrıca bkz. [Izlenecek yol: veri girişi için yeniden boyutlandırılabilir Windows formu oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Kullanıcı formu yeniden boyutlandırdığında iyi yanıt veren bir düzen oluşturmak için <xref:System.Windows.Forms.TableLayoutPanel> denetiminin nasıl kullanılacağını gösterir. Ayrıca, yerelleştirmeye iyi yanıt veren bir düzen gösterir.  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System, System. Data, System. Drawing ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Nasıl yapılır: Yerelleştirmeye İyi Cevap Veren Bir Windows Forms Düzeni Tasarlama](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
