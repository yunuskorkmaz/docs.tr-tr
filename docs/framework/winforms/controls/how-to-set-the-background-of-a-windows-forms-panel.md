---
title: Bir Panelin Arka Planını Ayarlama
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
ms.openlocfilehash: 36e552475334c25b9d5a6fafb82155c6ebcba266
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182103"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a>Nasıl yapılır: Windows Forms Panelinin Arka Planını Ayarlama
Windows Forms <xref:System.Windows.Forms.Panel> denetimi hem arka plan rengini hem de arka plan görüntüsünü görüntüleyebilir. Özellik, <xref:System.Windows.Forms.Control.BackColor%2A> etiketler ve radyo düğmeleri gibi içerdiği denetimler için arka plan rengini ayarlar. <xref:System.Windows.Forms.Control.BackgroundImage%2A> Özellik ayarlanmazsa, <xref:System.Windows.Forms.Control.BackColor%2A> seçim tüm paneli doldurur. <xref:System.Windows.Forms.Control.BackgroundImage%2A> Özellik ayarlanırsa, görüntü içerdiği denetimlerin arkasında görüntülenir.  
  
### <a name="to-set-the-background-programmatically"></a>Arka planı programlı olarak ayarlamak için  
  
1. Panelin <xref:System.Windows.Forms.Control.BackColor%2A> özelliğini türünde <xref:System.Drawing.Color?displayProperty=nameWithType>bir değere ayarlayın.  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. Sınıfın <xref:System.Windows.Forms.Control.BackgroundImage%2A> <xref:System.Drawing.Image.FromFile%2A> yöntemini kullanarak panelin özelliğini <xref:System.Drawing.Image?displayProperty=nameWithType> ayarlayın.  
  
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
