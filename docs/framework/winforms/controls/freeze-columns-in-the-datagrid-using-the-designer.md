---
title: 'Nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGridView denetiminde sütunları dondurma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
ms.openlocfilehash: 814eea9bbbee3e1a585eda67ec85d86994d8ce23
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539824"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGridView denetiminde sütunları dondurma
Kullanıcılar, Windows formlarında gösterilen verileri görüntülerken <xref:System.Windows.Forms.DataGridView> denetimi, bazen için ihtiyaç duydukları tek bir sütun veya sütun kümesi için sık bakın. Örneğin, müşteri bilgilerinin birçok sütunları içeren bir tablo görüntülediğinizde, müşteri adı dışında görünür bölgesi için diğer sütunları etkinleştirme sırasında her zaman görüntülemek için yararlı olur.  
  
 Bu davranışı elde etmek için denetiminde sütunları dondurma. Sütun dondurma, tüm sütunları solunda (veya sağdan sola dil komut sağındakiyle) de dondurulmuş. Diğer tüm sütunlar kaydırabilirsiniz sırada dondurulmuş sütun değiştirilmez. Sütun yeniden sıralamayı etkinse, dondurulmuş sütun Grup çözülmüş sütunlardan farklı olarak kabul edilir. Kullanıcı iki grupta sütunları konumlandırabilirsiniz, ancak bunlar bir sütun bir grubundan diğerine taşıyamazsınız.  
  
 Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form içeren bir <xref:System.Windows.Forms.DataGridView> denetimi. Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows uygulaması projesi oluşturmak](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-freeze-a-column-using-the-designer"></a>Tasarımcı kullanarak bir sütun dondurmak için  
  
1.  Akıllı etiket karakterini tıklayın (![akıllı etiket karakterini](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) sağ üst köşesindeki <xref:System.Windows.Forms.DataGridView> denetlemek ve ardından **sütunları Düzenle**.  
  
2.  Bir sütun seçin **seçili sütun** listesi.  
  
3.  İçinde **sütun özellikleri** kılavuz Ayarla <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> özelliğini `true`.  
  
    > [!NOTE]
    >  Ayrıca bir sütunu seçerek eklerken dondurmak **Frozen** kutusunda **Sütun Ekle** iletişim kutusu.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- [Nasıl yapılır: Ekleme ve Windows Forms Tasarımcısı'nı kullanarak DataGridView denetimindeki sütunları kaldırma](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Nasıl yapılır: Windows Forms Tasarımcısı'nı kullanarak DataGridView denetimindeki sütun yeniden sıralamayı etkinleştirme](../../../../docs/framework/winforms/controls/enable-column-reordering-in-the-datagrid-using-the-designer.md)
- [Nasıl yapılır: Sağdan sola metin Genelleştirme için Windows Forms'ta görüntüleme](https://msdn.microsoft.com/library/f0663385-2354-4c65-8676-706422283b14)
- [Nasıl yapılır: Bir Windows uygulaması projesi oluşturma](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)
- [Nasıl yapılır: Windows Forms'a denetimler ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
