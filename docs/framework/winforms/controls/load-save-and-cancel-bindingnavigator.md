---
title: BindingNavigator denetimine yükleme, kaydetme ve Iptal düğmeleri ekleme
description: Windows Forms BindingNavigator denetimine yükleme, kaydetme ve Iptal düğmeleri eklemeyi öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: d4db91b8cfaf2df253d0c4cf5d8a66e9157d4986
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173425"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>Nasıl yapılır: Windows Formları BindingNavigator Denetimine Yükleme, Kaydetme ve İptal Düğmeleri Ekleme

<xref:System.Windows.Forms.BindingNavigator>Denetim, <xref:System.Windows.Forms.ToolStrip> formunuzda verilere bağlı olan denetimleri gezme ve düzenleme için tasarlanan özel amaçlı bir denetimdir.

Bir <xref:System.Windows.Forms.ToolStrip> Denetim olduğundan, <xref:System.Windows.Forms.BindingNavigator> bileşen Kullanıcı için ek veya alternatif komutlar içerecek şekilde kolayca değiştirilebilir.

Aşağıdaki yordamda, bir <xref:System.Windows.Forms.TextBox> Denetim verilere bağlanır ve <xref:System.Windows.Forms.ToolStrip> forma eklenen denetim, yükleme, kaydetme ve İptal düğmelerini içerecek şekilde değiştirilir.

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>BindingNavigator bileşenine yükleme, kaydetme ve iptal düğmeleri ekleme

1. Visual Studio 'da <xref:System.Windows.Forms.TextBox> formunuza bir denetim ekleyin.

2. Bir <xref:System.Windows.Forms.BindingSource> veri kaynağına bağlı olan öğesine bağlayın. Bu örnekte, <xref:System.Windows.Forms.BindingSource> bir veritabanına bağlanır.

3. Veri kümesi ve tablo bağdaştırıcısı oluşturulduktan sonra forma bir denetim sürükleyin <xref:System.Windows.Forms.BindingNavigator> .

4. <xref:System.Windows.Forms.BindingNavigator>Denetimin <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> özelliğini, <xref:System.Windows.Forms.BindingSource> denetimlere bağlı olan form üzerinde olarak ayarlayın.

5. Denetimi seçin <xref:System.Windows.Forms.BindingNavigator> .

6. (Küçük siyah ok) tasarımcı eylemleri simgesine tıklayın, ![ ](./media/designer-actions-glyph.gif) böylece **BindingNavigator görevler** Iletişim kutusu görünür ve **öğeleri Düzenle**' yi seçin.

     **Öğeler koleksiyonu Düzenleyicisi** görünür.

7. **Öğe koleksiyonu düzenleyicisinde**, aşağıdakileri doldurun:

    1. <xref:System.Windows.Forms.ToolStripSeparator> <xref:System.Windows.Forms.ToolStripButton> Uygun türü seçerek ve <xref:System.Windows.Forms.ToolStripItem> **Ekle** düğmesine tıklayarak, ve üç öğesi ekleyin.

    2. <xref:System.Windows.Forms.ToolStripItem.Name%2A>Düğmelerin özelliğini sırasıyla **loadButton**, **saveButton**ve **CancelButton**olarak ayarlayın.

    3. <xref:System.Windows.Forms.ToolStripItem.Text%2A> **Yüklenecek**, **kaydedilecek**ve **iptal**edilecek düğmelerin özelliğini ayarlayın.

    4. <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>Düğmelerin her bir özelliğini **metin**olarak ayarlayın. Alternatif olarak, bu özelliği **Image** veya **ImageAndText**olarak ayarlayabilir ve görüntüde görüntülenecek şekilde ayarlayabilirsiniz <xref:System.Windows.Forms.ToolStripItem.Image%2A> .

    5. **Tamam**’a tıklayarak iletişim kutusunu kapatın. Düğmeleri öğesine eklenir <xref:System.Windows.Forms.ToolStrip> .

8. Forma sağ tıklayın ve **kodu görüntüle**' yi seçin.

9. Kod Düzenleyicisi 'nde, tablo bağdaştırıcısına veri yükleyen kod satırını bulun. Bu kod, adım 2 ' de veri bağlamayı ayarlarken oluşturulmuştur. Kod aşağıdakine benzer olmalıdır: `TableAdapterName.Fill(DataSetName.TableName)` . Büyük olasılıkla formun <xref:System.Windows.Forms.Form.Load> olayında olacaktır.

10. <xref:System.Windows.Forms.ToolStripItem.Click>Daha önce oluşturduğunuz **yükün** olayı için bir olay işleyicisi oluşturun <xref:System.Windows.Forms.ToolStripButton> ve bu veri yükleme kodunu buna taşıyın.

     Kodunuz artık aşağıdakine benzer şekilde görünmelidir:

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

11. <xref:System.Windows.Forms.ToolStripItem.Click>Daha önce oluşturduğunuz **kaydetme** olayı için bir olay işleyicisi oluşturun <xref:System.Windows.Forms.ToolStripButton> ve denetimin bağlandığı tablodaki verileri güncelleştirmek için kod yazın.

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
    > Bazı durumlarda, <xref:System.Windows.Forms.BindingNavigator> bileşen zaten bir **Kaydet** düğmesine sahiptir, ancak Windows Form Tasarımcısı hiçbir kod üretilmez. Bu durumda, <xref:System.Windows.Forms.ToolStripItem.Click> üzerinde tamamen yeni bir düğme oluşturmak yerine, önceki kodu bu düğmeye ait olay işleyicisine yerleştirebilirsiniz <xref:System.Windows.Forms.ToolStrip> . Ancak düğme varsayılan olarak devre dışıdır, bu nedenle düğmenin <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> özelliğini düğme işlevine doğru olacak şekilde ayarlamanız gerekir `true` .

12. <xref:System.Windows.Forms.ToolStripItem.Click>Daha önce oluşturduğunuz **iptal etme** olayı için bir olay işleyicisi oluşturun <xref:System.Windows.Forms.ToolStripButton> ve görüntülenen veri kaydındaki tüm değişiklikleri iptal etmek için kod yazın.

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
    > <xref:System.Windows.Forms.BindingSource.CancelEdit%2A>Yöntemi, veri satırının kapsamına alınır. Bir sonraki kayda gitmeden önce bu tek kaydı görüntülerken yaptığınız değişiklikleri kaydedin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [BindingNavigator denetimi](bindingnavigator-control-windows-forms.md)
- [BindingSource Bileşenine Genel Bakış](bindingsource-component-overview.md)
