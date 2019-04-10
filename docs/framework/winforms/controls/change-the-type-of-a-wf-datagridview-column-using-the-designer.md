---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Sütununun Türünü Değiştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: f42bfe9b407e8f81c0eaf5a654d246f7b83567c9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208559"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Sütununun Türünü Değiştirme
Bazen bir Windows Forms için zaten eklenmiş bir sütun türünü değiştirmek isteyeceksiniz <xref:System.Windows.Forms.DataGridView> denetimi. Örneğin, bazı denetim bir veri kaynağına bağlandığınızda otomatik oluşturulan sütunları türlerini değiştirmek isteyebilirsiniz. Görüntü tablo ilişkili bir tablodaki satırlara yabancı anahtarlar içeren sütunlar olduğunda bu kullanışlıdır. Bu durumda, bu yabancı anahtarları ile ilişkili tablodaki daha anlamlı değerleri gösteren birleşik giriş kutusu sütunları gösteren metin kutusu sütunları değiştirmek isteyebilirsiniz.  
  
 Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form içeren bir <xref:System.Windows.Forms.DataGridView> denetimi. Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-change-the-type-of-a-column-using-the-designer"></a>Tasarımcı kullanarak bir sütun türünü değiştirmek için  
  
1.  Akıllı etiket karakterini tıklayın (![akıllı etiket karakterini](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) sağ üst köşesindeki <xref:System.Windows.Forms.DataGridView> denetlemek ve ardından **sütunları Düzenle**.  
  
2.  Bir sütun seçin **seçili sütun** listesi.  
  
3.  İçinde **sütun özellikleri** kılavuz Ayarla `ColumnType` özelliğini yeni sütun türü.  
  
    > [!NOTE]
    >  `ColumnType` Sütun türünü temsil eden sınıf gösteren bir tasarım zaman-özelliği salt okunur bir özelliktir. Bir sütun sınıfta tanımlanan gerçek bir özellik değil.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Nasıl yapılır: Windows Forms’a Denetimler Ekleme](how-to-add-controls-to-windows-forms.md)
