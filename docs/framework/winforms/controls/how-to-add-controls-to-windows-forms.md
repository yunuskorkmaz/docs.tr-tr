---
title: 'Nasıl yapılır: Windows Forms’a Denetimler Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: 5c57d86b2f08733dc4a729bf6091eab23c6035f2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039704"
---
# <a name="how-to-add-controls-to-windows-forms"></a>Nasıl yapılır: Windows Forms’a Denetimler Ekleme
Çoğu form, bir kullanıcı arabirimi (UI) tanımlamak için formun yüzeyine denetimler eklenerek tasarlanır. *Denetim* , bilgileri göstermek veya Kullanıcı girişini kabul etmek için kullanılan bir form bileşenidir. Denetimler hakkında daha fazla bilgi için bkz. [Windows Forms denetimleri](index.md).

## <a name="to-draw-a-control-on-a-form"></a>Form üzerinde bir denetim çizmek için

1. Formunu açın. Daha fazla bilgi için [nasıl yapılır: Tasarımcıda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))Windows Forms görüntüleyin.

2. **Araç kutusunda**formunuza eklemek istediğiniz denetime tıklayın.

3. Form üzerinde, denetimin sol üst köşesinin bulunmasını istediğiniz yere tıklayın ve denetimin sağ alt köşesinin bulunmasını istediğiniz yere sürükleyin.

     Denetim, belirtilen konum ve boyutla forma eklenir.

    > [!NOTE]
    >  Her denetim için varsayılan bir boyut tanımlanmış. **Araç kutusundan** forma sürükleyerek, denetimin varsayılan boyutundaki formunuza bir denetim ekleyebilirsiniz.

## <a name="to-drag-a-control-to-a-form"></a>Bir denetimi forma sürüklemek için

1. Formunu açın. Daha fazla bilgi için [nasıl yapılır: Tasarımcıda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))Windows Forms görüntüleyin.

2. **Araç kutusunda**istediğiniz denetime tıklayın ve formunuza sürükleyin.

     Denetim, varsayılan boyutunda belirtilen konumda bulunan forma eklenir.

    > [!NOTE]
    >  **Araç kutusundaki** bir denetime çift tıklayarak formun varsayılan boyutunda sol üst köşesine ekleyebilirsiniz.

     Ayrıca, çalışma zamanında bir forma dinamik olarak denetim ekleyebilirsiniz. Aşağıdaki kod örneğinde, bir <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.Button> denetim tıklandığında forma bir denetim eklenecektir.

    > [!NOTE]
    >  Aşağıdaki yordam, bir **düğme** denetimi `Button1`olan bir form olması gerekir, zaten üzerine yerleştirilmiş.

## <a name="to-add-a-control-to-a-form-programmatically"></a>Bir forma programlı bir şekilde denetim eklemek için

1. Formunuzun sınıfı içindeki düğmenin `Click` olayını işleyen yöntemde, denetim değişkeninizin başvurusunu eklemek, `Location`denetimin öğesini ayarlamak ve denetimi eklemek için aşağıdakine benzer bir kod ekleyin.

    ```vb
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
       Dim MyText As New TextBox()
       MyText.Location = New Point(25, 25)
       Me.Controls.Add(MyText)
    End Sub
    ```

    ```csharp
    private void button1_Click(object sender, System.EventArgs e)
    {
       TextBox myText = new TextBox();
       myText.Location = new Point(25,25);
       this.Controls.Add (myText);
    }
    ```

    ```cpp
    private:
      System::Void button1_Click(System::Object ^  sender,
        System::EventArgs ^  e)
      {
        TextBox ^ myText = gcnew TextBox();
        myText->Location = Point(25,25);
        this->Controls->Add(myText);
      }
    ```

    > [!NOTE]
    >  Ayrıca, denetimin diğer özelliklerini başlatmak için de kod ekleyebilirsiniz.

    > [!IMPORTANT]
    >  Kötü amaçlı `UserControl`olarak başvurarak yerel bilgisayarınızı ağ üzerinden bir güvenlik riskine maruz kalabilirsiniz. Bu durum yalnızca zararlı bir kişinin zararlı bir denetim oluşturan bir sorun olduğu ve bunu projenize yanlışlıkla ekleyerek bir sorun olacaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimleri](index.md)
- [Windows Forms’da Denetimleri Düzenleme](arranging-controls-on-windows-forms.md)
- [Nasıl yapılır: Windows Forms denetimleri yeniden boyutlandır](how-to-resize-controls-on-windows-forms.md)
- [Nasıl yapılır: Windows Forms denetimi tarafından görünen metni ayarlama](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
