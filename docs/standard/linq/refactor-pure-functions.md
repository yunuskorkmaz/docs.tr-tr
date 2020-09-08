---
title: Saf işlevlerde yeniden düzenleme-LINQ to XML
description: Saf işlevler ve kodu yeniden düzenleme için nasıl kullanılacağı hakkında bilgi edinin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: 18418a1fc39bee9f08cbe92d42c842e3fc9e148a
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553916"
---
# <a name="refactor-into-pure-functions-linq-to-xml"></a>Saf işlevlere yeniden düzenleme (LINQ to XML)

Saf işlevsel dönüştürmelerin önemli bir yönü, saf işlevleri kullanarak kodu yeniden düzenleme hakkında bilgi ediniyor.

> [!NOTE]
> İşlevsel programlamada ortak terminoloji, programları saf işlevleri kullanarak yeniden düzenleme biçimleridir. Visual Basic ve C++ ' da bu, ilgili dillerdeki işlevlerin kullanımıyla hizalanır. Ancak C# ' de işlevleri yöntemler olarak adlandırılır. Bu tartışmanın amaçları doğrultusunda, saf bir işlev C# dilinde bir yöntem olarak uygulanır.

Daha önce bu bölümde belirtildiği gibi, saf bir işlev iki yararlı özelliğe sahiptir:

- Yan etkileri yoktur. İşlev herhangi bir değişken veya işlev dışındaki herhangi bir türdeki verileri değiştirmez.
- Tutarlıdır. Aynı giriş verisi kümesi verildiğinde, her zaman aynı çıkış değerini döndürür.

İşlevsel programlamaya geçiş yapmanın bir yolu, gereksiz yan etkileri ve dış bağımlılıkları ortadan kaldırmak için mevcut kodu yeniden düzenleme yöntemidir. Bu şekilde, var olan kodun saf işlev sürümlerini oluşturabilirsiniz.

Bu makalede, saf bir işlevin ne olduğu ve ne olmadığı açıklanmaktadır. [Öğretici: bir WordprocessingML belgesi öğreticisindeki Içeriği değiştirme](xml-shape-wordprocessingml-documents.md) bir WordprocessingML belgesinin nasıl düzenleneceğini gösterir ve saf bir işlev kullanarak yeniden düzenleme ile iki örnek içerir.

Aşağıdaki örneklerde, saf olmayan iki işlev ve bir saf işlev kontrast vardır.

## <a name="example-implement-a-non-pure-function-that-changes-a-static-class-member"></a>Örnek: statik sınıf üyesini değiştiren saf olmayan bir işlev uygulama

Aşağıdaki kodda, `HyphenatedConcat` statik sınıf üyesini değiştirdiği için işlev saf bir işlev değildir `aMember` :

```csharp
public class Program
{
    private static string aMember = "StringOne";

    public static void HyphenatedConcat(string appendStr)
    {
        aMember += '-' + appendStr;
    }

    public static void Main()
    {
        HyphenatedConcat("StringTwo");
        Console.WriteLine(aMember);
    }
}
```

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

Bu örnek aşağıdaki çıktıyı üretir:

```output
StringOne-StringTwo
```

Değiştirilen verilerin, veya erişimi olduğunu ya da `public` `private` `static` üye, `shared` üye veya örnek üyesi olduğunu unutmayın. Saf işlev, işlevin dışındaki verileri değiştirmez.

## <a name="example-implement-a-non-pure-function-that-changes-a-parameter"></a>Örnek: bir parametreyi değiştiren saf olmayan bir işlev uygulama

Ayrıca, parametresinin içeriğini değiştirdiği için aynı işlevin aşağıdaki sürümü saf değildir `sb` .

```csharp
public class Program
{
    public static void HyphenatedConcat(StringBuilder sb, String appendStr)
    {
        sb.Append('-' + appendStr);
    }

    public static void Main()
    {
        StringBuilder sb1 = new StringBuilder("StringOne");
        HyphenatedConcat(sb1, "StringTwo");
        Console.WriteLine(sb1);
    }
}
```

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

Programın bu sürümü ilk sürümle aynı çıktıyı üretir, çünkü `HyphenatedConcat` işlev üye işlevini çağırarak ilk parametresinin değerini (durum) değiştirdi <xref:System.Text.StringBuilder.Append%2A> . Bu değişiklik, `HyphenatedConcat` değer çağırma parametresi geçen olgusuna rağmen oluşur.

> [!IMPORTANT]
> Başvuru türleri için bir parametreyi değere göre geçirirseniz, başvurunun geçirildiği bir nesnenin kopyasına neden olur. Bu kopya, özgün başvurusuyla aynı örnek verileriyle ilişkili olmaya devam eder (başvuru değişkeni yeni bir nesneye atanana kadar). Bir parametreyi değiştirmek için bir işlev için başvuruya göre arama gerekli değildir.

## <a name="example-implement-a-pure-function"></a>Örnek: saf bir işlev uygulama

Programın bu sonraki sürümü, `HyphenatedConcat` işlevinin saf işlev olarak nasıl uygulanacağını gösterir.

```csharp
class Program
{
    public static string HyphenatedConcat(string s, string appendStr)
    {
        return (s + '-' + appendStr);
    }

    public static void Main(string[] args)
    {
        string s1 = "StringOne";
        string s2 = HyphenatedConcat(s1, "StringTwo");
        Console.WriteLine(s2);
    }
}
```

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

## <a name="standard-query-operators"></a>Standart sorgu işleçleri

Standart sorgu işleçlerinin önemli bir özelliği, saf işlevler olarak uygulanırlar.

Daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış (C#)](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) ve [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Saf işlevsel dönüşümlere giriş](introduction-pure-functional-transformations.md)
- [Fonksiyonel programlama ve kesinlik temelli programlama karşılaştırması](functional-vs-imperative-programming.md)
