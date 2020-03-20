---
title: 'Nasıl yapılır: Çalışma Zamanında Resmin Boyutunu veya Konumunu Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], controlling placement in PictureBox control [Windows Forms]
- examples [Windows Forms], PictureBox control
- PictureBox control [Windows Forms], picture size and alignment
- pictures [Windows Forms], controlling placement in PictureBox control [Windows Forms]
ms.assetid: d0b332a3-fae2-4891-957c-dc3e17743326
ms.openlocfilehash: fea813d7b9fe585e35b729b8b64e3a5f414ef76d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141972"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a><span data-ttu-id="f9902-102">Nasıl yapılır: Çalışma Zamanında Resmin Boyutunu veya Konumunu Değiştirme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="f9902-102">How to: Modify the Size or Placement of a Picture at Run Time (Windows Forms)</span></span>
<span data-ttu-id="f9902-103">Bir formüzerinde Windows <xref:System.Windows.Forms.PictureBox> Forms denetimini kullanırsanız, bu formdaki <xref:System.Windows.Forms.PictureBox.SizeMode%2A> özelliği şu şekilde ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f9902-103">If you use the Windows Forms <xref:System.Windows.Forms.PictureBox> control on a form, you can set the <xref:System.Windows.Forms.PictureBox.SizeMode%2A> property on it to:</span></span>  
  
- <span data-ttu-id="f9902-104">Resmin sol üst köşesini kontrolün sol üst köşesiyle hizala</span><span class="sxs-lookup"><span data-stu-id="f9902-104">Align the picture's upper left corner with the control's upper left corner</span></span>  
  
- <span data-ttu-id="f9902-105">Resmi denetim içinde ortala</span><span class="sxs-lookup"><span data-stu-id="f9902-105">Center the picture within the control</span></span>  
  
- <span data-ttu-id="f9902-106">Denetimin boyutunu görüntülenebilmek için ayarlama</span><span class="sxs-lookup"><span data-stu-id="f9902-106">Adjust the size of the control to fit the picture it displays</span></span>  
  
- <span data-ttu-id="f9902-107">Görüntülenedeki herhangi bir resmi denetime uyacak şekilde esnetin</span><span class="sxs-lookup"><span data-stu-id="f9902-107">Stretch any picture it displays to fit the control</span></span>  
  
 <span data-ttu-id="f9902-108">Bir resmi germe (özellikle bitmap biçiminde) görüntü kalitesinde bir kayıp yaratabilir.</span><span class="sxs-lookup"><span data-stu-id="f9902-108">Stretching a picture (especially one in bitmap format) can produce a loss in image quality.</span></span> <span data-ttu-id="f9902-109">Çalışma zamanında resim çizmek için grafik yönergeleri listeleri olan metafiles, bit eşlemler daha germe için daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="f9902-109">Metafiles, which are lists of graphics instructions for drawing images at run time, are better suited for stretching than bitmaps are.</span></span>  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a><span data-ttu-id="f9902-110">SizeMode özelliğini çalışma zamanında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="f9902-110">To set the SizeMode property at run time</span></span>  
  
1. <span data-ttu-id="f9902-111"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (varsayılan), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> <xref:System.Windows.Forms.PictureBox.SizeMode%2A> , , <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>veya <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span><span class="sxs-lookup"><span data-stu-id="f9902-111">Set <xref:System.Windows.Forms.PictureBox.SizeMode%2A> to <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (the default), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, or <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span></span> <span data-ttu-id="f9902-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal>görüntünün kontrolün sol üst köşesine yerleştirildiği anlamına gelir; görüntü denetimden daha büyükse, alt ve sağ kenarları kırpılır.</span><span class="sxs-lookup"><span data-stu-id="f9902-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal> means that the image is placed in the control's upper-left corner; if the image is larger than the control, its lower and right edges are clipped.</span></span> <span data-ttu-id="f9902-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>görüntünün denetim içinde ortalanmış olduğu anlamına gelir; görüntü denetimden daha büyükse, resmin dış kenarları kırpılır.</span><span class="sxs-lookup"><span data-stu-id="f9902-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> means that the image is centered within the control; if the image is larger than the control, the picture's outside edges are clipped.</span></span> <span data-ttu-id="f9902-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>denetimboyutunu görüntünün boyutuna ayarlanır anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f9902-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> means that the size of the control is adjusted to the size of the image.</span></span> <span data-ttu-id="f9902-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>tersidir ve görüntünün boyutunun denetimboyutuna ayarlanması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f9902-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> is the reverse, and means that the size of the image is adjusted to the size of the control.</span></span>  
  
     <span data-ttu-id="f9902-116">Aşağıdaki örnekte, görüntünün konumu için ayarlanan yol Belgelerim klasörüdür.</span><span class="sxs-lookup"><span data-stu-id="f9902-116">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="f9902-117">Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu dizini içereceğini varsayabileceğinizden, bu işlem yapılır.</span><span class="sxs-lookup"><span data-stu-id="f9902-117">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="f9902-118">Bu aynı zamanda en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenli bir şekilde çalıştırmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f9902-118">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="f9902-119">Aşağıdaki <xref:System.Windows.Forms.PictureBox> örnekte, denetimzaten eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="f9902-119">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
    ```vb  
    Private Sub StretchPic()  
       ' Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage  
       ' Load the picture into the control.  
       ' You should replace the bold image
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void StretchPic(){  
       // Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage;  
       // Load the picture into the control.  
       // You should replace the bold image
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Image.gif")  
    }  
    ```  
  
    ```cpp  
    private:  
       void StretchPic()  
       {  
          // Stretch the picture to fit the control.  
          pictureBox1->SizeMode = PictureBoxSizeMode::StretchImage;  
          // Load the picture into the control.  
          // You should replace the bold image
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f9902-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9902-120">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="f9902-121">Nasıl yapılır: Tasarımcıyı Kullanarak Resim Yükleme</span><span class="sxs-lookup"><span data-stu-id="f9902-121">How to: Load a Picture Using the Designer</span></span>](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="f9902-122">PictureBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f9902-122">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="f9902-123">Nasıl yapılır: Çalışma Zamanında Resimleri Ayarlama</span><span class="sxs-lookup"><span data-stu-id="f9902-123">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="f9902-124">PictureBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="f9902-124">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
