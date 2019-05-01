---
title: 'Nasıl yapılır: Bir Windows Forms panelinin arka planını ayarlama'
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
ms.openlocfilehash: 9336be2aebb10e5c0bd0bf4648cae34a3b5fe7c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013185"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a><span data-ttu-id="7465c-102">Nasıl yapılır: Bir Windows Forms panelinin arka planını ayarlama</span><span class="sxs-lookup"><span data-stu-id="7465c-102">How to: Set the Background of a Windows Forms Panel</span></span>
<span data-ttu-id="7465c-103">Bir Windows Forms <xref:System.Windows.Forms.Panel> denetim arka plan rengi hem de arka plan görüntüsü görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7465c-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="7465c-104"><xref:System.Windows.Forms.Control.BackColor%2A> Özelliği etiketleri ve radyo düğmeleri gibi içerdiği denetimlerle arka plan rengini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7465c-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for the contained controls, such as labels and radio buttons.</span></span> <span data-ttu-id="7465c-105">Varsa <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği ayarlı değil, <xref:System.Windows.Forms.Control.BackColor%2A> seçimi tüm panel doldurur.</span><span class="sxs-lookup"><span data-stu-id="7465c-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill the entire panel.</span></span> <span data-ttu-id="7465c-106">Varsa <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği ayarlanmışsa, görüntünün içerdiği denetimlerle görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7465c-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the contained controls.</span></span>  
  
### <a name="to-set-the-background-programmatically"></a><span data-ttu-id="7465c-107">Arka plan program üzerinden ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="7465c-107">To set the background programmatically</span></span>  
  
1. <span data-ttu-id="7465c-108">Bölmenin ayarlamak <xref:System.Windows.Forms.Control.BackColor%2A> türünde bir değer özelliğini <xref:System.Drawing.Color?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7465c-108">Set the panel's <xref:System.Windows.Forms.Control.BackColor%2A> property to a value of type <xref:System.Drawing.Color?displayProperty=nameWithType>.</span></span>  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. <span data-ttu-id="7465c-109">Bölmenin ayarlamak <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliğini kullanarak <xref:System.Drawing.Image.FromFile%2A> yöntemi <xref:System.Drawing.Image?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7465c-109">Set the panel's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image?displayProperty=nameWithType> class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7465c-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7465c-110">See also</span></span>

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="7465c-111">Panel Denetimi</span><span class="sxs-lookup"><span data-stu-id="7465c-111">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="7465c-112">Panel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7465c-112">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
