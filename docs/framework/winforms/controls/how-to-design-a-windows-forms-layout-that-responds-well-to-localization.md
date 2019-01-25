---
title: 'Nasıl yapılır: Yerelleştirmeye iyi cevap veren bir Windows Forms düzeni tasarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- application design [Windows Forms], localization
- Windows Forms, localization
- localization [Windows Forms], Windows Forms layout
ms.assetid: d13eff2d-701c-4b6e-8838-3885cbfb7223
ms.openlocfilehash: 15f290f7d076eede7a8092d7295df810e4e51bf3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563528"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a>Nasıl yapılır: Yerelleştirmeye iyi cevap veren bir Windows Forms düzeni tasarlama
Çalıştırılmaya hazır olduğunu form oluşturmaya uluslararası pazarlar için geliştirme hızını büyük ölçüde yerelleştirilmiş. Kullanabileceğiniz <xref:System.Windows.Forms.TableLayoutPanel> denetim değişiklikleri nedeniyle denetimleri yeniden boyutlandırma sırasında düzgün bir şekilde yanıt düzenleri uygulamak için kendi <xref:System.Windows.Forms.Control.Text%2A> özellik değerleri.  
  
## <a name="example"></a>Örnek  
 Bu formu görüntülenen dize değerlerini diğer dillere çevirme, orantılı olarak ayarlayan bir düzen oluşturma işlemini gösterir. Bu işlem çevirisi çağrılırken *yerelleştirme*. Daha fazla bilgi için [yerelleştirme](../../../../docs/standard/globalization-localization/localization.md).  
  
 Visual Studio'da bu görevi için kapsamlı desteği yoktur.  Ayrıca bkz: [izlenecek yol: Bir düzen oluşturma, yerelleştirme için oranı ayarlayan](https://msdn.microsoft.com/library/7k9fa71y\(v=vs.110\)).  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
1.  [Nasıl yapılır: Hizalama ve denetim TableLayoutPanel denetiminde uzatma](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2.  [İzlenecek yol: FlowLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme](https://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))  
  
3.  [Nasıl yapılır: TableLayoutPanel denetimi içindeki satırları ve sütunları span](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4.  [Nasıl yapılır: Bir TableLayoutPanel denetimindeki satırları ve sütunları Düzenle](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5.  [İzlenecek yol: Üzerinde Windows Forms denetimleri etiketleri akıllı kullanarak ortak görevleri gerçekleştirme](https://msdn.microsoft.com/library/xhz359sc\(v=vs.110\))  
  
6.  [İzlenecek yol: TableLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme](https://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))  
  
7.  [İzlenecek yol: Windows Forms denetimleri doldurma, kenar boşlukları ve AutoSize özelliği ile düzenleme](https://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))  
  
8.  [Nasıl yapılır: AutoSize ve TableLayoutPanel denetimini kullanarak Windows Formları yerelleştirme desteği](https://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))  
  
9. [İzlenecek yol: Veri girişi için yeniden boyutlandırılabilir Windows formu oluşturma](https://msdn.microsoft.com/library/991eahec\(v=vs.110\))  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  Ayrıca bkz: [nasıl yapılır: Derleme ve Visual Studio kullanarak tam bir Windows Formları kod örneği çalıştırma](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [Yerelleştirme](../../../../docs/standard/globalization-localization/localization.md)
