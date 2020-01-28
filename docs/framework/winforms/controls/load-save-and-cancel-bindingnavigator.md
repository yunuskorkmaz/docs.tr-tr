---
title: BindingNavigator denetimine yükleme, kaydetme ve Iptal düğmeleri ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: ac862d163f1bd8b66f29160d836bc459e4bf4081
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745133"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>Nasıl yapılır: Windows Formları BindingNavigator Denetimine Yükleme, Kaydetme ve İptal Düğmeleri Ekleme

<xref:System.Windows.Forms.BindingNavigator> denetimi, formunuzda verilere bağlı olan denetimleri gezme ve düzenleme için tasarlanan özel amaçlı bir <xref:System.Windows.Forms.ToolStrip> denetimidir.

<xref:System.Windows.Forms.ToolStrip> bir denetim olduğundan, <xref:System.Windows.Forms.BindingNavigator> bileşen Kullanıcı için ek veya alternatif komutlar içerecek şekilde kolayca değiştirilebilir.

Aşağıdaki yordamda, <xref:System.Windows.Forms.TextBox> bir denetim verilere bağlanır ve forma eklenen <xref:System.Windows.Forms.ToolStrip> denetimi yükleme, kaydetme ve İptal düğmelerini içerecek şekilde değiştirilir.

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>BindingNavigator bileşenine yükleme, kaydetme ve iptal düğmeleri ekleme

1. Visual Studio 'da formunuza bir <xref:System.Windows.Forms.TextBox> denetimi ekleyin.

2. Bir veri kaynağına bağlı bir <xref:System.Windows.Forms.BindingSource>bağlayın. Bu örnek için <xref:System.Windows.Forms.BindingSource> bir veritabanına bağlanır.

3. Veri kümesi ve tablo bağdaştırıcısı oluşturulduktan sonra forma <xref:System.Windows.Forms.BindingNavigator> denetimini sürükleyin.

4. <xref:System.Windows.Forms.BindingNavigator> denetiminin <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> özelliğini, denetimlere bağlı olan <xref:System.Windows.Forms.BindingSource> olarak ayarlayın.

5. <xref:System.Windows.Forms.BindingNavigator> denetimini seçin.

6. **BindingNavigator görevleri** iletişim kutusunun görünmesi ve **öğeleri Düzenle**' yi seçmek için akıllı etiket kabartmasını (![akıllı etiket karakter](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) tıklatın.

     **Öğeler koleksiyonu Düzenleyicisi** görünür.

7. **Öğe koleksiyonu düzenleyicisinde**, aşağıdakileri doldurun:

    1. Uygun türdeki <xref:System.Windows.Forms.ToolStripItem> seçerek ve **Ekle** düğmesine tıklayarak <xref:System.Windows.Forms.ToolStripSeparator> ve üç <xref:System.Windows.Forms.ToolStripButton> öğesi ekleyin.

    2. Düğmelerin <xref:System.Windows.Forms.ToolStripItem.Name%2A> özelliğini sırasıyla **loadButton**, **saveButton**ve **CancelButton**olarak ayarlayın.

    3. **Yüklenecek**, **kaydedilecek**ve **iptal**edilecek düğmelerin <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğini ayarlayın.

    4. Düğmelerin her biri için <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> özelliğini **metin**olarak ayarlayın. Alternatif olarak, bu özelliği **Image** veya **ImageAndText**olarak ayarlayabilir ve <xref:System.Windows.Forms.ToolStripItem.Image%2A> özelliğinde görüntülenecek şekilde ayarlayabilirsiniz.

    5. İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın. Düğmeler <xref:System.Windows.Forms.ToolStrip>eklenir.

8. Forma sağ tıklayın ve **kodu görüntüle**' yi seçin.

9. Kod Düzenleyicisi 'nde, tablo bağdaştırıcısına veri yükleyen kod satırını bulun. Bu kod, adım 2 ' de veri bağlamayı ayarlarken oluşturulmuştur. Kod aşağıdakine benzer olmalıdır: `TableAdapterName.Fill(DataSetName.TableName)`. Büyük olasılıkla formun <xref:System.Windows.Forms.Form.Load> olayında olacaktır.

10. Daha önce oluşturduğunuz **yükleme** <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolStripItem.Click> olayı için bir olay işleyicisi oluşturun ve bu veri yükleme kodunu buna taşıyın.

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

11. Daha önce oluşturduğunuz **kayıt**<xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolStripItem.Click> olayı için bir olay işleyicisi oluşturun ve denetimin bağlandığı tablodaki verileri güncelleştirmek için kod yazın.

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
    > Bazı durumlarda <xref:System.Windows.Forms.BindingNavigator> bileşeni zaten bir **Kaydet** düğmesine sahiptir, ancak Windows Form Tasarımcısı tarafından hiçbir kod üretilmez. Bu durumda, <xref:System.Windows.Forms.ToolStrip>üzerinde tamamen yeni bir düğme oluşturmak yerine, önceki kodu bu düğme için <xref:System.Windows.Forms.ToolStripItem.Click> olay işleyicisine yerleştirebilirsiniz. Ancak, düğme varsayılan olarak devre dışıdır, bu nedenle düğmenin <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> özelliğini düğmenin doğru çalışması için `true` olarak ayarlamanız gerekir.

12. Daha önce oluşturduğunuz **iptal** <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolStripItem.Click> olayı için bir olay işleyicisi oluşturun ve görüntülenen veri kaydındaki tüm değişiklikleri iptal etmek için kod yazın.

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
    > <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> yöntemi, veri satırının kapsamına alınır. Bir sonraki kayda gitmeden önce bu tek kaydı görüntülerken yaptığınız değişiklikleri kaydedin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [BindingNavigator Denetimi](bindingnavigator-control-windows-forms.md)
- [BindingSource Bileşenine Genel Bakış](bindingsource-component-overview.md)
