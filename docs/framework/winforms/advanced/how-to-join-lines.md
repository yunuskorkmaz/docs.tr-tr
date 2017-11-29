---
title: "Nasıl yapılır: Çizgileri Birleştirme"
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
- miter line join style
- bevel line join style
- line join
- drawing [Windows Forms], joining lines
- GraphicsPath object
- round line join style
- lines [Windows Forms], joining
- graphics [Windows Forms], joining lines
ms.assetid: 9fc480c2-3c75-4fd1-8ab5-296a99e820e2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f02da181d66f7bb26a8414782e42eff2570e6918
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-join-lines"></a>Nasıl yapılır: Çizgileri Birleştirme
Satır birleştirme, uçları karşıladığında veya üst üste iki çizgiyle biçimlendirilmiş ortak alandır. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]üç çizgi birleştirme stili sağlar: gönye, eğim ve yuvarlar. Çizgisi birleştirme stili bir özelliğidir <xref:System.Drawing.Pen> sınıfı. Çizgisi birleştirme stili için belirttiğinizde bir <xref:System.Drawing.Pen> nesnesi, birleştirme stili herhangi bir bağlı olan tüm satırları uygulanacak <xref:System.Drawing.Drawing2D.GraphicsPath> nesne bu kalem kullanarak çizilir.  
  
 Aşağıdaki çizimde eğik çizgi birleştirme örneğin sonuçlarını gösterir.  
  
 ![Kalemler](../../../../docs/framework/winforms/advanced/media/pens5.gif "pens5")  
  
## <a name="example"></a>Örnek  
 Kullanarak çizgisi birleştirme stili belirtebilirsiniz <xref:System.Drawing.Pen.LineJoin%2A> özelliği <xref:System.Drawing.Pen> sınıfı. Örnek bir eğik çizgi birleştirme yatay çizgi dikey çizgi arasındaki gösterir. Aşağıdaki kodda, değer <xref:System.Drawing.Drawing2D.LineJoin.Bevel> atanan <xref:System.Drawing.Pen.LineJoin%2A> özelliği üyesi olduğu <xref:System.Drawing.Drawing2D.LineJoin> numaralandırması. Diğer üyeleriyle <xref:System.Drawing.Drawing2D.LineJoin> numaralandırması olan <xref:System.Drawing.Drawing2D.LineJoin.Miter> ve <xref:System.Drawing.Drawing2D.LineJoin.Round>.  
  
 [!code-csharp[System.Drawing.UsingAPen#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çizgiler ve şekiller çizmek için kalem kullanma](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
