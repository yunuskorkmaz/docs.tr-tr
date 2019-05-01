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
author: KrzysztofCwalina
ms.openlocfilehash: c0790cd20daf859ec81e2252dc9bce46673daf90
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945515"
---
# <a name="names-of-classes-structs-and-interfaces"></a>Sınıf, Yapı ve Arabirimlerin Adları
Adlandırma yönergeleri izleyin, genel bir tür adlandırma için geçerlidir.  
  
 **✓ DO** sınıflar ve yapılar isimleri veya PascalCasing kullanarak isim deyimlere ile ad.  
  
 Fiili tümcecikleri adlandırılır yöntemleri, bu tür adlarını ayırır.  
  
 **✓ DO** ad arabirimleri sıfat tümcecikleri veya bazen isimleri veya isim deyimleri ile.  
  
 Nadiren isimleri ve isim ifadeleri kullanılmalıdır ve bir Özet sınıf ve bir arabirim türü olması gerektiğini gösterebilir.  
  
 **X DO NOT** bir önek (örneğin, "C") sınıfı adlar verin.  
  
 **✓ CONSIDER** adını bitiş türetilmiş adıyla sınıflar temel sınıf.  
  
 Bu çok okunabilir ve ilişki açıkça açıklar. Bu kod bazı örnekleri şunlardır: `ArgumentOutOfRangeException`, bir tür olduğundan, `Exception`, ve `SerializableAttribute`, bir tür olduğundan, `Attribute`. Ancak, bu kılavuzu uygulama içinde makul yükümlülükten kullanmak önemlidir; Örneğin, `Button` sınıfı, bir tür, `Control` olay rağmen `Control` adını görünmez.  
  
 **✓ DO** öneki arabirimi adları harfle türü bir arabirim olduğunu belirtmek için ediyorum.  
  
 Örneğin, `IComponent` (tanımlayıcı ad), `ICustomAttributeProvider` (isim deyim) ve `IPersistable` (gelen) uygun arabirimi adlarıdır. Diğer tür adları ile kısaltmalar önleyebilmemizdir.  
  
 **✓ DO** göre "t" arabirimi adı öneki burada sınıfıdır arabirimi standart uygulaması bir sınıf – arabirim çifti tanımlarken yalnızca adları farklı olduğundan emin olun.  
  
## <a name="names-of-generic-type-parameters"></a>Genel tür parametrelerinin adları  
 Genel türler için .NET Framework 2.0 eklendi. Yeni bir tür tanımlayıcı adlı bir özelliği kullanıma *tür parametresi*.  
  
 **✓ DO** tamamen kendinden açıklamalıdır tek harfli adıdır ve açıklayıcı bir ad, değer Ekle değil sürece genel tür parametreleri ile açıklayıcı adlar adı.  
  
 **✓ CONSIDER** kullanarak `T` tek tek harfli tür parametresi türleriyle türü parametre adı olarak.  
  
```  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 **✓ DO** önek tanımlayıcı türü parametre adları ile `T`.  
  
```  
public interface ISessionChannel<TSession> where TSession : ISession {  
    TSession Session { get; }  
}  
```  
  
 **✓ CONSIDER** kısıtlamaları belirten yerleştirilen bir tür parametresi parametresi adına üzerinde.  
  
 Örneğin, bir parametre, için kısıtlı `ISession` olarak adlandırılabilir `TSession`.  
  
## <a name="names-of-common-types"></a>Ortak Tür adları  
 **✓ DO** türetilmiş veya belirli .NET Framework türleri uygulama türleri adlandırırken aşağıdaki tabloda açıklanan yönergeleri izleyin.  
  
|Temel tür|Türetilmiş ve uygulama türü Kılavuzu|  
|---------------|------------------------------------------|  
|`System.Attribute`|**✓ DO** özel öznitelik sınıfları adlarına "Özniteliği" soneki ekleyin.|  
|`System.Delegate`|**✓ DO** olayları kullanılan temsilciler adlarını "EventHandler" soneki ekleyin.<br /><br /> **✓ DO** olay işleyicileri olarak kullanılanların dışındaki "Geri çağırma" adlarına temsilcileri soneki ekleyin.<br /><br /> **X DO NOT** temsilciye "Temsilci" soneki ekleyin.|  
|`System.EventArgs`|**✓ DO** "EventArgs." soneki ekleyin|  
|`System.Enum`|**X DO NOT** bu sınıftan türeyen; bunun yerine, dili tarafından desteklenen anahtar sözcüğü kullanın; örneğin, C# ' ta kullanmak `enum` anahtar sözcüğü.<br /><br /> **X DO NOT** "Enum" veya "Bayrağı." soneki ekleyin|  
|`System.Exception`|**✓ DO** "Özel durum." soneki ekleyin|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|**✓ DO** "Sözlük." soneki ekleyin Unutmayın `IDictionary` belirli bir koleksiyon türüdür, ancak bu kılavuz aşağıdaki daha genel koleksiyonlar yönerge göre önceliklidir.|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|**✓ DO** "Koleksiyonu." soneki ekleyin|  
|`System.IO.Stream`|**✓ DO** "Akış" soneki ekleyin|  
|`CodeAccessPermission IPermission`|**✓ DO** "İzni." soneki ekleyin|  
  
## <a name="naming-enumerations"></a>Adlandırma sabit listeleri  
 Numaralandırma türleri (numaralandırmalar olarak da bilinir) adlarını genel standart türü adlandırma kuralları (PascalCasing, vb.) izlemelidir. Ancak, özellikle numaralandırmalar için geçerli olan ek yönergeler de vardır.  
  
 **✓ DO** değerlerinin bit alanları olmadığı sürece bir sabit listesi için tekil tür adı kullanın.  
  
 **✓ DO** çoğul türü adı numaralandırması için bit alanları ile bayrakları enum olarak da bilinir değerler olarak kullanın.  
  
 **X DO NOT** "Enum" soneki enum türü adları kullanın.  
  
 **X DO NOT** enum "Bayrakları" sonekleri adlarını yazın veya "Bayrak" kullanın.  
  
 **X DO NOT** bir önek numaralandırma değeri adları (örneğin, "ad" ADO numaralandırmalar için.), "rtf" zengin metin numaralandırmalar, vb. için kullanın.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)
