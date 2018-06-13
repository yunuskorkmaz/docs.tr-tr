---
title: parametresi değiştiricisi (C# Başvurusu)
ms.date: 03/06/2018
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: 58500cf2caa1446af6b663f1b765c0be92309f1d
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2018
ms.locfileid: "34311916"
---
# <a name="in-parameter-modifier-c-reference"></a>parametresi değiştiricisi (C# Başvurusu)

`in` Anahtar sözcüğü başvuruya göre geçirilecek bağımsız değişkenler neden olur. Benzer; [ref](ref.md) veya [çıkışı](out-parameter-modifier.md) anahtar sözcüklerini dışındaki `in` bağımsız değişkenleri çağrılan yöntemi tarafından değiştirilemez. Oysa `ref` bağımsız değişkenleri değiştirilmiş, `out` bağımsız değişkenleri çağıran tarafından değiştirilmesi gerekir ve bu değişiklik observable arama bağlamında olan.

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

Önceki örnekte gösteren `in` değiştiricisi genellikle gereksiz çağrı sitede. Yalnızca yöntemi bildiriminde de gereklidir.

> [!NOTE] 
> `in` Anahtar sözcüğü de kullanılabilir bir genel tür parametresi tür parametresi, bir parçası olarak karşıtıdır olduğunu belirtmek için bir `foreach` deyimi, veya bir parçası olarak bir `join` yan tümcesinde bir LINQ Sorgu. Kullanımı hakkında daha fazla bilgi için `in` anahtar sözcüğü bu bağlamlarında bkz [içinde](in.md), tüm bu kullanımlar için bağlantılar sağlar.
  
 Değişkenler geçildi olarak `in` bağımsız değişkenleri, bir yöntem çağrısı iletilmeden önce başlatılmalıdır. Ancak, çağrılan yöntemin düzgün bir değer atamak veya bağımsız değişkeni değiştirin.  
  
 Ancak `in`, `ref`, ve `out` anahtar sözcükleri neden farklı bir çalışma zamanı davranışı, derleme zamanında yöntem imzası parçası değerlendirilmez. Bir yöntem aldığını tek fark ise, bu nedenle, yöntem aşırı yüklenemez bir `ref` veya `in` bağımsız değişkeni ve diğer alır bir `out` bağımsız değişkeni. Aşağıdaki kod, örneğin, derlenmez:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Aşırı yükleme varlığını temel `in` izin verilir:  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a>Çözümleme kurallarını aşırı yükleme

Değeriyle yöntemleriyle aşırı çözümleme kurallarını anlama `in` gerekçesi anlama tarafından bağımsız değişkenleri `in` bağımsız değişkenler. Yöntemlerini kullanarak tanımlama `in` parametreleri olan bir olası performans en iyi duruma getirme. Bazı `struct` tür bağımsız değişkenleri boyutu büyük ve yöntemleri sıkı döngüler veya kritik kod yolları çağrıldığında, bu yapıları kopyalama maliyetini önemlidir. Yöntemleri bildirmek `in` çağrılan yöntemin bağımsız durumunu değiştirmez çünkü bağımsız değişkenleri başvuruya göre güvenle geçirilebilir olduğunu belirtmek üzere parametreler. Bu bağımsız değişkenleri başvuruya göre geçirme (büyük olasılıkla) pahalı kopyası engeller. 

Belirtme `in` çağrısında bağımsız değişkenler için site genellikle isteğe bağlıdır. Bağımsız değişkenleri değere göre geçirme ile başvuru kullanarak geçirme arasındaki anlamsal fark yoktur `in` değiştiricisi. `in` Çağrısı sitede değiştiricisi olduğundan isteğe bağlı bağımsız değişkeninin değeri değişebilir belirtmek gerekmez. Açıkça eklemeniz `in` bağımsız değişkeni emin olmak için arama sitedeki değiştirici olmayan değere göre başvuruya göre geçirilir. Açıkça kullanarak `in` aşağıdaki iki etkilere sahiptir:

İlk olarak, belirtme `in` çağrısı site eşleşen ile tanımlanmış bir yöntem seçmek için derleyici zorlar `in` parametresi. Aksi durumda, yalnızca içinde varken, iki yöntemleri farklı olduğunda `in`, değeriyle aşırı daha iyi bir eşleşmedir.

İkinci olarak, belirtme `in` başvuruya göre bağımsız değişken geçirmek yapma bildirir. İle kullanılan bağımsız değişkenine `in` doğrudan başvuruda bulunulabilir bir konumu temsil etmesi gerekir. Aynı genel kurallar için `out` ve `ref` bağımsız değişkenleri uygulanır: sabitleri, normal özellikler veya değerler üretmesi diğer ifadeler kullanılamaz. Aksi takdirde, atlama `in` çağrısı salt okunur başvuru yöntemi olarak geçirmek için geçici bir değişken oluşturmak için sağlayacak site derleyici bildirir. Derleyici birkaç kısıtlamalarıyla üstesinden gelmek için geçici bir değişken oluşturur `in` bağımsız değişkenler:

- Derleme zamanı sabitleri olarak geçici bir değişken verir `in` parametreleri.
- Özellikleri veya diğer ifadeler için geçici bir değişken sağlayan `in` parametreleri.
- Geçici bir değişken değişkene izin verir söz konusu olduğunda bağımsız değişken türü örtük bir dönüştürme için parametre türü.

Tüm önceki örneklerde, derleyici sabiti, özelliği veya diğer ifade değerini depolar geçici bir değişken oluşturur.

Aşağıdaki kod, bu kurallar gösterilmektedir:

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

Şimdi, değer bağımsız değişken kullanarak başka bir yöntem kullanılabilir varsayalım. Aşağıdaki kodda gösterildiği gibi değişiklik sonuçları:

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

Başvuruya göre bağımsız değişken geçirildiği yalnızca yöntem çağrısı son sunucudur.

> [!NOTE]
> Önceki kod kullanan `int` Basitlik bağımsız değişken türü olarak. Çünkü `int` başvurusundan daha büyük olan çoğu modern makinelerinizde tek bir geçirme hiçbir faydası yoktur `int` salt okunur başvuru olarak. 

## <a name="limitations-on-in-parameters"></a>Sınırlamalar `in` parametreleri

Kullanamazsınız `in`, `ref`, ve `out` yöntemleri şu tür için anahtar sözcükleri:  
  
- Kullanarak tanımladığınız zaman uyumsuz yöntemleri [zaman uyumsuz](async.md) değiştiricisi.  
- Dahil yineleyici metotları bir [verim return](yield.md) veya `yield break` deyimi.  

## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../index.md)  
 [C# Programlama Kılavuzu](../../programming-guide/index.md)  
 [C# Anahtar Sözcükleri](index.md)  
 [Yöntem parametreleri](method-parameters.md) [başvuru semantiği ile değer türleri](../../reference-semantics-with-value-types.md)
