---
title: 'Nasıl yapılır: Bir Şekli Düz Renk ile Doldurma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], adding to shapes
- shapes [Windows Forms], filling
ms.assetid: 06088b31-bac9-4ef3-9ebe-06c2c764d6df
ms.openlocfilehash: d6fe7a252029ff80f21d99f7342fabb1d29fbe24
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211679"
---
# <a name="how-to-fill-a-shape-with-a-solid-color"></a>Nasıl yapılır: Bir Şekli Düz Renk ile Doldurma
Bir şekli düz renk ile doldurma için oluşturma bir <xref:System.Drawing.SolidBrush> nesnesi ve ardından, geçirin <xref:System.Drawing.SolidBrush> dolgu yöntemlerinden birini bağımsız değişkeni olarak bir nesne <xref:System.Drawing.Graphics> sınıfı. Aşağıdaki örnek, bir elips kırmızı renkle doldurma gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kodda, <xref:System.Drawing.SolidBrush.%23ctor%2A> Oluşturucusu alır bir <xref:System.Drawing.Color> yalnızca bağımsız değişken olarak nesnesi. Tarafından kullanılan değerleri <xref:System.Drawing.Color.FromArgb%2A> yöntemi alfa, kırmızı, yeşil ve mavi renk bileşenleri temsil eder. Bu değerlerin her birini, 0-255 aralığında olmalıdır. İlk 255 rengi ila tamamen opak ve ikinci 255 kırmızı bileşeni tam yoğunlukta gösterir gösterir. İki sıfır, yeşil ve mavi bileşenlerinin bir yoğunluğu 0 olduğunu gösterir.  
  
 Dört rakam (0, 0, 100, 60) geçirilen <xref:System.Drawing.Graphics.FillEllipse%2A> elipsin dikdörtgen boyutunu ve konumunu yöntemini belirtin. Dikdörtgen bir sol üst köşesinde sahiptir (0, 0), bir 100 genişlik ve yükseklik 60'a.  
  
 [!code-csharp[System.Drawing.UsingABrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şekilleri Doldurmak için Fırça Kullanma](using-a-brush-to-fill-shapes.md)
