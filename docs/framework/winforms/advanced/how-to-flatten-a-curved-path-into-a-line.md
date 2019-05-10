---
title: 'Nasıl yapılır: Eğik bir Yolu Düzleştirerek Çizgiye Dönüştürme'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
ms.openlocfilehash: d59a802618ddd5080c651e822ed4c09641f7f170
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645359"
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a>Nasıl yapılır: Eğik bir Yolu Düzleştirerek Çizgiye Dönüştürme
A <xref:System.Drawing.Drawing2D.GraphicsPath> nesnesi bir dizi satır ve Bézier eğrileri depolar. Eğrileri (elips yaylar, ana Eğriler) birkaç türde bir yola ekleyebilirsiniz, ancak yolda depolanmadan önce her eğrisinin bir Bézier eğri için dönüştürülür. Düzleştirme bir yol dizisi düz çizgiler ile yoldaki her Bézier eğri dönüştürme oluşur. Aşağıdaki çizim, önce ve sonra düzleştirme bir yolunu gösterir.  
  
 ![Düz çizgiler ve eğrilerle](./media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")  
  
### <a name="to-flatten-a-path"></a>Bir yol düzleştirmek için  
  
- çağrı <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> yöntemi bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesne. <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> Yöntem düzleştirilmiş ile özgün yolu arasında en fazla mesafe belirten bir düzlük bağımsız değişken alır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- [Çizgiler, Eğriler ve Şekiller](lines-curves-and-shapes.md)
- [Yollar Oluşturma ve Çizme](constructing-and-drawing-paths.md)
