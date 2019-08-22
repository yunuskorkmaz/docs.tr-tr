---
title: 'Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Metni Ayarlama'
ms.date: 08/20/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, captions
- Button control [Windows Forms], button text
- StdFont object and CommandButton caption
- captions [Windows Forms], Windows Forms controls
- Text property [Windows Forms], Windows Forms control
- Button control [Windows Forms], text display
- labels [Windows Forms], adding to CommandButton control
- buttons [Windows Forms], text
- captions [Windows Forms], setting
- text
- examples [Windows Forms], controls
- text [Windows Forms], Windows Forms controls
- controls [Windows Forms], captions
- forms [Windows Forms], captions
ms.assetid: 36b95bff-8780-479d-b86a-f1a0673653aa
ms.openlocfilehash: 887aa5ec9b97770903cd87459d6df5adc3f7ddf0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666148"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a>Nasıl yapılır: Windows Forms denetimi tarafından görünen metni ayarlama

Windows Forms denetimleri genellikle denetimin birincil işleviyle ilgili bazı metinleri görüntüler. Örneğin, bir <xref:System.Windows.Forms.Button> denetim genellikle düğme tıklandığında gerçekleştirilecek eylemi belirten bir başlık görüntüler. Tüm denetimler için, <xref:System.Windows.Forms.Control.Text%2A> özelliğini kullanarak metni ayarlayabilir veya döndürebilirsiniz. <xref:System.Windows.Forms.Control.Font%2A> Özelliğini kullanarak yazı tipini değiştirebilirsiniz.

Ayrıca, [tasarımcıyı](#designer)kullanarak metni de ayarlayabilirsiniz.

## <a name="programmatic"></a>Programatik

1. <xref:System.Windows.Forms.Control.Text%2A> Özelliği bir dizeye ayarlayın.

   Altı çizili erişim anahtarı oluşturmak için, erişim tuşu olacak harften önce bir ve işareti (&) içerir.

2. <xref:System.Windows.Forms.Control.Font%2A> Özelliğini türünde<xref:System.Drawing.Font>bir nesne olarak ayarlayın.

    ```vb
    Button1.Text = "Click here to save changes"
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)
    ```

    ```csharp
    button1.Text = "Click here to save changes";
    button1.Font = new Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point);
    ```

    ```cpp
    button1->Text = "Click here to save changes";
    button1->Font = new System::Drawing::Font("Arial", 10, FontStyle::Bold, GraphicsUnit::Point);
    ```

    > [!NOTE]
    > Bir kaçış karakteri kullanarak, normalde bunları farklı şekilde yorumlayacak Kullanıcı arabirimi öğelerinde menü öğeleri gibi özel bir karakter görüntüleyebilirsiniz. Örneğin, aşağıdaki kod satırı menü öğesinin metnini "tamamen farklı bir şey Için şimdi & okunacak şekilde ayarlar.

    ```vb
    MPMenuItem.Text = "&& Now For Something Completely Different"
    ```

    ```csharp
    mpMenuItem.Text = "&& Now For Something Completely Different";
    ```

    ```cpp
    mpMenuItem->Text = "&& Now For Something Completely Different";
    ```

## <a name="designer"></a>Tasarımcı

1. Visual Studio 'daki **Özellikler** penceresinde, denetimin **Text** özelliğini uygun bir dize olarak ayarlayın.

   Altı çizili kısayol tuşu oluşturmak için, kısayol tuşu olacak harften önce bir ve işareti (&) içerir.

2. **Özellikler** penceresinde,![ **yazı tipi** özelliğinin yanındaki üç nokta düğmesini (Visual Studio](./media/visual-studio-ellipsis-button.png)Özellikler penceresi) seçin.

   Standart yazı tipi iletişim kutusunda yazı tipi, yazı tipi stili, boyut, efekt (üstü çizili veya altı çizili) ve istediğiniz betiği seçin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [Nasıl yapılır: Windows Forms denetimleri için erişim tuşları oluşturma](how-to-create-access-keys-for-windows-forms-controls.md)
- [Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt verme](how-to-respond-to-windows-forms-button-clicks.md)
