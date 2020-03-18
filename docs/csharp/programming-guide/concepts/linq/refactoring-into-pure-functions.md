---
title: Saf Fonksiyonlara Yeniden Düzenleme (C#)
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: 4cf91ff078bd1c4582daa05475a91c4a4ecaba3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253105"
---
# <a name="refactoring-into-pure-functions-c"></a>Saf Fonksiyonlara Yeniden Düzenleme (C#)

Saf işlevsel dönüşümlerin önemli bir yönü, saf işlevleri kullanarak kodu nasıl yeniden düzenlemeyi öğrenmektir.  
  
> [!NOTE]
> İşlevsel programlamada yaygın olarak kullanılan adlandırma, programları saf işlevleri kullanarak yeniden düzenlemenizdir. Visual Basic ve C++'da bu, ilgili dillerdeki işlevlerin kullanımıyla uyumludur. Ancak, C#'da işlevler yöntem olarak adlandırılır. Bu tartışmanın amaçları için C#'da bir yöntem olarak saf bir işlev uygulanır.  
  
 Bu bölümde daha önce belirtildiği gibi, saf bir işlevin iki yararlı özelliği vardır:  
  
- Hiçbir yan etkisi yoktur. İşlev, herhangi bir değişkeni veya işlev dışında herhangi bir türdeki verileri değiştirmez.  
  
- Tutarlı. Aynı giriş veri kümesi göz önüne alındığında, her zaman aynı çıktı değerini döndürecektir.  
  
 İşlevsel programlamaya geçişin bir yolu, gereksiz yan etkileri ve dışa bağımlılıkları ortadan kaldırmak için varolan kodu yeniden duruma getirmektir. Bu şekilde, varolan kodun saf işlev sürümlerini oluşturabilirsiniz.  
  
 Bu konu, saf bir işlevin ne olduğunu ve ne olmadığını tartışır. [Öğretici: WordprocessingML Belgesinde (C#) öğreticide İçeriği niçin değiştirilir,](./shape-of-wordprocessingml-documents.md) WordprocessingML belgesinin nasıl değiştirilebildiğini gösterir ve saf bir işlev kullanarak nasıl yeniden kusturun iki örnek içerir.  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a>Yan Etkileri ve Dış Bağımlılıkları Ortadan Kaldırma  
 Aşağıdaki örnekler, saf olmayan iki işlev ve saf bir işlevle tezat atretmektedir.  
  
### <a name="non-pure-function-that-changes-a-class-member"></a>Sınıf Üyesini Değiştiren Saf Olmayan İşlev  
 Aşağıdaki kodda, `HyphenatedConcat` işlev saf bir işlev değildir, çünkü `aMember` sınıftaki veri üyesini değiştirir:  
  
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
  
 Değiştirilen verilerin sahip `public` olup olmadığının veya `private` erişip erişmediğinin veya üye `static` veya örnek üye olup olmadığının önemsiz olduğunu unutmayın. Saf bir işlev, işlev in dışındaki verileri değiştirmez.  
  
### <a name="non-pure-function-that-changes-an-argument"></a>Bağımsız Değişkeni Değiştiren Saf Olmayan İşlev  
 Ayrıca, aynı işlevin aşağıdaki sürümü, parametresinin içeriğini değiştirir, çünkü saf `sb`değildir.  
  
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
  
 `HyphenatedConcat` Programın bu sürümü, <xref:System.Text.StringBuilder.Append%2A> üye işlevi çağırarak ilk parametresinin değerini (durumunu) değiştirdiğinden, ilk sürümle aynı çıktıyı üretir. Bu değişikliğin, çağrı değeri parametre geçişi nin kullanımı gerçeğine `HyphenatedConcat` rağmen oluştuğunu unutmayın.  
  
> [!IMPORTANT]
> Başvuru türleri için, bir parametreyi değere göre geçerseniz, geçirilen bir nesneye başvurunun bir kopyasıyla sonuçlanır. Bu kopya hala özgün başvuruyla aynı örnek verilerle ilişkilidir (başvuru değişkeni yeni bir nesneye atanana kadar). Bir işlevin bir parametreyi değiştirmesi için çağrı-by-reference mutlaka gerekli değildir.  
  
### <a name="pure-function"></a>Saf Fonksiyon  
Programın bir sonraki sürümü, işlevin `HyphenatedConcat` saf bir işlev olarak nasıl uygulanacağını gösterir.  
  
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
  
 Yine, bu sürüm çıkış aynı `StringOne-StringTwo`satırı üretir: . Concatenated değerini korumak için, ara değişkende `s2`depolanır unutmayın.  
  
 Çok yararlı olabilecek bir yaklaşım, yerel olarak saf olmayan (diğer bir şekilde yerel değişkenleri beyan edip değiştirebilen) ancak genel olarak saf olan işlevleri yazmaktır. Bu tür işlevler arzu edilen kullanılabilirlik özelliklerinin çoğuna sahiptir, ancak basit bir döngü aynı şeyi gerçekleştireceği zaman özyineleme kullanmak zorunda kalmak gibi daha karmaşık işlevsel programlama deyimlerinden bazılarını önler.  
  
## <a name="standard-query-operators"></a>Standart Sorgu Operatörleri  
 Standart sorgu işleçlerinin önemli bir özelliği, bunların saf işlevler olarak uygulanmasıdır.  
  
 Daha fazla bilgi için, [Bkz. Standart Sorgu Operatörleri Genel Bakış (C#)](./standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Saf İşlevsel Dönüşümlere Giriş (C#)](./introduction-to-pure-functional-transformations.md)
- [Fonksiyonel Programlama ve Zorunlu Programlama (C#)](./functional-programming-vs-imperative-programming.md)
