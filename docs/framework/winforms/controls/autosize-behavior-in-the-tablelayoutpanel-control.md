---
title: "TableLayoutPanel Denetiminde AutoSize Davranışı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3d4813b7bd37c0c5bd9b04b37cb825067b35ce3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="autosize-behavior-in-the-tablelayoutpanel-control"></a>TableLayoutPanel Denetiminde AutoSize Davranışı
## <a name="distinct-autosize-behaviors"></a>Ayrı AutoSize davranışı  
 <xref:System.Windows.Forms.TableLayoutPanel> Denetimi, aşağıdaki yollarla otomatik boyutlandırma davranışını destekler:  
  
-   Aracılığıyla <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği;  
  
-   Aracılığıyla <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> özellikte <xref:System.Windows.Forms.TableLayoutPanel> denetimin sütun ve satır stilleri.  
  
### <a name="the-autosize-property-with-row-and-column-styles"></a>Satır ve sütun stilleri AutoSize özelliği  
 Aşağıdaki tabloda arasındaki etkileşim açıklanmıştır <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği ve <xref:System.Windows.Forms.TableLayoutPanel> denetimin sütun ve satır stilleri.  
  
|AutoSize ayarı|Stil etkileşim|  
|----------------------|-----------------------|  
|`false`|<xref:System.Windows.Forms.TableLayoutPanel> Denetimi soldan sağa doğru devam eder ve sütun veya satır için veya aşağıdaki sırayla alan ayırır.<br /><br /> 1.  Varsa <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> özelliği ayarlanmış <xref:System.Windows.Forms.SizeType.Absolute>, tarafından belirtilen piksel sayısı <xref:System.Windows.Forms.ColumnStyle.Width%2A> veya <xref:System.Windows.Forms.RowStyle.Height%2A> ayrılır.<br />2.  Varsa <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> özelliği ayarlanmış <xref:System.Windows.Forms.SizeType.AutoSize>, alt denetimin tarafından döndürülen piksel sayısı <xref:System.Windows.Forms.Control.GetPreferredSize%2A> yöntemi ayrılır.<br />3.  Tüm alanı sonra <xref:System.Windows.Forms.SizeType.Absolute> ve <xref:System.Windows.Forms.SizeType.AutoSize> sütunlara veya satırlara ayrılır, herhangi bir sütun veya satır ile <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> kümesine <xref:System.Windows.Forms.SizeType.Percent> orantılı olarak kalan boş alanı ayırmak için kullanılır|  
|`true`|Özel önceki etkileşimini benzer, <xref:System.Windows.Forms.SizeType.Percent> sütunlara veya satırlara otomatik boyutlandırma en boy edinin.<br /><br /> <xref:System.Windows.Forms.TableLayoutPanel> Denetimini genişleten sütun veya yeterli boş alan oluşturmak için satır böylece hiçbir sütun veya satır ile <xref:System.Windows.Forms.SizeType.Percent> stil içeriğini kırpar. <xref:System.Windows.Forms.TableLayoutPanel> Denetim ayırır yeni alana orantılı olarak göre <xref:System.Windows.Forms.ColumnStyle.Width%2A> veya <xref:System.Windows.Forms.RowStyle.Height%2A> özelliği.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [TableLayoutPanel denetimine genel bakış](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-overview.md)
