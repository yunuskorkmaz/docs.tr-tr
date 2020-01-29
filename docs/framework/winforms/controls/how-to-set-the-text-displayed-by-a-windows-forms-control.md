---
title: Denetim tarafından görünen metni ayarla
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
ms.openlocfilehash: eb02cbc3b335b0d5856f786b21d1d202cf444211
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738428"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a>Nasıl yapılır: Windows Forms denetimi tarafından görüntülenecek metni ayarlama

Windows Forms denetimleri genellikle denetimin birincil işleviyle ilgili bazı metinleri görüntüler. Örneğin, bir <xref:System.Windows.Forms.Button> denetimi genellikle düğme tıklandığında gerçekleştirilecek eylemi belirten bir başlık görüntüler. Tüm denetimler için <xref:System.Windows.Forms.Control.Text%2A> özelliğini kullanarak metni ayarlayabilir veya döndürebilirsiniz. <xref:System.Windows.Forms.Control.Font%2A> özelliğini kullanarak yazı tipini değiştirebilirsiniz.

Ayrıca, [tasarımcıyı](#designer)kullanarak metni de ayarlayabilirsiniz.

## <a name="programmatic"></a>Programatik

1. <xref:System.Windows.Forms.Control.Text%2A> özelliğini bir dizeye ayarlayın.

   Altı çizili erişim anahtarı oluşturmak için, erişim tuşu olacak harften önce bir ve işareti (&) içerir.

2. <xref:System.Windows.Forms.Control.Font%2A> özelliğini <xref:System.Drawing.Font>türünde bir nesne olarak ayarlayın.

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

2. **Özellikler** penceresinde, **yazı tipi** özelliğinin yanındaki üç nokta düğmesini (![üç nokta düğmesini (...) Visual Studio](./media/visual-studio-ellipsis-button.png)Özellikler penceresi) seçin.

   Standart yazı tipi iletişim kutusunda yazı tipi, yazı tipi stili, boyut, efekt (üstü çizili veya altı çizili) ve istediğiniz betiği seçin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [Nasıl yapılır: Windows Forms Denetimleri için Erişim Tuşları Oluşturma](how-to-create-access-keys-for-windows-forms-controls.md)
- [Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme](how-to-respond-to-windows-forms-button-clicks.md)
