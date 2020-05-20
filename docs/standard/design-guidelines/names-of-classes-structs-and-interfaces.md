---
title: Sınıf, Yapı ve Arabirimlerin Adları
description: .NET kitaplıklarını genişleten ve etkileşime geçen kitaplıklar tasarlamanın bir parçası olarak sınıfları, yapıları ve arabirimleri adlandırma yönergelerini kullanın.
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
ms.openlocfilehash: e7eee414c5bf5c69f63543ef240e50a4d2d948a3
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419089"
---
# <a name="names-of-classes-structs-and-interfaces"></a>Sınıf, Yapı ve Arabirimlerin Adları
Aşağıdaki adlandırma yönergeleri genel tür adlandırması için geçerlidir.

 ✔️ sınıfları ve yapıları, Pascalbüyük harfleri kullanarak isimler veya isim tümcecikleriyle adlandırın.

 Bu, tür adlarını, fiil tümcecikleriyle adlandırılan metotlardan ayırır.

 ✔️, sıfatıcı tümceciklerle ya da isimler veya isim tümcecikleriyle ara sıra ad arabirimleri YAPıN.

 İsimler ve ad tümcecikleri nadiren kullanılmalıdır ve bu, türün bir arabirim değil, soyut bir sınıf olması gerektiğini gösteriyor olabilir.

 ❌Sınıf adlarına bir ön ek vermeyin (ör. "C").

 ✔️, türetilmiş sınıfların adını temel sınıfın adı ile sona erdirmenizi düşünün.

 Bu çok okunabilir ve ilişkiyi açık bir şekilde açıklar. Kodda buna örnek olarak şunlar verilebilir:, `ArgumentOutOfRangeException` `Exception` ve türü `SerializableAttribute` `Attribute` . Ancak, bu kılavuz uygulanırken makul bir karardır kullanılması önemlidir; Örneğin, `Button` sınıfı bir tür `Control` olaydır, ancak `Control` adında görünmez.

 türün bir arabirim olduğunu göstermek için ı harfiyle önek arabirim adları ✔️.

 Örneğin, `IComponent` (açıklayıcı ad), `ICustomAttributeProvider` (ad tümceciği) ve `IPersistable` (sıfatıcı) uygun arabirim adlarıdır. Diğer tür adlarında olduğu gibi kısaltmaların önüne kaçının.

 ✔️, sınıfın standart bir uygulama olduğu bir sınıf-arabirim çifti tanımlarken adların yalnızca arabirim adındaki "I" ön ekiyle farklı olduğundan emin olun.

## <a name="names-of-generic-type-parameters"></a>Genel tür parametrelerinin adları
 .NET Framework 2,0 ' e Genel türler eklendi. Özellik, *Type parametresi*olarak adlandırılan yeni bir tanımlayıcı türü sunmuştur.

 ✔️, genel tür parametrelerini açıklayıcı adlarla, tek bir harf adı tamamen kendi kendine açıklama olmadığından ve açıklayıcı bir ad değer eklemedikçe tanımlayıcı adlarla adlandırın.

 ✔️ `T` tek harfli bir tür parametresine sahip türler için tür parametre adı olarak KULLANMAYı düşünün.

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 öneki tanımlayıcı tür parametre adlarını ile ✔️ `T` .

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 ✔️ parametre adında bir tür parametresine yerleştirilmiş olan kısıtlamaları belirtmeyi düşünün.

 Örneğin, ile kısıtlanmış bir parametre `ISession` çağrılabilir `TSession` .

## <a name="names-of-common-types"></a>Ortak türlerin adları
 ✔️, belirli .NET Framework türlerinden türetilen türleri adlandırırken veya BUNLARı uygulamadan aşağıdaki tabloda açıklanan yönergeleri izleyin.

|Temel tür|Türetilmiş/uygulama türü Kılavuzu|
|---------------|------------------------------------------|
|`System.Attribute`|✔️ "özniteliğini" sonekini özel öznitelik sınıflarının adlarına ekleme.|
|`System.Delegate`|✔️ "EventHandler" sonekini, olaylarda kullanılan temsilcilerin adlarına ekler.<br /><br /> ✔️, "geri çağırma" sonekini olay işleyicileri olarak kullanıldıkları dışındaki temsilcilerin adlarına ekler.<br /><br /> ❌"Temsilci" sonekini bir temsilciye eklemeyin.|
|`System.EventArgs`|"EventArgs" sonekini eklemek ✔️.|
|`System.Enum`|❌Bu sınıftan türemeyin; Bunun yerine diliniz tarafından desteklenen anahtar sözcüğü kullanın; Örneğin, C# ' de `enum` anahtar sözcüğünü kullanın.<br /><br /> ❌"Enum" veya "Flag" sonekini eklemeyin.|
|`System.Exception`|son eki "özel durum" ✔️ ekler.|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|"Sözlük" sonekini eklemek ✔️. `IDictionary`Bu, belirli bir koleksiyon türüdür, ancak bu kılavuz, aşağıdaki genel Koleksiyonlar Kılavuzu ' na göre önceliklidir.|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|"Collection" sonekini eklemek ✔️.|
|`System.IO.Stream`|"Stream" sonekini eklemek ✔️.|
|`CodeAccessPermission IPermission`|✔️ sonek "Iznini" ekleyin.|

## <a name="naming-enumerations"></a>Sabit listeleri adlandırma
 Genel olarak numaralandırma türlerinin (numaralandırmalar olarak da bilinir) adları, standart tür adlandırma kurallarını (Pascalbüyük harfleri, vb.) izlemelidir. Ancak, özel olarak Numaralandırmalar için uygulanan ek yönergeler vardır.

 ✔️, değerleri bit alanları olmadığı takdirde sabit listesi için tekil tür adı kullanın.

 ✔️, bit alanları olan bir numaralandırma için, Flags sabit listesi olarak da adlandırılan bir çoğul tür adı kullanın.

 ❌Enum türü adlarında bir "enum" soneki kullanmayın.

 ❌Enum türü adlarında "Flag" veya "Flags" soneklerini kullanmayın.

 ❌Sabit listesi değer adlarında bir ön ek kullanmayın (örn. "ad" with ADO numaralandırmaları, zengin metin numaralandırmaları için "RTF" vb.).

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Adlandırma yönergeleri](../../../docs/standard/design-guidelines/naming-guidelines.md)
