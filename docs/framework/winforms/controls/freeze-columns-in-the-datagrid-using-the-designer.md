---
title: 'Nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGridView denetiminde sütunları dondurma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
ms.openlocfilehash: e3581390a56e2dfd19ed0d760a618993ec124bfb
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716857"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGridView denetiminde sütunları dondurma
Kullanıcılar, Windows formlarında gösterilen verileri görüntülerken <xref:System.Windows.Forms.DataGridView> denetimi, bazen için ihtiyaç duydukları tek bir sütun veya sütun kümesi için sık bakın. Örneğin, müşteri bilgilerinin birçok sütunları içeren bir tablo görüntülediğinizde, müşteri adı dışında görünür bölgesi için diğer sütunları etkinleştirme sırasında her zaman görüntülemek için yararlı olur.  
  
 Bu davranışı elde etmek için denetiminde sütunları dondurma. Sütun dondurma, tüm sütunları solunda (veya sağdan sola dil komut sağındakiyle) de dondurulmuş. Diğer tüm sütunlar kaydırabilirsiniz sırada dondurulmuş sütun değiştirilmez. Sütun yeniden sıralamayı etkinse, dondurulmuş sütun Grup çözülmüş sütunlardan farklı olarak kabul edilir. Kullanıcı iki grupta sütunları konumlandırabilirsiniz, ancak bunlar bir sütun bir grubundan diğerine taşıyamazsınız.  
  
 Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form içeren bir <xref:System.Windows.Forms.DataGridView> denetimi. Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-freeze-a-column-using-the-designer"></a>Tasarımcı kullanarak bir sütun dondurmak için  
  
1.  Akıllı etiket karakterini tıklayın (![akıllı etiket karakterini](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) sağ üst köşesindeki <xref:System.Windows.Forms.DataGridView> denetlemek ve ardından **sütunları Düzenle**.  
  
2.  Bir sütun seçin **seçili sütun** listesi.  
  
3.  İçinde **sütun özellikleri** kılavuz Ayarla <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> özelliğini `true`.  
  
    > [!NOTE]
    >  Ayrıca bir sütunu seçerek eklerken dondurmak **Frozen** kutusunda **Sütun Ekle** iletişim kutusu.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- [Nasıl yapılır: Ekleme ve Windows Forms Tasarımcısı'nı kullanarak DataGridView denetimindeki sütunları kaldırma](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Nasıl yapılır: Windows Forms Tasarımcısı'nı kullanarak DataGridView denetimindeki sütun yeniden sıralamayı etkinleştirme](enable-column-reordering-in-the-datagrid-using-the-designer.md)
- [Nasıl yapılır: Sağdan sola metin Genelleştirme için Windows Forms'ta görüntüleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100))
- [Nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Nasıl yapılır: Windows Forms'a denetimler ekleme](how-to-add-controls-to-windows-forms.md)
