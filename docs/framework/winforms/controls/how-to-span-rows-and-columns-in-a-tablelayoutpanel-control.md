---
title: "Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Yayma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 24b281e6e1ab56e2c7387435bf2429e7e107c4b8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a>Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Yayma
Denetimlerini bir <xref:System.Windows.Forms.TableLayoutPanel> denetim bitişik satırları ve sütunları yayılabilir.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-span-columns-and-rows"></a>Satırları ve sütunları kapsanacak  
  
1.  Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> gelen denetim **araç** formunuza.  
  
2.  Sürükleme bir <xref:System.Windows.Forms.Button> gelen denetim **araç** sol üst hücresine <xref:System.Windows.Forms.TableLayoutPanel> denetim.  
  
3.  Ayarlama <xref:System.Windows.Forms.Button> denetimin **ColumnSpan** özelliğine **2**. Unutmayın <xref:System.Windows.Forms.Button> denetimi birinci ve ikinci sütunları kapsar.  
  
4.  Ayarlama <xref:System.Windows.Forms.Button> denetimin **RowSpan** özelliğine **2**. Unutmayın <xref:System.Windows.Forms.Button> denetim yayılan birinci ve ikinci satır.  
  
5.  Ayarlama <xref:System.Windows.Forms.Button> denetimin **ColumnSpan** özelliğine **1**. Unutmayın <xref:System.Windows.Forms.Button> denetimi ilk sütuna taşır ve birinci ve ikinci satır yayılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TableLayoutPanel Denetimi](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
