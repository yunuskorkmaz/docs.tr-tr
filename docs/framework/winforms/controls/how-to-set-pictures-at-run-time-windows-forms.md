---
title: "Nasıl yapılır: Çalışma Zamanında Resimleri Ayarlama (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 429c0c928d8bff4f837186040288d9447fc18687
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a><span data-ttu-id="6668d-102">Nasıl yapılır: Çalışma Zamanında Resimleri Ayarlama (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="6668d-102">How to: Set Pictures at Run Time (Windows Forms)</span></span>
<span data-ttu-id="6668d-103">Programlı olarak bir Windows Forms tarafından görüntülenen resmi ayarlama <xref:System.Windows.Forms.PictureBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="6668d-103">You can programmatically set the image displayed by a Windows Forms <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-set-a-picture-programmatically"></a><span data-ttu-id="6668d-104">Bir resmi programlı olarak ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="6668d-104">To set a picture programmatically</span></span>  
  
-   <span data-ttu-id="6668d-105">Ayarlama <xref:System.Windows.Forms.PictureBox.Image%2A> özelliğini kullanarak <xref:System.Drawing.Image.FromFile%2A> yöntemi <xref:System.Drawing.Image> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6668d-105">Set the <xref:System.Windows.Forms.PictureBox.Image%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image> class.</span></span>  
  
     <span data-ttu-id="6668d-106">Aşağıdaki örnekte görüntüsünün konumunu ayarlayın Belgelerim klasörünü yoludur.</span><span class="sxs-lookup"><span data-stu-id="6668d-106">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="6668d-107">Windows işletim sistemi çalıştıran bilgisayarların çoğu bu dizin içerdiğini varsayar çünkü bu, gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6668d-107">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="6668d-108">Bu, güvenli bir şekilde uygulamayı çalıştırmak minimum sistem erişim düzeyleri olan kullanıcılar da sağlar.</span><span class="sxs-lookup"><span data-stu-id="6668d-108">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="6668d-109">Aşağıdaki örnek bir formla varsayar bir <xref:System.Windows.Forms.PictureBox> denetimi zaten eklendi.</span><span class="sxs-lookup"><span data-stu-id="6668d-109">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
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
  
### <a name="to-clear-a-graphic"></a><span data-ttu-id="6668d-110">Grafik temizlemek için</span><span class="sxs-lookup"><span data-stu-id="6668d-110">To clear a graphic</span></span>  
  
-   <span data-ttu-id="6668d-111">İlk olarak, görüntü tarafından kullanılan belleği serbest ve grafiğin temizleyin.</span><span class="sxs-lookup"><span data-stu-id="6668d-111">First, release the memory being used by the image, and then clear the graphic.</span></span> <span data-ttu-id="6668d-112">Bellek yönetimi bir sorun olursa çöp toplama belleği daha sonra boş.</span><span class="sxs-lookup"><span data-stu-id="6668d-112">Garbage collection will free up the memory later if memory management becomes a problem.</span></span>  
  
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
    >  <span data-ttu-id="6668d-113">Neden hakkında daha fazla bilgi için kullanmanız gereken <xref:System.Drawing.Image.Dispose%2A> yöntemi bu şekilde bkz [yönetilmeyen kaynakları Temizleme](../../../../docs/standard/garbage-collection/unmanaged.md).</span><span class="sxs-lookup"><span data-stu-id="6668d-113">For more information on why you should use the <xref:System.Drawing.Image.Dispose%2A> method in this way, see [Cleaning Up Unmanaged Resources](../../../../docs/standard/garbage-collection/unmanaged.md).</span></span>  
  
     <span data-ttu-id="6668d-114">Grafik tasarım zamanında denetime yüklendi olsa bile bu kodu görüntü temizleyin.</span><span class="sxs-lookup"><span data-stu-id="6668d-114">This code will clear the image even if a graphic was loaded into the control at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6668d-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6668d-115">See Also</span></span>  
 <xref:System.Windows.Forms.PictureBox>  
 <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="6668d-116">PictureBox denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="6668d-116">PictureBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [<span data-ttu-id="6668d-117">Nasıl yapılır: tasarımcıyı kullanarak resim yükleme</span><span class="sxs-lookup"><span data-stu-id="6668d-117">How to: Load a Picture Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)  
 [<span data-ttu-id="6668d-118">Nasıl yapılır: çalışma zamanında boyutunu veya resim konumunu değiştirme</span><span class="sxs-lookup"><span data-stu-id="6668d-118">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)  
 [<span data-ttu-id="6668d-119">PictureBox denetimi</span><span class="sxs-lookup"><span data-stu-id="6668d-119">PictureBox Control</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
