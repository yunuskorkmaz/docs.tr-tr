---
title: Dönüştürme Sırası Neden Önemlidir
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], order significance
ms.assetid: 37d5f9dc-a5cf-4475-aa5d-34d714e808a9
ms.openlocfilehash: 4a65e588984241affea3083810b4901266480ea4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747465"
---
# <a name="why-transformation-order-is-significant"></a>Dönüştürme Sırası Neden Önemlidir
Tek bir <xref:System.Drawing.Drawing2D.Matrix> nesne tek bir dönüştürme veya bir dizi dönüşümleri depolayabilir. İkinci bir bileşik dönüştürme çağrılır. Bileşik bir dönüştürme matrisi, tek tek dönüşümlerinin matrislerde çarpılarak elde edilir.  
  
## <a name="composite-transform-examples"></a>Bileşik dönüştürme örnekleri  
 Bir bileşik dönüşümünde tek dönüştürmeler sırası önemlidir. İlk döndürebilir, ölçeklendirme, sonra Çevir, örneğin, farklı bir sonuç daha önce çeviri, döndürme sonra ölçeği alırsınız. İçinde [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], bileşik dönüşümler soldan sağa oluşturulur. S, R ve T ölçek, döndürme ve çeviri matrislerde sırasıyla varsa, ürün SRT (bu sırayla) ilk ölçeklendirilen bileşik dönüştürme matrisini olup, ardından döndürür, sonra çevirir. Ürün tarafından üretilen matris SRT TRS ürün tarafından üretilen matris farklıdır.  
  
 Sıralamanın önemli olduğu bir nedeni, döndürme ve ölçeklendirme dönüşümleri koordinat sistemi kaynağını göre yapılır olmasıdır. Kaynak ortalanmış bir nesneyi ölçekleme uzağa kaynağı taşıdığınız nesneyi ölçekleme değerinden farklı bir sonuç üretir. Benzer şekilde, kaynak ortalanmış bir nesneyi döndürme ayrılmak kaynağa taşınan bir nesneyi döndürme değerinden farklı bir sonuç üretir.  
  
 Aşağıdaki örnek, bileşik bir dönüştürme oluşturmak için ölçeklendirme, çevirme ve döndürme (bu sırayla) birleştirir. Bağımsız değişken <xref:System.Drawing.Drawing2D.MatrixOrder.Append> geçirilen <xref:System.Drawing.Graphics.RotateTransform%2A> yöntemi döndürme ve ölçeklendirme takip edeceğini gösterir. Benzer şekilde, bağımsız değişken <xref:System.Drawing.Drawing2D.MatrixOrder.Append> geçirilen <xref:System.Drawing.Graphics.TranslateTransform%2A> yöntemi gösterir çeviri, döndürme izler. <xref:System.Drawing.Drawing2D.MatrixOrder.Append> ve <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend> üyeleri <xref:System.Drawing.Drawing2D.MatrixOrder> sabit listesi.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.MiscLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#21)]  
  
 Aşağıdaki örnek önceki örnekteki gibi aynı yöntem çağrıları yapar, ancak çağrılarının sıra ters çevrilir. Sonuçta elde edilen işlem sırası olan ilk çevirme, ilk ölçek daha çok farklı bir sonuç üretir, Ölçek, ardından döndürme sonra döndürün, sonra çevir.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.MiscLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#22)]  
  
 Tek bir bileşik dönüştürme dönüşümlerini sırasını tersine çevirmek için bir yöntem çağrısı bir dizi sırasını tersine çevirmek için yoludur. İşlemlerin sırasını denetlemek için ikinci bir yolu, matris order bağımsız değişkeni değiştirmektir. Aşağıdaki örnek önceki örnekte, hariç aynıdır <xref:System.Drawing.Drawing2D.MatrixOrder.Append> değiştirildi <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend>. Sırasıyla, çevirme ve döndürme veya matris çarpım SRT, S, R ve T ölçek matrislerde olduğu sırada yapılır. Bileşik dönüştürme sırası ilk ölçek döndürün, sonra çevir.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.MiscLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#23)]  
  
 Hemen önceki örnekte aynı sonucunda, bu konudaki ilk örnek sonucudur. Biz yöntemi çağrı sırasını hem matris çarpım sırasını ters olmasıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Drawing2D.Matrix>
- [Koordinat Sistemleri ve Dönüştürmeler](coordinate-systems-and-transformations.md)
- [Yönetilen GDI+'da Dönüştürmeleri Kullanma](using-transformations-in-managed-gdi.md)
