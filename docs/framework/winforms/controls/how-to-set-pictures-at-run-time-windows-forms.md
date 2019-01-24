---
title: 'Nasıl yapılır: (Windows Forms) çalışma zamanında resimleri ayarlama'
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
ms.openlocfilehash: c7a65bcc65710324a4457c17dd728b4771550c06
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694080"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a><span data-ttu-id="38e9b-102">Nasıl yapılır: (Windows Forms) çalışma zamanında resimleri ayarlama</span><span class="sxs-lookup"><span data-stu-id="38e9b-102">How to: Set Pictures at Run Time (Windows Forms)</span></span>
<span data-ttu-id="38e9b-103">Bir Windows Forms tarafından görüntülenen resmi programla ayarlayabilir miyim <xref:System.Windows.Forms.PictureBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="38e9b-103">You can programmatically set the image displayed by a Windows Forms <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-set-a-picture-programmatically"></a><span data-ttu-id="38e9b-104">Bir resmi program üzerinden ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="38e9b-104">To set a picture programmatically</span></span>  
  
-   <span data-ttu-id="38e9b-105">Ayarlama <xref:System.Windows.Forms.PictureBox.Image%2A> özelliğini kullanarak <xref:System.Drawing.Image.FromFile%2A> yöntemi <xref:System.Drawing.Image> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="38e9b-105">Set the <xref:System.Windows.Forms.PictureBox.Image%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image> class.</span></span>  
  
     <span data-ttu-id="38e9b-106">Aşağıdaki örnekte, görüntüsünün konumunu ayarlayın Belgelerim klasörünü yoludur.</span><span class="sxs-lookup"><span data-stu-id="38e9b-106">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="38e9b-107">Windows işletim sistemi çalıştırılan bilgisayarların çoğu bu dizin içerdiğini varsayar çünkü bu, gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="38e9b-107">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="38e9b-108">Bu, güvenli bir şekilde uygulamayı çalıştırmak minimum sistem erişim düzeylerine sahip kullanıcılar da sağlar.</span><span class="sxs-lookup"><span data-stu-id="38e9b-108">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="38e9b-109">Aşağıdaki örnekte bir form varsayar bir <xref:System.Windows.Forms.PictureBox> denetim zaten eklendi.</span><span class="sxs-lookup"><span data-stu-id="38e9b-109">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
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
  
### <a name="to-clear-a-graphic"></a><span data-ttu-id="38e9b-110">Grafik temizlemek için</span><span class="sxs-lookup"><span data-stu-id="38e9b-110">To clear a graphic</span></span>  
  
-   <span data-ttu-id="38e9b-111">İlk olarak, görüntü tarafından kullanılan belleği serbest ve grafik temizleyin.</span><span class="sxs-lookup"><span data-stu-id="38e9b-111">First, release the memory being used by the image, and then clear the graphic.</span></span> <span data-ttu-id="38e9b-112">Bellek yönetimi, bir sorun olduğunda çöp toplama belleği daha sonra ücretsiz.</span><span class="sxs-lookup"><span data-stu-id="38e9b-112">Garbage collection will free up the memory later if memory management becomes a problem.</span></span>  
  
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
    >  <span data-ttu-id="38e9b-113">Neden hakkında daha fazla bilgi için kullanmalısınız <xref:System.Drawing.Image.Dispose%2A> bkz bu şekilde [Cleaning Up Unmanaged Resources](../../../../docs/standard/garbage-collection/unmanaged.md).</span><span class="sxs-lookup"><span data-stu-id="38e9b-113">For more information on why you should use the <xref:System.Drawing.Image.Dispose%2A> method in this way, see [Cleaning Up Unmanaged Resources](../../../../docs/standard/garbage-collection/unmanaged.md).</span></span>  
  
     <span data-ttu-id="38e9b-114">Grafik tasarım zamanında denetimin içine yüklenen olsa bile bu kodu görüntü temizler.</span><span class="sxs-lookup"><span data-stu-id="38e9b-114">This code will clear the image even if a graphic was loaded into the control at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38e9b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38e9b-115">See also</span></span>
- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [<span data-ttu-id="38e9b-116">PictureBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="38e9b-116">PictureBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="38e9b-117">Nasıl yapılır: Tasarımcıyı kullanarak resim yükleme</span><span class="sxs-lookup"><span data-stu-id="38e9b-117">How to: Load a Picture Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="38e9b-118">Nasıl yapılır: Çalışma zamanında resmin yerleştirme ve boyutunu değiştirme</span><span class="sxs-lookup"><span data-stu-id="38e9b-118">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="38e9b-119">PictureBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="38e9b-119">PictureBox Control</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
