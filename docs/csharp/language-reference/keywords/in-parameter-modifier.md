---
title: parametre değiştirici- C# başvuru
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: 10e7b91f9a6bf280c5f0654b243492bac8cde1e0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715247"
---
# <a name="in-parameter-modifier-c-reference"></a>parametre değiştiricide (C# başvuru)

`in` anahtar sözcüğü, bağımsız değişkenlerin başvuruya göre geçirilmesine neden olur. Bir değişken olması gereken, biçimsel parametreye bağımsız değişken için bir diğer ad oluşturur. Diğer bir deyişle, parametresindeki tüm işlemler bağımsız değişkende yapılır. `in` bağımsız değişkenleri, çağrılan yöntem tarafından değiştirilemediği için [ref](ref.md) veya [Out](out-parameter-modifier.md) anahtar kelimeleri gibidir. `ref` bağımsız değişkenler değiştirilebilir, `out` bağımsız değişkenler çağrılan yöntemle değiştirilmelidir ve bu değişiklikler çağıran bağlamda observable olmalıdır.

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

Yukarıdaki örnek, `in` değiştiricinin çağrı sitesinde genellikle gereksiz olduğunu gösterir. Yalnızca yöntem bildiriminde gereklidir.

> [!NOTE] 
> `in` anahtar sözcüğü, tür parametresinin değişken karşıtı olduğunu, `foreach` bildiriminin bir parçası olarak veya bir LINQ sorgusunda `join` yan tümcesinin bir parçası olarak belirtmek için genel bir tür parametresiyle birlikte kullanılabilir. Bu bağlamlarda `in` anahtar sözcüğünün kullanımı hakkında daha fazla bilgi için, bkz. [içindeki](in.md)tüm kullanımlar için bağlantı sağlayan.
  
`in` bağımsız değişken olarak geçirilen değişkenlerin bir yöntem çağrısında geçirilmeden önce başlatılması gerekir. Ancak çağrılan yöntem bir değer atayamayabilir veya bağımsız değişkeni değiştirebilir.  

`in` parametre değiştiricisi C# 7,2 ve üzeri sürümlerde kullanılabilir. Önceki sürümler derleyici hatası oluşturur `CS8107` ("özellik ' ReadOnly başvurular ' 7,0 içinde C# kullanılamaz. Lütfen dil sürümü 7,2 veya üstünü kullanın. ") Derleyici dili sürümünü yapılandırmak için bkz. [ C# dil sürümünü seçme](../configure-language-version.md).

`in`, `ref`ve `out` anahtar sözcükleri, aşırı yükleme çözümlemesi amacıyla yöntem imzasının bir parçası olarak kabul edilmez. Bu nedenle, tek fark bir yöntem `ref` veya `in` bağımsız değişken alırsa ve diğeri bir `out` bağımsız değişkeni alırsa Yöntemler aşırı yüklenemez. Aşağıdaki kod, örneğin derlenmeyecektir:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
`in` varlığına göre aşırı yüklemeye izin verilir:  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a>Aşırı yükleme çözümleme kuralları

`in` bağımsız değişkenler için mosyon 'yı anlayarak, değere ve `in` bağımsız değişkenlerine sahip yöntemler için aşırı yükleme çözümleme kurallarını anlayabilirsiniz. `in` parametrelerini kullanarak yöntemlerin tanımlanması potansiyel bir performans iyileştirmesidir. Bazı `struct` tür bağımsız değişkenleri boyutu büyük olabilir ve Yöntemler sıkı Döngülerde veya kritik kod yollarında çağrıldığında, bu yapıları kopyalama maliyeti kritik öneme sahiptir. Yöntemler bu bağımsız değişken durumunu değiştirmediğinden bağımsız değişkenlerin başvuruya güvenli bir şekilde geçirilebileceğini belirtmek için `in` parametrelerini bildirir. Bu bağımsız değişkenlerin başvuruya göre geçirilmesi, (potansiyel) pahalı kopyayı önler. 

