---
title: (Visual Basic) saf işlevler halinde yeniden düzenleme
ms.date: 07/20/2015
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
ms.openlocfilehash: 0a37b30278c850256355612cec09a4c017c7adc2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787172"
---
# <a name="refactoring-into-pure-functions-visual-basic"></a>(Visual Basic) saf işlevler halinde yeniden düzenleme

Saf işlevsel dönüşümlere önemli bir yönüdür saf işlevler kullanarak kodunuzu yeniden değiştirmenin nasıl öğrenmeye devam ettiği.

Bu bölümde daha önce belirtildiği gibi saf işlev iki yararlı özelliklere sahiptir:

- Bu, yan etkileri vardır. İşlevi, tüm değişkenler veya işlev dışında herhangi bir türde verileri değiştirmez.

- Tutarlı olur. Aynı giriş veri kümesi düşünüldüğünde, bu her zaman aynı çıkış değeri döndürür.

 Yollarından fonksiyonel programlama için geçiş, gereksiz yan etkileri ve dış bağımlılıkları ortadan kaldırmak için mevcut kodu yeniden düzenleyin sağlamaktır. Bu şekilde, varolan kod sürümlerini saf işlev oluşturabilirsiniz.

Bu konuda ele alınmıştır saf işlev ne olduğunu ve ne değildir. [Öğreticisi: (Visual Basic) WordprocessingML belgesindeki içeriği düzenleme](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) öğretici WordprocessingML belgesinin işlemek nasıl gösterir ve nasıl saf işlev kullanarak yeniden düzenleme için iki örnek verilmiştir.

## <a name="eliminating-side-effects-and-external-dependencies"></a>Yan etkiler ve dış bağımlılıkları ortadan kaldırır.

Aşağıdaki örnekler, iki saf olmayan işlevler ve saf işlev karşılaştırın.

### <a name="non-pure-function-that-changes-a-class-member"></a>Sınıf üyesi değişiklikleri saf olmayan işlevi

Aşağıdaki kodda, `HyphenatedConcat` işlevi değil, saf işlev değiştirdiği çünkü `aMember` sınıftaki veri üyesi:

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

```
StringOne-StringTwo
```

Bu verilerin değiştirilmesi olup ilgisiz olduğuna dikkat edin `public` veya `private` erişim ya da bir `shared` veya bir örnek üyesi. Saf işlev, işlev dışındaki tüm verileri değiştirmez.

### <a name="non-pure-function-that-changes-an-argument"></a>Bağımsız değişken değişiklikleri saf olmayan işlevi

Kendi parametre içeriğini değiştirir ayrıca, aynı işlevi aşağıdaki sürümü saf olmadığından `sb`.

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

Çünkü programın bu sürümünü aynı ilk sürümde çıktı üretir `HyphenatedConcat` işlevi, birinci parametresinin değerini (durum) çağırarak değişti <xref:System.Text.StringBuilder.Append%2A> üye işlevi. Bu değişikliği rağmen bu durumu kendi lehine oluştuğunu unutmayın, `HyphenatedConcat` çağrı değerli parametre geçirme kullanır.

> [!IMPORTANT]
> Değere göre bir parametre geçirirseniz başvuru türleri için geçirilen bir nesneye başvuru bir kopyasını sonuçlanır. (Yeni bir nesneye başvuru değişkenini atanıncaya kadar) Bu hala özgün başvuru aynı örnek verileri ile ilişkili bir kopyasıdır. Başvuru ile çağrı parametreyi değiştirmek bir işlev için mutlaka gerekli değildir.

### <a name="pure-function"></a>Saf işlev

Bu program'ın sonraki sürümü sorularının yanıtlarını nasıl uygulanacağı `HyphenatedConcat` işlevi saf işlev.

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

Bu sürümü çıktı satırını yeniden üretir: `StringOne-StringTwo`. Birleştirilmiş değer korumak için bu Ara değişkende depolandığını unutmayın `s2`.

Yerel olarak Hanuka işlevleri yazmak için kullanışlı bir yaklaşım olan (diğer bir deyişle, bunlar bildirme ve yerel değişkenleri değiştirin), ancak genel olarak saf. Bu tür işlevleri birçok arzu composability özelliklere sahip, ancak bazı basit döngüyü aynı şeyi yaptığınız zaman, özyineleme kullanmak zorunda gibi daha karışık işlevsel programlama deyimlerini, kaçının.

## <a name="standard-query-operators"></a>Standart sorgu işleçleri

Standart sorgu işleçlerinin önemli bir özelliği, saf işlevler uygulanan ' dir.

Daha fazla bilgi için [standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Saf işlevsel dönüşümlere (Visual Basic) giriş](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [İşlevsel Programlama ve Kesin programlama karşılaştırması (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
