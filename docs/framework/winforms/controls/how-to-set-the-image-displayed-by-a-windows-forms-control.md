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
ms.openlocfilehash: 99bde4fac7b3057358c7e6a8550efdb4cc351eb0
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037877"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a>Nasıl yapılır: Windows Forms denetimi tarafından gösterilecek resmi ayarlama

Birçok Windows Forms denetimi görüntü görüntüleyebilir. Bu görüntüler, **Kaydet** komutunu gösteren bir düğmedeki disket simgesi gibi denetimin amacını açıklığa kavuşturacak simgeler olabilir. Alternatif olarak, simgeler istediğiniz görünümü ve davranışı denetlemek için arka plan görüntüleri olabilir.

## <a name="to-set-the-image-displayed-by-a-control"></a>Bir denetim tarafından görüntülenecek resmi ayarlamak için

1. Denetimin `Image` veya `BackgroundImage` özelliğini türünde<xref:System.Drawing.Image>bir nesne olarak ayarlayın. Genellikle, <xref:System.Drawing.Image.FromFile%2A> yöntemini kullanarak görüntüyü bir dosyadan yüklüyorsunuz.

     Aşağıdaki kod örneğinde, görüntü konumu için ayarlanan yol **Resimlerim** klasörüdür. Windows işletim sistemi çalıştıran bilgisayarların çoğu bu dizini içerir. Bu Ayrıca, en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenle çalıştırmasına olanak sağlar. Aşağıdaki kod örneği, bir <xref:System.Windows.Forms.PictureBox> denetim eklenmiş bir formunuza sahip olmanızı gerektirir.

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
