---
title: parametre değiştiricisi içinde- C# başvurusu
ms.custom: seodec18
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: e39d470308ed5a2b2ed82ade0faf8ba925228c2c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661444"
---
# <a name="in-parameter-modifier-c-reference"></a>parametre değiştiricisi (C# Başvurusu)

`in` Anahtar sözcüğü, başvuruya göre geçirilecek bağımsız değişkenleri neden olur. Bir değişken olmalıdır bağımsız değişkeni için bir diğer ad biçimsel parametre kolaylaştırır. Diğer bir deyişle, herhangi bir işlem parametresinde bağımsız değişken üzerinde yapılır. Nasıl olduğunu [ref](ref.md) veya [kullanıma](out-parameter-modifier.md) anahtar sözcükler, tek farkı, `in` tarafından çağrılan yöntem bağımsız değişkenleri değiştirilemez. Oysa `ref` bağımsız değişkenleri değiştirilebilir, `out` bağımsız değişkenleri çağrılan yöntem tarafından değiştirilmelidir ve arama bağlamda observable söz konusu değişiklikler şunlardır.

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

Yukarıdaki örnekte gösteren `in` değiştiricisi gereksiz genellikle çağıran sitede. Ayrıca, yöntem bildiriminde yalnızca gereklidir.

> [!NOTE] 
> `in` Anahtar sözcüğü de kullanılabilir bir genel tür parametresi tür parametresi değişken karşıtı, kapsamında olduğunu belirtmek için bir `foreach` deyimi veya bir parçası olarak bir `join` bir LINQ sorgu yan tümcesi. Kullanımı hakkında daha fazla bilgi için `in` anahtar sözcüğü şu bağlamlarda bkz [içinde](in.md), bu kullanan tüm bağlantılar sağlar.
  
Değişkenleri olarak geçirildi `in` bağımsız değişken bir yöntem çağrısında iletilmeden önce başlatılması gerekir. Ancak, çağrılan yöntem olmayan bir değer atamak veya bağımsız değişkenini değiştirin.  

`in` Parametre değiştiricisi kullanılabilir C# 7.2 ve üzeri. Derleyici Hatası önceki sürümlerini oluşturmak `CS8107` ("özelliği 'salt okunur başvurular' kullanılabilir değil C# 7.0. Lütfen dil 7.2 veya üzeri bir sürümü kullanın.") Derleyici dil sürüm yapılandırmak için bkz [seçin C# dil sürümü](../configure-language-version.md).

`in`, `ref`, Ve `out` anahtar sözcükleri aşırı yükleme çözünürlüğü amacıyla yöntem imzasının parçası dikkate alınmaz. Tek fark, bir yöntem aldığını ise, bu nedenle, yöntemler aşırı yüklenemez bir `ref` veya `in` bağımsız değişkeni ve diğer alır bir `out` bağımsız değişken. Örneğin, aşağıdaki kod derlemeyecektir:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Aşırı yükleme varlığını temel alarak `in` izin verilir:  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a>Aşırı yükleme çözünürlüğü kuralları

Değer yöntemleriyle aşırı yükleme çözünürlüğü kurallarını anlamak `in` hacktivism anlama tarafından bağımsız değişkenleri `in` bağımsız değişkenler. Yöntemlerini kullanarak tanımlama `in` parametreleri olan bir olası performans iyileştirme. Bazı `struct` tür bağımsız değişkenleri boyutu büyük ve yöntemler sıkı döngüler veya kritik kod yollarını çağrıldığında, bu yapıları kopyalama maliyeti önemlidir. Yöntemi `in` çağrılan yöntem bağımsız durumunu değiştirmez çünkü bağımsız değişkenleri başvuruya göre güvenle geçirilebilir olduğunu belirtmek için parametreleri. Bu bağımsız değişkenleri başvuruya göre geçirme (büyük olasılıkla) pahalı kopyalama önler. 

Belirtme `in` çağrıda bağımsız değişkenler için site genellikle isteğe bağlıdır. Bağımsız değişkenler değere göre geçirme ve başvuru kullanarak geçirme arasındaki semantik farklılığı yok `in` değiştiricisi. `in` Değiştiricisi çağrı sitesinde olduğundan isteğe bağlı bağımsız değişkenin değeri değiştirilebilir belirtmek gerekmez. Açıkça eklemeniz `in` değiştirici bağımsız değişken emin olmak için çağrı sitesinde başvuruya göre değil değere göre geçirilir. Kullanarak açıkça `in` aşağıdaki iki etkisi olur:

İlk olarak belirterek `in` çağrısı site eşleşen ile tanımlanan bir yöntem seçmek için derleyicinin zorlar `in` parametresi. Aksi takdirde iki yöntem yalnızca içinde varken, farklı olduğunda `in`, değere göre aşırı daha iyi bir eşleşmedir.

İkinci olarak, belirtme `in` başvuruya göre bağımsız değişken geçmek için amacınız bildirir. İle kullanılan bağımsız değişkenine `in` doğrudan başvurulabilen bir konumu temsil etmelidir. Aynı genel kurallar için `out` ve `ref` bağımsız değişkenleri: Sabitler, sıradan özellikleri veya değerler üreten diğer ifadeler kullanamazsınız. Aksi takdirde, atlama `in` çağrısı salt okunur başvuru yöntemi olarak geçirmek için geçici bir değişken oluşturmak için sağlayacak site derleyici bildirir. Derleyici ile birkaç kısıtlamaları, geçici bir değişken oluşturur `in` bağımsız değişkenleri:

- Derleme zamanı sabiti olarak geçici bir değişkene izin verir `in` parametreleri.
- Özellikleri veya diğer ifadeler için geçici değişken sağlayan `in` parametreleri.
- Geçici bir değişken bağımsız değişkenleri sağlayan bir bağımsız değişken türü arasında örtük dönüşüm için parametre türü olduğu.

Tüm önceki örneklerde, derleyici sabiti, özelliği veya başka bir ifadenin değerini depolayan geçici bir değişken oluşturur.

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

Şimdi, değer değişkenleriyle kullanarak başka bir yöntem yoktu varsayalım. Sonuçları, aşağıdaki kodda gösterildiği gibi değiştirin:

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

Yalnızca yöntem çağrısında bağımsız değişkenini başvuruya göre geçirildiği son sunucudur.

> [!NOTE]
> Önceki kod `int` kolaylık olması için bağımsız değişken türü olarak. Çünkü `int` başvurusundan daha büyük olan en modern makineler'de, tek bir geçirme için hiçbir avantajı yoktur `int` salt okunur başvuru olarak. 

## <a name="limitations-on-in-parameters"></a>Sınırlamalar `in` parametreleri

Kullanamazsınız `in`, `ref`, ve `out` yöntemleri aşağıdaki türde için anahtar sözcükler:  
  
- Kullanarak tanımladığınız zaman uyumsuz yöntemlerde [zaman uyumsuz](async.md) değiştiricisi.  
- Yineleyici yöntemleri dahil bir [yield return](yield.md) veya `yield break` deyimi.  

## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Yöntem Parametreleri](method-parameters.md)
- [Güvenli verimli kod yazma](../../write-safe-efficient-code.md)
