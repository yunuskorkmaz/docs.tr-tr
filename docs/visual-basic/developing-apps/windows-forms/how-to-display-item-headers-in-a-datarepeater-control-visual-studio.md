---
title: 'Nasıl yapılır: DataRepeater denetiminde (Visual Studio) öğe üstbilgilerini görüntüleme'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, item headers
- DataRepeater, selection indicators
ms.assetid: 37321447-0ffa-43e1-bdc9-0480e392b90f
ms.openlocfilehash: eccac1b3b02da41a34d47072be267f6c51a7d490
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504567"
---
# <a name="how-to-display-item-headers-in-a-datarepeater-control-visual-studio"></a>Nasıl yapılır: DataRepeater denetiminde (Visual Studio) öğe üstbilgilerini görüntüleme
Öğe üst bilgisinde bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi bir gösterge sağlar, bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> seçilir. Zaman <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> özelliği <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> (varsayılan), her öğenin solundaki öğesi başlığı görüntülenir. Zaman <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> özelliği <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>, öğesi üst bilgisini her öğenin üst kısmında görüntülenir.  
  
 İlk seçili olduğunda, öğe üst bilgisi tarafından belirtilen rengi görüntülenir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> özelliği ve beyaz ok simgesi görüntülenir.  
  
> [!NOTE]
>  Ayarlarsanız <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> için <xref:System.Drawing.Color.White%2A>, öğe seçildiğinde seçimi simgesi görünür olmaz.  
  
 Bir alana olduğunda <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> odaklı öğesi başlığı değişiklikleri rengini <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> arka plan rengini ve siyah ok simgesi değişiklikler. Veri değiştirilirse, öğe üst bilgisinde bir kalem simgesi görüntülenir.  
  
 Varsayılan genişliğini (veya yüksekliği olduğunda <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> özelliği <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>) öğesinin başlığı 15 pikseldir. Ayarlayarak genişliğini değiştirebilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> özelliği.  
  
> [!NOTE]
>  Varsa <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> özelliği 11'den küçük bir değere ayarlandığında, gösterge simgeleri öğesi üstbilgisinde görüntülenmeyecek.  
  
 Öğe üst bilgilerini ayarlayarak gizleyebilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> özelliğini **False**. Zaman <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> ayarlanır **False**, bir öğe seçildiğinde yalnızca noktalı çizgi çevresinde göstergesidir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.  
  
> [!NOTE]
>  İzleyerek kendi seçimi göstergesi sağlayabilir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> özelliği <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> içinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> olayı <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.  
  
### <a name="to-change-the-appearance-of-item-headers"></a>Öğe üst bilgilerini görünümünü değiştirmek için  
  
1.  Windows Form Tasarımcısı'nda alt bölgesini seçin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
    > [!NOTE]
    >  Denetimin alt bölgeyi seçmeniz gerekir. Öğe şablonu bölümü seçin, farklı bir özellikler kümesini Özellikler penceresinde görünür.  
  
2.  Özellikler penceresinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> üstbilgileri rengini değiştirmek için özellik.  
  
    > [!NOTE]
    >  Ayarlarsanız <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> için <xref:System.Drawing.Color.White%2A>, öğe seçildiğinde seçimi simgesi görünür olmaz.  
  
3.  Kullanım <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> üstbilgileri genişliği (veya yüksekliği) değiştirileceğini özelliği.  
  
    > [!NOTE]
    >  Varsa <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> özelliği 11'den küçük bir değere ayarlandığında, gösterge simgeleri öğesi üstbilgisinde görüntülenmeyecek.  
  
### <a name="to-hide-item-headers"></a>Öğe üst bilgilerini gizlemek için  
  
1.  Windows Form Tasarımcısı'nda alt bölgesini seçin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
    > [!NOTE]
    >  Denetimin alt bölgeyi seçmeniz gerekir. Öğe şablonu bölümü seçin, farklı bir özellikler kümesini Özellikler penceresinde görünür.  
  
2.  Özellikler penceresinde ayarlayın <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> özelliğini **False**.  
  
     Bir öğe olduğunda <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> olduğu belirlenirse, tek belirti çevresinde bir noktalı çizgi olacaktır <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [DataRepeater Denetimine Giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [Nasıl yapılır: DataRepeater denetiminin görünümünü değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
- [Nasıl yapılır: DataRepeater denetimi düzenini değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)
- [DataRepeater Denetiminde Sorun Giderme](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
