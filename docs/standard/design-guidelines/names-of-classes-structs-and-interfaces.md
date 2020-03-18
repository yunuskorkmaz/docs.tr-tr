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
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="b94ab-102">Sınıf, Yapı ve Arabirimlerin Adları</span><span class="sxs-lookup"><span data-stu-id="b94ab-102">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="b94ab-103">İzleyen adlandırma yönergeleri genel tür adlandırma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b94ab-103">The naming guidelines that follow apply to general type naming.</span></span>

 <span data-ttu-id="b94ab-104">PascalCasing kullanarak ad sınıfları ve yapılarını isim veya isim tümcecikleriyle ✔️.</span><span class="sxs-lookup"><span data-stu-id="b94ab-104">✔️ DO name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>

 <span data-ttu-id="b94ab-105">Bu, tür adlarını fiil tümcecikleriyle birlikte isimlendirilen yöntemlerden ayırır.</span><span class="sxs-lookup"><span data-stu-id="b94ab-105">This distinguishes type names from methods, which are named with verb phrases.</span></span>

 <span data-ttu-id="b94ab-106">✔️ DO isim arabirimleri sıfat tümcecikleri veya bazen isim veya isim tümcecikleri ile.</span><span class="sxs-lookup"><span data-stu-id="b94ab-106">✔️ DO name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>

 <span data-ttu-id="b94ab-107">Alelade ve isme tümcecikleri nadiren kullanılmalıdır ve bu tür bir arabirim değil soyut bir sınıf olması gerektiğini gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="b94ab-107">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>

 <span data-ttu-id="b94ab-108">❌Sınıf adlarını bir önek vermeyin (örneğin, "C").</span><span class="sxs-lookup"><span data-stu-id="b94ab-108">❌ DO NOT give class names a prefix (e.g., "C").</span></span>

 <span data-ttu-id="b94ab-109">✔️ taban sınıfın adı ile türemiş sınıfların adını sona erdirme düşünün.</span><span class="sxs-lookup"><span data-stu-id="b94ab-109">✔️ CONSIDER ending the name of derived classes with the name of the base class.</span></span>

 <span data-ttu-id="b94ab-110">Bu çok okunabilir ve açıkça ilişki açıklar.</span><span class="sxs-lookup"><span data-stu-id="b94ab-110">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="b94ab-111">Kodda buna örnek olarak `ArgumentOutOfRangeException`şunlar verilebilir: `Exception`, `SerializableAttribute`bir tür , `Attribute`ve , bir tür .</span><span class="sxs-lookup"><span data-stu-id="b94ab-111">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="b94ab-112">Ancak, bu kılavuzun uygulanmasında makul bir yargı kullanmak önemlidir; örneğin, `Button` sınıf bir tür `Control` olaydır, `Control` ancak kendi adında görünmez.</span><span class="sxs-lookup"><span data-stu-id="b94ab-112">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>

 <span data-ttu-id="b94ab-113">✔️, türünün bir arabirim olduğunu belirtmek için I harfi ile önek arabirim adları.</span><span class="sxs-lookup"><span data-stu-id="b94ab-113">✔️ DO prefix interface names with the letter I, to indicate that the type is an interface.</span></span>

 <span data-ttu-id="b94ab-114">Örneğin, `IComponent` (açıklayıcı isim), `ICustomAttributeProvider` (isim tümceciği) `IPersistable` ve (sıfat) uygun arabirim adlarıdır.</span><span class="sxs-lookup"><span data-stu-id="b94ab-114">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="b94ab-115">Diğer tür adlarında olduğu gibi kısaltmalardan kaçının.</span><span class="sxs-lookup"><span data-stu-id="b94ab-115">As with other type names, avoid abbreviations.</span></span>

 <span data-ttu-id="b94ab-116">✔️ DO, sınıfın arabirimin standart bir uygulaması olduğu bir sınıf-arabirim çifti tanımlarken, adların yalnızca arabirim adı üzerindeki "I" önekine göre farklılık gösterir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b94ab-116">✔️ DO ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>

## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="b94ab-117">Genel Tip Parametrelerin Adları</span><span class="sxs-lookup"><span data-stu-id="b94ab-117">Names of Generic Type Parameters</span></span>
 <span data-ttu-id="b94ab-118">Genel ler .NET Framework 2.0'a eklendi.</span><span class="sxs-lookup"><span data-stu-id="b94ab-118">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="b94ab-119">Özellik, *tür parametresi*adı verilen yeni bir tanımlayıcı türünü tanıttı.</span><span class="sxs-lookup"><span data-stu-id="b94ab-119">The feature introduced a new kind of identifier called *type parameter*.</span></span>

 <span data-ttu-id="b94ab-120">✔️ DO, tek harfli bir ad tamamen açıklayıcı olmadığı ve açıklayıcı bir ad değer katmadığı sürece genel tür parametrelerini açıklayıcı adlarla adlandırın.</span><span class="sxs-lookup"><span data-stu-id="b94ab-120">✔️ DO name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>

 <span data-ttu-id="b94ab-121">✔️ Tek `T` harfli tür parametresi olan türler için tür parametre adı olarak kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="b94ab-121">✔️ CONSIDER using `T` as the type parameter name for types with one single-letter type parameter.</span></span>

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 <span data-ttu-id="b94ab-122">✔️ DO öneki tanımlayıcı türü parametre `T`adları ile .</span><span class="sxs-lookup"><span data-stu-id="b94ab-122">✔️ DO prefix descriptive type parameter names with `T`.</span></span>

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 <span data-ttu-id="b94ab-123">✔️ Parametre adına bir tür parametresine yerleştirilen kısıtlamaları gösteren göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="b94ab-123">✔️ CONSIDER indicating constraints placed on a type parameter in the name of the parameter.</span></span>

 <span data-ttu-id="b94ab-124">Örneğin, sınırlandırılmış `ISession` bir parametre . `TSession`</span><span class="sxs-lookup"><span data-stu-id="b94ab-124">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>

## <a name="names-of-common-types"></a><span data-ttu-id="b94ab-125">Ortak Türlerin Adları</span><span class="sxs-lookup"><span data-stu-id="b94ab-125">Names of Common Types</span></span>
 <span data-ttu-id="b94ab-126">✔️ DO, belirli .NET Framework türlerinden türetilen veya uygularken aşağıdaki tabloda açıklanan yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="b94ab-126">✔️ DO follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>

|<span data-ttu-id="b94ab-127">Taban Türü</span><span class="sxs-lookup"><span data-stu-id="b94ab-127">Base Type</span></span>|<span data-ttu-id="b94ab-128">Tür Yönergesi Tür Yönergesi</span><span class="sxs-lookup"><span data-stu-id="b94ab-128">Derived/Implementing Type Guideline</span></span>|
|---------------|------------------------------------------|
|`System.Attribute`|<span data-ttu-id="b94ab-129">✔️ DO özel öznitelik sınıflarının adlarına "Öznitelik" soneki ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b94ab-129">✔️ DO add the suffix "Attribute" to names of custom attribute classes.</span></span>|
|`System.Delegate`|<span data-ttu-id="b94ab-130">✔️ etkinliklerde kullanılan temsilci adlarına "EventHandler" eki ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b94ab-130">✔️ DO add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="b94ab-131">✔️ OLAY İşleyicisi olarak kullanılanlar dışındaki temsilci adlarına "Geri Arama" ekini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b94ab-131">✔️ DO add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="b94ab-132">❌Bir temsilciye "Temsilci" ekini EKLEMEYIN.</span><span class="sxs-lookup"><span data-stu-id="b94ab-132">❌ DO NOT add the suffix "Delegate" to a delegate.</span></span>|
|`System.EventArgs`|<span data-ttu-id="b94ab-133">✔️ "EventArgs" eki ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b94ab-133">✔️ DO add the suffix "EventArgs."</span></span>|
|`System.Enum`|<span data-ttu-id="b94ab-134">❌BU DERSTEN TÜRETİn; bunun yerine diliniz tarafından desteklenen anahtar kelimeyi kullanın; örneğin, C#'da anahtar `enum` sözcük kullanın.</span><span class="sxs-lookup"><span data-stu-id="b94ab-134">❌ DO NOT derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="b94ab-135">❌"Enum" veya "Bayrak" ekini EKLEMEYIN.</span><span class="sxs-lookup"><span data-stu-id="b94ab-135">❌ DO NOT add the suffix "Enum" or "Flag."</span></span>|
|`System.Exception`|<span data-ttu-id="b94ab-136">✔️ "Özel Durum" eki ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b94ab-136">✔️ DO add the suffix "Exception."</span></span>|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="b94ab-137">✔️ "Sözlük" soneki ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b94ab-137">✔️ DO add the suffix "Dictionary."</span></span> <span data-ttu-id="b94ab-138">Belirli `IDictionary` bir koleksiyon türü olduğunu unutmayın, ancak bu kılavuz aşağıdaki daha genel koleksiyonlar kılavuzundan önce gelir.</span><span class="sxs-lookup"><span data-stu-id="b94ab-138">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="b94ab-139">✔️ DO sonek "Koleksiyon ekleyin."</span><span class="sxs-lookup"><span data-stu-id="b94ab-139">✔️ DO add the suffix "Collection."</span></span>|
|`System.IO.Stream`|<span data-ttu-id="b94ab-140">✔️ DO sonek "Akış ekleyin."</span><span class="sxs-lookup"><span data-stu-id="b94ab-140">✔️ DO add the suffix "Stream."</span></span>|
|`CodeAccessPermission IPermission`|<span data-ttu-id="b94ab-141">✔️ "İzin" eki ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b94ab-141">✔️ DO add the suffix "Permission."</span></span>|

