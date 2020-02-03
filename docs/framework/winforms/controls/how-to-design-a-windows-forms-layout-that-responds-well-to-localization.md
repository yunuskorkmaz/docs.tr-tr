---
title: Yerelleştirme kullanımı kolay bir düzen tasarlama
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
ms.openlocfilehash: 36ffd532b9f539107307144d25c8d9d5f8ba634a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743288"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a>Nasıl yapılır: Yerelleştirmeye İyi Cevap Veren Bir Windows Forms Düzeni Tasarlama
Yerelleştirmeye izin veren formların oluşturulması uluslararası pazarlar için geliştirmeyi büyük ölçüde hızlandırır. Denetim yeniden boyutlandırılması, <xref:System.Windows.Forms.Control.Text%2A> özellik değerlerindeki değişiklikler nedeniyle düzgün şekilde yanıt veren düzenler uygulamak için <xref:System.Windows.Forms.TableLayoutPanel> denetimini kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu form, görüntülenen dize değerlerini diğer dillere çevirecek zaman orantılı olarak ayarlayan bir düzen oluşturmayı gösterir. Bu çeviri işlemine *Yerelleştirme*denir. Daha fazla bilgi için bkz. [Yerelleştirme](../../../standard/globalization-localization/localization.md).  
  
 Visual Studio 'da bu görev için kapsamlı destek vardır.  Ayrıca bkz. [Izlenecek yol: yerelleştirme Için orantı ayarlayan bir düzen oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).  
  
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
  
8. [Nasıl yapılır: AutoSize ve TableLayoutPanel denetimini kullanarak Windows Forms yerelleştirmeyi destekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))  
  
9. [İzlenecek yol: veri girişi için yeniden boyutlandırılabilir Windows formu oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System, System. Data, System. Drawing ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [Yerelleştirme](../../../standard/globalization-localization/localization.md)
