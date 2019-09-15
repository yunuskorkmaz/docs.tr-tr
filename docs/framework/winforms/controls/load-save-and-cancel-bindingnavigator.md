---
title: 'Nasıl yapılır: Windows Forms BindingNavigator Denetimine Yükleme, Kaydetme ve İptal Düğmeleri Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: 2d4867c0bc4feb7b43e15614fc56a3c709cef9e7
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991733"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>Nasıl yapılır: Windows Forms BindingNavigator Denetimine Yükleme, Kaydetme ve İptal Düğmeleri Ekleme

Denetim, formunuzda verilere bağlı olan denetimleri <xref:System.Windows.Forms.ToolStrip> gezme ve düzenleme için tasarlanan özel amaçlı bir denetimdir. <xref:System.Windows.Forms.BindingNavigator>

Bir <xref:System.Windows.Forms.ToolStrip> denetim olduğundan <xref:System.Windows.Forms.BindingNavigator> , bileşen Kullanıcı için ek veya alternatif komutlar içerecek şekilde kolayca değiştirilebilir.

Aşağıdaki yordamda, bir <xref:System.Windows.Forms.TextBox> denetim verilere bağlanır <xref:System.Windows.Forms.ToolStrip> ve forma eklenen denetim, yükleme, kaydetme ve İptal düğmelerini içerecek şekilde değiştirilir.

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>BindingNavigator bileşenine yükleme, kaydetme ve iptal düğmeleri ekleme

1. Visual Studio 'da formunuza bir <xref:System.Windows.Forms.TextBox> denetim ekleyin.

2. Bir <xref:System.Windows.Forms.BindingSource>veri kaynağına bağlı olan öğesine bağlayın. Bu örnekte <xref:System.Windows.Forms.BindingSource> , bir veritabanına bağlanır.

3. Veri kümesi ve tablo bağdaştırıcısı oluşturulduktan sonra forma bir <xref:System.Windows.Forms.BindingNavigator> denetim sürükleyin.

4. Denetimin özelliğini ,<xref:System.Windows.Forms.BindingSource> denetimlere bağlı olan form üzerinde olarak ayarlayın. <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> <xref:System.Windows.Forms.BindingNavigator>

5. <xref:System.Windows.Forms.BindingNavigator> Denetimi seçin.

6. **BindingNavigator görevleri** iletişim kutusu görünür ve **öğeleri Düzenle**' yi seçerek akıllı etiket glifi ' ne (![akıllı etiket karakteri](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) tıklayın.

     **Öğeler koleksiyonu Düzenleyicisi** görünür.

7. **Öğe koleksiyonu düzenleyicisinde**, aşağıdakileri doldurun:

    1. <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolStripSeparator> Uygun türü<xref:System.Windows.Forms.ToolStripItem> seçerek ve Ekle düğmesine tıklayarak, ve üç öğesi ekleyin.

    2. Düğmelerin özelliğini sırasıyla **loadButton**, **saveButton**ve **CancelButton**olarak ayarlayın. <xref:System.Windows.Forms.ToolStripItem.Name%2A>

    3. Yüklenecek, **kaydedilecek**ve **iptal**edilecek düğmelerin özelliğiniayarlayın.<xref:System.Windows.Forms.ToolStripItem.Text%2A>

    4. Düğmelerin her bir özelliğinimetinolarak<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> ayarlayın. Alternatif olarak, bu özelliği **Image** veya **ImageAndText**olarak ayarlayabilir ve görüntüde <xref:System.Windows.Forms.ToolStripItem.Image%2A> görüntülenecek şekilde ayarlayabilirsiniz.

    5. İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın. Düğmeleri öğesine <xref:System.Windows.Forms.ToolStrip>eklenir.

8. Forma sağ tıklayın ve **kodu görüntüle**' yi seçin.

9. Kod Düzenleyicisi 'nde, tablo bağdaştırıcısına veri yükleyen kod satırını bulun. Bu kod, adım 2 ' de veri bağlamayı ayarlarken oluşturulmuştur. Kod aşağıdakine benzer olmalıdır: `TableAdapterName.Fill(DataSetName.TableName)`. Büyük olasılıkla formun <xref:System.Windows.Forms.Form.Load> olayında olacaktır.

10. Daha önce oluşturduğunuz <xref:System.Windows.Forms.ToolStripItem.Click> **yükün** <xref:System.Windows.Forms.ToolStripButton> olayı için bir olay işleyicisi oluşturun ve bu veri yükleme kodunu buna taşıyın.

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

11. Daha önce oluşturduğunuz <xref:System.Windows.Forms.ToolStripItem.Click> **kaydetme** <xref:System.Windows.Forms.ToolStripButton> olayı için bir olay işleyicisi oluşturun ve denetimin bağlandığı tablodaki verileri güncelleştirmek için kod yazın.

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
    > Bazı durumlarda, <xref:System.Windows.Forms.BindingNavigator> bileşen zaten bir **Kaydet** düğmesine sahiptir, ancak Windows Form Tasarımcısı hiçbir kod üretilmez. Bu durumda, <xref:System.Windows.Forms.ToolStrip>üzerinde tamamen yeni bir düğme oluşturmak yerine, önceki <xref:System.Windows.Forms.ToolStripItem.Click> kodu bu düğmeye ait olay işleyicisine yerleştirebilirsiniz. Ancak düğme varsayılan olarak devre dışıdır, bu nedenle düğmenin <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> özelliğini `true` düğme işlevine doğru olacak şekilde ayarlamanız gerekir.

12. Daha önce oluşturduğunuz <xref:System.Windows.Forms.ToolStripItem.Click> **iptal etme** <xref:System.Windows.Forms.ToolStripButton> olayı için bir olay işleyicisi oluşturun ve görüntülenen veri kaydındaki tüm değişiklikleri iptal etmek için kod yazın.

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
    > <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> Yöntemi, veri satırının kapsamına alınır. Bir sonraki kayda gitmeden önce bu tek kaydı görüntülerken yaptığınız değişiklikleri kaydedin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [BindingNavigator Denetimi](bindingnavigator-control-windows-forms.md)
- [BindingSource Bileşenine Genel Bakış](bindingsource-component-overview.md)
