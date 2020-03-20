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
ms.openlocfilehash: cd599ac7e07b5210f8bcff1ffbc76b3d9ee563d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182113"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a><span data-ttu-id="fa565-102">Nasıl yapılır: Çalışma Zamanında Resimleri Ayarlama (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="fa565-102">How to: Set Pictures at Run Time (Windows Forms)</span></span>
<span data-ttu-id="fa565-103">Windows Forms <xref:System.Windows.Forms.PictureBox> denetimi tarafından görüntülenen görüntüyü programlı olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa565-103">You can programmatically set the image displayed by a Windows Forms <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-set-a-picture-programmatically"></a><span data-ttu-id="fa565-104">Resmi programlı olarak ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="fa565-104">To set a picture programmatically</span></span>  
  
- <span data-ttu-id="fa565-105">Sınıfın <xref:System.Windows.Forms.PictureBox.Image%2A> yöntemini <xref:System.Drawing.Image.FromFile%2A> kullanarak özelliği ayarlayın. <xref:System.Drawing.Image></span><span class="sxs-lookup"><span data-stu-id="fa565-105">Set the <xref:System.Windows.Forms.PictureBox.Image%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image> class.</span></span>  
  
     <span data-ttu-id="fa565-106">Aşağıdaki örnekte, görüntünün konumu için ayarlanan yol Belgelerim klasörüdür.</span><span class="sxs-lookup"><span data-stu-id="fa565-106">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="fa565-107">Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu dizini içereceğini varsayabileceğinizden, bu işlem yapılır.</span><span class="sxs-lookup"><span data-stu-id="fa565-107">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="fa565-108">Bu aynı zamanda en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenli bir şekilde çalıştırmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fa565-108">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="fa565-109">Aşağıdaki <xref:System.Windows.Forms.PictureBox> örnekte, denetimzaten eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="fa565-109">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
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
  
### <a name="to-clear-a-graphic"></a><span data-ttu-id="fa565-110">Bir grafiği temizlemek için</span><span class="sxs-lookup"><span data-stu-id="fa565-110">To clear a graphic</span></span>  
  
- <span data-ttu-id="fa565-111">Önce görüntü tarafından kullanılan belleği bırakın ve ardından grafiği temizleyin.</span><span class="sxs-lookup"><span data-stu-id="fa565-111">First, release the memory being used by the image, and then clear the graphic.</span></span> <span data-ttu-id="fa565-112">Bellek yönetimi bir sorun haline gelirse çöp toplama daha sonra bellek kadar serbest olacaktır.</span><span class="sxs-lookup"><span data-stu-id="fa565-112">Garbage collection will free up the memory later if memory management becomes a problem.</span></span>  
  
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
    > <span data-ttu-id="fa565-113"><xref:System.Drawing.Image.Dispose%2A> Yöntemi neden bu şekilde kullanmanız gerektiği hakkında daha fazla bilgi için, [Yönetilmeyen Kaynakları Temizleme'ye](../../../standard/garbage-collection/unmanaged.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="fa565-113">For more information on why you should use the <xref:System.Drawing.Image.Dispose%2A> method in this way, see [Cleaning Up Unmanaged Resources](../../../standard/garbage-collection/unmanaged.md).</span></span>  
  
     <span data-ttu-id="fa565-114">Bu kod, bir grafik tasarım zamanında denetime yüklense bile görüntüyü temizler.</span><span class="sxs-lookup"><span data-stu-id="fa565-114">This code will clear the image even if a graphic was loaded into the control at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa565-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa565-115">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [<span data-ttu-id="fa565-116">PictureBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fa565-116">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="fa565-117">Nasıl yapılır: Tasarımcıyı Kullanarak Resim Yükleme</span><span class="sxs-lookup"><span data-stu-id="fa565-117">How to: Load a Picture Using the Designer</span></span>](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="fa565-118">Nasıl yapılır: Çalışma Zamanında Resmin Boyutunu veya Konumunu Değiştirme</span><span class="sxs-lookup"><span data-stu-id="fa565-118">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="fa565-119">PictureBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="fa565-119">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
