---
title: Tasarımcıyı kullanarak DataGridView Denetimindeki sütunları dondurma
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
ms.openlocfilehash: af8e07d7b1b0524e33688fd9d879818aa13be041
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745674"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Denetimindeki Sütunları Dondurma
Kullanıcılar bir Windows Forms <xref:System.Windows.Forms.DataGridView> denetiminde görüntülendiklerinde verileri görüntülerken bazen tek bir sütuna veya sütun kümesine sıklıkla başvurmaları gerekir. Örneğin, çok sayıda sütun içeren bir müşteri bilgileri tablosu görüntülediğinizde, diğer sütunların görünür bölgenin dışına kaymasını sağlayan müşteri adını her zaman görüntülemesi yararlı olur.

 Bu davranışı başarmak için denetimdeki sütunları dondurabilirsiniz. Bir sütunu dondurduktan sonra, sol tarafında (veya sağdan sola dil betiklerine ait olan) tüm sütunlar da dondurulur. Dondurulmuş sütunlar, diğer tüm sütunlar kaydırılarken yerinde kalır. Sütun yeniden sıralama etkinse, Dondurulmuş sütunlar dondurulmamış sütunlardan farklı bir grup olarak değerlendirilir. Kullanıcılar her iki gruptaki sütunları yeniden konumlandırabilirsiniz, ancak bir sütunu bir gruptan diğerine taşıyamaz.

 Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGridView> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma Windows Forms uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).

## <a name="to-freeze-a-column-using-the-designer"></a>Tasarımcıyı kullanarak bir sütunu dondurmak için

1. <xref:System.Windows.Forms.DataGridView> denetiminin sağ üst köşesindeki akıllı etiket glifi ' ne (![akıllı etiket karakter](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) tıklayın ve ardından **Sütunları Düzenle**' yi seçin.

2. **Seçili sütunlar** listesinden bir sütun seçin.

3. **Sütun özellikleri** kılavuzunda <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> özelliğini `true`olarak ayarlayın.

    > [!NOTE]
    > Ayrıca **sütun Ekle** Iletişim kutusunda **dondurulmuş** kutuyu seçerek sütunu eklerken dondurabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- [Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimine Sütunlar Ekleme ve Kaldırma](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimindeki Sütun Yeniden Sıralamayı Etkinleştirme](enable-column-reordering-in-the-datagrid-using-the-designer.md)
- [Nasıl yapılır: Genelleştirme için Windows Forms içinde sağdan sola metin görüntüleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100))
- [Nasıl yapılır: Windows Forms uygulama projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Nasıl yapılır: Windows Forms’a Denetimler Ekleme](how-to-add-controls-to-windows-forms.md)
