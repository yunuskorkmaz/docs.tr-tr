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
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="ee4cf-103">Sınıf, Yapı ve Arabirimlerin Adları</span><span class="sxs-lookup"><span data-stu-id="ee4cf-103">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="ee4cf-104">Aşağıdaki adlandırma yönergeleri genel tür adlandırması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-104">The naming guidelines that follow apply to general type naming.</span></span>

 <span data-ttu-id="ee4cf-105">✔️ sınıfları ve yapıları, Pascalbüyük harfleri kullanarak isimler veya isim tümcecikleriyle adlandırın.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-105">✔️ DO name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>

 <span data-ttu-id="ee4cf-106">Bu, tür adlarını, fiil tümcecikleriyle adlandırılan metotlardan ayırır.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-106">This distinguishes type names from methods, which are named with verb phrases.</span></span>

 <span data-ttu-id="ee4cf-107">✔️, sıfatıcı tümceciklerle ya da isimler veya isim tümcecikleriyle ara sıra ad arabirimleri YAPıN.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-107">✔️ DO name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>

 <span data-ttu-id="ee4cf-108">İsimler ve ad tümcecikleri nadiren kullanılmalıdır ve bu, türün bir arabirim değil, soyut bir sınıf olması gerektiğini gösteriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-108">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>

 <span data-ttu-id="ee4cf-109">❌Sınıf adlarına bir ön ek vermeyin (ör. "C").</span><span class="sxs-lookup"><span data-stu-id="ee4cf-109">❌ DO NOT give class names a prefix (e.g., "C").</span></span>

 <span data-ttu-id="ee4cf-110">✔️, türetilmiş sınıfların adını temel sınıfın adı ile sona erdirmenizi düşünün.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-110">✔️ CONSIDER ending the name of derived classes with the name of the base class.</span></span>

 <span data-ttu-id="ee4cf-111">Bu çok okunabilir ve ilişkiyi açık bir şekilde açıklar.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-111">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="ee4cf-112">Kodda buna örnek olarak şunlar verilebilir:, `ArgumentOutOfRangeException` `Exception` ve türü `SerializableAttribute` `Attribute` .</span><span class="sxs-lookup"><span data-stu-id="ee4cf-112">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="ee4cf-113">Ancak, bu kılavuz uygulanırken makul bir karardır kullanılması önemlidir; Örneğin, `Button` sınıfı bir tür `Control` olaydır, ancak `Control` adında görünmez.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-113">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>

 <span data-ttu-id="ee4cf-114">türün bir arabirim olduğunu göstermek için ı harfiyle önek arabirim adları ✔️.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-114">✔️ DO prefix interface names with the letter I, to indicate that the type is an interface.</span></span>

 <span data-ttu-id="ee4cf-115">Örneğin, `IComponent` (açıklayıcı ad), `ICustomAttributeProvider` (ad tümceciği) ve `IPersistable` (sıfatıcı) uygun arabirim adlarıdır.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-115">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="ee4cf-116">Diğer tür adlarında olduğu gibi kısaltmaların önüne kaçının.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-116">As with other type names, avoid abbreviations.</span></span>

 <span data-ttu-id="ee4cf-117">✔️, sınıfın standart bir uygulama olduğu bir sınıf-arabirim çifti tanımlarken adların yalnızca arabirim adındaki "I" ön ekiyle farklı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-117">✔️ DO ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>

## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="ee4cf-118">Genel tür parametrelerinin adları</span><span class="sxs-lookup"><span data-stu-id="ee4cf-118">Names of Generic Type Parameters</span></span>
 <span data-ttu-id="ee4cf-119">.NET Framework 2,0 ' e Genel türler eklendi.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-119">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="ee4cf-120">Özellik, *Type parametresi*olarak adlandırılan yeni bir tanımlayıcı türü sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-120">The feature introduced a new kind of identifier called *type parameter*.</span></span>

 <span data-ttu-id="ee4cf-121">✔️, genel tür parametrelerini açıklayıcı adlarla, tek bir harf adı tamamen kendi kendine açıklama olmadığından ve açıklayıcı bir ad değer eklemedikçe tanımlayıcı adlarla adlandırın.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-121">✔️ DO name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>

 <span data-ttu-id="ee4cf-122">✔️ `T` tek harfli bir tür parametresine sahip türler için tür parametre adı olarak KULLANMAYı düşünün.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-122">✔️ CONSIDER using `T` as the type parameter name for types with one single-letter type parameter.</span></span>

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 <span data-ttu-id="ee4cf-123">öneki tanımlayıcı tür parametre adlarını ile ✔️ `T` .</span><span class="sxs-lookup"><span data-stu-id="ee4cf-123">✔️ DO prefix descriptive type parameter names with `T`.</span></span>

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 <span data-ttu-id="ee4cf-124">✔️ parametre adında bir tür parametresine yerleştirilmiş olan kısıtlamaları belirtmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-124">✔️ CONSIDER indicating constraints placed on a type parameter in the name of the parameter.</span></span>

 <span data-ttu-id="ee4cf-125">Örneğin, ile kısıtlanmış bir parametre `ISession` çağrılabilir `TSession` .</span><span class="sxs-lookup"><span data-stu-id="ee4cf-125">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>

