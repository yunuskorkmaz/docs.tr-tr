---
title: Saf işlevlerini (C#) yeniden düzenleme
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: ed9b33ed2b9669cb4412177086fc648865e4954a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="refactoring-into-pure-functions-c"></a>Saf işlevlerini (C#) yeniden düzenleme

Saf işlevsel Dönüşümlerin önemli bir durum kodu saf işlevler kullanılarak yeniden nasıl öğrenme.  
  
> [!NOTE]
>  İşlevsel programlama içinde ortak terminolojisi saf işlevleri kullanarak programları yeniden Düzenle ' dir. Visual Basic ve C++'de, bu işlevler ilgili dillerde kullanımı ile hizalar. Ancak, C# ' ta işlevleri yöntemleri olarak adlandırılır. Bu tartışma amaçları doğrultusunda, C# yöntemi olarak saf işlevi uygulanır.  
  
 Bu bölümde daha önce belirtildiği gibi saf işlevi iki yararlı özelliklere sahiptir:  
  
-   Hiçbir yan etkisi vardır. İşlev hiçbir değişken veya işlev dışında herhangi bir türde verileri değiştirmez.  
  
-   Tutarlı olur. Aynı dizi girdi verisi verildiğinde, her zaman aynı çıkış değerini döndürür.  
  
 İşlevsel programlama koddan bir gereksiz yan etkiler ve dış bağımlılıkları ortadan kaldırmak için var olan kodu yeniden düzenlemeniz için yoludur. Bu şekilde, var olan kodu saf işlevi sürümlerini oluşturabilirsiniz.  
  
 Bu konuda ele alınmıştır saf işlevi ne olduğu ve ne değildir. [Öğreticisi: WordprocessingML belgede (C#) içerik düzenleme](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) öğretici WordprocessingML belgeyi işlemek nasıl gösterir ve nasıl saf işlevi kullanarak düzenleme için iki örnek verilmiştir.  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a>Yan etkiler ve dış bağımlılıkları ortadan  
 Aşağıdaki örnekler, iki saf olmayan işlevler ve saf işlevi karşılaştırın.  
  
### <a name="non-pure-function-that-changes-a-class-member"></a>Sınıf üyesine değişiklikleri saf olmayan işlevi  
 Aşağıdaki kodda, `HyphenatedConcat` işlevi değil saf işlevi değiştirdiği çünkü `aMember` sınıfı veri üyesi:  
  
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
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```  
StringOne-StringTwo  
```  
  
 Değiştirilen verileri olup ilgisiz olup olmadığını Not `public` veya `private` erişim ya da bir `static` üyesi veya bir örnek üyesine. Saf işlevi işlevi dışında herhangi bir veri değiştirmez.  
  
### <a name="non-pure-function-that-changes-an-argument"></a>Bağımsız değişken değişiklikleri saf olmayan işlevi  
 Kendi parametresinin içeriğini değiştirdiği Ayrıca, aynı bu işlevi aşağıdaki sürümü saf olmadığından `sb`.  
  
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
  
 Çünkü programın bu sürümü aynı ilk sürüm olarak çıktı üretir `HyphenatedConcat` işlevini çağırarak, ilk parametresinin değeri (durum) değişti <xref:System.Text.StringBuilder.Append%2A> üye işlevi. Bu değişiklikle rağmen bu olgu oluştuğunu unutmayın, `HyphenatedConcat` çağrısı değerli parametre geçirme kullanır.  
  
> [!IMPORTANT]
>  Bir parametre değeri tarafından geçirirseniz başvuru türleri için geçirilen bir nesneye başvuru kopyasını sonuçlanır. (Yeni bir nesneye başvuru değişkeni atanıncaya kadar) Bu hala özgün başvuru olarak aynı örnek verilerle ilişkili bir kopyasıdır. Çağrı tarafından başvuru mutlaka bir işlev parametre değiştirmek gerekli değildir.  
  
### <a name="pure-function"></a>Saf işlevi  
Bu program sonraki sürümü nasıl uygulandığını gösterir `HyphenatedConcat` işlev saf işlevi.  
  
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
  
 Yeniden, bu sürümü aynı satır çıktı üretir: `StringOne-StringTwo`. Birleştirilmiş değer korumak için onu Ara değişkeninde depolandığını unutmayın `s2`.  
  
 Çok kullanışlı olabilir bir yaklaşım ise yerel olarak Hanuka işlevlerinin (diğer bir deyişle, bunlar bildirme ve yerel değişkenleri değiştirin), ancak genel olarak saf. Bu tür işlevler birçok arzu composability özelliklere sahip, ancak bazı basit bir döngüsü aynı şeyi başarmak zaman özyineleme kullanmak zorunda gibi daha karışık işlevsel programlama deyimleri, kaçının.  
  
## <a name="standard-query-operators"></a>Standart sorgu işleçleri  
 Bir önemli standart sorgu işleçleri saf işlevleri olarak uygulanan özelliğidir.  
  
 Daha fazla bilgi için bkz: [standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Giriş saf işlevsel Dönüşümleri (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [İşlevsel Programlama ve Kesinlik temelli programlama (C#)](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
