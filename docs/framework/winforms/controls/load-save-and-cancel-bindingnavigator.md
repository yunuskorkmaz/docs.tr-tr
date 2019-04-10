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
ms.openlocfilehash: 4d5cc91ca8bf71b2d5893f591652d777041e1a4d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304785"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>Nasıl yapılır: Windows Forms BindingNavigator Denetimine Yükleme, Kaydetme ve İptal Düğmeleri Ekleme
<xref:System.Windows.Forms.BindingNavigator> Denetimidir özel amaçlı <xref:System.Windows.Forms.ToolStrip> denetimi gezinme ve verilere bağlı denetimler formunuzdaki işlemek için tasarlanmıştır.  
  
 Çünkü bu bir <xref:System.Windows.Forms.ToolStrip> denetimi <xref:System.Windows.Forms.BindingNavigator> bileşen kolayca değiştirilebilir ek veya alternatif komut kullanıcı için eklenecek.  
  
 Aşağıdaki yordamda bir <xref:System.Windows.Forms.TextBox> denetimin verilere bağlı ve <xref:System.Windows.Forms.ToolStrip> kaydetme, yükleme, içerir ve İptal düğmeleri değiştirilmişse forma eklenen denetimi.  
  
### <a name="to-add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>Yük eklemek, kaydetme ve İptal düğmeleri BindingNavigator bileşenine  
  
1. Ekleme bir <xref:System.Windows.Forms.TextBox> form denetimi.  
  
2. Öğeyi bir <xref:System.Windows.Forms.BindingSource>, bir veri kaynağına bağlı. Bu örnekte, <xref:System.Windows.Forms.BindingSource> veritabanına bağlanır.  
  
3. Veri kümesi ve tablo bağdaştırıcısı oluşturulur, sonra sürükleyin bir <xref:System.Windows.Forms.BindingNavigator> forma.  
  
4. Ayarlama <xref:System.Windows.Forms.BindingNavigator> denetimin <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> özelliğini <xref:System.Windows.Forms.BindingSource> denetimlere bağlı form üzerindeki.  
  
5. Seçin <xref:System.Windows.Forms.BindingNavigator> denetimi.  
  
6. Akıllı etiket karakterini tıklayın (![akıllı etiket karakterini](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) böylece **BindingNavigator görevleri** iletişim kutusu açılır ve seçin **öğedüzenleme**.  
  
     **Öğeler Koleksiyonu Düzenleyicisi** görünür.  
  
7. İçinde **öğeler Koleksiyonu Düzenleyicisi**, aşağıdaki adımları tamamlayın:  
  
    1.  Ekle bir <xref:System.Windows.Forms.ToolStripSeparator> ve üç <xref:System.Windows.Forms.ToolStripButton> uygun türünü seçerek öğeleri <xref:System.Windows.Forms.ToolStripItem> tıklayıp **Ekle** düğmesi.  
  
    2.  Ayarlama <xref:System.Windows.Forms.ToolStripItem.Name%2A> düğmelere özelliği **LoadButton**, **saveButton yapın**, ve **CancelButton**sırasıyla.  
  
    3.  Ayarlama <xref:System.Windows.Forms.ToolStripItem.Text%2A> düğmelere özelliği **yük**, **Kaydet**, ve **iptal**.  
  
    4.  Ayarlama <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> her düğme için özellik **metin**. Alternatif olarak, bu özelliği ayarlayın **görüntü** veya **ImageAndText**ve görüntülenen resmi ayarlama <xref:System.Windows.Forms.ToolStripItem.Image%2A> özelliği.  
  
    5.  Tıklayın **Tamam** iletişim kutusunu kapatın. Düğmeleri eklenen <xref:System.Windows.Forms.ToolStrip>.  
  
8. Formun sağ tıklatın ve seçin **kodu görüntüle**.  
  
9. Kod Düzenleyicisi'nde tablo bağdaştırıcısı veri yükleyen kod satırını bulun. Veri bağlama 2. adımda ayarladığınızda bu kod üretildi. Kodu aşağıdakine benzer olmalıdır: `TableAdapterName.Fill(DataSetName.TableName)`. Çoğu olacak büyük olasılıkla formun olması <xref:System.Windows.Forms.Form.Load> olay.  
  
10. İçin bir olay işleyicisi oluşturun <xref:System.Windows.Forms.ToolStripItem.Click> olayı **yük** <xref:System.Windows.Forms.ToolStripButton> daha önce oluşturduğunuz ve bu veri yükleme kod içine taşıyın.  
  
     Kodunuzun aşağıdakine benzer görünmelidir:  
  
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
  
11. İçin bir olay işleyicisi oluşturun <xref:System.Windows.Forms.ToolStripItem.Click> olayı **Kaydet** <xref:System.Windows.Forms.ToolStripButton> daha önce oluşturduğunuz ve tablo denetimi içindeki verileri güncelleştirmek için kod yazma bağlanır.  
  
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
    > Bazı durumlarda, <xref:System.Windows.Forms.BindingNavigator> bileşeni zaten sahip olacak bir **Kaydet** düğmesi, ancak hiçbir kod oluşturulduğunu Windows Form Tasarımcısı tarafından. Bu durumda, önceki kodu koyabilirsiniz <xref:System.Windows.Forms.ToolStripItem.Click> üzerinde tamamen yeni bir düğme oluşturmak yerine bu düğme için olay işleyicisi <xref:System.Windows.Forms.ToolStrip>. Ayarlamanız gerekir ancak düğmenin varsayılan olarak devre dışıdır <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> düğmenin özelliği `true` düğme işlevi doğru olması.
  
12. İçin bir olay işleyicisi oluşturun <xref:System.Windows.Forms.ToolStripItem.Click> olayı **iptal** <xref:System.Windows.Forms.ToolStripButton> daha önce oluşturduğunuz ve görüntülenen veri kaydına değişiklikleri iptal etmek için kod yazın.  
  
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
    >  <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> Yöntemi veri satırı için kapsamlı. Sonraki kayda gitmeden önce tek bir kayıt görüntülerken yaptığınız tüm değişiklikleri kaydedin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [BindingNavigator Denetimi](bindingnavigator-control-windows-forms.md)
- [BindingSource Bileşenine Genel Bakış](bindingsource-component-overview.md)
