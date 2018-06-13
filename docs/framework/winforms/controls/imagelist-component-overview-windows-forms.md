---
title: ImageList Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ImageList
helpviewer_keywords:
- collection controls [Windows Forms], images
- icon list control
- ImageList component [Windows Forms], about ImageList component
ms.assetid: 7e25d89b-5633-40c1-afc3-82e0e301ffa2
ms.openlocfilehash: bda9bb71dd2e9b6da2de2444013ed724979f61af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535291"
---
# <a name="imagelist-component-overview-windows-forms"></a>ImageList Bileşenine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ImageList> bileşen denetimleri tarafından görüntülenebilen görüntüleri depolamak için kullanılır. Görüntü listesi görüntülerinin tek, tutarlı bir katalog için kod yazmayı sağlar. Örneğin, tarafından görüntülenen görüntüleri döndürebilirsiniz bir <xref:System.Windows.Forms.Button> düğmenin değiştirerek sadece denetim <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> veya <xref:System.Windows.Forms.ButtonBase.ImageKey%2A> özelliği. Ayrıca, aynı resim listesi birden çok denetimleri ile ilişkilendirebilirsiniz. Örneğin, her ikisi de kullanıyorsanız, bir <xref:System.Windows.Forms.ListView> denetim ve <xref:System.Windows.Forms.TreeView> denetimi dosyaları, görüntü listedeki bir dosyanın simgeyi değiştirme aynı listesini görüntülemek için her iki görünümde de görünen için yeni simgesine neden olur.  
  
## <a name="using-imagelist-with-controls"></a>ImageList denetimler ile kullanma  
 Görüntü listesi olan herhangi bir denetimle kullanabilirsiniz bir `ImageList` özelliği — veya durumunda <xref:System.Windows.Forms.ListView> denetimi <xref:System.Windows.Forms.ListView.SmallImageList%2A> ve <xref:System.Windows.Forms.ListView.LargeImageList%2A> özellikleri. Görüntü listesi ile ilişkilendirilebilir denetimleri içerir: <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ToolBar>, <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.RadioButton>, ve <xref:System.Windows.Forms.Label> kontrol eder. Görüntü listesi denetimi ile ilişkilendirmek için denetimin ayarlamak `ImageList` adını özelliğine <xref:System.Windows.Forms.ImageList> bileşeni.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Anahtar özelliği <xref:System.Windows.Forms.ImageList> bileşeni <xref:System.Windows.Forms.ImageList.Images%2A>, ilişkili denetimi tarafından kullanılacak resimler içeriyor. Tek tek her görüntü dizini değerini veya kendi anahtar tarafından erişilebilir. <xref:System.Windows.Forms.ImageList.ColorDepth%2A> Özelliği, görüntüleri ile işlenen renk sayısını belirler. Görüntüleri tüm tarafından belirlenen aynı boyutta görüntülenir <xref:System.Windows.Forms.ImageList.ImageSize%2A> özelliği. Daha büyük görüntüleri uyacak şekilde ölçeklendirilir.  
  
 Kullanıyorsanız [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], uygulamalarınızda kullanabileceğiniz standart görüntüleri büyük kitaplığı erişimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ImageList>  
 [Nasıl yapılır: Windows Forms ImageList Bileşeni ile Görüntü Ekleme veya Kaldırma](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
