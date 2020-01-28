---
title: 'Nasıl yapılır: Çalışma Zamanında Resimleri Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pictures [Windows Forms], setting display
- examples [Windows Forms], PictureBox control
- bitmaps [Windows Forms], displaying in PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding images
- images [Windows Forms], adding with PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 18ca41d0-68a5-4660-985e-a6c1fbc01d76
ms.openlocfilehash: bd0509c05fd9c1cfc0c631fcd613c64d20296f6b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746740"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a><span data-ttu-id="28789-102">Nasıl yapılır: Çalışma Zamanında Resimleri Ayarlama (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="28789-102">How to: Set Pictures at Run Time (Windows Forms)</span></span>
<span data-ttu-id="28789-103">Bir Windows Forms <xref:System.Windows.Forms.PictureBox> denetimi tarafından görünen görüntüyü programlı bir şekilde ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28789-103">You can programmatically set the image displayed by a Windows Forms <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-set-a-picture-programmatically"></a><span data-ttu-id="28789-104">Bir resmi programlı bir şekilde ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="28789-104">To set a picture programmatically</span></span>  
  
- <span data-ttu-id="28789-105"><xref:System.Drawing.Image> sınıfının <xref:System.Drawing.Image.FromFile%2A> yöntemini kullanarak <xref:System.Windows.Forms.PictureBox.Image%2A> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="28789-105">Set the <xref:System.Windows.Forms.PictureBox.Image%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image> class.</span></span>  
  
     <span data-ttu-id="28789-106">Aşağıdaki örnekte, görüntü konumu için ayarlanan yol Belgelerim klasörüdür.</span><span class="sxs-lookup"><span data-stu-id="28789-106">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="28789-107">Bu, Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu dizini içerdiğini varsaydığı için yapılır.</span><span class="sxs-lookup"><span data-stu-id="28789-107">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="28789-108">Bu Ayrıca, en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenle çalıştırmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="28789-108">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="28789-109">Aşağıdaki örnekte, <xref:System.Windows.Forms.PictureBox> denetimi zaten eklenmiş bir form varsayılır.</span><span class="sxs-lookup"><span data-stu-id="28789-109">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
    ```vb  
    Private Sub LoadNewPict()  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadNewPict(){  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    }  
    ```  
  
    ```cpp  
    private:  
       void LoadNewPict()  
       {  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
### <a name="to-clear-a-graphic"></a><span data-ttu-id="28789-110">Grafiği temizlemek için</span><span class="sxs-lookup"><span data-stu-id="28789-110">To clear a graphic</span></span>  
  
- <span data-ttu-id="28789-111">İlk olarak, görüntü tarafından kullanılan belleği serbest bırakın ve grafiği temizleyin.</span><span class="sxs-lookup"><span data-stu-id="28789-111">First, release the memory being used by the image, and then clear the graphic.</span></span> <span data-ttu-id="28789-112">Bellek yönetimi bir sorun haline gelirse çöp toplama belleği daha sonra boşaltacaktır.</span><span class="sxs-lookup"><span data-stu-id="28789-112">Garbage collection will free up the memory later if memory management becomes a problem.</span></span>  
  
    ```vb  
    If Not (PictureBox1.Image Is Nothing) Then  
       PictureBox1.Image.Dispose()  
       PictureBox1.Image = Nothing  
    End If  
    ```  
  
    ```csharp  
    if (pictureBox1.Image != null)   
    {  
       pictureBox1.Image.Dispose();  
       pictureBox1.Image = null;  
    }  
    ```  
  
    ```cpp  
    if (pictureBox1->Image != nullptr)  
    {  
       pictureBox1->Image->Dispose();  
       pictureBox1->Image = nullptr;  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="28789-113"><xref:System.Drawing.Image.Dispose%2A> yöntemini bu şekilde nasıl kullanmanız gerektiği hakkında daha fazla bilgi için bkz. [yönetilmeyen kaynakları temizleme](../../../standard/garbage-collection/unmanaged.md).</span><span class="sxs-lookup"><span data-stu-id="28789-113">For more information on why you should use the <xref:System.Drawing.Image.Dispose%2A> method in this way, see [Cleaning Up Unmanaged Resources](../../../standard/garbage-collection/unmanaged.md).</span></span>  
  
     <span data-ttu-id="28789-114">Bu kod, tasarım zamanında denetime bir grafik yüklense bile görüntüyü temizler.</span><span class="sxs-lookup"><span data-stu-id="28789-114">This code will clear the image even if a graphic was loaded into the control at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28789-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28789-115">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [<span data-ttu-id="28789-116">PictureBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="28789-116">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="28789-117">Nasıl yapılır: Tasarımcıyı Kullanarak Resim Yükleme</span><span class="sxs-lookup"><span data-stu-id="28789-117">How to: Load a Picture Using the Designer</span></span>](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="28789-118">Nasıl yapılır: Çalışma Zamanında Resmin Boyutunu veya Konumunu Değiştirme</span><span class="sxs-lookup"><span data-stu-id="28789-118">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="28789-119">PictureBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="28789-119">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
