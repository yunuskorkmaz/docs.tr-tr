---
title: 'Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Yayma'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
ms.openlocfilehash: a215b2b4e05bab5c81d2779d4b67d5b9d57b6ba5
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039696"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a>Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Yayma
Bir <xref:System.Windows.Forms.TableLayoutPanel> denetimdeki denetimler bitişik satır ve sütunlara yayılabilir.

## <a name="to-span-columns-and-rows"></a>Sütunları ve satırları yayma

1. <xref:System.Windows.Forms.TableLayoutPanel> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin.

2. <xref:System.Windows.Forms.Button> **Araç kutusundan** denetimin<xref:System.Windows.Forms.TableLayoutPanel> sol üst hücresine bir denetim sürükleyin.

3. Denetimin ColumnSpan özelliğini **2**olarak ayarlayın. <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Button> Denetimin birinci ve ikinci sütunları yaydığına unutmayın.

4. Denetimin RowSpan özelliğini **2**olarak ayarlayın. <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Button> Denetimin birinci ve ikinci satırları yaydığına unutmayın.

5. Denetimin ColumnSpan özelliğini **1**olarak ayarlayın. <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Button> Denetimin ilk sütuna taşındığını ve birinci ve ikinci satırlara yayıldığına unutmayın.

## <a name="see-also"></a>Ayrıca bkz.

- [TableLayoutPanel Denetimi](tablelayoutpanel-control-windows-forms.md)