## <a name="names-of-common-types"></a><span data-ttu-id="ee4cf-126">Ortak türlerin adları</span><span class="sxs-lookup"><span data-stu-id="ee4cf-126">Names of Common Types</span></span>
 <span data-ttu-id="ee4cf-127">✔️, belirli .NET Framework türlerinden türetilen türleri adlandırırken veya BUNLARı uygulamadan aşağıdaki tabloda açıklanan yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-127">✔️ DO follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>

|<span data-ttu-id="ee4cf-128">Temel tür</span><span class="sxs-lookup"><span data-stu-id="ee4cf-128">Base Type</span></span>|<span data-ttu-id="ee4cf-129">Türetilmiş/uygulama türü Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ee4cf-129">Derived/Implementing Type Guideline</span></span>|
|---------------|------------------------------------------|
|`System.Attribute`|<span data-ttu-id="ee4cf-130">✔️ "özniteliğini" sonekini özel öznitelik sınıflarının adlarına ekleme.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-130">✔️ DO add the suffix "Attribute" to names of custom attribute classes.</span></span>|
|`System.Delegate`|<span data-ttu-id="ee4cf-131">✔️ "EventHandler" sonekini, olaylarda kullanılan temsilcilerin adlarına ekler.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-131">✔️ DO add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="ee4cf-132">✔️, "geri çağırma" sonekini olay işleyicileri olarak kullanıldıkları dışındaki temsilcilerin adlarına ekler.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-132">✔️ DO add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="ee4cf-133">❌"Temsilci" sonekini bir temsilciye eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-133">❌ DO NOT add the suffix "Delegate" to a delegate.</span></span>|
|`System.EventArgs`|<span data-ttu-id="ee4cf-134">"EventArgs" sonekini eklemek ✔️.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-134">✔️ DO add the suffix "EventArgs."</span></span>|
|`System.Enum`|<span data-ttu-id="ee4cf-135">❌Bu sınıftan türemeyin; Bunun yerine diliniz tarafından desteklenen anahtar sözcüğü kullanın; Örneğin, C# ' de `enum` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-135">❌ DO NOT derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="ee4cf-136">❌"Enum" veya "Flag" sonekini eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-136">❌ DO NOT add the suffix "Enum" or "Flag."</span></span>|
|`System.Exception`|<span data-ttu-id="ee4cf-137">son eki "özel durum" ✔️ ekler.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-137">✔️ DO add the suffix "Exception."</span></span>|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="ee4cf-138">"Sözlük" sonekini eklemek ✔️.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-138">✔️ DO add the suffix "Dictionary."</span></span> <span data-ttu-id="ee4cf-139">`IDictionary`Bu, belirli bir koleksiyon türüdür, ancak bu kılavuz, aşağıdaki genel Koleksiyonlar Kılavuzu ' na göre önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-139">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="ee4cf-140">"Collection" sonekini eklemek ✔️.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-140">✔️ DO add the suffix "Collection."</span></span>|
|`System.IO.Stream`|<span data-ttu-id="ee4cf-141">"Stream" sonekini eklemek ✔️.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-141">✔️ DO add the suffix "Stream."</span></span>|
|`CodeAccessPermission IPermission`|<span data-ttu-id="ee4cf-142">✔️ sonek "Iznini" ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-142">✔️ DO add the suffix "Permission."</span></span>|

## <a name="naming-enumerations"></a><span data-ttu-id="ee4cf-143">Sabit listeleri adlandırma</span><span class="sxs-lookup"><span data-stu-id="ee4cf-143">Naming Enumerations</span></span>
 <span data-ttu-id="ee4cf-144">Genel olarak numaralandırma türlerinin (numaralandırmalar olarak da bilinir) adları, standart tür adlandırma kurallarını (Pascalbüyük harfleri, vb.) izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-144">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="ee4cf-145">Ancak, özel olarak Numaralandırmalar için uygulanan ek yönergeler vardır.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-145">However, there are additional guidelines that apply specifically to enums.</span></span>

 <span data-ttu-id="ee4cf-146">✔️, değerleri bit alanları olmadığı takdirde sabit listesi için tekil tür adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-146">✔️ DO use a singular type name for an enumeration unless its values are bit fields.</span></span>

 <span data-ttu-id="ee4cf-147">✔️, bit alanları olan bir numaralandırma için, Flags sabit listesi olarak da adlandırılan bir çoğul tür adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-147">✔️ DO use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>

 <span data-ttu-id="ee4cf-148">❌Enum türü adlarında bir "enum" soneki kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-148">❌ DO NOT use an "Enum" suffix in enum type names.</span></span>

 <span data-ttu-id="ee4cf-149">❌Enum türü adlarında "Flag" veya "Flags" soneklerini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-149">❌ DO NOT use "Flag" or "Flags" suffixes in enum type names.</span></span>

 <span data-ttu-id="ee4cf-150">❌Sabit listesi değer adlarında bir ön ek kullanmayın (örn. "ad" with ADO numaralandırmaları, zengin metin numaralandırmaları için "RTF" vb.).</span><span class="sxs-lookup"><span data-stu-id="ee4cf-150">❌ DO NOT use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>

 <span data-ttu-id="ee4cf-151">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="ee4cf-151">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="ee4cf-152">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="ee4cf-152">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ee4cf-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee4cf-153">See also</span></span>

- [<span data-ttu-id="ee4cf-154">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ee4cf-154">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="ee4cf-155">Adlandırma yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ee4cf-155">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
