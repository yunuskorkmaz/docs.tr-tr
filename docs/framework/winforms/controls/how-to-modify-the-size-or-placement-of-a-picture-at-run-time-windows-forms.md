---
title: 'Nasıl yapılır: Çalışma Zamanında Resmin Boyutunu veya Konumunu Değiştirme (Windows Forms)'
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
ms.openlocfilehash: 9e6e114e0a9d7e5e9c17ba21ef941703cd108784
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534780"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a><span data-ttu-id="e3527-102">Nasıl yapılır: Çalışma Zamanında Resmin Boyutunu veya Konumunu Değiştirme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e3527-102">How to: Modify the Size or Placement of a Picture at Run Time (Windows Forms)</span></span>
<span data-ttu-id="e3527-103">Windows Forms kullanırsanız <xref:System.Windows.Forms.PictureBox> denetim bir form üzerinde ayarladığınız <xref:System.Windows.Forms.PictureBox.SizeMode%2A> özelliği için:</span><span class="sxs-lookup"><span data-stu-id="e3527-103">If you use the Windows Forms <xref:System.Windows.Forms.PictureBox> control on a form, you can set the <xref:System.Windows.Forms.PictureBox.SizeMode%2A> property on it to:</span></span>  
  
-   <span data-ttu-id="e3527-104">Resmin sol üst köşedeki denetimin sol üst köşedeki ile hizalayın</span><span class="sxs-lookup"><span data-stu-id="e3527-104">Align the picture's upper left corner with the control's upper left corner</span></span>  
  
-   <span data-ttu-id="e3527-105">Merkezi Denetim içindeki resmi</span><span class="sxs-lookup"><span data-stu-id="e3527-105">Center the picture within the control</span></span>  
  
-   <span data-ttu-id="e3527-106">Görüntülediği resim uymak için denetimi boyutunu ayarlama</span><span class="sxs-lookup"><span data-stu-id="e3527-106">Adjust the size of the control to fit the picture it displays</span></span>  
  
-   <span data-ttu-id="e3527-107">Denetim uyacak şekilde görüntüler herhangi bir resmi uzatma</span><span class="sxs-lookup"><span data-stu-id="e3527-107">Stretch any picture it displays to fit the control</span></span>  
  
 <span data-ttu-id="e3527-108">Bir resmi (özellikle bir bit eşlem biçimi) uzatma görüntü kalitesini kaybına üretebilir.</span><span class="sxs-lookup"><span data-stu-id="e3527-108">Stretching a picture (especially one in bitmap format) can produce a loss in image quality.</span></span> <span data-ttu-id="e3527-109">Çalışma zamanında resimleri çizim için grafik yönergeleri listeleridir, meta dosyaları, bit eşlemler daha uzatma için daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="e3527-109">Metafiles, which are lists of graphics instructions for drawing images at run time, are better suited for stretching than bitmaps are.</span></span>  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a><span data-ttu-id="e3527-110">Çalışma zamanında SizeMode özelliğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e3527-110">To set the SizeMode property at run time</span></span>  
  
1.  <span data-ttu-id="e3527-111">Ayarlama <xref:System.Windows.Forms.PictureBox.SizeMode%2A> için <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (varsayılan), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, veya <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span><span class="sxs-lookup"><span data-stu-id="e3527-111">Set <xref:System.Windows.Forms.PictureBox.SizeMode%2A> to <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (the default), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, or <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span></span> <span data-ttu-id="e3527-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal> Görüntü denetimin sol üst köşede yerleştirilir anlamına gelir; Görüntü Denetim daha büyükse, alt ve sağ kenarları kırpılır.</span><span class="sxs-lookup"><span data-stu-id="e3527-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal> means that the image is placed in the control's upper-left corner; if the image is larger than the control, its lower and right edges are clipped.</span></span> <span data-ttu-id="e3527-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> görüntü denetim içinde ortalanır anlamına gelir; Görüntü Denetim daha büyükse resmin dış kenarları kırpılır.</span><span class="sxs-lookup"><span data-stu-id="e3527-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> means that the image is centered within the control; if the image is larger than the control, the picture's outside edges are clipped.</span></span> <span data-ttu-id="e3527-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> Denetimin boyutunu görüntü boyutuna ayarlanır anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e3527-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> means that the size of the control is adjusted to the size of the image.</span></span> <span data-ttu-id="e3527-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> geriye doğru olduğundan ve görüntünün boyutuna denetimi boyutuna ayarlanır anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e3527-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> is the reverse, and means that the size of the image is adjusted to the size of the control.</span></span>  
  
     <span data-ttu-id="e3527-116">Aşağıdaki örnekte görüntüsünün konumunu ayarlayın Belgelerim klasörünü yoludur.</span><span class="sxs-lookup"><span data-stu-id="e3527-116">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="e3527-117">Windows işletim sistemi çalıştıran bilgisayarların çoğu bu dizin içerdiğini varsayar çünkü bu, gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e3527-117">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="e3527-118">Bu, güvenli bir şekilde uygulamayı çalıştırmak minimum sistem erişim düzeyleri olan kullanıcılar da sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3527-118">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="e3527-119">Aşağıdaki örnek bir formla varsayar bir <xref:System.Windows.Forms.PictureBox> denetimi zaten eklendi.</span><span class="sxs-lookup"><span data-stu-id="e3527-119">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e3527-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e3527-120">See Also</span></span>  
 <xref:System.Windows.Forms.PictureBox>  
 [<span data-ttu-id="e3527-121">Nasıl yapılır: Tasarımcıyı Kullanarak Resim Yükleme</span><span class="sxs-lookup"><span data-stu-id="e3527-121">How to: Load a Picture Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)  
 [<span data-ttu-id="e3527-122">PictureBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e3527-122">PictureBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [<span data-ttu-id="e3527-123">Nasıl yapılır: Çalışma Zamanında Resimleri Ayarlama</span><span class="sxs-lookup"><span data-stu-id="e3527-123">How to: Set Pictures at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)  
 [<span data-ttu-id="e3527-124">PictureBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="e3527-124">PictureBox Control</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
