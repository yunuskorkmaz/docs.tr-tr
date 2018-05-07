---
title: for (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: 9d7ab9e37be61384c33833381f44257169c81c31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="for-c-reference"></a>for (C# Başvurusu)
Kullanarak bir `for` döngü, çalıştırabileceğiniz bir deyim veya deyimleri bloğu art arda için belirtilen ifadeyi değerlendirir kadar `false`. Bu tür bir döngü hem de önceden yinelemek için döngü istediğiniz kaç kez bilmeniz diğer uygulamalar diziler yineleme için yararlıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, değeri `i` konsola yazılır ve her döngü sırasında 1 azaltılır.  
  
 [!code-csharp[csrefKeywordsIteration#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_1.cs)]  
  
 `for` Deyimi önceki örnekte aşağıdaki eylemleri gerçekleştirir.  
  
1.  İlk olarak, ilk değişkenin değeri olarak `i` kurulur. Bu adım, döngü yineler birçok kez nasıl bağımsız olarak yalnızca bir kez gerçekleşir. Bu başlatılması döngü işlemin dışında oluşmasını olarak düşünebilirsiniz.  
  
2.  Koşulunu hesaplamayı (`i <= 5`), değeri `i` 5 ile karşılaştırılır.  
  
    -   Varsa `i` küçük veya ona eşit için 5, koşulu değerlendirir `true`, ve aşağıdaki eylemler gerçekleşir.  
  
        1.  `Console.WriteLine` Döngü gövdesine ifade değerini görüntüler `i`.  
  
        2.  Değeri `i` 1 artırılır.  
  
        3.  Döngü koşulu yeniden değerlendirmek için 2. adım başlangıcını döndürür.  
  
    -   Varsa `i` 5'ten büyük olduğu için koşulu değerlendirir `false`, ve döngüden çıkın.  
  
 Unutmayın ilk değeri `i` 5'ten büyük döngünün gövdesi bile bir kez çalıştırmaz.  
  
 Her `for` deyimi başlatıcısı, koşul ve yineleyici bölümleri tanımlar. Bu bölümler genellikle döngü tekrarlanan kaç kez belirler.  
  
```csharp  
for (initializer; condition; iterator)  
    body  
```  
  
 Bölümler aşağıdaki amaca hizmet eder.  
  
-   Başlatıcı bölüm ilk koşul ayarlar. Döngü girmeden önce bu bölümdeki deyimleri yalnızca bir kez çalıştırın. Bölüm yalnızca aşağıdaki iki seçenekten birini içerebilir.  
  
    -   Bildirim ve başlatma İlk örnekte gösterildiği gibi bir yerel döngü değişkenin (`int i = 1`). Değişkeni döngü için yerel olan ve gelen döngü dışında erişilemez.  
  
    -   Sıfır veya daha fazla deyim expressons virgülle ayırarak aşağıdaki listeden.  
  
        -   [atama](../../../csharp/language-reference/operators/assignment-operator.md) deyimi  
  
        -   bir yöntemi çağrıldı  
  
        -   önek veya sonek [artırma](../../../csharp/language-reference/operators/increment-operator.md) ifadesi gibi `++i` veya `i++`  
  
        -   önek veya sonek [azaltma](../../../csharp/language-reference/operators/decrement-operator.md) ifadesi gibi `--i` veya `i--`  
  
        -   kullanarak bir nesne oluşturulmasını [yeni](../../../csharp/language-reference/keywords/new-operator.md)  
  
        -   [await](../../../csharp/language-reference/keywords/await.md) ifadesi  
  
-   Koşul bölüm döngü çıkmalıdır veya yeniden çalışması gerektiğini belirlemek için değerlendirilen boolean bir ifade içeriyor.  
  
-   Yineleyici bölümü döngüden gövdesinin her yinelemeden sonra ne olacağını tanımlar. Yineleyici bölüm sıfır veya daha fazla virgülle ayırarak aşağıdaki deyimi ifadeleri içerir:  
  
    -   [atama](../../../csharp/language-reference/operators/assignment-operator.md) deyimi  
  
    -   bir yöntemi çağrıldı  
  
    -   önek veya sonek [artırma](../../../csharp/language-reference/operators/increment-operator.md) ifadesi gibi `++i` veya `i++`  
  
    -   önek veya sonek [azaltma](../../../csharp/language-reference/operators/decrement-operator.md) ifadesi gibi `--i` veya `i--`  
  
    -   kullanarak bir nesne oluşturulmasını [yeni](../../../csharp/language-reference/keywords/new-operator.md)  
  
    -   [await](../../../csharp/language-reference/keywords/await.md) ifadesi  
  
-   Döngünün gövdesi bir deyim, boş bir deyimi veya sıfır veya daha fazla deyimleri ayraçlar içinde kapsayan tarafından oluşturduğunuz deyimleri bloğu oluşur.  
  
     İşyeri dışında bölünebilir bir `for` kullanarak döngü [sonu](../../../csharp/language-reference/keywords/break.md) anahtar sözcüğü veya adım sonraki yinelemeye kullanarak [devam](../../../csharp/language-reference/keywords/continue.md) anahtar sözcüğü. Kullanarak her döngü çıkabilirsiniz bir [goto](../../../csharp/language-reference/keywords/goto.md), [dönmek](../../../csharp/language-reference/keywords/return.md), veya [throw](../../../csharp/language-reference/keywords/throw.md) deyimi.  
  
 Bu konudaki ilk örnek tür en tipik gösterir `for` döngüsü bölümleri için aşağıdaki seçenekleri sağlar.  
  
-   Başlatıcı bildirir ve bir yerel döngü değişkenini `i`, döngü yineleme sayısını tutar.  
  
-   Koşul değişkenin değeri olarak döngü bilinen son bir değer olan 5 karşı denetler.  
  
-   Sonek artırma deyimi yineleyici kullanıyorsa `i++`, her döngü tekrarında kaydetmesini.  
  
 Aşağıdaki örnek birkaç genel seçenek daha az gösterilmektedir: Başlatıcı bölümünde bir dış döngü değişkene bir değer atama, çağırma `Console.WriteLine` hem Başlatıcı yineleyici bölümleri ve iki değerlerini değiştirme yöntemi Yineleyici bölümünde değişkenleri.  
  
 [!code-csharp[csrefKeywordsIteration#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_2.cs)]  
  
 Tüm tanımlayan bir ifade bir `for` deyimi isteğe bağlıdır. Örneğin, aşağıdaki deyim sonsuz bir döngüde oluşturur.  
  
 [!code-csharp[csrefKeywordsIteration#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_3.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)  
 [for Deyimi (C++)](/cpp/cpp/for-statement-cpp)  
 [Yineleme Deyimleri](../../../csharp/language-reference/keywords/iteration-statements.md)
