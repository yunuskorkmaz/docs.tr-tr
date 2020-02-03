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
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727791"
---
# <a name="names-of-classes-structs-and-interfaces"></a>Sınıf, Yapı ve Arabirimlerin Adları
Aşağıdaki adlandırma yönergeleri genel tür adlandırması için geçerlidir.

 ✔️ sınıfları ve yapıları, Pascalbüyük harfleri kullanarak isimler veya isim tümcecikleriyle adlandırın.

 Bu, tür adlarını, fiil tümcecikleriyle adlandırılan metotlardan ayırır.

 ✔️, sıfatıcı tümceciklerle ya da isimler veya isim tümcecikleriyle ara sıra ad arabirimleri YAPıN.

 İsimler ve ad tümcecikleri nadiren kullanılmalıdır ve bu, türün bir arabirim değil, soyut bir sınıf olması gerektiğini gösteriyor olabilir.

 ❌, sınıf adlarına önek vermez (örneğin, "C").

 ✔️, türetilmiş sınıfların adını temel sınıfın adı ile sona erdirmenizi düşünün.

 Bu çok okunabilir ve ilişkiyi açık bir şekilde açıklar. Bu kodda bazı örnekler şunlardır: `ArgumentOutOfRangeException``Exception`ve `SerializableAttribute`olan `Attribute`türü. Ancak, bu kılavuz uygulanırken makul bir karardır kullanılması önemlidir; Örneğin, `Button` sınıfı bir tür `Control` olayıdır, ancak `Control` adında görünmez.

 türün bir arabirim olduğunu göstermek için ı harfiyle önek arabirim adları ✔️.

 Örneğin, `IComponent` (tanımlayıcı ad), `ICustomAttributeProvider` (ad tümceciği) ve `IPersistable` (sıfatıcı) uygun arabirim adlarıdır. Diğer tür adlarında olduğu gibi kısaltmaların önüne kaçının.

 ✔️, sınıfın standart bir uygulama olduğu bir sınıf-arabirim çifti tanımlarken adların yalnızca arabirim adındaki "I" ön ekiyle farklı olduğundan emin olun.

## <a name="names-of-generic-type-parameters"></a>Genel tür parametrelerinin adları
 .NET Framework 2,0 ' e Genel türler eklendi. Özellik, *Type parametresi*olarak adlandırılan yeni bir tanımlayıcı türü sunmuştur.

 ✔️, genel tür parametrelerini açıklayıcı adlarla, tek bir harf adı tamamen kendi kendine açıklama olmadığından ve açıklayıcı bir ad değer eklemedikçe tanımlayıcı adlarla adlandırın.

 ✔️ tek harfli bir tür parametresine sahip türler için tür parametre adı olarak `T` kullanmayı göz önünde bulundurun.

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 ✔️ önek açıklayıcı tür parametre adlarını `T`olarak YAPıN.

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 ✔️ parametre adında bir tür parametresine yerleştirilmiş olan kısıtlamaları belirtmeyi düşünün.

 Örneğin, `ISession` kısıtlanmış bir parametre `TSession`çağrılabilir.

## <a name="names-of-common-types"></a>Ortak türlerin adları
 ✔️, belirli .NET Framework türlerinden türetilen türleri adlandırırken veya BUNLARı uygulamadan aşağıdaki tabloda açıklanan yönergeleri izleyin.

|Temel tür|Türetilmiş/uygulama türü Kılavuzu|
|---------------|------------------------------------------|
|`System.Attribute`|✔️ "özniteliğini" sonekini özel öznitelik sınıflarının adlarına ekleme.|
|`System.Delegate`|✔️ "EventHandler" sonekini, olaylarda kullanılan temsilcilerin adlarına ekler.<br /><br /> ✔️, "geri çağırma" sonekini olay işleyicileri olarak kullanıldıkları dışındaki temsilcilerin adlarına ekler.<br /><br /> ❌, "temsilci" sonekini bir temsilciye eklemez.|
|`System.EventArgs`|"EventArgs" sonekini eklemek ✔️.|
|`System.Enum`|❌ bu sınıftan türetilmiyor; Bunun yerine diliniz tarafından desteklenen anahtar sözcüğü kullanın; Örneğin, içinde C#`enum` anahtar sözcüğünü kullanın.<br /><br /> ❌ "enum" veya "Flag" sonekini eklemeyin.|
|`System.Exception`|son eki "özel durum" ✔️ ekler.|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|"Sözlük" sonekini eklemek ✔️. `IDictionary` belirli bir koleksiyon türüdür, ancak bu kılavuz, aşağıdaki genel Koleksiyonlar Kılavuzu üzerinden önceliklidir.|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|"Collection" sonekini eklemek ✔️.|
|`System.IO.Stream`|"Stream" sonekini eklemek ✔️.|
|`CodeAccessPermission IPermission`|✔️ sonek "Iznini" ekleyin.|

## <a name="naming-enumerations"></a>Sabit listeleri adlandırma
 Genel olarak numaralandırma türlerinin (numaralandırmalar olarak da bilinir) adları, standart tür adlandırma kurallarını (Pascalbüyük harfleri, vb.) izlemelidir. Ancak, özel olarak Numaralandırmalar için uygulanan ek yönergeler vardır.

 ✔️, değerleri bit alanları olmadığı takdirde sabit listesi için tekil tür adı kullanın.

 ✔️, bit alanları olan bir numaralandırma için, Flags sabit listesi olarak da adlandırılan bir çoğul tür adı kullanın.

 ❌ enum türü adlarında bir "enum" soneki kullanmayın.

 ❌ enum türü adlarında "Flag" veya "Flags" soneklerini kullanmayın.

 ❌, sabit listesi değer adlarında (örn. "ad", zengin metin çeteleleri için "RTF") bir ön ek kullanmaz.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)
