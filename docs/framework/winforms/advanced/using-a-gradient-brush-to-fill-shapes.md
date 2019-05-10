---
title: Şekilleri Doldurmak için Gradyan Fırçası Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [Windows Forms], gradient brushes
- gradient brushes
- examples [Windows Forms], gradient brushes
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
ms.openlocfilehash: 7ff555ba4fd81e9123e5f9e9feed38a0ec9d0a08
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063613"
---
# <a name="using-a-gradient-brush-to-fill-shapes"></a>Şekilleri Doldurmak için Gradyan Fırçası Kullanma
Bir şekli bir yavaş yavaş değişen rengi ile doldurmak için gradyan fırçası kullanabilirsiniz. Örneğin, bir şekli olarak şeklin sol kenardan sağ kenarına taşıyın, yavaş yavaş değişen renk ile doldurma için Yatay Gradyan kullanabilirsiniz. Siyah bir sol kenarı ile bir dikdörtgen Imagine (kırmızı, yeşil ve mavi bileşenleriyle belirtildiği 0, 0, 0) ve bir sağ kenar diğer bir deyişle kırmızı (255, 0, 0 tarafından gösterilen). 256 piksel genişliğinde dikdörtgen ise kırmızı bileşeni belirli bir pikselin bir pikselin solunda kırmızı bileşeni büyük olacaktır. Bir satırdaki en soldaki piksel renk bileşeni (0, 0, 0) sahip, ikinci piksel olan (1, 0, 0), üçüncü piksel (2, 0, 0) sahip vb. (255, 0, 0) renk bileşenleri en sağdaki piksel gelene kadar. Bu ilişkilendirilmiş renk değerleri renk gradyanı olun.  
  
 Yatay, dikey taşıdığınızda veya belirli bir Eğimli satırını paralel olarak doğrusal gradyan rengini değiştirir. İç ve bir yol sınırları hakkında hareket yolu gradyan rengini değiştirir. Yol gradyanları çok çeşitli efektler elde etmek için özelleştirebilirsiniz.  
  
 Doğrusal gradyan fırçası ile bir dikdörtgen doldurulmuş ve yolun gradyan fırçası ile bir elips doldurulmuş aşağıda gösterilmiştir:  
  
 ![Gradyan fırçası ile bir elips doldurulmuş bir dikdörtgen.](./media/using-a-gradient-brush-to-fill-shapes/rectangle-ellipse-gradient-brush.png)  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Doğrusal gradyan oluşturma](how-to-create-a-linear-gradient.md)  
 Bir doğrusal gradyan kullanarak oluşturulacağını gösterir <xref:System.Drawing.Drawing2D.LinearGradientBrush> sınıfı.  
  
 [Nasıl yapılır: Yol gradyanı oluşturma](how-to-create-a-path-gradient.md)  
 Kullanarak bir yol gradyanı oluşturma işlemini açıklamaktadır <xref:System.Drawing.Drawing2D.PathGradientBrush> sınıfı.  
  
 [Nasıl yapılır: Bir Gradyana gama düzeltmesi uygulama](how-to-apply-gamma-correction-to-a-gradient.md)  
 Gradyan fırça gama düzeltmesi kullanmayı açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 Bu sınıfın bir açıklama içerir ve tüm üyelerini bağlantılar.  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=nameWithType>  
 Bu sınıfın bir açıklama içerir ve tüm üyelerini bağlantılar.
