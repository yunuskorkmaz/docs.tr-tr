---
title: İfade bir değerdir, bu nedenle atama işleminin hedefi olamaz
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: b2c33cb9ba0479df5e69b6979a789253f9fae565
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597339"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a>İfade bir değerdir, bu nedenle atama işleminin hedefi olamaz
Bir deyim, deyim için bir değer atamak çalışır. Yalnızca bir yazılabilir değişken, özelliği veya dizi öğesi için çalışma zamanında bir değer atayabilirsiniz. Aşağıdaki örnek nasıl bu hata oluşabilir gösterir.  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 Benzer örnekler dizi öğeleri ve özellikleri ile uygulayabilirsiniz.  
  
 **Dolaylı erişim.** Bir değer türü aracılığıyla dolaylı erişim de bu hata oluşturabilirsiniz. Değerini ayarlama girişiminde aşağıdaki kod örneği göz önünde bulundurun <xref:System.Drawing.Point> dolaylı olarak aracılığıyla erişerek <xref:System.Windows.Forms.Control.Location%2A>.  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 Yalnızca geçici bir ayırma için oluşturduğundan önceki örnekteki son deyim başarısız <xref:System.Drawing.Point> yapısı tarafından döndürülen <xref:System.Windows.Forms.Control.Location%2A> özelliği. Bir yapı bir değer türüdür ve ifade çalıştıktan sonra geçici yapısı korunmaz. Sorun bildirme ve kullanma için bir değişken çözülür <xref:System.Windows.Forms.Control.Location%2A>, için daha kalıcı bir ayırma oluşturur <xref:System.Drawing.Point> yapısı. Aşağıdaki örnek, önceki örnekte bulunan son deyim değiştirebilirsiniz kod gösterir.  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 **Hata Kimliği:** BC30068  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Deyimi, deyim için bir değer atar, ifade tek yazılabilir değişkeni, özelliği veya dizi öğesi ile değiştirin.  
  
-   İfade bir değer türü (genellikle bir yapı) aracılığıyla dolaylı erişim yaparsa, değer türü tutacak bir değişken oluşturun.  
  
-   Uygun yapısını (veya başka bir değer türü) değişkene atayın.  
  
-   Bir değer atamak üzere bir özelliğe erişmek için bu değişkeni kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İşleçler ve İfadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
- [Yordam Sorunlarını Giderme](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
