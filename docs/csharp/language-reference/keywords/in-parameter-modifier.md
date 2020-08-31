---
description: parametre değiştiricisi-C# başvurusu
title: parametre değiştiricisi-C# başvurusu
ms.date: 03/19/2020
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: 613be9248e6ce9b974bcab1b59abd30469e9e180
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118410"
---
# <a name="in-parameter-modifier-c-reference"></a>parametre değiştiricide (C# Başvurusu)

`in`Anahtar sözcüğü, bağımsız değişkenlerin başvuruya göre geçirilmesine neden olur. Bir değişken olması gereken, biçimsel parametreye bağımsız değişken için bir diğer ad oluşturur. Diğer bir deyişle, parametresindeki tüm işlemler bağımsız değişkende yapılır. [Başvuru](ref.md) veya [Çıkış](out-parameter-modifier.md) anahtar kelimeleri gibidir, bu `in` bağımsız değişkenler çağrılan yöntem tarafından değiştirilemez. `ref`Bağımsız değişkenler değiştirilebilir, `out` bağımsız değişkenler çağrılan yöntemle değiştirilmelidir ve bu değişiklikler çağıran bağlamda Observable ' tır.

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

Yukarıdaki örnek, `in` değiştiricinin çağrı sitesinde genellikle gereksiz olduğunu gösterir. Yalnızca yöntem bildiriminde gereklidir.

> [!NOTE]
> `in`Anahtar sözcüğü, tür parametresinin değişken karşıtı olduğunu, bir deyimin parçası olarak `foreach` veya bir `join` LINQ sorgusundaki yan tümcesinin bir parçası olarak belirtmek için genel bir tür parametresiyle de kullanılabilir. Bu bağlamlarda anahtar sözcüğünün kullanımı hakkında daha fazla bilgi için, `in` bkz. [içindeki](in.md)tüm kullanımları için bağlantı sağlayan.
  
Bağımsız değişken olarak geçirilen değişkenlerin `in` bir yöntem çağrısında geçirilmeden önce başlatılması gerekir. Ancak çağrılan yöntem bir değer atayamayabilir veya bağımsız değişkeni değiştirebilir.  

`in`Parametre değiştiricisi C# 7,2 ve üzeri sürümlerde kullanılabilir. Önceki sürümlerde derleyici hatası `CS8107` ("' ReadOnly başvuruları" özelliği C# 7,0 ' de kullanılamaz. Lütfen dil sürümü 7,2 veya üstünü kullanın. ") Derleyici dili sürümünü yapılandırmak için bkz. [C# dil sürümünü seçme](../configure-language-version.md).

`in`, `ref` Ve `out` anahtar kelimeleri, aşırı yükleme çözümlemesi amacıyla yöntem imzasının bir parçası olarak kabul edilmez. Bu nedenle, tek fark bir yöntemin bir `ref` veya bağımsız değişken alırsa `in` ve diğeri bir bağımsız değişken alırsa Yöntemler aşırı yüklenemez `out` . Aşağıdaki kod, örneğin derlenmeyecektir:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Varlığına göre aşırı yüklemeye `in` izin verilir:  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a>Aşırı yükleme çözümleme kuralları

`in`Bağımsız değişkenler için mosyon 'yı anlayarak değere ve bağımsız değişkenlerle ile yöntemler için aşırı yükleme çözümleme kurallarını anlayabilirsiniz `in` . Parametreleri kullanarak yöntemlerin tanımlanması `in` potansiyel bir performans iyileştirmesidir. Bazı `struct` tür bağımsız değişkenleri boyutu büyük olabilir ve Yöntemler sıkı Döngülerde veya kritik kod yollarında çağrıldığında, bu yapıları kopyalama maliyeti kritik öneme sahiptir. Yöntemler, bu `in` bağımsız değişkenin durumunu değiştirmediğinden bağımsız değişkenlerin başvuruya güvenli bir şekilde geçirilebileceğini belirtmek için parametreler bildirir. Bu bağımsız değişkenlerin başvuruya göre geçirilmesi, (potansiyel) pahalı kopyayı önler.

`in`Çağrı sitesinde bağımsız değişkenlerin belirtilmesi genellikle isteğe bağlıdır. Bağımsız değişkenleri değere göre geçirme ve değiştiricisini kullanarak başvuruya göre geçirme arasında herhangi bir semantik fark yoktur `in` . `in`Bağımsız değişkenin değerinin değiştirilip değiştirilemeyeceğini belirtmeniz gerekmiyorsa, çağrı sitesindeki değiştirici isteğe bağlıdır. `in`Bağımsız değişkenin değere göre değil başvuruya göre geçirildiğinden emin olmak için çağrı sitesine açıkça değiştiricisini eklersiniz. Açıkça kullanmak `in` aşağıdaki iki etkiye sahiptir:

İlk olarak, `in` çağıran sitede belirtme, derleyicinin eşleşen bir parametreyle tanımlanmış bir yöntemi seçmesini zorlar `in` . Aksi takdirde, iki yöntem yalnızca varlığı içinde farklılık gösteriyorsa `in` , bu değer aşırı yükleme daha iyi bir eşleşmedir.

İkincisi, belirtme, `in` bir bağımsız değişkeni başvuruya göre geçirme amacınızı bildirir. İle kullanılan bağımsız değişken, `in` doğrudan başvuruda bulunulabilir bir konumu temsil etmelidir. Ve bağımsız değişkenler için aynı genel kurallar `out` `ref` geçerlidir: sabitleri, olağan özellikleri veya değer üreten diğer ifadeleri kullanamazsınız. Aksi takdirde, `in` çağıran sitede atlama yöntemi derleyiciye bildirir ve bu, yönteme salt okuma başvurusu ile geçirilecek geçici bir değişken oluşturmasına izin verir. Derleyici, bağımsız değişkenlerle birkaç kısıtlamayı aşmak için geçici bir değişken oluşturur `in` :

- Geçici bir değişken, derleme zamanı sabitlerinin parametre olarak kullanılmasına izin verir `in` .
- Geçici bir değişken özellikler veya parametreler için diğer ifadelere izin verir `in` .
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
> Önceki kod `int` basitlik için bağımsız değişken türü olarak kullanılır. `int`Çoğu modern makinenin bir başvurusundan daha büyük olmadığından, tek tek bir `int` salt okunur başvuru olarak geçirilme avantajı yoktur.

## <a name="limitations-on-in-parameters"></a>Parametrelerle ilgili sınırlamalar `in`

`in` `ref` `out` Aşağıdaki tür yöntemler için, ve anahtar sözcüklerini kullanamazsınız:  
  
- Zaman [uyumsuz](async.md) değiştirici kullanarak tanımladığınız zaman uyumsuz yöntemler.  
- Bir [yield return](yield.md) veya bildiri içeren Yineleyici yöntemleri `yield break` .
- Uzantı yönteminin ilk bağımsız değişkeni, `in` Bu bağımsız değişken bir struct olmadığı takdirde değiştiriciye sahip olamaz.
- Bu bağımsız değişkenin genel bir tür olduğu bir genişletme yönteminin ilk bağımsız değişkeni (Bu tür bir struct gibi kısıtlanıyor olsa bile).

## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [Yöntem Parametreleri](method-parameters.md)
- [Güvenli verimli kod yazma](../../write-safe-efficient-code.md)
