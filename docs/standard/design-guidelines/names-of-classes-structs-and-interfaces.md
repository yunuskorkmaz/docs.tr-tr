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
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="48517-102">Sınıf, Yapı ve Arabirimlerin Adları</span><span class="sxs-lookup"><span data-stu-id="48517-102">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="48517-103">Aşağıdaki adlandırma yönergeleri genel tür adlandırması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="48517-103">The naming guidelines that follow apply to general type naming.</span></span>

 <span data-ttu-id="48517-104">✔️ sınıfları ve yapıları, Pascalbüyük harfleri kullanarak isimler veya isim tümcecikleriyle adlandırın.</span><span class="sxs-lookup"><span data-stu-id="48517-104">✔️ DO name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>

 <span data-ttu-id="48517-105">Bu, tür adlarını, fiil tümcecikleriyle adlandırılan metotlardan ayırır.</span><span class="sxs-lookup"><span data-stu-id="48517-105">This distinguishes type names from methods, which are named with verb phrases.</span></span>

 <span data-ttu-id="48517-106">✔️, sıfatıcı tümceciklerle ya da isimler veya isim tümcecikleriyle ara sıra ad arabirimleri YAPıN.</span><span class="sxs-lookup"><span data-stu-id="48517-106">✔️ DO name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>

 <span data-ttu-id="48517-107">İsimler ve ad tümcecikleri nadiren kullanılmalıdır ve bu, türün bir arabirim değil, soyut bir sınıf olması gerektiğini gösteriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="48517-107">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>

 <span data-ttu-id="48517-108">❌, sınıf adlarına önek vermez (örneğin, "C").</span><span class="sxs-lookup"><span data-stu-id="48517-108">❌ DO NOT give class names a prefix (e.g., "C").</span></span>

 <span data-ttu-id="48517-109">✔️, türetilmiş sınıfların adını temel sınıfın adı ile sona erdirmenizi düşünün.</span><span class="sxs-lookup"><span data-stu-id="48517-109">✔️ CONSIDER ending the name of derived classes with the name of the base class.</span></span>

 <span data-ttu-id="48517-110">Bu çok okunabilir ve ilişkiyi açık bir şekilde açıklar.</span><span class="sxs-lookup"><span data-stu-id="48517-110">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="48517-111">Bu kodda bazı örnekler şunlardır: `ArgumentOutOfRangeException``Exception`ve `SerializableAttribute`olan `Attribute`türü.</span><span class="sxs-lookup"><span data-stu-id="48517-111">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="48517-112">Ancak, bu kılavuz uygulanırken makul bir karardır kullanılması önemlidir; Örneğin, `Button` sınıfı bir tür `Control` olayıdır, ancak `Control` adında görünmez.</span><span class="sxs-lookup"><span data-stu-id="48517-112">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>

 <span data-ttu-id="48517-113">türün bir arabirim olduğunu göstermek için ı harfiyle önek arabirim adları ✔️.</span><span class="sxs-lookup"><span data-stu-id="48517-113">✔️ DO prefix interface names with the letter I, to indicate that the type is an interface.</span></span>

 <span data-ttu-id="48517-114">Örneğin, `IComponent` (tanımlayıcı ad), `ICustomAttributeProvider` (ad tümceciği) ve `IPersistable` (sıfatıcı) uygun arabirim adlarıdır.</span><span class="sxs-lookup"><span data-stu-id="48517-114">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="48517-115">Diğer tür adlarında olduğu gibi kısaltmaların önüne kaçının.</span><span class="sxs-lookup"><span data-stu-id="48517-115">As with other type names, avoid abbreviations.</span></span>

 <span data-ttu-id="48517-116">✔️, sınıfın standart bir uygulama olduğu bir sınıf-arabirim çifti tanımlarken adların yalnızca arabirim adındaki "I" ön ekiyle farklı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="48517-116">✔️ DO ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>

## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="48517-117">Genel tür parametrelerinin adları</span><span class="sxs-lookup"><span data-stu-id="48517-117">Names of Generic Type Parameters</span></span>
 <span data-ttu-id="48517-118">.NET Framework 2,0 ' e Genel türler eklendi.</span><span class="sxs-lookup"><span data-stu-id="48517-118">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="48517-119">Özellik, *Type parametresi*olarak adlandırılan yeni bir tanımlayıcı türü sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="48517-119">The feature introduced a new kind of identifier called *type parameter*.</span></span>

 <span data-ttu-id="48517-120">✔️, genel tür parametrelerini açıklayıcı adlarla, tek bir harf adı tamamen kendi kendine açıklama olmadığından ve açıklayıcı bir ad değer eklemedikçe tanımlayıcı adlarla adlandırın.</span><span class="sxs-lookup"><span data-stu-id="48517-120">✔️ DO name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>

 <span data-ttu-id="48517-121">✔️ tek harfli bir tür parametresine sahip türler için tür parametre adı olarak `T` kullanmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="48517-121">✔️ CONSIDER using `T` as the type parameter name for types with one single-letter type parameter.</span></span>

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 <span data-ttu-id="48517-122">✔️ önek açıklayıcı tür parametre adlarını `T`olarak YAPıN.</span><span class="sxs-lookup"><span data-stu-id="48517-122">✔️ DO prefix descriptive type parameter names with `T`.</span></span>

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 <span data-ttu-id="48517-123">✔️ parametre adında bir tür parametresine yerleştirilmiş olan kısıtlamaları belirtmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="48517-123">✔️ CONSIDER indicating constraints placed on a type parameter in the name of the parameter.</span></span>

 <span data-ttu-id="48517-124">Örneğin, `ISession` kısıtlanmış bir parametre `TSession`çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="48517-124">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>

