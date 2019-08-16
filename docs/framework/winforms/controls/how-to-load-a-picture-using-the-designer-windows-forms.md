---
title: 'Nasıl yapılır: Tasarımcıyı kullanarak resim yükleme (Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 818bc63b5b3bea6c73804f716a72ba3cd1a62b4c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039689"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>Nasıl yapılır: Tasarımcıyı kullanarak resim yükleme (Windows Forms)

Windows Forms <xref:System.Windows.Forms.PictureBox> denetimiyle, <xref:System.Windows.Forms.PictureBox.Image%2A> özelliği geçerli bir resim olarak ayarlayarak tasarım zamanında form üzerinde bir resim yükleyebilir ve görüntüleyebilirsiniz. Aşağıdaki tabloda, kabul edilebilir dosya türleri gösterilmektedir.

|Tür|Dosya adı uzantısı|
|---|---|
|Biteş|. bmp|
|Simge|. ico|
|GIF|Resimler|
|Dosyasına|. wmf|
|JPEG|. jpg|

## <a name="to-display-a-picture-at-design-time"></a>Tasarım zamanında resim görüntüleme

1. Form üzerinde <xref:System.Windows.Forms.PictureBox> bir denetim çizin.

2. **Özellikler** penceresinde, <xref:System.Windows.Forms.PictureBox.Image%2A> özelliği seçin ve ardından **Aç** iletişim kutusunu göstermek için üç nokta düğmesini seçin.

3. Belirli bir dosya türünü arıyorsanız (örneğin,. gif dosyaları), bu **tür dosyalar** kutusunda seçin.

4. Göstermek istediğiniz dosyayı seçin.

## <a name="to-clear-the-picture-at-design-time"></a>Tasarım zamanında resmi temizlemek için

1. **Özellikler** penceresinde, <xref:System.Windows.Forms.PictureBox.Image%2A> özelliği seçin. Görüntü nesnesinin adının solunda görüntülenen küçük küçük resim resmine sağ tıklayın ve ardından **Sıfırla**' yı seçin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.PictureBox>
- [PictureBox Denetimine Genel Bakış](picturebox-control-overview-windows-forms.md)
- [Nasıl yapılır: Çalışma zamanında bir resmin boyutunu veya yerleşimini değiştirme](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [Nasıl yapılır: Çalışma zamanında resimleri ayarlama](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox Denetimi](picturebox-control-windows-forms.md)
