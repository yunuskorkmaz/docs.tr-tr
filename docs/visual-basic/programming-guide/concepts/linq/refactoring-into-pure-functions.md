---
title: Saf IŞLEVLERE yeniden düzenleme (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
ms.openlocfilehash: e951b3e9108f26a9c861eb49c44bb0a510131819
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834911"
---
# <a name="refactoring-into-pure-functions-visual-basic"></a>Saf IŞLEVLERE yeniden düzenleme (Visual Basic)

Saf işlevsel dönüştürmelerin önemli bir yönü, saf işlevleri kullanarak kodu yeniden düzenleme hakkında bilgi ediniyor.

Daha önce bu bölümde belirtildiği gibi, saf bir işlev iki yararlı özelliğe sahiptir:

- Yan etkileri yoktur. İşlev herhangi bir değişken veya işlev dışındaki herhangi bir türdeki veriyi değiştirmez.

- Tutarlıdır. Aynı giriş verisi kümesi verildiğinde, her zaman aynı çıkış değerini döndürür.

 İşlevsel programlamaya geçiş yapmanın bir yolu, gereksiz yan etkileri ve dış bağımlılıkları ortadan kaldırmak için mevcut kodu yeniden düzenleme yöntemidir. Bu şekilde, var olan kodun saf işlev sürümlerini oluşturabilirsiniz.

Bu konuda, saf bir işlevin ne olduğu ve ne olmadığı açıklanmaktadır. [Öğretici: bir WordprocessingML belgesi (Visual Basic) öğreticisindeki Içeriği düzenleme](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) bir WordprocessingML belgesinin nasıl düzenleneceğini gösterir ve saf bir işlev kullanarak yeniden düzenleme ile iki örnek içerir.

## <a name="eliminating-side-effects-and-external-dependencies"></a>Yan etkileri ve dış bağımlılıkları ortadan kaldırma

Aşağıdaki örneklerde, saf olmayan iki işlev ve bir saf işlev kontrast vardır.

### <a name="non-pure-function-that-changes-a-class-member"></a>Bir sınıf üyesini değiştiren saf olmayan Işlev

Aşağıdaki kodda `HyphenatedConcat` işlevi saf bir işlev değildir, çünkü sınıfta `aMember` veri üyesini değiştirir:

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

Değiştirilen verilerin `public` veya `private` erişimine sahip olup olmadığını veya `shared` üyesi mi yoksa örnek üyesini mi olduğunu unutmayın. Saf bir işlev, işlevin dışındaki herhangi bir veriyi değiştirmez.

### <a name="non-pure-function-that-changes-an-argument"></a>Bir bağımsız değişkeni değiştiren saf olmayan Işlev

Ayrıca, aynı işlevin aşağıdaki sürümü saf değildir çünkü parametresinin içeriğini değiştirir, `sb`.

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

Programın bu sürümü ilk sürümle aynı çıktıyı üretir, çünkü `HyphenatedConcat` işlevi, <xref:System.Text.StringBuilder.Append%2A> üye işlevini çağırarak ilk parametresinin değerini (durum) değiştirdi. Bu değişiklik, `HyphenatedConcat` ' ın değer olarak çağırma parametresi geçirdiğine rağmen meydana gelir.

> [!IMPORTANT]
> Başvuru türleri için bir parametreyi değere göre geçirirseniz, başvurunun geçirildiği bir nesnenin kopyasına neden olur. Bu kopya, özgün başvurusuyla aynı örnek verileriyle ilişkili olmaya devam eder (başvuru değişkeni yeni bir nesneye atanana kadar). Bir parametreyi değiştirmek için bir işlev için başvuruya göre arama gerekli değildir.

### <a name="pure-function"></a>Saf Işlev

Programın bu sonraki sürümü, `HyphenatedConcat` işlevini saf işlev olarak nasıl uygulayacağınızı barındırdı.

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

Yine, bu sürüm aynı çıkış satırını üretir: `StringOne-StringTwo`. Art arda gelen değeri bekletmek için `s2` ara değişkeninde depolandığını unutmayın.

Çok yararlı olabilecek bir yaklaşım, yerel olarak etkileyici olan işlevleri yazmak (yani yerel değişkenleri bildirdikleri ve değiştirdiklerinde), ancak Global olarak saf bir yaklaşımdır. Bu gibi işlevler, istenen ek özelliklerin çoğuna sahiptir, ancak basit bir döngü aynı şeyi gerçekleştirirken özyineleme kullanmak zorunda kalmadan, daha fazla çalışan işlevsel programlama deyimidir.

## <a name="standard-query-operators"></a>Standart sorgu Işleçleri

Standart sorgu işleçlerinin önemli bir özelliği, saf işlevler olarak uygulanırlar.

Daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Saf Işlevsel dönüşümlere giriş (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [Fonksiyonel programlama ile kesinlik temelli programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
