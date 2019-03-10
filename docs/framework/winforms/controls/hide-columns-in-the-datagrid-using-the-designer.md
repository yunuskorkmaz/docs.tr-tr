---
title: 'Nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGridView denetiminde sütunları gizleme'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: b65c83592334c84c7790da5877efdc9af84380f0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708398"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGridView denetiminde sütunları gizleme
Bazen yalnızca bazı Windows Forms'ta mevcut olan sütunları görüntülemek isteyeceksiniz <xref:System.Windows.Forms.DataGridView> denetimi. Örneğin, bir çalışan görüntülemek isteyebilirsiniz maaş sütun diğer kullanıcılardan gizleyerek sırasında yönetim kimlik bilgilerine sahip kullanıcılar için. Alternatif olarak, denetimi yalnızca bazılarının görüntülemek istediğiniz çok sayıda sütun içeren bir veri kaynağına bağlamak isteyebilirsiniz. Bu durumda, genellikle görüntüleme yerine gizlemeden ilgilenen olmayan sütunları kaldırır. Daha fazla bilgi için [nasıl yapılır: Ekle ve Kaldır sütunları Windows Forms DataGridView Tasarımcısı'nı kullanarak denetiminde](add-and-remove-columns-in-the-datagrid-using-the-designer.md).  
  
 Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form içeren bir <xref:System.Windows.Forms.DataGridView> denetimi. Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-hide-a-column-using-the-designer"></a>Tasarımcı kullanarak bir sütunu gizlemek için  
  
1.  Akıllı etiket karakterini tıklayın (![akıllı etiket karakterini](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) sağ üst köşesindeki <xref:System.Windows.Forms.DataGridView> denetlemek ve ardından **sütunları Düzenle**.  
  
2.  Bir sütun seçin **seçili sütun** listesi.  
  
3.  İçinde **sütun özellikleri** kılavuz Ayarla <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> özelliğini `false`.  
  
    > [!NOTE]
    >  Bir sütunu kaldırarak eklerken gizleyebilirsiniz **görünür** onay kutusuna **Sütun Ekle** iletişim kutusu.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [Nasıl yapılır: Ekleme ve Windows Forms Tasarımcısı'nı kullanarak DataGridView denetimindeki sütunları kaldırma](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Nasıl yapılır: Windows Forms'a denetimler ekleme](how-to-add-controls-to-windows-forms.md)
