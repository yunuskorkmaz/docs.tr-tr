---
title: 'Nasıl yapılır: Tarafından görüntülenen resmi ayarlama bir Windows Forms denetimi'
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
ms.openlocfilehash: 93bc7970ce7c287273f8bd7ff50b07c6658e2a08
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644930"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a>Nasıl yapılır: Tarafından görüntülenen resmi ayarlama bir Windows Forms denetimi
Çeşitli Windows Forms denetimleri, görüntüleri görüntüleyebilirsiniz. Bu görüntüler gibi bir disket simgesini gösteren düğme üzerinde denetimin amacını açıklamak simgeler olabilir **Kaydet** komutu. Alternatif olarak, simgeler arka plan görüntüleri görünümünü ve davranışını istediğiniz hakkında denetim vermek olabilir.  
  
### <a name="to-set-the-image-displayed-by-a-control"></a>Bir denetimi tarafından görüntülenen resmi ayarlama  
  
1.  Denetimin ayarlamak `Image` veya `BackgroundImage` türünde bir nesne özelliğini <xref:System.Drawing.Image>. Genellikle, görüntüyü bir dosyadan kullanarak yüklüyor gibi <xref:System.Drawing.Image.FromFile%2A> yöntemi.  
  
     Aşağıdaki kod örneğinde yolunu ayarlamak için görüntü konumunu **Resimlerim** klasör. Windows işletim sistemi çalıştırılan bilgisayarların çoğu bu dizine dahil edilir. Bu uygulamayı güvenli bir şekilde çalıştırmak minimum sistem erişim düzeylerine sahip kullanıcılar da sağlar. Aşağıdaki kod örneği bir formla zaten sahip olmasını gerektirir. bir <xref:System.Windows.Forms.PictureBox> denetimi eklendi.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
