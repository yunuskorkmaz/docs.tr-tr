---
title: Sınıf, Yapı ve Arabirimlerin Adları
ms.date: 10/22/2008
helpviewer_keywords:
- type names, guidelines
- classes [.NET Framework], names
- enumerations [.NET Framework], names
- names [.NET Framework], interfaces
- common type names
- names [.NET Framework], type names
- names [.NET Framework], classes
- interfaces [.NET Framework], names
- generic type parameters
ms.assetid: 87a4b0da-ed64-43b1-ac43-968576c444ce
ms.openlocfilehash: 2c528348c0e84037a80df9797c56f03b51c73adc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400598"
---
# <a name="names-of-classes-structs-and-interfaces"></a>Sınıf, Yapı ve Arabirimlerin Adları
İzleyen adlandırma yönergeleri genel tür adlandırma için geçerlidir.

 PascalCasing kullanarak ad sınıfları ve yapılarını isim veya isim tümcecikleriyle ✔️.

 Bu, tür adlarını fiil tümcecikleriyle birlikte isimlendirilen yöntemlerden ayırır.

 ✔️ DO isim arabirimleri sıfat tümcecikleri veya bazen isim veya isim tümcecikleri ile.

 Alelade ve isme tümcecikleri nadiren kullanılmalıdır ve bu tür bir arabirim değil soyut bir sınıf olması gerektiğini gösterebilir.

 ❌Sınıf adlarını bir önek vermeyin (örneğin, "C").

 ✔️ taban sınıfın adı ile türemiş sınıfların adını sona erdirme düşünün.

 Bu çok okunabilir ve açıkça ilişki açıklar. Kodda buna örnek olarak `ArgumentOutOfRangeException`şunlar verilebilir: `Exception`, `SerializableAttribute`bir tür , `Attribute`ve , bir tür . Ancak, bu kılavuzun uygulanmasında makul bir yargı kullanmak önemlidir; örneğin, `Button` sınıf bir tür `Control` olaydır, `Control` ancak kendi adında görünmez.

 ✔️, türünün bir arabirim olduğunu belirtmek için I harfi ile önek arabirim adları.

 Örneğin, `IComponent` (açıklayıcı isim), `ICustomAttributeProvider` (isim tümceciği) `IPersistable` ve (sıfat) uygun arabirim adlarıdır. Diğer tür adlarında olduğu gibi kısaltmalardan kaçının.

 ✔️ DO, sınıfın arabirimin standart bir uygulaması olduğu bir sınıf-arabirim çifti tanımlarken, adların yalnızca arabirim adı üzerindeki "I" önekine göre farklılık gösterir olmasını sağlar.

## <a name="names-of-generic-type-parameters"></a>Genel Tip Parametrelerin Adları
 Genel ler .NET Framework 2.0'a eklendi. Özellik, *tür parametresi*adı verilen yeni bir tanımlayıcı türünü tanıttı.

 ✔️ DO, tek harfli bir ad tamamen açıklayıcı olmadığı ve açıklayıcı bir ad değer katmadığı sürece genel tür parametrelerini açıklayıcı adlarla adlandırın.

 ✔️ Tek `T` harfli tür parametresi olan türler için tür parametre adı olarak kullanmayı düşünün.

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 ✔️ DO öneki tanımlayıcı türü parametre `T`adları ile .

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 ✔️ Parametre adına bir tür parametresine yerleştirilen kısıtlamaları gösteren göz önünde bulundurun.

 Örneğin, sınırlandırılmış `ISession` bir parametre . `TSession`

## <a name="names-of-common-types"></a>Ortak Türlerin Adları
 ✔️ DO, belirli .NET Framework türlerinden türetilen veya uygularken aşağıdaki tabloda açıklanan yönergeleri izleyin.

|Taban Türü|Tür Yönergesi Tür Yönergesi|
|---------------|------------------------------------------|
|`System.Attribute`|✔️ DO özel öznitelik sınıflarının adlarına "Öznitelik" soneki ekleyin.|
|`System.Delegate`|✔️ etkinliklerde kullanılan temsilci adlarına "EventHandler" eki ekleyin.<br /><br /> ✔️ OLAY İşleyicisi olarak kullanılanlar dışındaki temsilci adlarına "Geri Arama" ekini ekleyin.<br /><br /> ❌Bir temsilciye "Temsilci" ekini EKLEMEYIN.|
|`System.EventArgs`|✔️ "EventArgs" eki ekleyin.|
|`System.Enum`|❌BU DERSTEN TÜRETİn; bunun yerine diliniz tarafından desteklenen anahtar kelimeyi kullanın; örneğin, C#'da anahtar `enum` sözcük kullanın.<br /><br /> ❌"Enum" veya "Bayrak" ekini EKLEMEYIN.|
|`System.Exception`|✔️ "Özel Durum" eki ekleyin.|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|✔️ "Sözlük" soneki ekleyin. Belirli `IDictionary` bir koleksiyon türü olduğunu unutmayın, ancak bu kılavuz aşağıdaki daha genel koleksiyonlar kılavuzundan önce gelir.|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|✔️ DO sonek "Koleksiyon ekleyin."|
|`System.IO.Stream`|✔️ DO sonek "Akış ekleyin."|
|`CodeAccessPermission IPermission`|✔️ "İzin" eki ekleyin.|

## <a name="naming-enumerations"></a>Adlandırma Tümumerations
 Genel olarak numaralandırma türlerinin adları (enums olarak da adlandırılır) standart tür adlandırma kurallarına (PascalCasing, vb.) uymalıdır. Ancak, özellikle enumlar için geçerli olan ek yönergeler vardır.

 ✔️ d değerleri bit alanları olmadığı sürece numaralandırma için tekil bir tür adı kullanın.

 ✔️ D'ye, bayraklar enum olarak da adlandırılan bit alanları değerlerini içeren bir numaralandırma için çoğul tür adı kullanın.

 ❌ENUM türü adlarında "Enum" soneki kullanmaYIN.

 ❌ENUM türü adlarında "Bayrak" veya "Bayraklar" soneki kullanmayın.

 ❌Numaralandırma değer adlarında önek (örneğin, ADO enumları için "reklam", zengin metin enumları için "rtf") bir önek KULLANMAYIN.

 *2005, 2009 Microsoft Corporation © bölümleri. Tüm hakları saklıdır.*

 *Pearson Education, Inc.'in izniyle [Framework Design Guidelines: Conventions, Idioms and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina ve Brad Abrams tarafından 22 Ekim 2008'de Addison-Wesley Professional tarafından Microsoft Windows Geliştirme Serisi'nin bir parçası olarak yayımlandı.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)
