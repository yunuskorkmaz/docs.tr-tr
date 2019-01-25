---
title: TableLayoutPanel Denetiminde AutoSize Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- localizing forms
- layout [Windows Forms], AutoSize
- sizing [Windows Forms], automatic
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- automatic sizing
- AutoSizeMode property
ms.assetid: 9233e0c3-2fa6-405e-8701-959479b1250e
ms.openlocfilehash: fdaa34ace1f5322c9296d2520d275fdf3f176048
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515738"
---
# <a name="autosize-behavior-in-the-tablelayoutpanel-control"></a>TableLayoutPanel Denetiminde AutoSize Davranışı
## <a name="distinct-autosize-behaviors"></a>Farklı AutoSize davranışları  
 <xref:System.Windows.Forms.TableLayoutPanel> Denetimi, aşağıdaki yollarla otomatik boyutlandırma davranışını destekler:  
  
-   Aracılığıyla <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği;  
  
-   Aracılığıyla <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> özelliği <xref:System.Windows.Forms.TableLayoutPanel> denetimin sütun ve satır stilleri.  
  
### <a name="the-autosize-property-with-row-and-column-styles"></a>AutoSize özelliği ile satır ve sütun stilleri  
 Aşağıdaki tabloda arasındaki etkileşim açıklanmıştır <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği ve <xref:System.Windows.Forms.TableLayoutPanel> denetimin sütun ve satır stilleri.  
  
|AutoSize ayarı|Stil etkileşimi|  
|----------------------|-----------------------|  
|`false`|<xref:System.Windows.Forms.TableLayoutPanel> Denetimi soldan sağa devam eder ve sütun veya satır ya da aşağıdaki sırayla alanı ayırır.<br /><br /> 1.  Varsa <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> özelliği <xref:System.Windows.Forms.SizeType.Absolute>, tarafından belirtilen piksel sayısı <xref:System.Windows.Forms.ColumnStyle.Width%2A> veya <xref:System.Windows.Forms.RowStyle.Height%2A> ayrılır.<br />2.  Varsa <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> özelliği <xref:System.Windows.Forms.SizeType.AutoSize>, alt denetimin tarafından döndürülen piksel sayısı <xref:System.Windows.Forms.Control.GetPreferredSize%2A> yöntemi ayrılır.<br />3.  Alan sonra <xref:System.Windows.Forms.SizeType.Absolute> ve <xref:System.Windows.Forms.SizeType.AutoSize> satırları veya sütunları ayrılır, herhangi bir sütun veya satır ile <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> kümesine <xref:System.Windows.Forms.SizeType.Percent> orantılı olarak kalan boş alanı ayırmak için kullanılır|  
|`true`|Benzer şekilde, önceki etkileşimi, özel durum, <xref:System.Windows.Forms.SizeType.Percent> satırları veya sütunları otomatik boyutlandırma boyut alma.<br /><br /> <xref:System.Windows.Forms.TableLayoutPanel> Denetimi genişletir yeterli boş alan oluşturmak için satır ve sütun böylece hiçbir sütun veya satır ile <xref:System.Windows.Forms.SizeType.Percent> stil içeriğini kırpar. <xref:System.Windows.Forms.TableLayoutPanel> Denetim ayırır yeni alanına orantılı olarak göre <xref:System.Windows.Forms.ColumnStyle.Width%2A> veya <xref:System.Windows.Forms.RowStyle.Height%2A> özelliği.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.TableLayoutPanel>
- [TableLayoutPanel Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-overview.md)
