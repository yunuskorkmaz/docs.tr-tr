---
title: "İfade bir değerdir, bu nedenle atama işleminin hedefi olamaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords: BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bec3e2d298160bd0b459dc3b7ef93b94648e439a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a>İfade bir değerdir, bu nedenle atama işleminin hedefi olamaz
Bir ifade için bir değer atamak bir deyim çalışır. Çalışma zamanında yalnızca bir yazılabilir değişkeni, özelliği veya dizi öğesi için bir değer atayabilirsiniz. Aşağıdaki örnek, bu hata oluşabilir nasıl gösterilmektedir.  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 Benzer örnekler, özellikleri ve dizi öğeleri için geçerli olabilir.  
  
 **Dolaylı erişim.** Değer türü aracılığıyla dolaylı erişimi de bu hata oluşmasına neden olabilir. Değerini ayarlamaya çalışır aşağıdaki kod örneğinde, göz önünde bulundurun <xref:System.Drawing.Point> dolaylı olarak üzerinden erişerek <xref:System.Windows.Forms.Control.Location%2A>.  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 Yalnızca geçici ayırma için oluşturduğundan önceki örnekte son deyim başarısız <xref:System.Drawing.Point> tarafından döndürülen yapısı <xref:System.Windows.Forms.Control.Location%2A> özelliği. Değer türü yapısıdır ve ifade çalıştıktan sonra geçici yapısı korunmaz. Sorun bildirme ve bir değişken için kullanarak çözülene <xref:System.Windows.Forms.Control.Location%2A>, daha fazla kalıcı ayırma için oluşturan <xref:System.Drawing.Point> yapısı. Aşağıdaki örnek önceki örnekte son deyim değiştirebilirsiniz kodu gösterir.  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 **Hata Kimliği:** BC30068  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Deyim bir ifade için bir değer atarsa, ifade tek yazılabilir değişken, özelliği veya dizi öğesi ile değiştirin.  
  
-   Deyim bir değer türü (genellikle bir yapı) aracılığıyla dolaylı erişim yaparsa, değer türü tutmak için bir değişken oluşturun.  
  
-   Uygun yapısı (veya başka bir değer türü) değişkenine atayın.  
  
-   Bir değer atamak üzere bir özelliğe erişmek için değişkeni kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşleçler ve ifadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Deyimleri](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Sorun giderme yordamları](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