## <a name="names-of-common-types"></a><span data-ttu-id="48517-125">Ortak türlerin adları</span><span class="sxs-lookup"><span data-stu-id="48517-125">Names of Common Types</span></span>
 <span data-ttu-id="48517-126">✔️, belirli .NET Framework türlerinden türetilen türleri adlandırırken veya BUNLARı uygulamadan aşağıdaki tabloda açıklanan yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="48517-126">✔️ DO follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>

|<span data-ttu-id="48517-127">Temel tür</span><span class="sxs-lookup"><span data-stu-id="48517-127">Base Type</span></span>|<span data-ttu-id="48517-128">Türetilmiş/uygulama türü Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="48517-128">Derived/Implementing Type Guideline</span></span>|
|---------------|------------------------------------------|
|`System.Attribute`|<span data-ttu-id="48517-129">✔️ "özniteliğini" sonekini özel öznitelik sınıflarının adlarına ekleme.</span><span class="sxs-lookup"><span data-stu-id="48517-129">✔️ DO add the suffix "Attribute" to names of custom attribute classes.</span></span>|
|`System.Delegate`|<span data-ttu-id="48517-130">✔️ "EventHandler" sonekini, olaylarda kullanılan temsilcilerin adlarına ekler.</span><span class="sxs-lookup"><span data-stu-id="48517-130">✔️ DO add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="48517-131">✔️, "geri çağırma" sonekini olay işleyicileri olarak kullanıldıkları dışındaki temsilcilerin adlarına ekler.</span><span class="sxs-lookup"><span data-stu-id="48517-131">✔️ DO add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="48517-132">❌, "temsilci" sonekini bir temsilciye eklemez.</span><span class="sxs-lookup"><span data-stu-id="48517-132">❌ DO NOT add the suffix "Delegate" to a delegate.</span></span>|
|`System.EventArgs`|<span data-ttu-id="48517-133">"EventArgs" sonekini eklemek ✔️.</span><span class="sxs-lookup"><span data-stu-id="48517-133">✔️ DO add the suffix "EventArgs."</span></span>|
|`System.Enum`|<span data-ttu-id="48517-134">❌ bu sınıftan türetilmiyor; Bunun yerine diliniz tarafından desteklenen anahtar sözcüğü kullanın; Örneğin, içinde C#`enum` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="48517-134">❌ DO NOT derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="48517-135">❌ "enum" veya "Flag" sonekini eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="48517-135">❌ DO NOT add the suffix "Enum" or "Flag."</span></span>|
|`System.Exception`|<span data-ttu-id="48517-136">son eki "özel durum" ✔️ ekler.</span><span class="sxs-lookup"><span data-stu-id="48517-136">✔️ DO add the suffix "Exception."</span></span>|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="48517-137">"Sözlük" sonekini eklemek ✔️.</span><span class="sxs-lookup"><span data-stu-id="48517-137">✔️ DO add the suffix "Dictionary."</span></span> <span data-ttu-id="48517-138">`IDictionary` belirli bir koleksiyon türüdür, ancak bu kılavuz, aşağıdaki genel Koleksiyonlar Kılavuzu üzerinden önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="48517-138">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="48517-139">"Collection" sonekini eklemek ✔️.</span><span class="sxs-lookup"><span data-stu-id="48517-139">✔️ DO add the suffix "Collection."</span></span>|
|`System.IO.Stream`|<span data-ttu-id="48517-140">"Stream" sonekini eklemek ✔️.</span><span class="sxs-lookup"><span data-stu-id="48517-140">✔️ DO add the suffix "Stream."</span></span>|
|`CodeAccessPermission IPermission`|<span data-ttu-id="48517-141">✔️ sonek "Iznini" ekleyin.</span><span class="sxs-lookup"><span data-stu-id="48517-141">✔️ DO add the suffix "Permission."</span></span>|

## <a name="naming-enumerations"></a><span data-ttu-id="48517-142">Sabit listeleri adlandırma</span><span class="sxs-lookup"><span data-stu-id="48517-142">Naming Enumerations</span></span>
 <span data-ttu-id="48517-143">Genel olarak numaralandırma türlerinin (numaralandırmalar olarak da bilinir) adları, standart tür adlandırma kurallarını (Pascalbüyük harfleri, vb.) izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="48517-143">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="48517-144">Ancak, özel olarak Numaralandırmalar için uygulanan ek yönergeler vardır.</span><span class="sxs-lookup"><span data-stu-id="48517-144">However, there are additional guidelines that apply specifically to enums.</span></span>

 <span data-ttu-id="48517-145">✔️, değerleri bit alanları olmadığı takdirde sabit listesi için tekil tür adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="48517-145">✔️ DO use a singular type name for an enumeration unless its values are bit fields.</span></span>

 <span data-ttu-id="48517-146">✔️, bit alanları olan bir numaralandırma için, Flags sabit listesi olarak da adlandırılan bir çoğul tür adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="48517-146">✔️ DO use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>

 <span data-ttu-id="48517-147">❌ enum türü adlarında bir "enum" soneki kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="48517-147">❌ DO NOT use an "Enum" suffix in enum type names.</span></span>

 <span data-ttu-id="48517-148">❌ enum türü adlarında "Flag" veya "Flags" soneklerini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="48517-148">❌ DO NOT use "Flag" or "Flags" suffixes in enum type names.</span></span>

 <span data-ttu-id="48517-149">❌, sabit listesi değer adlarında (örn. "ad", zengin metin çeteleleri için "RTF") bir ön ek kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="48517-149">❌ DO NOT use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>

 <span data-ttu-id="48517-150">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="48517-150">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="48517-151">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="48517-151">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="48517-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48517-152">See also</span></span>

- [<span data-ttu-id="48517-153">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="48517-153">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="48517-154">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="48517-154">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
