---
title: Bir Panelin Arka Planını Ayarlama
description: Tasarımcıyı kullanarak bir Windows Forms panelinin arka plan rengini ve arka plan görüntüsünü ayarlamayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: 096cbd8d-45cc-47b8-b1ef-a27f60ea8be0
ms.openlocfilehash: 109ff6184de9c79d1576207bbeb29ad939670b6f
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173386"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a>Nasıl yapılır: Windows Forms Panelinin Arka Planını Ayarlama
Windows Forms <xref:System.Windows.Forms.Panel> Denetim, hem arka plan rengi hem de arka plan görüntüsü görüntüleyebilir. <xref:System.Windows.Forms.Control.BackColor%2A>Özelliği, Etiketler ve radyo düğmeleri gibi içerilen denetimlerin arka plan rengini ayarlar. <xref:System.Windows.Forms.Control.BackgroundImage%2A>Özellik ayarlanmamışsa, <xref:System.Windows.Forms.Control.BackColor%2A> seçim tüm Panelin tamamını dolduracaktır. <xref:System.Windows.Forms.Control.BackgroundImage%2A>Özellik ayarlandıysa, görüntü içerilen denetimlerin arkasında görüntülenir.  
  
### <a name="to-set-the-background-programmatically"></a>Arka planı programlı olarak ayarlamak için  
  
1. Panelin <xref:System.Windows.Forms.Control.BackColor%2A> özelliğini, türünde bir değer olarak ayarlayın <xref:System.Drawing.Color?displayProperty=nameWithType> .  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. <xref:System.Windows.Forms.Control.BackgroundImage%2A>Sınıfının yöntemini kullanarak bölmenin özelliğini ayarlayın <xref:System.Drawing.Image.FromFile%2A> <xref:System.Drawing.Image?displayProperty=nameWithType> .  
  
    ```vb  
    ' You should replace the bolded image
    ' in the sample below with an image of your own choosing.  
    Panel1.BackgroundImage = Image.FromFile _  
        (System.Environment.GetFolderPath _  
        (System.Environment.SpecialFolder.Personal) _  
        & "\Image.gif")  
    ```  
  
    ```csharp  
    // You should replace the bolded image
    // in the sample below with an image of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    panel1.BackgroundImage = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    ```  
  
    ```cpp  
    // You should replace the bolded image
    // in the sample below with an image of your own choosing.  
    panel1->BackgroundImage = Image::FromFile(String::Concat(  
       System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\Image.gif"));  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Panel Denetimi](panel-control-windows-forms.md)
- [Panel Denetimine Genel Bakış](panel-control-overview-windows-forms.md)
