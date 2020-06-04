---
title: Saf İşlevler Halinde Yeniden Düzenleme
ms.date: 07/20/2015
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
ms.openlocfilehash: 415b088661eca347330f4776901d68ee514d8dad
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413485"
---
# <a name="refactoring-into-pure-functions-visual-basic"></a>Saf IŞLEVLERE yeniden düzenleme (Visual Basic)

Saf işlevsel dönüştürmelerin önemli bir yönü, saf işlevleri kullanarak kodu yeniden düzenleme hakkında bilgi ediniyor.

Daha önce bu bölümde belirtildiği gibi, saf bir işlev iki yararlı özelliğe sahiptir:

- Yan etkileri yoktur. İşlev herhangi bir değişken veya işlev dışındaki herhangi bir türdeki veriyi değiştirmez.

- Tutarlıdır. Aynı giriş verisi kümesi verildiğinde, her zaman aynı çıkış değerini döndürür.

 İşlevsel programlamaya geçiş yapmanın bir yolu, gereksiz yan etkileri ve dış bağımlılıkları ortadan kaldırmak için mevcut kodu yeniden düzenleme yöntemidir. Bu şekilde, var olan kodun saf işlev sürümlerini oluşturabilirsiniz.

Bu konuda, saf bir işlevin ne olduğu ve ne olmadığı açıklanmaktadır. [Öğretici: bir WordprocessingML belgesi (Visual Basic) öğreticisindeki Içeriği düzenleme](tutorial-manipulating-content-in-a-wordprocessingml-document.md) bir WordprocessingML belgesinin nasıl düzenleneceğini gösterir ve saf bir işlev kullanarak yeniden düzenleme ile iki örnek içerir.

## <a name="eliminating-side-effects-and-external-dependencies"></a>Yan etkileri ve dış bağımlılıkları ortadan kaldırma

Aşağıdaki örneklerde, saf olmayan iki işlev ve bir saf işlev kontrast vardır.

### <a name="non-pure-function-that-changes-a-class-member"></a>Bir sınıf üyesini değiştiren saf olmayan Işlev

Aşağıdaki kodda, `HyphenatedConcat` işlev saf bir işlev değildir, çünkü `aMember` sınıfındaki veri üyesini değiştirir:

```vb
Module Module1
    Dim aMember As String = "StringOne"

    Public Sub HyphenatedConcat(ByVal appendStr As String)
        aMember = aMember & "-" & appendStr
    End Sub

    Sub Main()
        HyphenatedConcat("StringTwo")
        Console.WriteLine(aMember)
    End Sub
End Module
```

Bu kod aşağıdaki çıktıyı üretir:

```console
StringOne-StringTwo
```

Değiştirilen verilerin veya `public` `private` bir `shared` üye ya da bir örnek üyesi olup olmadığı konusunda ilgisiz olduğunu unutmayın. Saf bir işlev, işlevin dışındaki herhangi bir veriyi değiştirmez.

### <a name="non-pure-function-that-changes-an-argument"></a>Bir bağımsız değişkeni değiştiren saf olmayan Işlev

Ayrıca, parametresinin içeriğini değiştirdiği için aynı işlevin aşağıdaki sürümü saf değildir `sb` .

```vb
Module Module1
    Public Sub HyphenatedConcat(ByVal sb As StringBuilder, ByVal appendStr As String)
        sb.Append("-" & appendStr)
    End Sub

    Sub Main()
        Dim sb1 As StringBuilder = New StringBuilder("StringOne")
        HyphenatedConcat(sb1, "StringTwo")
        Console.WriteLine(sb1)
    End Sub
End Module
```

Programın bu sürümü ilk sürümle aynı çıktıyı üretir, çünkü `HyphenatedConcat` işlev üye işlevini çağırarak ilk parametresinin değerini (durum) değiştirdi <xref:System.Text.StringBuilder.Append%2A> . Bu değişiklik, bu olguyu, çağrı- `HyphenatedConcat` değer parametresini kullanan bir olgusuna rağmen oluştuğunu unutmayın.

> [!IMPORTANT]
> Başvuru türleri için bir parametreyi değere göre geçirirseniz, başvurunun geçirildiği bir nesnenin kopyasına neden olur. Bu kopya, özgün başvurusuyla aynı örnek verileriyle ilişkili olmaya devam eder (başvuru değişkeni yeni bir nesneye atanana kadar). Bir parametreyi değiştirmek için bir işlev için başvuruya göre arama gerekli değildir.

### <a name="pure-function"></a>Saf Işlev

Programın bu sonraki sürümü, `HyphenatedConcat` işlevin saf işlev olarak nasıl uygulanacağını barındırdı.

```vb
Module Module1
    Public Function HyphenatedConcat(ByVal s As String, ByVal appendStr As String) As String
        Return (s & "-" & appendStr)
    End Function

    Sub Main()
        Dim s1 As String = "StringOne"
        Dim s2 As String = HyphenatedConcat(s1, "StringTwo")
        Console.WriteLine(s2)
    End Sub
End Module
```

Yine, bu sürüm aynı çıkış satırını üretir: `StringOne-StringTwo` . Birleştirilmiş değeri bekletmek için, ara değişkende depolandığını unutmayın `s2` .

Çok yararlı olabilecek bir yaklaşım, yerel olarak etkileyici olan işlevleri yazmak (yani yerel değişkenleri bildirdikleri ve değiştirdiklerinde), ancak Global olarak saf bir yaklaşımdır. Bu gibi işlevler, istenen ek özelliklerin çoğuna sahiptir, ancak basit bir döngü aynı şeyi gerçekleştirirken özyineleme kullanmak zorunda kalmadan, daha fazla çalışan işlevsel programlama deyimidir.

## <a name="standard-query-operators"></a>Standart sorgu Işleçleri

Standart sorgu işleçlerinin önemli bir özelliği, saf işlevler olarak uygulanırlar.

Daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış (Visual Basic)](standard-query-operators-overview.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Saf Işlevsel dönüşümlere giriş (Visual Basic)](introduction-to-pure-functional-transformations.md)
- [Fonksiyonel programlama ile kesinlik temelli programlama (Visual Basic)](functional-programming-vs-imperative-programming.md)
