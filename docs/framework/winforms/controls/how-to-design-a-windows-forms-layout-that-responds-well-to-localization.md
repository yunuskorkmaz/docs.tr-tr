---
title: 'Nasıl yapılır: Yerelleştirmeye İyi Cevap Veren Bir Windows Forms Düzeni Tasarlama'
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
ms.openlocfilehash: 131dc688d2a742fa7a0d99ec7858d4e280c9882f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310765"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a>Nasıl yapılır: Yerelleştirmeye İyi Cevap Veren Bir Windows Forms Düzeni Tasarlama
Çalıştırılmaya hazır olduğunu form oluşturmaya uluslararası pazarlar için geliştirme hızını büyük ölçüde yerelleştirilmiş. Kullanabileceğiniz <xref:System.Windows.Forms.TableLayoutPanel> denetim değişiklikleri nedeniyle denetimleri yeniden boyutlandırma sırasında düzgün bir şekilde yanıt düzenleri uygulamak için kendi <xref:System.Windows.Forms.Control.Text%2A> özellik değerleri.  
  
## <a name="example"></a>Örnek  
 Bu formu görüntülenen dize değerlerini diğer dillere çevirme, orantılı olarak ayarlayan bir düzen oluşturma işlemini gösterir. Bu işlem çevirisi çağrılırken *yerelleştirme*. Daha fazla bilgi için [yerelleştirme](../../../standard/globalization-localization/localization.md).  
  
 Visual Studio'da bu görevi için kapsamlı desteği yoktur.  Ayrıca bkz: [izlenecek yol: Bir düzen oluşturma, yerelleştirme için oranı ayarlayan](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
## <a name="additional-resources"></a>Ek kaynaklar
1. [Nasıl yapılır: TableLayoutPanel Denetiminde Bir Denetimi Hizalama ve Uzatma](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  

3. [Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Yayma](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4. [Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5. [İzlenecek yol: Windows Forms Denetimlerindeki Akıllı Etiketleri Kullanarak Ortak Görevleri Gerçekleştirme](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
  
6. [İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  

7. [İzlenecek yol: Doldurma, Kenar Boşlukları ve AutoSize Özelliği ile Windows Forms Denetimlerini Düzenleme](windows-forms-controls-padding-autosize.md)  
  
8. [Nasıl yapılır: AutoSize ve TableLayoutPanel denetimini kullanarak Windows Formları yerelleştirme desteği](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))  
  
9. [İzlenecek yol: Veri girişi için yeniden boyutlandırılabilir Windows formu oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [Yerelleştirme](../../../standard/globalization-localization/localization.md)
