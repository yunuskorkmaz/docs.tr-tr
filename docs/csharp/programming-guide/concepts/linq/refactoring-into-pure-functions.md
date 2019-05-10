---
title: Saf işlevler halinde (C#) yeniden düzenleme
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: 3a498588e9ca1ab85602946b75b593804fa0953a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596891"
---
# <a name="refactoring-into-pure-functions-c"></a>Saf işlevler halinde (C#) yeniden düzenleme

Saf işlevsel dönüşümlere önemli bir yönüdür saf işlevler kullanarak kodunuzu yeniden değiştirmenin nasıl öğrenmeye devam ettiği.  
  
> [!NOTE]
>  Saf işlevler kullanan programlar yeniden düzenleyin, işlevsel programlama, ortak terminoloji olur. Visual Basic ve C++ dillerinde, kendi dillerde işlevleri kullanarak bu hizalar. Ancak, C# dilinde işlevler yöntemi çağrılır. Bu tartışma amacı doğrultusunda, saf işlev C# dilinde bir yöntem olarak uygulanır.  
  
 Bu bölümde daha önce belirtildiği gibi saf işlev iki yararlı özelliklere sahiptir:  
  
- Bu, yan etkileri vardır. İşlevi, tüm değişkenler veya işlev dışında herhangi bir türde verileri değiştirmez.  
  
- Tutarlı olur. Aynı giriş veri kümesi düşünüldüğünde, bu her zaman aynı çıkış değeri döndürür.  
  
 Yollarından fonksiyonel programlama için geçiş, gereksiz yan etkileri ve dış bağımlılıkları ortadan kaldırmak için mevcut kodu yeniden düzenleyin sağlamaktır. Bu şekilde, varolan kod sürümlerini saf işlev oluşturabilirsiniz.  
  
 Bu konuda ele alınmıştır saf işlev ne olduğunu ve ne değildir. [Öğreticisi: WordprocessingML belgesindeki içeriği düzenleme (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) öğretici WordprocessingML belgesinin işlemek nasıl gösterir ve nasıl saf işlev kullanarak yeniden düzenleme için iki örnek verilmiştir.  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a>Yan etkiler ve dış bağımlılıkları ortadan kaldırır.  
 Aşağıdaki örnekler, iki saf olmayan işlevler ve saf işlev karşılaştırın.  
  
### <a name="non-pure-function-that-changes-a-class-member"></a>Sınıf üyesi değişiklikleri saf olmayan işlevi  
 Aşağıdaki kodda, `HyphenatedConcat` işlevi değil, saf işlev değiştirdiği çünkü `aMember` sınıftaki veri üyesi:  
  
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
  
 Bu verilerin değiştirilmesi olup ilgisiz olduğuna dikkat edin `public` veya `private` erişim ya da bir `static` veya bir örnek üyesi. Saf işlev, işlev dışındaki tüm verileri değiştirmez.  
  
### <a name="non-pure-function-that-changes-an-argument"></a>Bağımsız değişken değişiklikleri saf olmayan işlevi  
 Kendi parametre içeriğini değiştirir ayrıca, aynı işlevi aşağıdaki sürümü saf olmadığından `sb`.  
  
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
  
 Çünkü programın bu sürümünü aynı ilk sürümde çıktı üretir `HyphenatedConcat` işlevi, birinci parametresinin değerini (durum) çağırarak değişti <xref:System.Text.StringBuilder.Append%2A> üye işlevi. Bu değişikliği rağmen bu durumu kendi lehine oluştuğunu unutmayın, `HyphenatedConcat` çağrı değerli parametre geçirme kullanır.  
  
> [!IMPORTANT]
>  Değere göre bir parametre geçirirseniz başvuru türleri için geçirilen bir nesneye başvuru bir kopyasını sonuçlanır. (Yeni bir nesneye başvuru değişkenini atanıncaya kadar) Bu hala özgün başvuru aynı örnek verileri ile ilişkili bir kopyasıdır. Başvuru ile çağrı parametreyi değiştirmek bir işlev için mutlaka gerekli değildir.  
  
### <a name="pure-function"></a>Saf işlev  
Bu program'ın sonraki sürümü nasıl uygulayacağınızı gösteren `HyphenatedConcat` işlevi saf işlev.  
  
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
  
 Bu sürümü çıktı satırını yeniden üretir: `StringOne-StringTwo`. Birleştirilmiş değer korumak için bu Ara değişkende depolandığını unutmayın `s2`.  
  
 Yerel olarak Hanuka işlevleri yazmak için kullanışlı bir yaklaşım olan (diğer bir deyişle, bunlar bildirme ve yerel değişkenleri değiştirin), ancak genel olarak saf. Bu tür işlevleri birçok arzu composability özelliklere sahip, ancak bazı basit döngüyü aynı şeyi yaptığınız zaman, özyineleme kullanmak zorunda gibi daha karışık işlevsel programlama deyimlerini, kaçının.  
  
## <a name="standard-query-operators"></a>Standart sorgu işleçleri  
 Standart sorgu işleçlerinin önemli bir özelliği, saf işlevler uygulanan ' dir.  
  
 Daha fazla bilgi için [standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Giriş saf işlevsel dönüşümlere (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [İşlevsel Programlama ve Kesin programlama karşılaştırması (C#)](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
