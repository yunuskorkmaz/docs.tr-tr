---
title: İfade bir değerdir, bu nedenle atama işleminin hedefi olamaz
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: 9e4dbaf2f2800454c673cd58ddec4cf0f6e5c6b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409515"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a>İfade bir değerdir, bu nedenle atama işleminin hedefi olamaz

Deyim bir ifadeye değer atamaya çalışır. Çalışma zamanında yalnızca yazılabilir bir değişkene, özelliğe veya dizi öğesine bir değer atayabilirsiniz. Aşağıdaki örnekte bu hatanın nasıl gerçekleşebileceği gösterilmektedir.

```vb
Dim yesterday As Integer
ReadOnly maximum As Integer = 45
yesterday + 1 = DatePart(DateInterval.Day, Now)
' The preceding line is an ERROR because of an expression on the left.
maximum = 50
' The preceding line is an ERROR because maximum is declared ReadOnly.
```

Benzer örnekler Özellikler ve dizi öğelerine uygulanabilir.

**Dolaylı erişim.** Bir değer türü üzerinden dolaylı erişim bu hatayı da oluşturabilir. Aşağıdaki kod örneğini göz önünde bulundurun <xref:System.Drawing.Point> . Bu, değeri dolaylı olarak aracılığıyla uygulamasına erişerek değerini ayarlamaya çalışır <xref:System.Windows.Forms.Control.Location%2A> .

```vb
' Assume this code runs inside Form1.
Dim exitButton As New System.Windows.Forms.Button()
exitButton.Text = "Exit this form"
exitButton.Location.X = 140
' The preceding line is an ERROR because of no storage for Location.
```

Önceki örneğin son açıklaması, <xref:System.Drawing.Point> özelliği tarafından döndürülen yapı için yalnızca geçici bir ayırma oluşturduğundan başarısız olur <xref:System.Windows.Forms.Control.Location%2A> . Yapı bir değer türüdür ve ifade çalıştıktan sonra geçici yapı korunmaz. Bu sorun, için bir değişkeni bildirerek ve kullanılarak çözümlenir ve <xref:System.Windows.Forms.Control.Location%2A> Bu da yapı için daha kalıcı bir ayırma oluşturur <xref:System.Drawing.Point> . Aşağıdaki örnek, önceki örnekte yer alan son deyimin yerini alacak kodu gösterir.

```vb
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)
exitButton.Location = exitLocation
```

**Hata kimliği:** BC30068

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Deyim bir ifadeye değer atadığında, ifadeyi tek bir yazılabilir değişken, özellik veya dizi öğesiyle değiştirin.

- İfade bir değer türü (genellikle bir yapı) üzerinden dolaylı erişim yapıyorsa, değer türünü tutmak için bir değişken oluşturun.

- Değişkene uygun yapıyı (veya başka bir değer türünü) atayın.

- Değerini bir değer atamak için özelliğe erişmek üzere kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [İşleçler ve Ifadeler](../../programming-guide/language-features/operators-and-expressions/index.md)
- [Deyimler](../../programming-guide/language-features/statements.md)
- [Yordam Sorunlarını Giderme](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
