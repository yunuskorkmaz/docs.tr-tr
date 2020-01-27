---
title: Denetimleri Bağlama
ms.date: 03/30/2017
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c307d8c5b3bc32e15e6de048c434854ef1bbc65
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747187"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a>Nasıl yapılır: Windows Forms denetimleri bağlama

Kullanıcının çalışma zamanında yeniden boyutlandırabilmesini sağlayan bir form tasarlıyorsanız, formunuzdaki denetimlerin düzgün şekilde yeniden boyutlandırılması ve yeniden konumlandırılması gerekir. Denetimleri formla dinamik olarak yeniden boyutlandırmak için Windows Forms denetimlerinin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini kullanabilirsiniz. <xref:System.Windows.Forms.Control.Anchor%2A> özelliği, denetimin bir bağlantı konumunu tanımlar. Bir denetim bir forma tutturulduğu ve form yeniden boyutlandırılırken denetim, denetim ve çapa konumları arasındaki mesafeyi korur. Örneğin, formun sol, sağ ve alt kenarlarına sabitlenmiş bir <xref:System.Windows.Forms.TextBox> denetiminiz varsa, form yeniden boyutlandırılırken, formun sağ ve sol taraflarından aynı mesafeyi sağlamak için <xref:System.Windows.Forms.TextBox> denetimi yatay olarak yeniden boyutlandırılır. Ayrıca, denetimin kendi konumu formun alt kenarından her zaman aynı uzaklıkta olacak şekilde dikey olarak konumlandırılır. Bir denetim tutturulmaz ve form yeniden boyutlandırılırsa formun kenarlarına göre denetimin konumu değişir.

<xref:System.Windows.Forms.Control.Anchor%2A> özelliği <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği ile etkileşime girer. Daha fazla bilgi için bkz. [AutoSize özelliğine genel bakış](autosize-property-overview.md).

## <a name="anchor-a-control-on-a-form"></a>Form üzerinde bir denetimi bağlama

1. Visual Studio 'da, bağlamak istediğiniz denetimi seçin.

    > [!NOTE]
    > CTRL tuşuna basarak, her denetime tıklayarak ve sonra bu yordamın geri kalanını izleyerek birden çok denetimi aynı anda bağlayabilirsiniz.

2. **Özellikler** penceresinde <xref:System.Windows.Forms.Control.Anchor%2A> özelliğinin sağ tarafındaki oka tıklayın.

     Çapraz gösteren bir düzenleyici görüntülenir.

3. Bir tutturucu ayarlamak için, çapraz pencerenin üst, sol, sağ veya alt bölümüne tıklayın.

     Denetimler en üste ve varsayılan olarak sola bağlanır.

4. Bağlanan denetimin bir tarafını temizlemek için, çapraz bu ARM öğesine tıklayın.

5. <xref:System.Windows.Forms.Control.Anchor%2A> Özellik düzenleyicisini kapatmak için <xref:System.Windows.Forms.Control.Anchor%2A> özelliği adına yeniden tıklayın.

Formunuz çalışma zamanında görüntülendiğinde denetim, formun kenarından aynı uzaklıkta konumlandırılmış şekilde yeniden boyutlandırılır. Sabitlenmiş kenardan uzaklık, denetim Windows Form Tasarımcısı konumlandırıldığında tanımlanan uzaklıktan her zaman aynı kalır.

> [!NOTE]
> <xref:System.Windows.Forms.ComboBox> denetimi gibi bazı denetimlerin yüksekliğine sınırı vardır. Denetimin ya da kapsayıcısının alt kısmına tutturmamak denetimin yükseklik sınırını aşmasına izin vermez.

Devralınan denetimlerin tutturulamayacak `Protected` olması gerekir. Bir denetimin erişim düzeyini değiştirmek için, **Özellikler** penceresinde `Modifiers` özelliğini ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimleri](index.md)
- [AutoSize Özelliğine Genel Bakış](autosize-property-overview.md)
- [Nasıl yapılır: Windows Forms’a Denetimleri Yerleştirme](how-to-dock-controls-on-windows-forms.md)
- [İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [İzlenecek yol: Doldurma, Kenar Boşlukları ve AutoSize Özelliği ile Windows Forms Denetimlerini Düzenleme](windows-forms-controls-padding-autosize.md)
