---
title: =&gt;İşleci (C# Başvurusu)
ms.date: 10/02/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 44cb0485aefa8b0ab10a00ae0525180020ce436d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="gt-operator-c-reference"></a>=&gt;İşleci (C# Başvurusu)

`=>` İşleci, C# iki yolla kullanılabilir:

- Olarak [lambda işleci](#lamba-operator) içinde bir [lambda ifadesi](../../lambda-expressions.md), girdi değişkenleri lambda gövdesinden ayırır.
 
- İçinde bir [ifade gövdesi tanımı](#expression-body-definition), üye uygulamasından bir üye adı ayırır. 

## <a name="lambda-operator"></a>Lambda işleci

`=>` Belirteci lambda işleci çağrılır. İçinde kullanılan *lambda ifadeleri* girdi değişkenleri sol taraftaki sağ tarafında lambda gövde ayırmak için. Lambda ifadeleri satır içi ifadeler daha esnek ancak anonim yöntemler benzer; yine de uygun istiyor musunuz? yöntem sözdiziminde ifade LINQ sorgularında yaygın olarak kullanılır. Daha fazla bilgi için bkz: [Lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Aşağıdaki örnek bulmak ve bir dizeler dizisi kısa dize uzunluğu görüntülemek için iki yolunu gösterir. Lambda ifadesi örnek ilk bölümünü uygular (`w => w.Length`) her öğesine `words` dizi ve kullandığı <xref:System.Linq.Enumerable.Min%2A> en küçük uzunluk bulmak için yöntem. Karşılaştırma için ikinci bölümü örneğin aynı şeyi yapmak için sorgu sözdizimini kullanır daha uzun bir çözüm gösterilmektedir.  
  
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
 `=>` Atama işleci olarak aynı önceliğe sahip (`=`) ve sağa ilişkilendirilebilir.  
  
 Giriş değişkeninin türü açıkça belirtin veya bunu Infer derleyici sağlar; Her iki durumda da değişkeni kesinlikle derleme zamanında tür belirtilmiş. Bir türü belirttiğinizde, parantez içine tür adı ve değişken adı aşağıdaki örnekte gösterildiği gibi almalısınız.  
  
```csharp  
int shortestWordLength = words.Min((string w) => w.Length);  
```  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir lambda ifadesi standart sorgu işleci aşırı için yazma gösterilmektedir <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> iki bağımsız değişkeni alır. Lambda ifadesi birden fazla parametre içerdiğinden parametreleri parantez içine alınmalıdır. İkinci parametre `index`, koleksiyondaki geçerli öğenin dizinini temsil eder. `Where` İfade olan uzunlukta olan dizin konumlarına dizideki değerinden tüm dizeleri döndürür.  
  
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

Bir ifade gövdesi tanımı yüksek oranda sıkıştırılmış, okunabilir bir biçimde bir üyenin uygulamasını sağlar. Genel sözdizimi aşağıdaki gibidir:

```csharp
member => expression;
```
Burada *ifade* geçerli bir ifade değil. Unutmayın *ifade* olabilir bir *deyimi ifade* üyenin dönüş türü ise yalnızca `void`, veya bir oluşturucu veya bir sonlandırıcı üyesiyse.

İfade gövdesi tanımları yöntem ve özellik get deyimleri için C# 6 ile başlayarak desteklenir. Dizin oluşturucular C# 7 ile başlayan desteklenir ve ifade gövdesi Oluşturucular, sonlandırıcılar, tanımlarında deyimleri özelliğini ayarlayın.

İçin bir ifade gövdesi tanımı aşağıda verilmiştir bir `Person.ToString` yöntemi:

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

Aşağıdaki yöntem tanımını kestirme sürümü şöyledir:

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```
İfade gövdesi tanımları hakkında daha ayrıntılı bilgi için bkz: [ifade bodied üyeleri](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="see-also"></a>Ayrıca Bkz.  
[C# başvurusu](../../../csharp/language-reference/index.md)   
[C# programlama kılavuzu](../../../csharp/programming-guide/index.md)   
[Lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
[İfade bodied üyeleri](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).