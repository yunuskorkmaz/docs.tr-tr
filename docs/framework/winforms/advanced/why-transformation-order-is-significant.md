---
title: "Dönüştürme Sırası Neden Önemlidir"
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
helpviewer_keywords: transformations [Windows Forms], order signficance
ms.assetid: 37d5f9dc-a5cf-4475-aa5d-34d714e808a9
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8b170c9247b2415c724c1306a4c21d067c823b4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="why-transformation-order-is-significant"></a>Dönüştürme Sırası Neden Önemlidir
Tek bir <xref:System.Drawing.Drawing2D.Matrix> nesnesi, tek bir dönüştürmeyi veya bir dizi dönüştürmeyi depolayabilir. İkinci bileşik dönüştürme adı verilir. Bileşik bir dönüştürme matrisi tek dönüştürmeler matrisleri çarpılarak elde edilir.  
  
## <a name="composite-transform-examples"></a>Bileşik dönüştürme örnekleri  
 Bileşik bir dönüşümünde tek dönüştürmeler sırası önemlidir. İlk döndürme, Ölçek, sonra Çevir, örneğin, farklı bir sonuç ilk Çevir, döndürme sonra ölçeği daha alırsınız. İçinde [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], bileşik dönüşümler soldan sağa yerleşiktir. S, R ve T ölçek, döndürme ve çeviri matrisleri sırasıyla varsa, ürün SRT (sırayla) bu ilk ölçekler bileşik dönüştürme matrisini olduğundan, ardından döndürür, sonra çevirir. Ürün tarafından üretilen matris SRT TRS ürün tarafından üretilen matris farklıdır.  
  
 Sırası önemlidir bir döndürme ve ölçekleme gibi dönüştürmeleri koordinat sistemi kaynağa göre yapılır nedenidir. Kaynağa ortalanmış bir nesneyi ölçekleme kaynağını çıktığınızda taşınan bir nesneyi ölçekleme daha farklı bir sonuç oluşturur. Benzer şekilde, kaynak ortalanmış bir nesne döndürme kaynağını çıktığınızda taşınmış olan bir nesne döndürme daha farklı bir sonuç oluşturur.  
  
 Aşağıdaki örnek, bileşik bir dönüşüm oluşturmak için ölçeklendirme, çevirme ve döndürme (sırayla) birleştirir. Bağımsız değişken <xref:System.Drawing.Drawing2D.MatrixOrder.Append> geçirilen <xref:System.Drawing.Graphics.RotateTransform%2A> yöntemi gösterir döndürme ölçeklendirme izler. Benzer şekilde, bağımsız değişkeni <xref:System.Drawing.Drawing2D.MatrixOrder.Append> geçirilen <xref:System.Drawing.Graphics.TranslateTransform%2A> yöntemi gösterir çeviri döndürme izler. <xref:System.Drawing.Drawing2D.MatrixOrder.Append>ve <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend> üyeleri olan <xref:System.Drawing.Drawing2D.MatrixOrder> numaralandırması.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#21)]  
  
 Aşağıdaki örnek Yukarıdaki örnekteki gibi aynı yöntemi çağrısı yapar, ancak çağrıları sırasını tersine çevrildi. Sonuçta elde edilen işlem sırası olan ilk Çevir, ilk ölçek daha çok farklı bir sonuç oluşturur, Ölçek sonra döndürme sonra döndürün, sonra çevir.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#22)]  
  
 Bileşik dönüştürmeyi bireysel dönüşümler sırasını tersine çevirmek için bir yöntem çağrıları dizisini sırasını tersine çevirmek için yoludur. İşlemlerin sırasını denetlemek için ikinci bir yolu, matris order bağımsız değişkeni değiştirmektir. Aşağıdaki örnek bir önceki örnekte, hariç aynıdır <xref:System.Drawing.Drawing2D.MatrixOrder.Append> değiştirildi <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend>. Çevir, sırasıyla ve döndürün veya matris çarpım S, R ve T ölçek için matrislerini nerede SRT, sırayla yapılır. Bileşik dönüştürme sırasını ilk ölçek döndürün, sonra çevir.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#23)]  
  
 Hemen önceki örnek aynı sonucunda, bu konunun ilk örnekte sonucudur. Biz yöntem çağrılarını sırasını ve matris çarpım sırasını tersine olmasıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Drawing2D.Matrix>  
 [Koordinat sistemleri ve dönüştürmeler](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [Yönetilen GDI +'da dönüştürmeleri kullanma](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
