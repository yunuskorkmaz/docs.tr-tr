---
title: "Nasıl yapılır: Bir Bölgeyle Kırpma Kullanma"
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
- regions [Windows Forms], clipping
- regions [Windows Forms], restricting drawing surface
ms.assetid: 43d121b4-e14c-4901-b25c-2d6c25ba4e29
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b57ffa91a41900e10aa921bd42509b1288134ff3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-clipping-with-a-region"></a>Nasıl yapılır: Bir Bölgeyle Kırpma Kullanma
Özelliklerinden birini <xref:System.Drawing.Graphics> kırpma bölgesinin bir sınıftır. Gerçekleştirilen tüm çizim bir verilen <xref:System.Drawing.Graphics> nesnedir, kırpma bölgesi kısıtlı <xref:System.Drawing.Graphics> nesnesi. Kırpma bölgesinin çağırarak ayarlayabileceğiniz <xref:System.Drawing.Graphics.SetClip%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tek bir Çokgen oluşan bir yol oluşturur. Ardından bu yola göre bir bölge kodu oluşturur. Bölge geçirilir <xref:System.Drawing.Graphics.SetClip%2A> yöntemi bir <xref:System.Drawing.Graphics> nesnesi ve ardından iki dizeyi çizilir.  
  
 Aşağıdaki çizimde kırpılmış dizeleri gösterir.  
  
 ![Küçük](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [GDI +'daki bölgeler](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 [Bölgeleri kullanma](../../../../docs/framework/winforms/advanced/using-regions.md)
