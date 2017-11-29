---
title: "Nasıl yapılır: Bir Şekli Düz Renk ile Doldurma"
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
- colors [Windows Forms], adding to shapes
- shapes [Windows Forms], filling
ms.assetid: 06088b31-bac9-4ef3-9ebe-06c2c764d6df
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb3e160392a903083386d9942f8e2cfe31ee89a4
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-fill-a-shape-with-a-solid-color"></a>Nasıl yapılır: Bir Şekli Düz Renk ile Doldurma
Bir şekli düz renk ile doldurma için oluşturun bir <xref:System.Drawing.SolidBrush> nesne ve daha sonra geçirin <xref:System.Drawing.SolidBrush> nesnesi dolgu yöntemlerinden birini bağımsız değişken olarak <xref:System.Drawing.Graphics> sınıfı. Aşağıdaki örnek, bir elips dolgu rengi kırmızı ile gösterilmiştir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kodda, <xref:System.Drawing.SolidBrush.%23ctor%2A> Oluşturucusu geçen bir <xref:System.Drawing.Color> nesnesi yalnızca bağımsız değişken olarak. Tarafından kullanılan değerleri <xref:System.Drawing.Color.FromArgb%2A> yöntemi rengi alfa, kırmızı, yeşil ve mavi bileşenlerini temsil eder. Bu değerlerin her birini 0 ile 255 arasında olmalıdır. İlk 255 rengi tamamıyla opak ve ikinci 255 kırmızı bileşenini tam yoğunlukta gösterir gösterir. Yeşil ve mavi bileşenleri bir yoğunluğu 0 olan iki sıfır belirtin.  
  
 Dört rakam (0, 0, 100, 60) geçirilen <xref:System.Drawing.Graphics.FillEllipse%2A> yöntemi elips için sınırlayıcı dikdörtgenini boyutunu ve konumunu belirtin. Dikdörtgen bir sol üst köşesindeki sahip (0, 0), 100 genişliğini bir ve 60 yüksekliğini bir.  
  
 [!code-csharp[System.Drawing.UsingABrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Şekilleri doldurmak için fırça kullanma](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
