---
title: "Nasıl yapılır: Windows Formları BindingNavigator Denetimine Yükleme, Kaydetme ve İptal Düğmeleri Ekleme"
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
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2dd45b33fb1f99c280e126b9e601692a85da5dba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>Nasıl yapılır: Windows Formları BindingNavigator Denetimine Yükleme, Kaydetme ve İptal Düğmeleri Ekleme
<xref:System.Windows.Forms.BindingNavigator> Denetimidir özel amaçlı <xref:System.Windows.Forms.ToolStrip> gezinme ve verilere bağlı denetimler formunuzda düzenleme yöneliktir denetim.  
  
 Çünkü bir <xref:System.Windows.Forms.ToolStrip> denetimi <xref:System.Windows.Forms.BindingNavigator> bileşen kolayca değiştirilebilir kullanıcı için ek veya alternatif komutlar eklenecek.  
  
 Aşağıdaki yordamda bir <xref:System.Windows.Forms.TextBox> denetim verilere bağlı ve <xref:System.Windows.Forms.ToolStrip> yükleme, kaydetme, içerir ve İptal düğmeleri forma eklenen denetim değiştirdi.  
  
### <a name="to-add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>Yük eklemek, kaydetme ve İptal düğmeleri BindingNavigator bileşenine  
  
1.  Ekleme bir <xref:System.Windows.Forms.TextBox> Formunuza denetim.  
  
2.  Kendisine bağlı bir <xref:System.Windows.Forms.BindingSource>, bir veri kaynağına bağlı. Bu örnek için <xref:System.Windows.Forms.BindingSource> bir veritabanına bağlı.  
  
3.  Veri kümesi ve tablo bağdaştırıcısı oluşturulur sonra sürükleyin bir <xref:System.Windows.Forms.BindingNavigator> forma denetim.  
  
4.  Ayarlama <xref:System.Windows.Forms.BindingNavigator> denetimin <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> özelliğine <xref:System.Windows.Forms.BindingSource> denetimlere bağlı form üzerinde.  
  
5.  Seçin <xref:System.Windows.Forms.BindingNavigator> denetim.  
  
6.  Akıllı etiket karakteri tıklayın (![akıllı etiket karakteri](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) böylece **BindingNavigator görevleri** iletişim kutusu görüntülenir ve seçin **öğedüzenleme**.  
  
     **Öğeleri koleksiyonu Düzenleyicisi** görüntülenir.  
  
7.  İçinde **öğeleri koleksiyonu Düzenleyicisi**, aşağıdaki adımları tamamlayın:  
  
    1.  Ekle bir <xref:System.Windows.Forms.ToolStripSeparator> ve üç <xref:System.Windows.Forms.ToolStripButton> uygun türünü seçerek öğeleri <xref:System.Windows.Forms.ToolStripItem> tıklatıp **Ekle** düğmesi.  
  
    2.  Ayarlama <xref:System.Windows.Forms.ToolStripItem.Name%2A> düğmelere özelliğinin**LoadButton**,**saveButton yapın**, ve**CancelButton**sırasıyla.  
  
    3.  Ayarlama <xref:System.Windows.Forms.ToolStripItem.Text%2A> düğmelere özelliğinin**yük** `,` **kaydetmek**, ve**iptal**.  
  
    4.  Ayarlama <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> özelliği her düğmelere**metin**. Alternatif olarak, bu özellik ayarlayabileceğiniz**görüntü**veya**ImageAndText**ve görüntülenecek resmi ayarlama <xref:System.Windows.Forms.ToolStripItem.Image%2A> özelliği.  
  
    5.  Tıklatın **Tamam** iletişim kutusunu kapatın. Düğmeleri eklenir <xref:System.Windows.Forms.ToolStrip>.  
  
8.  Forma sağ tıklayın ve seçin **görünümü kodu**.  
  
9. Kod Düzenleyicisi'nde tablo bağdaştırıcısı verileri yükler kod satırını bulun. Bu kod, 2. adımda veri bağlama ayarladığınızda oluşturuldu. Kod aşağıdakine benzer olmalıdır: `TableAdapterName.Fill(DataSetName.TableName)`. Çoğu içinde büyük olasılıkla formun olması <xref:System.Windows.Forms.Form.Load> olay.  
  
10. İçin bir olay işleyicisi oluşturun <xref:System.Windows.Forms.ToolStripItem.Click> olayı**yük** <xref:System.Windows.Forms.ToolStripButton> daha önce oluşturduğunuz ve bu veri yükleme kod dosyasına taşıyın.  
  
     Kodunuzu aşağıdakine benzer görünmelidir:  
  
    ```vb  
    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click  
        TableAdapterName.Fill(DataSetName.TableName)  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Fill(DataSetName.TableName);  
    }  
    ```  
  
11. İçin bir olay işleyicisi oluşturun <xref:System.Windows.Forms.ToolStripItem.Click> olayı **kaydetmek** <xref:System.Windows.Forms.ToolStripButton> daha önce oluşturduğunuz ve denetim tablodaki verileri güncelleştirmek için kod yazma bağlanır.  
  
    ```vb  
    Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click  
        TableAdapterName.Update(DataSetName.TableName)  
    End Sub  
    ```  
  
    ```csharp  
    private void SaveButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Update(DataSetName.TableName);  
    }  
    ```  
  
    > [!NOTE]
    >  Bazı durumlarda, <xref:System.Windows.Forms.BindingNavigator> bileşeni zaten olacaktır bir**kaydetmek** düğmesi, ancak hiçbir kod oluşturulduğunu Windows Form Tasarımcısı tarafından. Bu durumda, önceki kodda yerleştirebilirsiniz <xref:System.Windows.Forms.ToolStripItem.Click> tamamen yeni bir düğme oluşturma yerine bu düğme için olay işleyicisini <xref:System.Windows.Forms.ToolStrip>. Ayarlamanız gerekir böylece ancak düğmesi varsayılan olarak devre dışıdır <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> düğme özelliğinin `true` düğmesi işlevi doğru olması.  
  
12. İçin bir olay işleyicisi oluşturun <xref:System.Windows.Forms.ToolStripItem.Click> olayı**iptal** <xref:System.Windows.Forms.ToolStripButton> daha önce oluşturduğunuz ve görüntülenen verileri kaydı değişiklikleri iptal etmek için kod yazma.  
  
    ```vb  
    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click  
        BindingSourceName.CancelEdit()  
    End Sub  
    ```  
  
    ```csharp  
    private void CancelButton_Click(System.Object sender, System.EventArgs e)  
    {  
        BindingSourceName.CancelEdit();  
    }  
    ```  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> Yöntemi veri satırının kapsamlı. Sonraki kayda gitmeden önce tek tek kaydı görüntülerken yaptığınız değişiklikleri kaydedin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.ToolStrip>  
 [BindingNavigator Denetimi](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [BindingSource Bileşenine Genel Bakış](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)
