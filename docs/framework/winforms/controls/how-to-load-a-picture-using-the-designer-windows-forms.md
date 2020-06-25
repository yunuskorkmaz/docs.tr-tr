---
title: 'Nasıl yapılır: Tasarımcıyı Kullanarak Resim Yükleme'
description: Tasarım zamanında bir forma bir resim yüklemek ve göstermek için Windows Forms PictureBox denetimini nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: a05ffe19412fc7a4e3e02f01336d89cce39fac8a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325603"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>Nasıl yapılır: Tasarımcıyı Kullanarak Resim Yükleme (Windows Formları)

Windows Forms <xref:System.Windows.Forms.PictureBox> denetimiyle, <xref:System.Windows.Forms.PictureBox.Image%2A> özelliği geçerli bir resim olarak ayarlayarak tasarım zamanında form üzerinde bir resim yükleyebilir ve görüntüleyebilirsiniz. Aşağıdaki tabloda, kabul edilebilir dosya türleri gösterilmektedir.

|Tür|Dosya adı uzantısı|
|---|---|
|Biteş|.bmp|
|Simge|. ico|
|GIF|.gif|
|Dosyasına|. wmf|
|JPEG|.jpg|

## <a name="to-display-a-picture-at-design-time"></a>Tasarım zamanında resim görüntüleme

1. <xref:System.Windows.Forms.PictureBox>Form üzerinde bir denetim çizin.

2. **Özellikler** penceresinde, <xref:System.Windows.Forms.PictureBox.Image%2A> özelliği seçin ve ardından **Aç** iletişim kutusunu göstermek için üç nokta düğmesini seçin.

3. Belirli bir dosya türünü arıyorsanız (örneğin,. gif dosyaları), bu **tür dosyalar** kutusunda seçin.

4. Göstermek istediğiniz dosyayı seçin.

## <a name="to-clear-the-picture-at-design-time"></a>Tasarım zamanında resmi temizlemek için

1. **Özellikler** penceresinde, <xref:System.Windows.Forms.PictureBox.Image%2A> özelliği seçin. Görüntü nesnesinin adının solunda görüntülenen küçük küçük resim resmine sağ tıklayın ve ardından **Sıfırla**' yı seçin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.PictureBox>
- [PictureBox Denetimine Genel Bakış](picturebox-control-overview-windows-forms.md)
- [Nasıl yapılır: Çalışma Zamanında Resmin Boyutunu veya Konumunu Değiştirme](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [Nasıl yapılır: Çalışma Zamanında Resimleri Ayarlama](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox Denetimi](picturebox-control-windows-forms.md)
