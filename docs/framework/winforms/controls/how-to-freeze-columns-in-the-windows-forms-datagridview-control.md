---
title: "Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Dondurma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], freezing columns
- DataGridView control [Windows Forms], columns always in view
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: baf2b0218c1818d6a92ca7790c8c50bd94ecfd9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Dondurma
Kullanıcılar Windows Forms'ta görüntülenen verileri görüntülerken <xref:System.Windows.Forms.DataGridView> denetim, bazen için ihtiyaç duydukları tek bir sütun veya sütun kümesi için sık bakın. Örneğin, müşteri bilgilerinin pek çok sütun içeren bir tablo görüntülerken, müşteri adı görünür bölgesinin dışındaki ilerlemek için diğer sütunları etkinleştirme sırasında her zaman görüntülemek kullanışlıdır.  
  
 Bu davranış elde etmek için denetiminde sütunları dondurma. Bir sütun dondurma, tüm sütunlar solunda (veya sağdan sola dil komut sağındaki) de dondurulmuş. Diğer tüm sütunları kaydırabilirsiniz sırada dondurulmuş sütun yerinde kalır.  
  
> [!NOTE]
>  Sütun yeniden sıralamayı etkinleştirilirse dondurulmuş sütunların çözülmüş sütunlarından ayrı bir grup olarak kabul edilir. Kullanıcılar ya da Grup sütun konumunu değiştirebilirsiniz, ancak bunlar bir sütun bir gruptan diğerine taşıyamazsınız.  
  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> Bir sütunun özelliği sütun her zaman ızgara içinde görünür olup olmadığını belirler.  
  
 Visual Studio'da bu görev için desteği yoktur.  Ayrıca bkz. [nasıl yapılır: Windows Forms DataGridView denetimi kullanarak Tasarımcı Dondur sütunlar](http://msdn.microsoft.com/library/717ss6s6\(v=vs.110\)).  
  
### <a name="to-freeze-a-column-programmatically"></a>Bir sütunu program aracılığıyla dondurmak için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> özelliğine `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1` adlı bir sütun içeren `AddToCartButton`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView>  
 [Temel sütun, satır ve hücre özellikleri Windows Forms DataGridView denetiminde](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [Nasıl yapılır: Windows Forms DataGridView denetiminde sütun yeniden sıralamayı etkinleştirme](../../../../docs/framework/winforms/controls/how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
