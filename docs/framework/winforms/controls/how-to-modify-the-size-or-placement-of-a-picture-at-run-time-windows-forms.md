---
title: 'Nasıl yapılır: Çalışma zamanında (Windows Forms) boyutunu veya bir resim yerleşimini Değiştir'
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
ms.openlocfilehash: d0a86d7fe53dba3da6bd63587561f82877bc2f06
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59328341"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a><span data-ttu-id="3749e-102">Nasıl yapılır: Çalışma zamanında (Windows Forms) boyutunu veya bir resim yerleşimini Değiştir</span><span class="sxs-lookup"><span data-stu-id="3749e-102">How to: Modify the Size or Placement of a Picture at Run Time (Windows Forms)</span></span>
<span data-ttu-id="3749e-103">Windows Forms kullanırsanız <xref:System.Windows.Forms.PictureBox> denetimi bir form üzerinde ayarladığınız <xref:System.Windows.Forms.PictureBox.SizeMode%2A> özelliği için:</span><span class="sxs-lookup"><span data-stu-id="3749e-103">If you use the Windows Forms <xref:System.Windows.Forms.PictureBox> control on a form, you can set the <xref:System.Windows.Forms.PictureBox.SizeMode%2A> property on it to:</span></span>  
  
-   <span data-ttu-id="3749e-104">Resmin sol üst köşesinde denetimin sol üst köşesinde ile Hizala</span><span class="sxs-lookup"><span data-stu-id="3749e-104">Align the picture's upper left corner with the control's upper left corner</span></span>  
  
-   <span data-ttu-id="3749e-105">Merkezi Denetim içindeki resmi</span><span class="sxs-lookup"><span data-stu-id="3749e-105">Center the picture within the control</span></span>  
  
-   <span data-ttu-id="3749e-106">Denetimin görüntülediği resmi uyacak şekilde boyutu değiştirin</span><span class="sxs-lookup"><span data-stu-id="3749e-106">Adjust the size of the control to fit the picture it displays</span></span>  
  
-   <span data-ttu-id="3749e-107">Denetime sığması için görüntüler herhangi bir resmi Uzat</span><span class="sxs-lookup"><span data-stu-id="3749e-107">Stretch any picture it displays to fit the control</span></span>  
  
 <span data-ttu-id="3749e-108">Bir resim (özellikle bir bit eşlem biçimi) uzatma görüntü kalitesini kaybına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="3749e-108">Stretching a picture (especially one in bitmap format) can produce a loss in image quality.</span></span> <span data-ttu-id="3749e-109">Çalışma zamanında resimleri çizim için grafik yönergeleri listeleridir, meta dosyaları, bit eşlemler daha uzatma için daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="3749e-109">Metafiles, which are lists of graphics instructions for drawing images at run time, are better suited for stretching than bitmaps are.</span></span>  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a><span data-ttu-id="3749e-110">Çalışma zamanında SizeMode özelliğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="3749e-110">To set the SizeMode property at run time</span></span>  
  
1. <span data-ttu-id="3749e-111">Ayarlama <xref:System.Windows.Forms.PictureBox.SizeMode%2A> için <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (varsayılan), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, veya <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span><span class="sxs-lookup"><span data-stu-id="3749e-111">Set <xref:System.Windows.Forms.PictureBox.SizeMode%2A> to <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (the default), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, or <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span></span> <span data-ttu-id="3749e-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal> Görüntü denetimin sol üst köşedeki yerleştirilir anlamına gelir; görüntü denetimi büyükse, kendi alt ve sağ kenarları kırpılır.</span><span class="sxs-lookup"><span data-stu-id="3749e-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal> means that the image is placed in the control's upper-left corner; if the image is larger than the control, its lower and right edges are clipped.</span></span> <span data-ttu-id="3749e-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> görüntü denetimi içinde ortalanır anlamına gelir; görüntü denetimi büyükse, resmin dış kenarları kırpılır.</span><span class="sxs-lookup"><span data-stu-id="3749e-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> means that the image is centered within the control; if the image is larger than the control, the picture's outside edges are clipped.</span></span> <span data-ttu-id="3749e-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> Denetimin boyutunu görüntü boyutuna ayarlanır anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3749e-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> means that the size of the control is adjusted to the size of the image.</span></span> <span data-ttu-id="3749e-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> geriye doğru olduğundan ve görüntünün boyutu denetimin boyutuna ayarlanır anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3749e-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> is the reverse, and means that the size of the image is adjusted to the size of the control.</span></span>  
  
     <span data-ttu-id="3749e-116">Aşağıdaki örnekte, görüntüsünün konumunu ayarlayın Belgelerim klasörünü yoludur.</span><span class="sxs-lookup"><span data-stu-id="3749e-116">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="3749e-117">Windows işletim sistemi çalıştırılan bilgisayarların çoğu bu dizin içerdiğini varsayar çünkü bu, gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3749e-117">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="3749e-118">Bu, güvenli bir şekilde uygulamayı çalıştırmak minimum sistem erişim düzeylerine sahip kullanıcılar da sağlar.</span><span class="sxs-lookup"><span data-stu-id="3749e-118">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="3749e-119">Aşağıdaki örnekte bir form varsayar bir <xref:System.Windows.Forms.PictureBox> denetim zaten eklendi.</span><span class="sxs-lookup"><span data-stu-id="3749e-119">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3749e-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3749e-120">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="3749e-121">Nasıl yapılır: Tasarımcıyı kullanarak resim yükleme</span><span class="sxs-lookup"><span data-stu-id="3749e-121">How to: Load a Picture Using the Designer</span></span>](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="3749e-122">PictureBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3749e-122">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="3749e-123">Nasıl yapılır: Çalışma zamanında resimleri ayarlama</span><span class="sxs-lookup"><span data-stu-id="3749e-123">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="3749e-124">PictureBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="3749e-124">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
