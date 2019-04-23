---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetiminde Satır Ekleme ve Silmeyi Engelleme'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: 9f78068597edb616017876c9c72b01d44111f6f0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220558"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetiminde Satır Ekleme ve Silmeyi Engelleme
Bazen kullanıcıların yeni veri satırı girme veya var olan satır silme önlemek istersiniz, <xref:System.Windows.Forms.DataGridView> denetimi. Yeni satırlar, denetimin altındaki yeni kayıtlar için özel satırda girilir. Yeni kayıtlar için satır satır eklemeyi devre dışı bıraktığınızda görüntülenmez. Daha sonra denetim salt okunur tamamen silme satır ve hücre düzenleme devre dışı bırakarak yapabilirsiniz.  
  
 Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form içeren bir <xref:System.Windows.Forms.DataGridView> denetimi. Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-prevent-row-addition-and-deletion"></a>Satır ekleme ve silme işlemlerini önlemek için  
  
-   Akıllı etiket karakterini tıklayın (![akıllı etiket karakterini](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) sağ üst köşesindeki <xref:System.Windows.Forms.DataGridView> denetlemek ve ardından temizleyin **eklemeyi etkinleştir** ve **silmeyi etkinleştir** onay kutuları.  
  
    > [!NOTE]
    >  Salt okunur tamamen denetimi yapmak için Temizle **düzenlemeyi etkinleştir** onay kutusu.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [Nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Nasıl yapılır: Windows Forms'a denetimler ekleme](how-to-add-controls-to-windows-forms.md)
