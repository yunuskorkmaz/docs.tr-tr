---
title: ImageList Bileşenine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- ImageList
helpviewer_keywords:
- collection controls [Windows Forms], images
- icon list control
- ImageList component [Windows Forms], about ImageList component
ms.assetid: 7e25d89b-5633-40c1-afc3-82e0e301ffa2
ms.openlocfilehash: b46204375cb046d637f4c9e1d888f37d10ea1f57
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728095"
---
# <a name="imagelist-component-overview-windows-forms"></a>ImageList Bileşenine Genel Bakış (Windows Forms)

Windows Forms <xref:System.Windows.Forms.ImageList> bileşeni, görüntüleri depolamak için kullanılır ve daha sonra denetimler tarafından görüntülenebilir. Görüntü listesi, tek ve tutarlı bir resim kataloğu için kod yazmanıza olanak tanır. Örneğin, düğmenin <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> veya <xref:System.Windows.Forms.ButtonBase.ImageKey%2A> özelliğini değiştirerek bir <xref:System.Windows.Forms.Button> denetimi tarafından görüntülenmiş resimleri döndürebilirsiniz. Aynı görüntü listesini birden fazla denetim ile de ilişkilendirebilirsiniz. Örneğin, aynı dosya listesini göstermek için hem <xref:System.Windows.Forms.ListView> denetimi hem de bir <xref:System.Windows.Forms.TreeView> denetimi kullanıyorsanız, görüntü listesindeki bir dosyanın simgesini değiştirmek, yeni simgenin her iki görünümde görünmesine neden olur.

## <a name="using-imagelist-with-controls"></a>Denetimlerle ImageList kullanma

`ImageList` bir özelliği olan herhangi bir denetimle veya <xref:System.Windows.Forms.ListView> denetimi, <xref:System.Windows.Forms.ListView.SmallImageList%2A> ve <xref:System.Windows.Forms.ListView.LargeImageList%2A> özellikleri olan bir görüntü listesi kullanabilirsiniz. Bir görüntü listesi ile ilişkilendirilebilen denetimler şunlardır: <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ToolBar>, <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.RadioButton>ve <xref:System.Windows.Forms.Label> denetimleri. Görüntü listesini bir denetimle ilişkilendirmek için denetimin `ImageList` özelliğini <xref:System.Windows.Forms.ImageList> bileşenin adı olarak ayarlayın.

## <a name="key-properties"></a>Anahtar Özellikler

<xref:System.Windows.Forms.ImageList> bileşenin anahtar özelliği, ilişkili denetim tarafından kullanılacak resimleri içeren <xref:System.Windows.Forms.ImageList.Images%2A>. Her bir görüntüye, dizin değeri veya anahtarı tarafından erişilebilir. <xref:System.Windows.Forms.ImageList.ColorDepth%2A> özelliği, görüntülerin birlikte işlendiği renklerin sayısını belirler. Resimlerin hepsi aynı boyutta görüntülenir ve <xref:System.Windows.Forms.ImageList.ImageSize%2A> özelliği tarafından ayarlanır. Daha büyük olan görüntüler sığacak şekilde ölçeklendirilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ImageList>
- [Nasıl yapılır: Windows Forms ImageList Bileşeni ile Görüntü Ekleme veya Kaldırma](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