Çağrı sitesinde bağımsız değişkenler için `in` belirtmek genellikle isteğe bağlıdır. Bağımsız değişkenleri değere göre geçirme ve `in` değiştiricisini kullanarak başvuruya göre geçirme arasında herhangi bir semantik fark yoktur. Bağımsız değişkenin değerinin değiştirilip değiştirilemeyeceğini belirtmeniz gerekmiyorsa, çağrı sitesindeki `in` değiştiricisi isteğe bağlıdır. Bağımsız değişkenin değere göre değil başvuruya göre geçirildiğinden emin olmak için çağrı sitesine `in` değiştiricisini açıkça eklersiniz. Açıkça `in` kullanımı aşağıdaki iki etkiye sahiptir:

İlk olarak, çağıran sitede `in` belirttiğinizde, derleyicinin eşleşen bir `in` parametresiyle tanımlanmış bir yöntemi seçmesini zorlar. Aksi takdirde, iki yöntem yalnızca `in`olduğunda farklılık gösteriyorsa, değer aşırı yüklemesi daha iyi bir eşleşmedir.

İkincisi, `in` belirtmek için bir bağımsız değişkeni başvuruya göre geçirme amacınızı bildirir. `in` ile kullanılan bağımsız değişken, doğrudan başvuruda bulunulabilir bir konumu temsil etmelidir. `out` ve `ref` bağımsız değişkenleri için aynı genel kurallar geçerlidir: sabitleri, olağan özellikleri veya değer üreten diğer ifadeleri kullanamazsınız. Aksi takdirde, çağrı sitesindeki `in` atlanması derleyiciye bildirir ve bu, yönteme salt okuma başvurusu ile geçirilecek geçici bir değişken oluşturmasına izin verir. Derleyici, `in` bağımsız değişkenlerle çeşitli kısıtlamaları aşmak için geçici bir değişken oluşturur:

- Geçici bir değişken, `in` parametre olarak derleme zamanı sabitlerine izin verir.
- Geçici bir değişken özellikler veya `in` parametrelere yönelik diğer ifadelere izin verir.
- Geçici bir değişken, bağımsız değişken türünden parametre türüne örtük bir dönüştürme olduğu bağımsız değişkenlere izin verir.

Önceki tüm örneklerde, derleyici sabit, özellik veya başka bir ifadenin değerini depolayan geçici bir değişken oluşturur.

Aşağıdaki kod bu kuralları gösterir:

```csharp
static void Method(in int argument)
{
    // implementation removed
}

Method(5); // OK, temporary variable created.
Method(5L); // CS1503: no implicit conversion from long to int
short s = 0;
Method(s); // OK, temporary int created with the value 0
Method(in s); // CS1503: cannot convert from in short to in int
int i = 42;
Method(i); // passed by readonly reference
Method(in i); // passed by readonly reference, explicitly using `in`
```

Şimdi, değer bağımsız değişkenlerine göre kullanılan başka bir yöntem bulunduğunu varsayalım. Sonuçlar aşağıdaki kodda gösterildiği gibi değişir:

```csharp
static void Method(int argument)
{
    // implementation removed
}

static void Method(in int argument)
{
    // implementation removed
}

Method(5); // Calls overload passed by value
Method(5L); // CS1503: no implicit conversion from long to int
short s = 0;
Method(s); // Calls overload passed by value.
Method(in s); // CS1503: cannot convert from in short to in int
int i = 42;
Method(i); // Calls overload passed by value
Method(in i); // passed by readonly reference, explicitly using `in`
```

Bağımsız değişkenin başvuruya göre geçirildiği tek yöntem çağrısı son bir yöntemdir.

> [!NOTE]
> Yukarıdaki kod basitlik için bağımsız değişken türü olarak `int` kullanır. `int` çoğu modern makinelerdeki bir başvurudan daha büyük olmadığından, tek bir `int` salt okunur başvuru olarak geçirilmesi avantajına sahip değildir. 

## <a name="limitations-on-in-parameters"></a>`in` parametrelerinin sınırlamaları

Aşağıdaki tür yöntemler için `in`, `ref`ve `out` anahtar sözcüklerini kullanamazsınız:  
  
- Zaman [uyumsuz](async.md) değiştirici kullanarak tanımladığınız zaman uyumsuz yöntemler.  
- Bir [yield return](yield.md) veya `yield break` ifadesini içeren Yineleyici yöntemleri.  

## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Yöntem Parametreleri](method-parameters.md)
- [Güvenli verimli kod yazma](../../write-safe-efficient-code.md)
