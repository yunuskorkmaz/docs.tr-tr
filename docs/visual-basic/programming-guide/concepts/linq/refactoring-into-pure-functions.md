---
title: "Saf işlevleri (Visual Basic) yeniden düzenleme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d0a1b8d314cf1403ef5065e5432f7acd15ebb440
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="refactoring-into-pure-functions-visual-basic"></a>Saf işlevleri (Visual Basic) yeniden düzenleme
Saf işlevsel Dönüşümlerin önemli bir durum kodu saf işlevler kullanılarak yeniden nasıl öğrenme.  
  
 Bu bölümde daha önce belirtildiği gibi saf işlevi iki yararlı özelliklere sahiptir:  
  
-   Hiçbir yan etkisi vardır. İşlev hiçbir değişken veya işlev dışında herhangi bir türde verileri değiştirmez.  
  
-   Tutarlı olur. Aynı dizi girdi verisi verildiğinde, her zaman aynı çıkış değerini döndürür.  
  
 İşlevsel programlama koddan bir gereksiz yan etkiler ve dış bağımlılıkları ortadan kaldırmak için var olan kodu yeniden düzenlemeniz için yoludur. Bu şekilde, var olan kodu saf işlevi sürümlerini oluşturabilirsiniz.  
  
 Bu konuda ele alınmıştır saf işlevi ne olduğu ve ne değildir. [Öğreticisi: düzenleme içerik WordprocessingML belgedeki (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) öğretici WordprocessingML belgeyi işlemek nasıl gösterir ve nasıl saf işlevi kullanarak düzenleme için iki örnek verilmiştir.  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a>Yan etkiler ve dış bağımlılıkları ortadan  
 Aşağıdaki örnekler, iki saf olmayan işlevler ve saf işlevi karşılaştırın.  
  
### <a name="non-pure-function-that-changes-a-class-member"></a>Sınıf üyesine değişiklikleri saf olmayan işlevi  
 Aşağıdaki kodda, `HypenatedConcat` işlevi değil saf işlevi değiştirdiği çünkü `aMember` sınıfı veri üyesi:  
  
```vb  
Module Module1  
    Dim aMember As String = "StringOne"  
  
    Public Sub HypenatedConcat(ByVal appendStr As String)  
        aMember = aMember & "-" & appendStr  
    End Sub  
  
    Sub Main()  
        HypenatedConcat("StringTwo")  
        Console.WriteLine(aMember)  
    End Sub  
End Module  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```  
StringOne-StringTwo  
```  
  
 Değiştirilen verileri olup ilgisiz olup olmadığını Not `public` veya `private` erişim ya da bir `shared` üyesi veya bir örnek üyesine. Saf işlevi işlevi dışında herhangi bir veri değiştirmez.  
  
### <a name="non-pure-function-that-changes-an-argument"></a>Bağımsız değişken değişiklikleri saf olmayan işlevi  
 Kendi parametresinin içeriğini değiştirdiği Ayrıca, aynı bu işlevi aşağıdaki sürümü saf olmadığından `sb`.  
  
```vb  
Module Module1  
    Public Sub HypenatedConcat(ByVal sb As StringBuilder, ByVal appendStr As String)  
        sb.Append("-" & appendStr)  
    End Sub  
  
    Sub Main()  
        Dim sb1 As StringBuilder = New StringBuilder("StringOne")  
        HypenatedConcat(sb1, "StringTwo")  
        Console.WriteLine(sb1)  
    End Sub  
End Module  
```  
  
 Çünkü programın bu sürümü aynı ilk sürüm olarak çıktı üretir `HypenatedConcat` işlevini çağırarak, ilk parametresinin değeri (durum) değişti <xref:System.Text.StringBuilder.Append%2A> üye işlevi. Bu değişiklikle rağmen bu olgu oluştuğunu unutmayın, `HypenatedConcat` çağrısı değerli parametre geçirme kullanır.  
  
> [!IMPORTANT]
>  Bir parametre değeri tarafından geçirirseniz başvuru türleri için geçirilen bir nesneye başvuru kopyasını sonuçlanır. (Yeni bir nesneye başvuru değişkeni atanıncaya kadar) Bu hala özgün başvuru olarak aynı örnek verilerle ilişkili bir kopyasıdır. Çağrı tarafından başvuru mutlaka bir işlev parametre değiştirmek gerekli değildir.  
  
### <a name="pure-function"></a>Saf işlevi  
 Bu program sonraki sürümü hows nasıl uygulanacağını `HypenatedConcat` işlev saf işlevi.  
  
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
  
 Yeniden, bu sürümü aynı satır çıktı üretir: `StringOne-StringTwo`. Birleştirilmiş değer korumak için onu Ara değişkeninde depolandığını unutmayın `s2`.  
  
 Çok kullanışlı olabilir bir yaklaşım ise yerel olarak Hanuka işlevlerinin (diğer bir deyişle, bunlar bildirme ve yerel değişkenleri değiştirin), ancak genel olarak saf. Bu tür işlevler birçok arzu composability özelliklere sahip, ancak bazı basit bir döngüsü aynı şeyi başarmak zaman özyineleme kullanmak zorunda gibi daha karışık işlevsel programlama deyimleri, kaçının.  
  
## <a name="standard-query-operators"></a>Standart sorgu işleçleri  
 Bir önemli standart sorgu işleçleri saf işlevleri olarak uygulanan özelliğidir.  
  
 Daha fazla bilgi için bkz: [standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Giriş saf işlevsel Dönüşümleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [İşlevsel Programlama vs. Kesinlik temelli programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
