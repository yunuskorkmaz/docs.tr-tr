---
title: 'Nasıl yapılır: Çalışma zamanında resimleri ayarlama (Windows Forms)'
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
ms.openlocfilehash: 99d78a275c8ad8f55d9b0832a794545b65da7e20
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917523"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a><span data-ttu-id="52401-102">Nasıl yapılır: Çalışma zamanında resimleri ayarlama (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="52401-102">How to: Set Pictures at Run Time (Windows Forms)</span></span>
<span data-ttu-id="52401-103">Windows Forms <xref:System.Windows.Forms.PictureBox> denetimi tarafından görünen görüntüyü programlı bir şekilde ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52401-103">You can programmatically set the image displayed by a Windows Forms <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-set-a-picture-programmatically"></a><span data-ttu-id="52401-104">Bir resmi programlı bir şekilde ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="52401-104">To set a picture programmatically</span></span>  
  
- <span data-ttu-id="52401-105"><xref:System.Windows.Forms.PictureBox.Image%2A> Sınıfının yöntemini<xref:System.Drawing.Image.FromFile%2A>kullanaraközelliğiayarlayın. <xref:System.Drawing.Image></span><span class="sxs-lookup"><span data-stu-id="52401-105">Set the <xref:System.Windows.Forms.PictureBox.Image%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image> class.</span></span>  
  
     <span data-ttu-id="52401-106">Aşağıdaki örnekte, görüntü konumu için ayarlanan yol Belgelerim klasörüdür.</span><span class="sxs-lookup"><span data-stu-id="52401-106">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="52401-107">Bu, Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu dizini içerdiğini varsaydığı için yapılır.</span><span class="sxs-lookup"><span data-stu-id="52401-107">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="52401-108">Bu Ayrıca, en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenle çalıştırmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="52401-108">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="52401-109">Aşağıdaki örnekte, bir <xref:System.Windows.Forms.PictureBox> denetimin zaten eklendiği bir form varsayılır.</span><span class="sxs-lookup"><span data-stu-id="52401-109">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
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
  
### <a name="to-clear-a-graphic"></a><span data-ttu-id="52401-110">Grafiği temizlemek için</span><span class="sxs-lookup"><span data-stu-id="52401-110">To clear a graphic</span></span>  
  
- <span data-ttu-id="52401-111">İlk olarak, görüntü tarafından kullanılan belleği serbest bırakın ve grafiği temizleyin.</span><span class="sxs-lookup"><span data-stu-id="52401-111">First, release the memory being used by the image, and then clear the graphic.</span></span> <span data-ttu-id="52401-112">Bellek yönetimi bir sorun haline gelirse çöp toplama belleği daha sonra boşaltacaktır.</span><span class="sxs-lookup"><span data-stu-id="52401-112">Garbage collection will free up the memory later if memory management becomes a problem.</span></span>  
  
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
    > <span data-ttu-id="52401-113"><xref:System.Drawing.Image.Dispose%2A> Yöntemi bu şekilde nasıl kullanmanız gerektiği hakkında daha fazla bilgi için bkz. [yönetilmeyen kaynakları temizleme](../../../standard/garbage-collection/unmanaged.md).</span><span class="sxs-lookup"><span data-stu-id="52401-113">For more information on why you should use the <xref:System.Drawing.Image.Dispose%2A> method in this way, see [Cleaning Up Unmanaged Resources](../../../standard/garbage-collection/unmanaged.md).</span></span>  
  
     <span data-ttu-id="52401-114">Bu kod, tasarım zamanında denetime bir grafik yüklense bile görüntüyü temizler.</span><span class="sxs-lookup"><span data-stu-id="52401-114">This code will clear the image even if a graphic was loaded into the control at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52401-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52401-115">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [<span data-ttu-id="52401-116">PictureBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="52401-116">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="52401-117">Nasıl yapılır: Tasarımcıyı kullanarak resim yükleme</span><span class="sxs-lookup"><span data-stu-id="52401-117">How to: Load a Picture Using the Designer</span></span>](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="52401-118">Nasıl yapılır: Çalışma zamanında bir resmin boyutunu veya yerleşimini değiştirme</span><span class="sxs-lookup"><span data-stu-id="52401-118">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="52401-119">PictureBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="52401-119">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
