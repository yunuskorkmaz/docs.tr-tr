---
title: =&gt; İşleci (C# Başvurusu)
ms.date: 10/02/2017
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: b9216cf61b6b9368112f769d952457df4aab4297
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44080543"
---
# <a name="gt-operator-c-reference"></a>=&gt; İşleci (C# Başvurusu)

`=>` İşleci, C# dilinde iki şekilde kullanılabilir:

- Olarak [lambda işleci](#lamba-operator) içinde bir [lambda ifadesi](../../lambda-expressions.md), lambda gövdesinden girdi değişkenleri ayırır.
 
- İçinde bir [ifade gövdesi tanımına](#expression-body-definition), üye uygulamasından bir üye adı ayıran. 

## <a name="lambda-operator"></a>Lambda işleci

`=>` Belirteci lambda işlecini çağrılır. İçinde kullanılan *lambda ifadeleri* işlecin sağ tarafındaki lambda gövdesinden sol tarafında giriş değişkenleri ayırmak için. Lambda ifadeleri, satır içi ifadeler anonim yöntemler daha esnek ancak benzer olan; yöntem sözdizimi ifade LINQ sorgularında yaygın olarak kullanılır. Daha fazla bilgi için [Lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Aşağıdaki örnek, bulmak ve dizelerden oluşan bir dizi kısa dize uzunluğunu görüntülemek için iki yolunu gösterir. Bir lambda ifadesi örneği ilk bölümünü uygular (`w => w.Length`) her öğesine `words` dizisi ve kullandığı <xref:System.Linq.Enumerable.Min%2A> en küçük uzunluğunu bulmak için yöntemi. Karşılaştırma için ikinci bölümü örneğin aynı şeyi yapmak için sorgu söz dizimi kullanan daha uzun bir çözüm gösterilmektedir.  
  
```csharp  
string[] words = { "cherry", "apple", "blueberry" };  
  
// Use method syntax to apply a lambda expression to each element  
// of the words array.   
int shortestWordLength = words.Min(w => w.Length);  
Console.WriteLine(shortestWordLength);  
  
// Compare the following code that uses query syntax.  
// Get the lengths of each word in the words array.  
var query = from w in words  
            select w.Length;  
// Apply the Min method to execute the query and get the shortest length.  
int shortestWordLength2 = query.Min();  
Console.WriteLine(shortestWordLength2);  
  
// Output:   
// 5  
// 5  
```  
  
### <a name="remarks"></a>Açıklamalar  
 `=>` İşleci atama işleci aynı önceliğe sahiptir (`=`) ve sağa ilişkilendirilmiştir.  
  
 Giriş değişkeninin türünü açıkça belirtmeniz veya, derleyicinin sağlar; Her iki durumda da, değişken derleme zamanında kesin olarak. Bir türü belirttiğinizde, parantez içinde tür adı ve değişken adı aşağıdaki örnekte gösterildiği gibi almalısınız.  
  
```csharp  
int shortestWordLength = words.Min((string w) => w.Length);  
```  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, standart sorgu işleci aşırı yüklemesi için bir lambda ifadesinin nasıl yazılacağını gösterir <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> , iki bağımsız değişkeni alır. Lambda ifadesi birden fazla parametre olduğundan, parametreleri, parantez içine alınmalıdır. İkinci parametre `index`, koleksiyondaki geçerli öğenin dizinini temsil eder. `Where` İfade, uzunlukları Dizin konumlarını dizideki değerinden küçük olan tüm dizeleri döndürür.  
  
```csharp  
static void Main(string[] args)  
{  
    string[] digits = { "zero", "one", "two", "three", "four", "five",   
            "six", "seven", "eight", "nine" };  
  
    Console.WriteLine("Example that uses a lambda expression:");  
    var shortDigits = digits.Where((digit, index) => digit.Length < index);  
    foreach (var sD in shortDigits)  
    {  
        Console.WriteLine(sD);  
    }  
  
    // Output:  
    // Example that uses a lambda expression:  
    // five  
    // six  
    // seven  
    // eight  
    // nine  
}  
```  
## <a name="expression-body-definition"></a>İfade gövdesi tanımı

Bir ifade gövdesi tanımına, yüksek oranda sıkıştırılmış, okunabilir formda bir üyenin uygulamasını sağlar. Bu genel sözdizimi aşağıdaki gibidir:

```csharp
member => expression;
```
Burada *ifade* geçerli bir ifadedir. Unutmayın *ifade* olabilir bir *deyim ifadesi* üyenin dönüş türü ise yalnızca `void`, veya üye bir oluşturucu ya da bir sonlandırıcı ise.

Yöntem ve özellik get deyimleri için ifade gövdesi tanımları, C# 6 ile başlayarak desteklenir. Sonlandırıcılar, Oluşturucular için ifade gövdesi tanımları deyimleri özelliğini ayarlayın ve dizin oluşturucular, C# 7 ile başlayan desteklenir.

Bir ifade gövdesi tanımı verilmiştir bir `Person.ToString` yöntemi:

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

Aşağıdaki yöntem tanımının bir toplu sürümdür:

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```
İfade gövdesi tanımları hakkında daha ayrıntılı bilgi için bkz: [ifade gövdeli üyeler](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)   
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)   
- [Lambda İfadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
- [İfade gövdeli üyeler](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).