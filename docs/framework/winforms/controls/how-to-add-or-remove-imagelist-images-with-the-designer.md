---
title: 'Nasıl yapılır: Tasarımcı ile ImageList Görüntüleri Ekleme veya Kaldırma'
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: 57c124f19d208192cb2d4500274f7f897948252a
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960162"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a>Nasıl yapılır: Tasarımcı ile ImageList Görüntüleri Ekleme veya Kaldırma

Görüntüleri ekleyebileceğiniz bir <xref:System.Windows.Forms.ImageList> bileşen birkaç farklı yol. Akıllı etiket ile ilişkili kullanarak, çok hızlı bir şekilde bir görüntüleri ekleyebilirsiniz <xref:System.Windows.Forms.ImageList>, ya da diğer bazı özellikleri ayarlıyorsanız <xref:System.Windows.Forms.ImageList>, Özellikler penceresinde görüntülerle eklemek daha kullanışlı bulabilirsiniz. Kod kullanarak, görüntüleri de ekleyebilirsiniz. Kod ile görüntü ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Ekle veya Kaldır görüntülerle Windows Forms ImageList bileşeni](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md). Genellikle, doldurmanız <xref:System.Windows.Forms.ImageList> bileşen görüntülerle önce bir denetimle ilişkilidir, ancak bu zorunlu değildir.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-add-or-remove-images-by-using-the-properties-window"></a>Ekleme veya Özellikler penceresini kullanarak görüntüleri kaldırma

1. Seçin <xref:System.Windows.Forms.ImageList> bileşeni veya forma bir tane ekleyin.

2. Özellikler penceresinde üç nokta düğmesini (![Visual Studio Özellikler penceresinde üç nokta düğmesini (…)](./media/visual-studio-ellipsis-button.png)) yanındaki <xref:System.Windows.Forms.ImageList.Images%2A> özelliği.

3. İçinde **görüntü Koleksiyonu Düzenleyicisi**, tıklayın **Ekle** veya **Kaldır** görüntüleri eklemek veya listeden kaldırmak için.

### <a name="to-add-or-remove-images-using-the-smart-tag"></a>Akıllı etiket kullanarak görüntüleri eklemek veya kaldırmak için

1. Seçin <xref:System.Windows.Forms.ImageList> bileşeni veya forma bir tane ekleyin.

2. Akıllı etiket karakterini tıklayın (![akıllı etiket karakterini](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))

3. İçinde **ImageList görevleri** iletişim kutusunda **seçin görüntüleri**.

4. İçinde **Editor Kolekce Images** tıklayın **Ekle** veya **Kaldır** görüntüleri eklemek veya listeden kaldırmak için.

## <a name="see-also"></a>Ayrıca bkz.

- [Görüntüler, Bit Eşlemler ve Meta Dosyaları](../advanced/images-bitmaps-and-metafiles.md)
- [İzlenecek yol: Üzerinde Windows Forms denetimleri etiketleri akıllı kullanarak ortak görevleri gerçekleştirme](performing-common-tasks-using-smart-tags-on-wf-controls.md)
- [ImageList Bileşeni](imagelist-component-windows-forms.md)
