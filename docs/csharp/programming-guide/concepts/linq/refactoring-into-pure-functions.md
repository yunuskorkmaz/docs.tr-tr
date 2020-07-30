---
title: Saf IŞLEVLERE yeniden düzenleme (C#)
description: Saf işlevleri kullanarak kodu yeniden düzenleme hakkında bilgi edinin. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: cc5dd26923e2edaed34c8f1b742b3dfa1e935e68
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87300234"
---
# <a name="refactoring-into-pure-functions-c"></a>Saf IŞLEVLERE yeniden düzenleme (C#)

Saf işlevsel dönüştürmelerin önemli bir yönü, saf işlevleri kullanarak kodu yeniden düzenleme hakkında bilgi ediniyor.  
  
> [!NOTE]
> İşlevsel programlamada ortak terminoloji, programları saf işlevleri kullanarak yeniden düzenleme biçimleridir. Visual Basic ve C++ ' da bu, ilgili dillerdeki işlevlerin kullanımıyla hizalanır. Ancak C# ' de işlevleri yöntemler olarak adlandırılır. Bu tartışmanın amaçları doğrultusunda, saf bir işlev C# dilinde bir yöntem olarak uygulanır.  
  
 Daha önce bu bölümde belirtildiği gibi, saf bir işlev iki yararlı özelliğe sahiptir:  
  
- Yan etkileri yoktur. İşlev herhangi bir değişken veya işlev dışındaki herhangi bir türdeki veriyi değiştirmez.  
  
- Tutarlıdır. Aynı giriş verisi kümesi verildiğinde, her zaman aynı çıkış değerini döndürür.  
  
 İşlevsel programlamaya geçiş yapmanın bir yolu, gereksiz yan etkileri ve dış bağımlılıkları ortadan kaldırmak için mevcut kodu yeniden düzenleme yöntemidir. Bu şekilde, var olan kodun saf işlev sürümlerini oluşturabilirsiniz.  
  
 Bu konuda, saf bir işlevin ne olduğu ve ne olmadığı açıklanmaktadır. [Öğretici: WordprocessingML belgesi (C#) öğreticisindeki Içeriği düzenleme](./shape-of-wordprocessingml-documents.md) bir WordprocessingML belgesinin nasıl düzenleneceğini gösterir ve saf bir işlev kullanarak yeniden düzenleme ile iki örnek içerir.  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a>Yan etkileri ve dış bağımlılıkları ortadan kaldırma  
 Aşağıdaki örneklerde, saf olmayan iki işlev ve bir saf işlev kontrast vardır.  
  
### <a name="non-pure-function-that-changes-a-class-member"></a>Bir sınıf üyesini değiştiren saf olmayan Işlev  
 Aşağıdaki kodda, `HyphenatedConcat` işlev saf bir işlev değildir, çünkü `aMember` sınıfındaki veri üyesini değiştirir:  
  
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
  
 Bu kod şu çıkışı oluşturur:  
  
```output  
StringOne-StringTwo  
```  
  
 Değiştirilen verilerin veya `public` `private` bir `static` üye ya da bir örnek üyesi olup olmadığı konusunda ilgisiz olduğunu unutmayın. Saf bir işlev, işlevin dışındaki herhangi bir veriyi değiştirmez.  
  
### <a name="non-pure-function-that-changes-an-argument"></a>Bir bağımsız değişkeni değiştiren saf olmayan Işlev  
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
  
 Programın bu sürümü ilk sürümle aynı çıktıyı üretir, çünkü `HyphenatedConcat` işlev üye işlevini çağırarak ilk parametresinin değerini (durum) değiştirdi <xref:System.Text.StringBuilder.Append%2A> . Bu değişiklik, bu olguyu, çağrı- `HyphenatedConcat` değer parametresini kullanan bir olgusuna rağmen oluştuğunu unutmayın.  
  
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
  
 Yine, bu sürüm aynı çıkış satırını üretir: `StringOne-StringTwo` . Birleştirilmiş değeri bekletmek için, ara değişkende depolandığını unutmayın `s2` .  
  
 Çok yararlı olabilecek bir yaklaşım, yerel olarak etkileyici olan işlevleri yazmak (yani yerel değişkenleri bildirdikleri ve değiştirdiklerinde), ancak Global olarak saf bir yaklaşımdır. Bu gibi işlevler, istenen ek özelliklerin çoğuna sahiptir, ancak basit bir döngü aynı şeyi gerçekleştirirken özyineleme kullanmak zorunda kalmadan, daha fazla çalışan işlevsel programlama deyimidir.  
  
## <a name="standard-query-operators"></a>Standart sorgu Işleçleri  
 Standart sorgu işleçlerinin önemli bir özelliği, saf işlevler olarak uygulanırlar.  
  
 Daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış (C#)](./standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Saf Işlevsel dönüşümlere giriş (C#)](./introduction-to-pure-functional-transformations.md)
- [Fonksiyonel programlama ile kesinlik temelli programlama (C#)](./functional-programming-vs-imperative-programming.md)
