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
ms.openlocfilehash: 6d9f4d806b39e6e1272ddbb60befdaf8c76e46b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a>Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Resmi Ayarlama
Çeşitli Windows Forms denetimleri görüntüleri görüntüleyebilirsiniz. Bu görüntüleri belirten düğmesi üzerinde bir disket simgesi gibi denetimi amacını açıklığa simgeler olabilir **kaydetmek** komutu. Alternatif olarak, simgeler denetim istediğiniz davranış ve görünümünü sağlamak için arka plan görüntüleri olabilir.  
  
### <a name="to-set-the-image-displayed-by-a-control"></a>Bir denetimi tarafından görüntülenen resmi ayarlamak için  
  
1.  Denetimin ayarlamak `Image` veya `BackgroundImage` türünde bir nesne için özellik <xref:System.Drawing.Image>. Genellikle, bir dosyadan kullanarak yükleme resmi <xref:System.Drawing.Image.FromFile%2A> yöntemi.  
  
     Aşağıdaki kod örneğinde yolunu ayarlama görüntüsünün konumu için **resimler** klasör. Windows işletim sistemi çalıştıran bilgisayarların çoğu bu dizine dahil edilir. Bu uygulama güvenli bir şekilde çalıştırmak minimum sistem erişim düzeyleri olan kullanıcılar da sağlar. Aşağıdaki kod örneğinde bir formla zaten sahip olmasını gerektiren bir <xref:System.Windows.Forms.PictureBox> eklenmiş denetimi.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Image.FromFile%2A>  
 <xref:System.Drawing.Image>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>
