---
title: Saf IŞLEVLERE yeniden düzenleme (C#)
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: 4cf91ff078bd1c4582daa05475a91c4a4ecaba3e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253105"
---
# <a name="refactoring-into-pure-functions-c"></a>Saf IŞLEVLERE yeniden düzenleme (C#)

Saf işlevsel dönüştürmelerin önemli bir yönü, saf işlevleri kullanarak kodu yeniden düzenleme hakkında bilgi ediniyor.  
  
> [!NOTE]
> İşlevsel programlamada ortak terminoloji, programları saf işlevleri kullanarak yeniden düzenleme biçimleridir. Visual Basic ve C++' de, bu, ilgili dillerdeki işlevlerin kullanımıyla hizalanır. Ancak, içindeki C#işlevleri yöntemler olarak adlandırılır. Bu tartışmanın amaçları doğrultusunda, saf bir işlev ' de C#bir yöntem olarak uygulanır.  
  
 Daha önce bu bölümde belirtildiği gibi, saf bir işlev iki yararlı özelliğe sahiptir:  
  
- Yan etkileri yoktur. İşlev herhangi bir değişken veya işlev dışındaki herhangi bir türdeki veriyi değiştirmez.  
  
- Tutarlıdır. Aynı giriş verisi kümesi verildiğinde, her zaman aynı çıkış değerini döndürür.  
  
 İşlevsel programlamaya geçiş yapmanın bir yolu, gereksiz yan etkileri ve dış bağımlılıkları ortadan kaldırmak için mevcut kodu yeniden düzenleme yöntemidir. Bu şekilde, var olan kodun saf işlev sürümlerini oluşturabilirsiniz.  
  
 Bu konuda, saf bir işlevin ne olduğu ve ne olmadığı açıklanmaktadır. [Öğretici: WordprocessingML belgesi (C#)](./shape-of-wordprocessingml-documents.md) öğreticisindeki içeriği işlemek bir WordprocessingML belgesinin nasıl düzenleneceğini gösterir ve saf bir işlev kullanarak yeniden düzenleme ile iki örnek içerir.  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a>Yan etkileri ve dış bağımlılıkları ortadan kaldırma  
 Aşağıdaki örneklerde, saf olmayan iki işlev ve bir saf işlev kontrast vardır.  
  
### <a name="non-pure-function-that-changes-a-class-member"></a>Bir sınıf üyesini değiştiren saf olmayan Işlev  
 Aşağıdaki kodda, `HyphenatedConcat` işlev saf bir işlev değildir, çünkü sınıfındaki `aMember` veri üyesini değiştirir:  
  
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
  
```output  
StringOne-StringTwo  
```  
  
 Değiştirilen `public` `static` verilerin veya bir üye ya da bir örnek üyesi olup olmadığı konusunda ilgisiz olduğunu unutmayın. `private` Saf bir işlev, işlevin dışındaki herhangi bir veriyi değiştirmez.  
  
### <a name="non-pure-function-that-changes-an-argument"></a>Bir bağımsız değişkeni değiştiren saf olmayan Işlev  
 Ayrıca, parametresinin `sb`içeriğini değiştirdiği için aynı işlevin aşağıdaki sürümü saf değildir.  
  
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
  
 Programın bu sürümü ilk sürümle aynı çıktıyı üretir, çünkü `HyphenatedConcat` işlev <xref:System.Text.StringBuilder.Append%2A> üye işlevini çağırarak ilk parametresinin değerini (durum) değiştirdi. Bu değişiklik, bu olguyu, çağrı- `HyphenatedConcat` değer parametresini kullanan bir olgusuna rağmen oluştuğunu unutmayın.  
  
> [!IMPORTANT]
> Başvuru türleri için bir parametreyi değere göre geçirirseniz, başvurunun geçirildiği bir nesnenin kopyasına neden olur. Bu kopya, özgün başvurusuyla aynı örnek verileriyle ilişkili olmaya devam eder (başvuru değişkeni yeni bir nesneye atanana kadar). Bir parametreyi değiştirmek için bir işlev için başvuruya göre arama gerekli değildir.  
  
### <a name="pure-function"></a>Saf Işlev  
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
  
 Yine, bu sürüm aynı çıkış satırını üretir: `StringOne-StringTwo`. Birleştirilmiş değeri bekletmek için, ara değişkende `s2`depolandığını unutmayın.  
  
 Çok yararlı olabilecek bir yaklaşım, yerel olarak etkileyici olan işlevleri yazmak (yani yerel değişkenleri bildirdikleri ve değiştirdiklerinde), ancak Global olarak saf bir yaklaşımdır. Bu gibi işlevler, istenen ek özelliklerin çoğuna sahiptir, ancak basit bir döngü aynı şeyi gerçekleştirirken özyineleme kullanmak zorunda kalmadan, daha fazla çalışan işlevsel programlama deyimidir.  
  
## <a name="standard-query-operators"></a>Standart sorgu Işleçleri  
 Standart sorgu işleçlerinin önemli bir özelliği, saf işlevler olarak uygulanırlar.  
  
 Daha fazla bilgi için bkz. [Standart sorgu IşleçlerineC#genel bakış ()](./standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Saf Işlevsel Dönüştürmelere giriş (C#)](./introduction-to-pure-functional-transformations.md)
- [İşlevsel Programlama ve Kesinlik temelli programlamaC#()](./functional-programming-vs-imperative-programming.md)