## <a name="naming-enumerations"></a><span data-ttu-id="b94ab-142">Adlandırma Tümumerations</span><span class="sxs-lookup"><span data-stu-id="b94ab-142">Naming Enumerations</span></span>
 <span data-ttu-id="b94ab-143">Genel olarak numaralandırma türlerinin adları (enums olarak da adlandırılır) standart tür adlandırma kurallarına (PascalCasing, vb.) uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="b94ab-143">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="b94ab-144">Ancak, özellikle enumlar için geçerli olan ek yönergeler vardır.</span><span class="sxs-lookup"><span data-stu-id="b94ab-144">However, there are additional guidelines that apply specifically to enums.</span></span>

 <span data-ttu-id="b94ab-145">✔️ d değerleri bit alanları olmadığı sürece numaralandırma için tekil bir tür adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="b94ab-145">✔️ DO use a singular type name for an enumeration unless its values are bit fields.</span></span>

 <span data-ttu-id="b94ab-146">✔️ D'ye, bayraklar enum olarak da adlandırılan bit alanları değerlerini içeren bir numaralandırma için çoğul tür adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="b94ab-146">✔️ DO use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>

 <span data-ttu-id="b94ab-147">❌ENUM türü adlarında "Enum" soneki kullanmaYIN.</span><span class="sxs-lookup"><span data-stu-id="b94ab-147">❌ DO NOT use an "Enum" suffix in enum type names.</span></span>

 <span data-ttu-id="b94ab-148">❌ENUM türü adlarında "Bayrak" veya "Bayraklar" soneki kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="b94ab-148">❌ DO NOT use "Flag" or "Flags" suffixes in enum type names.</span></span>

 <span data-ttu-id="b94ab-149">❌Numaralandırma değer adlarında önek (örneğin, ADO enumları için "reklam", zengin metin enumları için "rtf") bir önek KULLANMAYIN.</span><span class="sxs-lookup"><span data-stu-id="b94ab-149">❌ DO NOT use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>

 <span data-ttu-id="b94ab-150">*2005, 2009 Microsoft Corporation © bölümleri. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="b94ab-150">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="b94ab-151">*Pearson Education, Inc.'in izniyle [Framework Design Guidelines: Conventions, Idioms and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina ve Brad Abrams tarafından 22 Ekim 2008'de Addison-Wesley Professional tarafından Microsoft Windows Geliştirme Serisi'nin bir parçası olarak yayımlandı.*</span><span class="sxs-lookup"><span data-stu-id="b94ab-151">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="b94ab-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b94ab-152">See also</span></span>

- [<span data-ttu-id="b94ab-153">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="b94ab-153">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="b94ab-154">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="b94ab-154">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
