---
title: GDI+'daki Bölgeler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, regions
- drawing [Windows Forms], regions
- regions
ms.assetid: 52184f9b-16dd-4bbd-85be-029112644ceb
ms.openlocfilehash: 33d4f4ecca7b9d777fa4eab5b6d031de10f03ccc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076035"
---
# <a name="regions-in-gdi"></a>GDI+'daki Bölgeler
Bir bölge, bir çıktı cihazına görüntü alanının bölümüdür. Bölgeler (tek bir dikdörtgen) basit veya karmaşık (çokgenler ve kapalı Eğriler birleşimi) olabilir. Aşağıdaki resimde iki bölgeleri gösterir: bir bir dikdörtgen oluşturulur ve diğer bir yolu oluşturulur.  
  
 ![Bölgeleri](./media/aboutgdip02-art27.gif "AboutGdip02_Art27")  
  
## <a name="using-regions"></a>Bölgeleri Kullanma  
 Bölgeler, kırpma için sık kullanılan ve isabet sınaması. Kırpma çizim ekran alanı, genellikle güncelleştirilmesi gerekiyor bölümü belirli bir bölgeye kısıtlama içerir. İsabet sınaması bir fare düğmesine basıldığında imleci ekranın belirli bir bölgede olup olmadığını belirlemek için denetleme içerir.  
  
 Bir dikdörtgen ya da yolu bir bölgeden oluşturabilirsiniz. Ayrıca, mevcut bölgelerimiz birleştirerek karmaşık bölgeler oluşturabilirsiniz. <xref:System.Drawing.Region> Sınıfı bölgeleri birleştirmek için aşağıdaki yöntemleri sağlar: <xref:System.Drawing.Region.Intersect%2A>, <xref:System.Drawing.Region.Union%2A>, <xref:System.Drawing.Region.Xor%2A>, <xref:System.Drawing.Region.Exclude%2A>, ve <xref:System.Drawing.Region.Complement%2A>.  
  
 İki bölgeler kesişimini hem bölgelerine ait olan tüm noktaları kümesidir. Bir ya da diğer veya her iki bölgeleri ait tüm noktaları kümesini birleşimdir. Bir bölge tümleme bölgede değil tüm noktaları kümesidir. Aşağıdaki resimde, önceki resimde gösterilen iki bölgeleri birleşimini ve kesişimi gösterir.  
  
 ![Bölgeleri](./media/aboutgdip02-art28.gif "AboutGdip02_Art28")  
  
 <xref:System.Drawing.Region.Xor%2A> Bölge çiftine uygulanan yöntemi, tek bir bölge veya diğer, ancak ikisini birden ait tüm noktaları içeren bir bölge üretir. <xref:System.Drawing.Region.Exclude%2A> Bölge çiftine uygulanan yöntem, ilk bölgeye ikinci bir bölgede değil tüm noktaları içeren bir bölge üretir. Uygulamasını neden bölgeler aşağıda gösterilmektedir <xref:System.Drawing.Region.Xor%2A> ve <xref:System.Drawing.Region.Exclude%2A> yöntemleri için bu konunun başında gösterilen iki bölgeleri.  
  
 ![Bölgeleri](./media/aboutgdip02-art29.gif "AboutGdip02_Art29")  
  
 Bir bölge doldurmak için ihtiyacınız bir <xref:System.Drawing.Graphics> nesnesi bir <xref:System.Drawing.Brush> nesnesi ve bir <xref:System.Drawing.Region> nesne. <xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.FillRegion%2A> yöntemi ve <xref:System.Drawing.Brush> nesneyi dolgu rengini veya desenini gibi özniteliklerini depolar. Aşağıdaki örnek, bir bölgeye düz renk ile doldurur.  
  
 [!code-csharp[LinesCurvesAndShapes#61](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#61)]
 [!code-vb[LinesCurvesAndShapes#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Region?displayProperty=nameWithType>
- [Çizgiler, Eğriler ve Şekiller](lines-curves-and-shapes.md)
- [Bölgeleri Kullanma](using-regions.md)
