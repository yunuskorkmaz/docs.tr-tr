---
title: Sınıflar, yapılar ve arabirimleri adları
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1841fbfcb76d5b56681b63ec4b39e9a7418707f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="names-of-classes-structs-and-interfaces"></a>Sınıflar, yapılar ve arabirimleri adları
Genel bir tür adlandırma için izleyin adlandırma yönergeleri uygulayın.  
  
 **✓ YAPMAK** sınıflar ve yapılar isimleri veya PascalCasing kullanarak isim deyimlere ile ad.  
  
 Bu tür adları fiil tümcecikleri adlı yöntemlerden ayırır.  
  
 **✓ YAPMAK** ad arabirimleri sıfat tümcecikleri veya bazen isimleri veya isim deyimleri ile.  
  
 Nadiren isimleri ve isim tümcecikleri kullanılmalıdır ve türü soyut bir sınıf ve bir arabirim olmalıdır gösterebilir.  
  
 **X yok** bir önek (örneğin, "C") sınıfı adlar verin.  
  
 **✓ DÜŞÜNÜN** adını bitiş türetilmiş adıyla sınıflar temel sınıf.  
  
 Bu çok okunabilir ve ilişkiyi açıkça açıklar. Bu kod bazı örnekleri şunlardır: `ArgumentOutOfRangeException`, bir tür olduğu, `Exception`, ve `SerializableAttribute`, bir tür olduğu, `Attribute`. Ancak, bu kılavuz uygulamada makul karar kullanmak önemlidir; Örneğin, `Button` sınıfı, bir tür, `Control` olay, ancak `Control` adını görünmüyor.  
  
 **✓ YAPMAK** öneki arabirimi adları harfle türü bir arabirim olduğunu belirtmek için ediyorum.  
  
 Örneğin, `IComponent` (tanımlayıcı bir isim), `ICustomAttributeProvider` (isim tümcecik) ve `IPersistable` (gelen) uygun arabirimi adlardır. Diğer tür adları olduğu gibi ile kısaltmalar kaçının.  
  
 **✓ YAPMAK** göre "t" arabirimi adı öneki burada sınıfıdır arabirimi standart uygulaması bir sınıf – arabirim çifti tanımlarken yalnızca adları farklı olduğundan emin olun.  
  
## <a name="names-of-generic-type-parameters"></a>Genel tür parametreleri adları  
 Genel türler için .NET Framework 2.0 eklendi. Tanımlayıcı adlı yeni bir tür özellik sunulmuştur *tür parametresi*.  
  
 **✓ YAPMAK** tamamen kendinden açıklamalıdır tek harfli adıdır ve açıklayıcı bir ad, değer Ekle değil sürece genel tür parametreleri ile açıklayıcı adlar adı.  
  
 **✓ DÜŞÜNÜN** kullanarak `T` tek tek harfli tür parametresi türleriyle türü parametre adı olarak.  
  
```  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 **✓ YAPMAK** önek tanımlayıcı türü parametre adları ile `T`.  
  
```  
public interface ISessionChannel<TSession> where TSession : ISession{  
    TSession Session { get; }  
}  
```  
  
 **✓ DÜŞÜNÜN** kısıtlamaları belirten yerleştirilen bir tür parametresi parametresi adına üzerinde.  
  
 Örneğin, bir parametre kısıtlı için `ISession` olarak adlandırılabilir `TSession`.  
  
## <a name="names-of-common-types"></a>Adları genel türleri  
 **✓ YAPMAK** türetilmiş veya belirli .NET Framework türleri uygulama türleri adlandırırken aşağıdaki tabloda açıklanan yönergeleri izleyin.  
  
|Temel tür|Türetilmiş ve uygulama türü Kılavuzu|  
|---------------|------------------------------------------|  
|`System.Attribute`|**✓ YAPMAK** özel öznitelik sınıfları adlarına "Özniteliği" soneki ekleyin.|  
|`System.Delegate`|**✓ YAPMAK** olayları kullanılan temsilciler adlarını "EventHandler" soneki ekleyin.<br /><br /> **✓ YAPMAK** olay işleyicileri olarak kullanılanların dışındaki "Geri çağırma" adlarına temsilcileri soneki ekleyin.<br /><br /> **X yok** temsilciye "Temsilci" soneki ekleyin.|  
|`System.EventArgs`|**✓ YAPMAK** "EventArgs." soneki ekleyin|  
|`System.Enum`|**X yok** bu sınıftan türeyen; bunun yerine, dili tarafından desteklenen anahtar sözcüğü kullanın; örneğin, C# ' ta kullanmak `enum` anahtar sözcüğü.<br /><br /> **X yok** "Enum" veya "Bayrağı." soneki ekleyin|  
|`System.Exception`|**✓ YAPMAK** "Özel durum." soneki ekleyin|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|**✓ YAPMAK** "Sözlük." soneki ekleyin Unutmayın `IDictionary` koleksiyonu belirli bir türde değil, ancak bu kılavuz aşağıdaki daha genel koleksiyonları kural göre önceliklidir.|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|**✓ YAPMAK** "Koleksiyonu." soneki ekleyin|  
|`System.IO.Stream`|**✓ YAPMAK** "Akış" soneki ekleyin|  
|`CodeAccessPermission IPermission`|**✓ YAPMAK** "İzni." soneki ekleyin|  
  
## <a name="naming-enumerations"></a>Numaralandırmalar adlandırma  
 Numaralandırma türleri (numaralandırmaları olarak da bilinir) adlarını genel standart türü adlandırma kuralları (PascalCasing, vb.) izlemelidir. Ancak, özellikle numaralandırmaları uygulamak ek yönergeler vardır.  
  
 **✓ YAPMAK** değerlerinin bit alanları olmadığı sürece bir sabit listesi için tekil tür adı kullanın.  
  
 **✓ YAPMAK** çoğul türü adı numaralandırması için bit alanları ile bayrakları enum olarak da bilinir değerler olarak kullanın.  
  
 **X yok** "Enum" soneki enum türü adları kullanın.  
  
 **X yok** enum "Bayrakları" sonekleri adlarını yazın veya "Bayrak" kullanın.  
  
 **X yok** bir önek numaralandırma değeri adları (örneğin, "ad" ADO numaralandırmalar için.), "rtf" zengin metin numaralandırmalar, vb. için kullanın.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)
