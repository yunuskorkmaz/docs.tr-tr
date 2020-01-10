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
ms.openlocfilehash: 96d9904af0106d797c9fc5199bda76da53874451
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709250"
---
# <a name="names-of-classes-structs-and-interfaces"></a>Sınıf, Yapı ve Arabirimlerin Adları
Aşağıdaki adlandırma yönergeleri genel tür adlandırması için geçerlidir.  
  
 **✓ DO** sınıflar ve yapılar isimleri veya PascalCasing kullanarak isim deyimlere ile ad.  
  
 Bu, tür adlarını, fiil tümcecikleriyle adlandırılan metotlardan ayırır.  
  
 **✓ DO** ad arabirimleri sıfat tümcecikleri veya bazen isimleri veya isim deyimleri ile.  
  
 İsimler ve ad tümcecikleri nadiren kullanılmalıdır ve bu, türün bir arabirim değil, soyut bir sınıf olması gerektiğini gösteriyor olabilir.  
  
 **X DO NOT** bir önek (örneğin, "C") sınıfı adlar verin.  
  
 **✓ CONSIDER** adını bitiş türetilmiş adıyla sınıflar temel sınıf.  
  
 Bu çok okunabilir ve ilişkiyi açık bir şekilde açıklar. Bu kodda bazı örnekler şunlardır: `ArgumentOutOfRangeException``Exception`ve `SerializableAttribute`olan `Attribute`türü. Ancak, bu kılavuz uygulanırken makul bir karardır kullanılması önemlidir; Örneğin, `Button` sınıfı bir tür `Control` olayıdır, ancak `Control` adında görünmez.  
  
 **✓ DO** öneki arabirimi adları harfle türü bir arabirim olduğunu belirtmek için ediyorum.  
  
 Örneğin, `IComponent` (tanımlayıcı ad), `ICustomAttributeProvider` (ad tümceciği) ve `IPersistable` (sıfatıcı) uygun arabirim adlarıdır. Diğer tür adlarında olduğu gibi kısaltmaların önüne kaçının.  
  
 **✓ DO** göre "t" arabirimi adı öneki burada sınıfıdır arabirimi standart uygulaması bir sınıf – arabirim çifti tanımlarken yalnızca adları farklı olduğundan emin olun.  
  
## <a name="names-of-generic-type-parameters"></a>Genel tür parametrelerinin adları  
 .NET Framework 2,0 ' e Genel türler eklendi. Özellik, *Type parametresi*olarak adlandırılan yeni bir tanımlayıcı türü sunmuştur.  
  
 **✓ DO** tamamen kendinden açıklamalıdır tek harfli adıdır ve açıklayıcı bir ad, değer Ekle değil sürece genel tür parametreleri ile açıklayıcı adlar adı.  
  
 **✓ CONSIDER** kullanarak `T` tek tek harfli tür parametresi türleriyle türü parametre adı olarak.  
  
```csharp  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 **✓ DO** önek tanımlayıcı türü parametre adları ile `T`.  
  
```csharp  
public interface ISessionChannel<TSession> where TSession : ISession {  
    TSession Session { get; }  
}  
```  
  
 **✓ CONSIDER** kısıtlamaları belirten yerleştirilen bir tür parametresi parametresi adına üzerinde.  
  
 Örneğin, `ISession` kısıtlanmış bir parametre `TSession`çağrılabilir.  
  
## <a name="names-of-common-types"></a>Ortak türlerin adları  
 **✓ DO** türetilmiş veya belirli .NET Framework türleri uygulama türleri adlandırırken aşağıdaki tabloda açıklanan yönergeleri izleyin.  
  
|Temel tür|Türetilmiş/uygulama türü Kılavuzu|  
|---------------|------------------------------------------|  
|`System.Attribute`|**✓ DO** özel öznitelik sınıfları adlarına "Özniteliği" soneki ekleyin.|  
|`System.Delegate`|**✓ DO** olayları kullanılan temsilciler adlarını "EventHandler" soneki ekleyin.<br /><br /> **✓ DO** olay işleyicileri olarak kullanılanların dışındaki "Geri çağırma" adlarına temsilcileri soneki ekleyin.<br /><br /> **X DO NOT** temsilciye "Temsilci" soneki ekleyin.|  
|`System.EventArgs`|**✓ DO** "EventArgs." soneki ekleyin|  
|`System.Enum`|**X DO NOT** bu sınıftan türeyen; bunun yerine, dili tarafından desteklenen anahtar sözcüğü kullanın; örneğin, C# ' ta kullanmak `enum` anahtar sözcüğü.<br /><br /> **X DO NOT** "Enum" veya "Bayrağı." soneki ekleyin|  
|`System.Exception`|**✓ DO** "Özel durum." soneki ekleyin|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|**✓ DO** "Sözlük." soneki ekleyin `IDictionary` belirli bir koleksiyon türüdür, ancak bu kılavuz, aşağıdaki genel Koleksiyonlar Kılavuzu üzerinden önceliklidir.|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|**✓ DO** "Koleksiyonu." soneki ekleyin|  
|`System.IO.Stream`|**✓ DO** "Akış" soneki ekleyin|  
|`CodeAccessPermission IPermission`|**✓ DO** "İzni." soneki ekleyin|  
  
## <a name="naming-enumerations"></a>Sabit listeleri adlandırma  
 Genel olarak numaralandırma türlerinin (numaralandırmalar olarak da bilinir) adları, standart tür adlandırma kurallarını (Pascalbüyük harfleri, vb.) izlemelidir. Ancak, özel olarak Numaralandırmalar için uygulanan ek yönergeler vardır.  
  
 **✓ DO** değerlerinin bit alanları olmadığı sürece bir sabit listesi için tekil tür adı kullanın.  
  
 **✓ DO** çoğul türü adı numaralandırması için bit alanları ile bayrakları enum olarak da bilinir değerler olarak kullanın.  
  
 **X DO NOT** "Enum" soneki enum türü adları kullanın.  
  
 **X DO NOT** enum "Bayrakları" sonekleri adlarını yazın veya "Bayrak" kullanın.  
  
 **X DO NOT** bir önek numaralandırma değeri adları (örneğin, "ad" ADO numaralandırmalar için.), "rtf" zengin metin numaralandırmalar, vb. için kullanın.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)
