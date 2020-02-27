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
ms.openlocfilehash: 4473b20eea57088104a51eb1b6c080219223d214
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628650"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme

Denetimlerinizin satırlarını ve sütunlarını düzenlemek için, **sütun ve satır stilleri** iletişim kutusu olarak adlandırılan <xref:System.Windows.Forms.TableLayoutPanel> denetimin koleksiyon düzenleyicisini kullanabilirsiniz.

> [!NOTE]
> Bir denetimin birden çok satır veya sütunu yaymasına isterseniz, denetimin `RowSpan` ve `ColumnSpan` özelliklerini ayarlayın. Daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms denetimleri bir TableLayoutPanel kullanarak düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).
>
> Bir hücrenin içindeki bir denetimi hizalamak istiyorsanız veya bir denetimin bir hücrede Esnetme olmasını istiyorsanız denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini kullanın. Daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms denetimleri bir TableLayoutPanel kullanarak düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).

## <a name="to-edit-rows-and-columns"></a>Satırları ve sütunları düzenlemek için

1. **Araç kutusundan** bir <xref:System.Windows.Forms.TableLayoutPanel> denetimini formunuza sürükleyin.

2. <xref:System.Windows.Forms.TableLayoutPanel> denetimin tasarımcı eylemleri simgesine (![küçük siyah ok](./media/designer-actions-glyph.gif)) tıklayın ve **satır ve sütunları Düzenle** ' yi seçerek **sütun ve satır stilleri** iletişim kutusunu açın. Ayrıca <xref:System.Windows.Forms.TableLayoutPanel> denetimine sağ tıklayıp, kısayol menüsünden **satırları ve sütunları Düzenle** ' yi seçebilirsiniz.

3. Sütun eklemek veya kaldırmak için **üye türü** açılan liste kutusundan **sütunlar** ' ı seçin.

4. Satır eklemek veya kaldırmak için **üye türü** açılan liste kutusundan **Satırlar** ' ı seçin.

5. **Üye** listesinin sonuna bir satır veya sütun eklemek için **Ekle** düğmesine tıklayın.

6. Listede seçili olan öğeden önce bir satır veya sütun eklemek için **Ekle** düğmesine tıklayın.

7. Bir satır veya sütun ekliyorsanız, yeni satır veya sütun için **Boyut türünü** seçin. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.SizeType>.

8. Bir satırı veya sütunu kaldırmak için **Kaldır** düğmesine tıklayarak **üye** listesinde o anda seçili olan öğeyi silin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.SizeType>
- [TableLayoutPanel Denetimi](tablelayoutpanel-control-windows-forms.md)
