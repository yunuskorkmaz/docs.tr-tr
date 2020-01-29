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
ms.openlocfilehash: 9bb094ce0b7945f23a2e9b8614e56c9492d5f832
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736029"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a><span data-ttu-id="de46f-102">Nasıl yapılır: Çalışma Zamanında Resmin Boyutunu veya Konumunu Değiştirme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="de46f-102">How to: Modify the Size or Placement of a Picture at Run Time (Windows Forms)</span></span>
<span data-ttu-id="de46f-103">Bir form üzerinde Windows Forms <xref:System.Windows.Forms.PictureBox> denetimini kullanıyorsanız, üzerinde <xref:System.Windows.Forms.PictureBox.SizeMode%2A> özelliğini şu şekilde ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="de46f-103">If you use the Windows Forms <xref:System.Windows.Forms.PictureBox> control on a form, you can set the <xref:System.Windows.Forms.PictureBox.SizeMode%2A> property on it to:</span></span>  
  
- <span data-ttu-id="de46f-104">Resmin sol üst köşesini denetimin sol üst köşesinden hizalayın</span><span class="sxs-lookup"><span data-stu-id="de46f-104">Align the picture's upper left corner with the control's upper left corner</span></span>  
  
- <span data-ttu-id="de46f-105">Denetimin içindeki resmi Ortala</span><span class="sxs-lookup"><span data-stu-id="de46f-105">Center the picture within the control</span></span>  
  
- <span data-ttu-id="de46f-106">Denetimin boyutunu gösterdiği resme uyacak şekilde ayarlayın</span><span class="sxs-lookup"><span data-stu-id="de46f-106">Adjust the size of the control to fit the picture it displays</span></span>  
  
- <span data-ttu-id="de46f-107">Denetimin sığması için görüntülediği tüm resimleri uzat</span><span class="sxs-lookup"><span data-stu-id="de46f-107">Stretch any picture it displays to fit the control</span></span>  
  
 <span data-ttu-id="de46f-108">Bir resmi uzatma (özellikle bit eşlem biçiminde), görüntü kalitesinde bir kayıp üretebilir.</span><span class="sxs-lookup"><span data-stu-id="de46f-108">Stretching a picture (especially one in bitmap format) can produce a loss in image quality.</span></span> <span data-ttu-id="de46f-109">Çalışma zamanında görüntülerin çizilmesine yönelik grafik yönergelerinin listesi olan meta dosyalar, bit eşlemlerden uzama için daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="de46f-109">Metafiles, which are lists of graphics instructions for drawing images at run time, are better suited for stretching than bitmaps are.</span></span>  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a><span data-ttu-id="de46f-110">Çalışma zamanında SizeMode özelliğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="de46f-110">To set the SizeMode property at run time</span></span>  
  
1. <span data-ttu-id="de46f-111"><xref:System.Windows.Forms.PictureBox.SizeMode%2A> <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (varsayılan), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>veya <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="de46f-111">Set <xref:System.Windows.Forms.PictureBox.SizeMode%2A> to <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (the default), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, or <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span></span> <span data-ttu-id="de46f-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal>, görüntünün denetimin sol üst köşesine yerleştirildiği anlamına gelir; görüntü denetimden büyükse, alt ve sağ kenarları kırpılır.</span><span class="sxs-lookup"><span data-stu-id="de46f-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal> means that the image is placed in the control's upper-left corner; if the image is larger than the control, its lower and right edges are clipped.</span></span> <span data-ttu-id="de46f-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, görüntünün denetimin içinde ortalanmasıdır; görüntü denetimden büyükse, resmin dış kenarları kırpılır.</span><span class="sxs-lookup"><span data-stu-id="de46f-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> means that the image is centered within the control; if the image is larger than the control, the picture's outside edges are clipped.</span></span> <span data-ttu-id="de46f-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, denetimin boyutunun görüntünün boyutuna ayarlandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="de46f-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> means that the size of the control is adjusted to the size of the image.</span></span> <span data-ttu-id="de46f-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> ters ve görüntünün boyutunun denetimin boyutuna ayarlandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="de46f-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> is the reverse, and means that the size of the image is adjusted to the size of the control.</span></span>  
  
     <span data-ttu-id="de46f-116">Aşağıdaki örnekte, görüntü konumu için ayarlanan yol Belgelerim klasörüdür.</span><span class="sxs-lookup"><span data-stu-id="de46f-116">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="de46f-117">Bu, Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu dizini içerdiğini varsaydığı için yapılır.</span><span class="sxs-lookup"><span data-stu-id="de46f-117">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="de46f-118">Bu Ayrıca, en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenle çalıştırmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="de46f-118">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="de46f-119">Aşağıdaki örnekte, <xref:System.Windows.Forms.PictureBox> denetimi zaten eklenmiş bir form varsayılır.</span><span class="sxs-lookup"><span data-stu-id="de46f-119">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="de46f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de46f-120">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="de46f-121">Nasıl yapılır: Tasarımcıyı Kullanarak Resim Yükleme</span><span class="sxs-lookup"><span data-stu-id="de46f-121">How to: Load a Picture Using the Designer</span></span>](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="de46f-122">PictureBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="de46f-122">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="de46f-123">Nasıl yapılır: Çalışma Zamanında Resimleri Ayarlama</span><span class="sxs-lookup"><span data-stu-id="de46f-123">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="de46f-124">PictureBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="de46f-124">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
