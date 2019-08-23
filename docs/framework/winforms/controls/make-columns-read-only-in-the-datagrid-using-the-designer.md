---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimindeki Sütunları Salt Okunur Yapma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 82be9d31ff6bb3f2f5dd8a55b4426103d466bdd6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952099"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimindeki Sütunları Salt Okunur Yapma
Varsayılan olarak, kullanıcılar Windows Forms <xref:System.Windows.Forms.DataGridView> denetiminde görünen metin ve sayısal verileri değiştirebilir. Değişiklik için amaçlanmış verileri göstermek istiyorsanız, verileri içeren sütunları salt okunurdur yapmalısınız. Denetimi tamamen salt okuma yapma hakkında bilgi için bkz [. nasıl yapılır: Tasarımcı](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)kullanarak Windows Forms DataGridView denetiminde satır eklemeyi ve silmeyi önleyin.

 Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGridView> denetim içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.

## <a name="to-make-a-column-read-only-by-using-the-designer"></a>Tasarımcıyı kullanarak bir sütunu salt okunabilir hale getirmek için

1. <xref:System.Windows.Forms.DataGridView> Denetimin sağ üst köşesindeki akıllı etiket karakterini (![akıllı etiket karakter](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) tıklayın ve ardından **Sütunları Düzenle**' yi seçin.

2. **Seçili sütunlar** listesinden bir sütun seçin.

3. **Sütun özellikleri** kılavuzunda, <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> özelliğini olarak `true`ayarlayın.

    > [!NOTE]
    > Sütun **Ekle** iletişim kutusundaki salt **Oku** onay kutusunu seçerek de bir sütunu salt okunabilir hale getirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [Nasıl yapılır: Tasarımcıyı kullanarak Windows Forms DataGridView denetiminde sütun ekleme ve kaldırma](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGridView denetiminde satır eklemeyi ve silmeyi engelleme](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [Nasıl yapılır: Windows Forms uygulama projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md)
