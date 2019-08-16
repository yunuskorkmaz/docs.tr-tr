---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimindeki Sütunları Gizleme'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: d502a89913e108254848151e9058ac6ae83a9638
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039770"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimindeki Sütunları Gizleme
Bazen Windows Forms <xref:System.Windows.Forms.DataGridView> denetiminde kullanılabilir olan sütunlardan yalnızca bazılarını göstermek isteyeceksiniz. Örneğin, yönetim kimlik bilgilerine sahip kullanıcılara bir çalışan maaş sütununu diğer kullanıcılardan gizleyerek göstermek isteyebilirsiniz. Alternatif olarak, denetimi çok sayıda sütun içeren bir veri kaynağına bağlamak isteyebilirsiniz, yalnızca bir kısmı görüntülenir. Bu durumda, genellikle bu sütunları gizlemek yerine, görüntüleme konusunda İlgilendiğiniz sütunları kaldırırsınız. Daha fazla bilgi için [nasıl yapılır: Tasarımcıyı](add-and-remove-columns-in-the-datagrid-using-the-designer.md)kullanarak Windows Forms DataGridView denetiminde sütun ekleyin ve kaldırın.

 Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGridView> denetim içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.

## <a name="to-hide-a-column-using-the-designer"></a>Tasarımcıyı kullanarak bir sütunu gizlemek için

1. <xref:System.Windows.Forms.DataGridView> Denetimin sağ üst köşesindeki akıllı etiket karakterini (![akıllı etiket karakter](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) tıklayın ve ardından **Sütunları Düzenle**' yi seçin.

2. **Seçili sütunlar** listesinden bir sütun seçin.

3. **Sütun özellikleri** kılavuzunda, <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> özelliğini olarak `false`ayarlayın.

    > [!NOTE]
    >  **Sütun Ekle** Iletişim kutusundaki **görünür** onay kutusunu temizleyerek bir sütunu eklerken de gizleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [Nasıl yapılır: Tasarımcıyı kullanarak Windows Forms DataGridView denetiminde sütun ekleme ve kaldırma](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Nasıl yapılır: Windows Forms uygulama projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md)
