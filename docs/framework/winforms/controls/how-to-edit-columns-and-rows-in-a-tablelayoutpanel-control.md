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
ms.openlocfilehash: 99ff3286592da0a097835b8f35d687475ca54fb0
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040290"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme

Denetimlerinizin satırlarını ve sütunlarını düzenlemek için, <xref:System.Windows.Forms.TableLayoutPanel> **sütun ve satır stilleri** iletişim kutusu adlı denetimin koleksiyon düzenleyicisini kullanabilirsiniz.

> [!NOTE]
> Bir denetimin birden çok satır veya sütunu yaymasına isterseniz, denetim üzerindeki `RowSpan` ve `ColumnSpan` özelliklerini ayarlayın. Daha fazla bilgi için bkz [. İzlenecek yol: TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)kullanarak Windows Forms denetimlerini düzenleme.
>
> Bir hücrenin içindeki bir denetimi hizalamak istiyorsanız veya bir denetimin bir hücrede Esnetme olmasını istiyorsanız denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini kullanın. Daha fazla bilgi için bkz [. İzlenecek yol: TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)kullanarak Windows Forms denetimlerini düzenleme.

## <a name="to-edit-rows-and-columns"></a>Satırları ve sütunları düzenlemek için

1. <xref:System.Windows.Forms.TableLayoutPanel> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin.

2. ![](./media/vs-winformsmttagglyph.gif "") Denetimin akıllı etiket glifi ' ne (akıllı etiket karakteri VS_WinFormSmtTagGlyph) tıklayın ve sütun ve satır stilleri iletişim kutusunu açmak için satırları ve sütunları Düzenle ' yi seçin. <xref:System.Windows.Forms.TableLayoutPanel> Ayrıca <xref:System.Windows.Forms.TableLayoutPanel> denetime sağ tıklayıp kısayol menüsünden **satırları ve sütunları Düzenle** ' yi seçebilirsiniz.

3. Sütun eklemek veya kaldırmak için **üye türü** açılan liste kutusundan **sütunlar** ' ı seçin.

4. Satır eklemek veya kaldırmak için **üye türü** açılan liste kutusundan **Satırlar** ' ı seçin.

5. **Üye** listesinin sonuna bir satır veya sütun eklemek için **Ekle** düğmesine tıklayın.

6. Listede seçili olan öğeden önce bir satır veya sütun eklemek için **Ekle** düğmesine tıklayın.

7. Bir satır veya sütun ekliyorsanız, yeni satır veya sütun için **Boyut türünü** seçin. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.SizeType>.

8. Bir satırı veya sütunu kaldırmak için **Kaldır** düğmesine tıklayarak **üye** listesinde o anda seçili olan öğeyi silin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.SizeType>
- [TableLayoutPanel Denetimi](tablelayoutpanel-control-windows-forms.md)
