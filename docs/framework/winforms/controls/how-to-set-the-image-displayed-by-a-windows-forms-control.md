---
title: 'Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Resmi Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
ms.openlocfilehash: 1de835bda5ac906837ac3fbd97b87f68f14d1953
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013146"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a><span data-ttu-id="a36e9-102">Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Resmi Ayarlama</span><span class="sxs-lookup"><span data-stu-id="a36e9-102">How to: Set the Image Displayed by a Windows Forms Control</span></span>
<span data-ttu-id="a36e9-103">Çeşitli Windows Forms denetimleri, görüntüleri görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a36e9-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="a36e9-104">Bu görüntüler gibi bir disket simgesini gösteren düğme üzerinde denetimin amacını açıklamak simgeler olabilir **Kaydet** komutu.</span><span class="sxs-lookup"><span data-stu-id="a36e9-104">These images can be icons that clarify the purpose of the control, such as a diskette icon on a button denoting the **Save** command.</span></span> <span data-ttu-id="a36e9-105">Alternatif olarak, simgeler arka plan görüntüleri görünümünü ve davranışını istediğiniz hakkında denetim vermek olabilir.</span><span class="sxs-lookup"><span data-stu-id="a36e9-105">Alternatively, the icons can be background images to give the control the appearance and behavior you want.</span></span>  
  
### <a name="to-set-the-image-displayed-by-a-control"></a><span data-ttu-id="a36e9-106">Bir denetimi tarafından görüntülenen resmi ayarlama</span><span class="sxs-lookup"><span data-stu-id="a36e9-106">To set the image displayed by a control</span></span>  
  
1. <span data-ttu-id="a36e9-107">Denetimin ayarlamak `Image` veya `BackgroundImage` türünde bir nesne özelliğini <xref:System.Drawing.Image>.</span><span class="sxs-lookup"><span data-stu-id="a36e9-107">Set the control's `Image` or `BackgroundImage` property to an object of type <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="a36e9-108">Genellikle, görüntüyü bir dosyadan kullanarak yüklüyor gibi <xref:System.Drawing.Image.FromFile%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a36e9-108">Generally, you will be loading the image from a file by using the <xref:System.Drawing.Image.FromFile%2A> method.</span></span>  
  
     <span data-ttu-id="a36e9-109">Aşağıdaki kod örneğinde yolunu ayarlamak için görüntü konumunu **Resimlerim** klasör.</span><span class="sxs-lookup"><span data-stu-id="a36e9-109">In the following code example, the path set for the location of the image is the **My Pictures** folder.</span></span> <span data-ttu-id="a36e9-110">Windows işletim sistemi çalıştırılan bilgisayarların çoğu bu dizine dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="a36e9-110">Most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="a36e9-111">Bu uygulamayı güvenli bir şekilde çalıştırmak minimum sistem erişim düzeylerine sahip kullanıcılar da sağlar.</span><span class="sxs-lookup"><span data-stu-id="a36e9-111">This also enables users with minimal system access levels to run the application safely.</span></span> <span data-ttu-id="a36e9-112">Aşağıdaki kod örneği bir formla zaten sahip olmasını gerektirir. bir <xref:System.Windows.Forms.PictureBox> denetimi eklendi.</span><span class="sxs-lookup"><span data-stu-id="a36e9-112">The following code example requires that you already have a form with a <xref:System.Windows.Forms.PictureBox> control added.</span></span>  
  
    ```vb  
    ' Replace the image named below  
    ' with an icon of your own choosing.  
    PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.MyPictures) _  
       & "\Image.gif")  
    ```  
  
    ```csharp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.MyPictures)  
       + @"\Image.gif");  
    ```  
  
    ```cpp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    pictureBox1->Image = Image::FromFile(String::Concat  
       (System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::MyPictures),  
       "\\Image.gif"));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a36e9-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a36e9-113">See also</span></span>

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
