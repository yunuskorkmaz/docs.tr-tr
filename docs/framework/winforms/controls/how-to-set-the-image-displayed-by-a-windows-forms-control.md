---
title: "Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Resmi Ayarlama"
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
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4bf42fc90e19cbac0f165b59c0c6d3dfb7456b5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a><span data-ttu-id="76daf-102">Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Resmi Ayarlama</span><span class="sxs-lookup"><span data-stu-id="76daf-102">How to: Set the Image Displayed by a Windows Forms Control</span></span>
<span data-ttu-id="76daf-103">Çeşitli Windows Forms denetimleri görüntüleri görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76daf-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="76daf-104">Bu görüntüleri belirten düğmesi üzerinde bir disket simgesi gibi denetimi amacını açıklığa simgeler olabilir **kaydetmek** komutu.</span><span class="sxs-lookup"><span data-stu-id="76daf-104">These images can be icons that clarify the purpose of the control, such as a diskette icon on a button denoting the **Save** command.</span></span> <span data-ttu-id="76daf-105">Alternatif olarak, simgeler denetim istediğiniz davranış ve görünümünü sağlamak için arka plan görüntüleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="76daf-105">Alternatively, the icons can be background images to give the control the appearance and behavior you want.</span></span>  
  
### <a name="to-set-the-image-displayed-by-a-control"></a><span data-ttu-id="76daf-106">Bir denetimi tarafından görüntülenen resmi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="76daf-106">To set the image displayed by a control</span></span>  
  
1.  <span data-ttu-id="76daf-107">Denetimin ayarlamak `Image` veya `BackgroundImage` türünde bir nesne için özellik <xref:System.Drawing.Image>.</span><span class="sxs-lookup"><span data-stu-id="76daf-107">Set the control's `Image` or `BackgroundImage` property to an object of type <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="76daf-108">Genellikle, bir dosyadan kullanarak yükleme resmi <xref:System.Drawing.Image.FromFile%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="76daf-108">Generally, you will be loading the image from a file by using the <xref:System.Drawing.Image.FromFile%2A> method.</span></span>  
  
     <span data-ttu-id="76daf-109">Aşağıdaki kod örneğinde yolunu ayarlama görüntüsünün konumu için **resimler** klasör.</span><span class="sxs-lookup"><span data-stu-id="76daf-109">In the following code example, the path set for the location of the image is the **My Pictures** folder.</span></span> <span data-ttu-id="76daf-110">Windows işletim sistemi çalıştıran bilgisayarların çoğu bu dizine dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="76daf-110">Most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="76daf-111">Bu uygulama güvenli bir şekilde çalıştırmak minimum sistem erişim düzeyleri olan kullanıcılar da sağlar.</span><span class="sxs-lookup"><span data-stu-id="76daf-111">This also enables users with minimal system access levels to run the application safely.</span></span> <span data-ttu-id="76daf-112">Aşağıdaki kod örneğinde bir formla zaten sahip olmasını gerektiren bir <xref:System.Windows.Forms.PictureBox> eklenmiş denetimi.</span><span class="sxs-lookup"><span data-stu-id="76daf-112">The following code example requires that you already have a form with a <xref:System.Windows.Forms.PictureBox> control added.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="76daf-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="76daf-113">See Also</span></span>  
 <xref:System.Drawing.Image.FromFile%2A>  
 <xref:System.Drawing.Image>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>
