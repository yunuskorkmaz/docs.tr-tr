---
title: Denetimlerde kenar boşluğu ve doldurma
description: Kenar boşluğu ve doldurma özellikleriyle Windows form denetimlerinde kenar boşlukları ve doldurma ekleme hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- Padding property [Windows Forms]
- layout [Windows Forms], margins and padding
- Windows Forms, layout
- Margin property [Windows Forms]
ms.assetid: 3781b5a1-3085-4072-bed0-44670c23ffdc
ms.openlocfilehash: 4279f39bb4f89fbda8be472f49c8e60853abcac6
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174490"
---
# <a name="margin-and-padding-in-windows-forms-controls"></a>Windows Forms Denetimlerinde Kenar Boşluğu Bırakma ve Doldurma
Denetimlerin formunuza kesin olarak yerleştirilmesi birçok uygulama için yüksek önceliktir. <xref:System.Windows.Forms?displayProperty=nameWithType>Ad alanı, bunu gerçekleştirmek için size birçok düzen özelliği sunar. En önemlisi ikisi <xref:System.Windows.Forms.Control.Margin%2A> ve <xref:System.Windows.Forms.Control.Padding%2A> özelliklerdir.  
  
 Özelliği, denetimin <xref:System.Windows.Forms.Control.Margin%2A> kenarlıklarından belirli bir uzaklıkta bulunan diğer denetimleri tutan denetimin etrafındaki boşluğu tanımlar.  
  
 Özelliği, denetimin <xref:System.Windows.Forms.Control.Padding%2A> içeriklerini (örneğin, <xref:System.Windows.Forms.Control.Text%2A> özelliğinin değeri) denetimin kenarlıklarından belirtilen uzaklıktan tutup denetimin içeriğini tutan bir denetimin iç kısmında yer alan alanı tanımlar.  
  
 Aşağıdaki çizim, <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.Control.Margin%2A> bir denetimdeki ve özelliklerini gösterir.  
  
 ![Windows Forms denetimleri için doldurma ve kenar boşluğu](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")  
  
 Visual Studio 'da bu özellik için tasarım zamanı desteği vardır. Ayrıca bkz. [Izlenecek yol: doldurma, kenar boşlukları ve AutoSize özelliği ile Windows Forms denetimleri yerleştirme](windows-forms-controls-padding-autosize.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- <xref:System.Windows.Forms.Control.LayoutEngine%2A>
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
