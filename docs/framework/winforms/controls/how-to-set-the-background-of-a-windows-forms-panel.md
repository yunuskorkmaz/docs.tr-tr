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
ms.openlocfilehash: ba2619354403793aea7ca15d43649da9637079a6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744735"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a>Nasıl yapılır: Windows Forms Panelinin Arka Planını Ayarlama
Bir Windows Forms <xref:System.Windows.Forms.Panel> denetimi hem arka plan rengini hem de arka plan görüntüsünü görüntüleyebilir. <xref:System.Windows.Forms.Control.BackColor%2A> özelliği, Etiketler ve radyo düğmeleri gibi içerilen denetimlerin arka plan rengini ayarlar. <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği ayarlanmamışsa, <xref:System.Windows.Forms.Control.BackColor%2A> seçimi Panelin tamamını dolduracaktır. <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği ayarlandıysa, görüntü içerilen denetimlerin arkasında görüntülenir.  
  
### <a name="to-set-the-background-programmatically"></a>Arka planı programlı olarak ayarlamak için  
  
1. Panelin <xref:System.Windows.Forms.Control.BackColor%2A> özelliğini <xref:System.Drawing.Color?displayProperty=nameWithType>türünde bir değere ayarlayın.  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. <xref:System.Drawing.Image?displayProperty=nameWithType> sınıfının <xref:System.Drawing.Image.FromFile%2A> yöntemini kullanarak bölmenin <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliğini ayarlayın.  
  
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
