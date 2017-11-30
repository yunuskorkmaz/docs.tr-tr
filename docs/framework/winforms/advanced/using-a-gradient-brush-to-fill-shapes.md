---
title: "Şekilleri Doldurmak için Gradyan Fırçası Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- brushes [Windows Forms], gradient brushes
- gradient brushes
- examples [Windows Forms], gradient brushes
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5a1c4ab7c2ee6f7164b6158dcb4ca4721be12650
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="using-a-gradient-brush-to-fill-shapes"></a>Şekilleri Doldurmak için Gradyan Fırçası Kullanma
Bir şekli kademeli olarak değişen bir renkle doldurmak için gradyan fırçası kullanabilirsiniz. Örneğin, bir şekli şeklin sol kenarından sağ kenarı hareket ederken, yavaş yavaş değişir renkle doldurma için yatay bir gradyan kullanabilirsiniz. Dikdörtgene siyah olan sol kenar düşünün (kırmızı, yeşil ve mavi bileşenleri tarafından temsil edilen 0, 0, 0) ve bir sağ kenar diğer bir deyişle kırmızı (255, 0, 0 tarafından gösterilen). Dikdörtgen 256 piksel genişliğinde ise, verilen piksel kırmızı bileşeninin bir solunda piksel kırmızı bileşeninin fazla olacaktır. Bir satırda soldaki piksel renk bileşenleri (0, 0, 0) varsa, ikinci piksel (1, 0, 0) sahip, üçüncü piksel (2, 0, 0) sahip vb. renk bileşenleri (255, 0, 0) sahip bir sağdaki piksel ulaşana kadar. Bu Ara değerli renk değerleri renk gradyan olun.  
  
 Yatay, dikey taşımak veya belirli bir Eğimli satırını paralel olarak doğrusal gradyan rengi değişir. Sınır bir yolu ve iç hakkında taşırken yol gradyanı rengi değişir. Yol gradyanları çok çeşitli efektler elde etmek için özelleştirebilirsiniz.  
  
 Aşağıdaki çizimde bir dikdörtgen doğrusal gradyan fırçası ile doldurulur ve yolun gradyan fırçası ile elips doldurulmuş gösterir.  
  
 ![Gradyan](../../../../docs/framework/winforms/advanced/media/gradient2.png "gradient2")  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: doğrusal gradyan oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-a-linear-gradient.md)  
 Doğrusal gradyan kullanarak bir oluşturmayı gösteren <xref:System.Drawing.Drawing2D.LinearGradientBrush> sınıfı.  
  
 [Nasıl yapılır: yol gradyanı oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-a-path-gradient.md)  
 Kullanarak bir yol gradyanı oluşturma açıklanmaktadır <xref:System.Drawing.Drawing2D.PathGradientBrush> sınıfı.  
  
 [Nasıl yapılır: bir Gradyana gama düzeltmesi uygulama](../../../../docs/framework/winforms/advanced/how-to-apply-gamma-correction-to-a-gradient.md)  
 Gama düzeltmesi ile bir gradyan fırçası kullanımı açıklanmaktadır.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 Bu sınıf için bir açıklama içerir ve tüm üyeleri bağlantılar içerir.  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=nameWithType>  
 Bu sınıf için bir açıklama içerir ve tüm üyeleri bağlantılar içerir.
