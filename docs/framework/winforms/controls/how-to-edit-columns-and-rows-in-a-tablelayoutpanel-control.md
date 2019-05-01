---
title: 'Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: 2149cac7fb15052c2602ef20a6684696730aae1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941524"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme
Koleksiyon Düzenleyicisi kullanabilirsiniz <xref:System.Windows.Forms.TableLayoutPanel> adlı Denetim **sütun ve satır stilleri** satırları ve sütunları, denetimlerin Düzenle iletişim kutusunda,.  
  
> [!NOTE]
>  Birden çok satır veya sütuna yayılmasını denetim istiyorsanız ayarlayın `RowSpan` ve `ColumnSpan` denetim özellikleri. Daha fazla bilgi için [izlenecek yol: TableLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
>   
>  Bir denetimi hücrede hizalamak istiyorsanız veya bir hücreyi uzatmak için bir denetim istiyorsanız, denetimin kullanın <xref:System.Windows.Forms.Control.Anchor%2A> özelliği. Daha fazla bilgi için [izlenecek yol: TableLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
>   
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-edit-rows-and-columns"></a>Satırları ve sütunları düzenlemek için  
  
1. Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi **araç kutusu** formunuza.  
  
2. Tıklayın <xref:System.Windows.Forms.TableLayoutPanel> denetimin akıllı etiket karakterini (![akıllı etiket karakterini](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) seçip **satırları ve sütunları Düzenle** açmak için  **Sütun ve satır stilleri** iletişim kutusu. Ayrıca sağ tıklayabilirsiniz <xref:System.Windows.Forms.TableLayoutPanel> seçin ve Denetim **satırları ve sütunları Düzenle** kısayol menüsünden.  
  
3. Sütun ekleme veya kaldırma için seçin **sütunları** gelen **üye türü** aşağı açılan liste kutusu.  
  
4. Satır eklediğinizde veya kaldırdığınızda için seçin **satırları** gelen **üye türü** aşağı açılan liste kutusu.  
  
5. Tıklayın **Ekle** sonuna bir satır veya sütun eklemek için Ekle düğmesine **üye** listesi.  
  
6. Tıklayın **Ekle** bir satır veya sütun önce geçerli seçilmiş öğe listesine eklemek için düğme.  
  
7. Bir satır veya sütun ekliyorsanız seçin **boyut türü** yeni satır veya sütun. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.SizeType>.  
  
8. Bir satır veya sütun kaldırmak için tıklayın **Kaldır** seçili öğeyi silmek için düğmeyi **üye** listesi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.SizeType>
- [TableLayoutPanel Denetimi](tablelayoutpanel-control-windows-forms.md)
