---
title: parametre değiştirici - C# Referans
ms.date: 03/19/2020
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: 20956f9e25b6830a8876824a4c9dad1dbc4c4f3e
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249376"
---
# <a name="in-parameter-modifier-c-reference"></a>parametre değiştirici (C# Reference)

Anahtar `in` kelime bağımsız değişkenlerin başvuruyla geçirilmesine neden olur. Bu, resmi parametreyi bağımsız değişken için bir diğer ad yapar, bu da bir değişken olmalıdır. Başka bir deyişle, parametre üzerinde herhangi bir işlem bağımsız değişken üzerinde yapılır. Bu, `in` bağımsız değişkenlerin çağrılan yöntemle değiştirilememek [dışında, ref](ref.md) veya [çıkış](out-parameter-modifier.md) anahtar kelimeleri gibidir. Bağımsız `ref` değişkenler değiştirilebilirken, `out` bağımsız değişkenler çağrılan yöntem tarafından değiştirilmelidir ve bu değişiklikler çağrı bağlamında gözlemlenebilir.

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

Önceki örnek, değiştiricinin `in` arama yerinde genellikle gereksiz olduğunu gösterir. Yalnızca yöntem bildiriminde gereklidir.

> [!NOTE]
> Anahtar `in` kelime, tür parametresinin bir `foreach` deyimin parçası olarak veya LINQ sorgusundaki bir yan tümcenin `join` parçası olarak karşıt olduğunu belirtmek için genel bir tür parametresi ile de kullanılabilir. Bu bağlamlarda `in` anahtar kelimenin kullanımı hakkında daha fazla bilgi için, tüm bu kullanımlara bağlantılar sağlayan içeriye bakın. [in](in.md)
  
Bağımsız değişken `in` olarak geçirilen değişkenler, bir yöntem çağrısında geçirilmeden önce başharflere geçirilmelidir. Ancak, çağrılan yöntem bir değer atamaz veya bağımsız değişkeni değiştiremez.  

`in` Parametre değiştirici C# 7.2 ve sonraki durumlarda kullanılabilir. Önceki sürümlerde derleyici hatası `CS8107` oluşturulur ("Özellik 'yalnızca başvuru' C# 7.0'da kullanılamaz. Lütfen dil sürüm 7.2 veya daha büyük kullanın.") Derleyici dili sürümünü yapılandırmak için [C# dil sürümünü seçin'e](../configure-language-version.md)bakın.

, `in` `ref`ve `out` anahtar kelimeler aşırı yük çözümlemesi amacıyla yöntem imzasının bir parçası olarak kabul edilmez. Bu nedenle, tek fark bir yöntemin bir `ref` bağımsız `in` değişken ilerlerken `out` diğerinin bir bağımsız değişken almasıysa, yöntemler aşırı yüklenemez. Örneğin, aşağıdaki kod derlenilmeyecektir:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Varlığına göre aşırı `in` yüklemeye izin verilir:  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a>Aşırı yükleme çözünürlüğü kuralları

Bağımsız değişkenlerin motivasyonunu anlayarak, değerlere `in` karşılık gelen bağımsız değişkenlerle yöntemleriçin aşırı yük çözümleme kurallarını anlayabilirsiniz. `in` Parametreleri kullanarak `in` yöntemleri tanımlamak potansiyel bir performans optimizasyonudur. Bazı `struct` tür bağımsız değişkenleri boyutu büyük olabilir ve yöntemleri sıkı döngüler veya kritik kod yolları çağrıldığında, bu yapıları kopyalama maliyeti önemlidir. Çağrılan `in` yöntem bu bağımsız değişkenin durumunu değiştirmediği için bağımsız değişkenlerin güvenle başvuruyla geçirilebileceğini belirtmek için parametreleri bildiren yöntemler. Bu bağımsız değişkenleri referansla geçirme (potansiyel olarak) pahalı kopyayı önler.

Arama `in` sitesindeki bağımsız değişkenler için belirtme genellikle isteğe bağlıdır. Bağımsız değişkenleri değere göre geçirmekle `in` değiştirici kullanarak referansla geçirmek arasında anlamsal bir fark yoktur. Bağımsız `in` değişkenin değerinin değiştirilebileceğini belirtmeniz gerekmedığından, arama sitesindeki değiştirici isteğe bağlıdır. Bağımsız değişkenin `in` değere göre değil, referans la geçtiğinden emin olmak için çağrı yerindeki değiştiriciyi açıkça eklersiniz. Açıkça kullanarak `in` aşağıdaki iki etkisi vardır:

İlk olarak, `in` çağrı yerinde belirtilmesi derleyiciyi eşleşen `in` bir parametre ile tanımlanan bir yöntem seçmeye zorlar. Aksi takdirde, iki yöntem sadece `in`varlığında farklı olduğunda , değer aşırı yük daha iyi bir maç.

İkinci olarak, `in` belirtme, bir bağımsız değişkeni başvuruyla geçirme niyetinizi bildirir. Kullanılan bağımsız `in` değişken, doğrudan başvurulabilen bir konumu temsil etmelidir. Aynı genel kurallar `out` `ref` ve bağımsız değişkenler geçerlidir: Değerleri üreten sabitleri, sıradan özellikleri veya diğer ifadeleri kullanamazsınız. Aksi takdirde, `in` çağrı yerinde atlayarak, derleyiciye yönteme salt okunur başvuruyla geçmek için geçici bir değişken oluşturmasına izin vereceğini bildirir. Derleyici bağımsız değişkenlerle `in` çeşitli kısıtlamaları aşmak için geçici bir değişken oluşturur:

- Geçici bir değişken, zaman sabitlerinin `in` parametre olarak derlenmesine olanak tanır.
- Geçici bir değişken, parametreler için `in` özellikler veya diğer ifadelere izin verir.
- Geçici bir değişken, bağımsız değişken türünden parametre türüne örtülü dönüştürme nin olduğu bağımsız değişkenlere izin verir.

Önceki tüm örneklerde derleyici, sabitin, özelliğin veya diğer ifadenin değerini depolayan geçici bir değişken oluşturur.

Aşağıdaki kod şu kuralları göstermektedir:

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

Şimdi, değer bağımsız değişkenleri tarafından kullanılan başka bir yöntem kullanılabilir olduğunu varsayalım. Sonuçlar aşağıdaki kodda gösterildiği gibi değişir:

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

Bağımsız değişkenin başvuru yla geçtiği tek yöntem çağrısı son yöntemdir.

> [!NOTE]
> Önceki kod basitlik için bağımsız değişken türü olarak kullanır. `int` Çoğu `int` modern makinelerde bir referans daha büyük olduğundan, tek bir `int` okuma referans olarak geçen hiçbir yararı yoktur.

## <a name="limitations-on-in-parameters"></a>Parametrelerüzerindeki `in` sınırlamalar

Aşağıdaki yöntem türleri `in`için `ref`, `out` ve anahtar kelimeleri kullanamazsınız:  
  
- Async değiştirici kullanarak tanımladığınız [async](async.md) yöntemleri.  
- [Verim getirisi](yield.md) veya `yield break` deyimi içeren yineleyici yöntemleri.
- Bir uzantı yönteminin ilk `in` bağımsız değişkeni, bu bağımsız değişken bir yapı olmadığı sürece değiştiriciye sahip olamaz.
- Bu bağımsız değişkenin genel bir tür olduğu bir uzantı yönteminin ilk bağımsız değişkeni (bu tür bir yapı olarak sınırlandırılsa bile.)

## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [Yöntem Parametreleri](method-parameters.md)
- [Güvenli verimli kod yazın](../../write-safe-efficient-code.md)
