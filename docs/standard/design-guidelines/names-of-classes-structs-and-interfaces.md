---
title: Sınıf, yapı ve arabirimlerin adları
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
ms.openlocfilehash: 0c56f840bc5ebd5070c9b686384751acab3f0203
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44064796"
---
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="1898d-102">Sınıf, yapı ve arabirimlerin adları</span><span class="sxs-lookup"><span data-stu-id="1898d-102">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="1898d-103">Adlandırma yönergeleri izleyin, genel bir tür adlandırma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="1898d-103">The naming guidelines that follow apply to general type naming.</span></span>  
  
 <span data-ttu-id="1898d-104">**✓ DO** sınıflar ve yapılar isimleri veya PascalCasing kullanarak isim deyimlere ile ad.</span><span class="sxs-lookup"><span data-stu-id="1898d-104">**✓ DO** name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>  
  
 <span data-ttu-id="1898d-105">Fiili tümcecikleri adlandırılır yöntemleri, bu tür adlarını ayırır.</span><span class="sxs-lookup"><span data-stu-id="1898d-105">This distinguishes type names from methods, which are named with verb phrases.</span></span>  
  
 <span data-ttu-id="1898d-106">**✓ DO** ad arabirimleri sıfat tümcecikleri veya bazen isimleri veya isim deyimleri ile.</span><span class="sxs-lookup"><span data-stu-id="1898d-106">**✓ DO** name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>  
  
 <span data-ttu-id="1898d-107">Nadiren isimleri ve isim ifadeleri kullanılmalıdır ve bir Özet sınıf ve bir arabirim türü olması gerektiğini gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="1898d-107">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>  
  
 <span data-ttu-id="1898d-108">**X DO NOT** bir önek (örneğin, "C") sınıfı adlar verin.</span><span class="sxs-lookup"><span data-stu-id="1898d-108">**X DO NOT** give class names a prefix (e.g., "C").</span></span>  
  
 <span data-ttu-id="1898d-109">**✓ CONSIDER** adını bitiş türetilmiş adıyla sınıflar temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="1898d-109">**✓ CONSIDER** ending the name of derived classes with the name of the base class.</span></span>  
  
 <span data-ttu-id="1898d-110">Bu çok okunabilir ve ilişki açıkça açıklar.</span><span class="sxs-lookup"><span data-stu-id="1898d-110">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="1898d-111">Bu kod bazı örnekleri şunlardır: `ArgumentOutOfRangeException`, bir tür olduğundan, `Exception`, ve `SerializableAttribute`, bir tür olduğundan, `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="1898d-111">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="1898d-112">Ancak, bu kılavuzu uygulama içinde makul yükümlülükten kullanmak önemlidir; Örneğin, `Button` sınıfı, bir tür, `Control` olay rağmen `Control` adını görünmez.</span><span class="sxs-lookup"><span data-stu-id="1898d-112">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>  
  
 <span data-ttu-id="1898d-113">**✓ DO** öneki arabirimi adları harfle türü bir arabirim olduğunu belirtmek için ediyorum.</span><span class="sxs-lookup"><span data-stu-id="1898d-113">**✓ DO** prefix interface names with the letter I, to indicate that the type is an interface.</span></span>  
  
 <span data-ttu-id="1898d-114">Örneğin, `IComponent` (tanımlayıcı ad), `ICustomAttributeProvider` (isim deyim) ve `IPersistable` (gelen) uygun arabirimi adlarıdır.</span><span class="sxs-lookup"><span data-stu-id="1898d-114">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="1898d-115">Diğer tür adları ile kısaltmalar önleyebilmemizdir.</span><span class="sxs-lookup"><span data-stu-id="1898d-115">As with other type names, avoid abbreviations.</span></span>  
  
 <span data-ttu-id="1898d-116">**✓ DO** göre "t" arabirimi adı öneki burada sınıfıdır arabirimi standart uygulaması bir sınıf – arabirim çifti tanımlarken yalnızca adları farklı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="1898d-116">**✓ DO** ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>  
  
## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="1898d-117">Genel tür parametrelerinin adları</span><span class="sxs-lookup"><span data-stu-id="1898d-117">Names of Generic Type Parameters</span></span>  
 <span data-ttu-id="1898d-118">Genel türler için .NET Framework 2.0 eklendi.</span><span class="sxs-lookup"><span data-stu-id="1898d-118">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="1898d-119">Yeni bir tür tanımlayıcı adlı bir özelliği kullanıma *tür parametresi*.</span><span class="sxs-lookup"><span data-stu-id="1898d-119">The feature introduced a new kind of identifier called *type parameter*.</span></span>  
  
 <span data-ttu-id="1898d-120">**✓ DO** tamamen kendinden açıklamalıdır tek harfli adıdır ve açıklayıcı bir ad, değer Ekle değil sürece genel tür parametreleri ile açıklayıcı adlar adı.</span><span class="sxs-lookup"><span data-stu-id="1898d-120">**✓ DO** name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>  
  
 <span data-ttu-id="1898d-121">**✓ CONSIDER** kullanarak `T` tek tek harfli tür parametresi türleriyle türü parametre adı olarak.</span><span class="sxs-lookup"><span data-stu-id="1898d-121">**✓ CONSIDER** using `T` as the type parameter name for types with one single-letter type parameter.</span></span>  
  
```  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 <span data-ttu-id="1898d-122">**✓ DO** önek tanımlayıcı türü parametre adları ile `T`.</span><span class="sxs-lookup"><span data-stu-id="1898d-122">**✓ DO** prefix descriptive type parameter names with `T`.</span></span>  
  
```  
public interface ISessionChannel<TSession> where TSession : ISession {  
    TSession Session { get; }  
}  
```  
  
 <span data-ttu-id="1898d-123">**✓ CONSIDER** kısıtlamaları belirten yerleştirilen bir tür parametresi parametresi adına üzerinde.</span><span class="sxs-lookup"><span data-stu-id="1898d-123">**✓ CONSIDER** indicating constraints placed on a type parameter in the name of the parameter.</span></span>  
  
 <span data-ttu-id="1898d-124">Örneğin, bir parametre, için kısıtlı `ISession` olarak adlandırılabilir `TSession`.</span><span class="sxs-lookup"><span data-stu-id="1898d-124">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>  
  
## <a name="names-of-common-types"></a><span data-ttu-id="1898d-125">Ortak Tür adları</span><span class="sxs-lookup"><span data-stu-id="1898d-125">Names of Common Types</span></span>  
 <span data-ttu-id="1898d-126">**✓ DO** türetilmiş veya belirli .NET Framework türleri uygulama türleri adlandırırken aşağıdaki tabloda açıklanan yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="1898d-126">**✓ DO** follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>  
  
|<span data-ttu-id="1898d-127">Temel tür</span><span class="sxs-lookup"><span data-stu-id="1898d-127">Base Type</span></span>|<span data-ttu-id="1898d-128">Türetilmiş ve uygulama türü Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1898d-128">Derived/Implementing Type Guideline</span></span>|  
|---------------|------------------------------------------|  
|`System.Attribute`|<span data-ttu-id="1898d-129">**✓ DO** özel öznitelik sınıfları adlarına "Özniteliği" soneki ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1898d-129">**✓ DO** add the suffix "Attribute" to names of custom attribute classes.</span></span>|  
|`System.Delegate`|<span data-ttu-id="1898d-130">**✓ DO** olayları kullanılan temsilciler adlarını "EventHandler" soneki ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1898d-130">**✓ DO** add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="1898d-131">**✓ DO** olay işleyicileri olarak kullanılanların dışındaki "Geri çağırma" adlarına temsilcileri soneki ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1898d-131">**✓ DO** add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="1898d-132">**X DO NOT** temsilciye "Temsilci" soneki ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1898d-132">**X DO NOT** add the suffix "Delegate" to a delegate.</span></span>|  
|`System.EventArgs`|<span data-ttu-id="1898d-133">**✓ DO** "EventArgs." soneki ekleyin</span><span class="sxs-lookup"><span data-stu-id="1898d-133">**✓ DO** add the suffix "EventArgs."</span></span>|  
|`System.Enum`|<span data-ttu-id="1898d-134">**X DO NOT** bu sınıftan türeyen; bunun yerine, dili tarafından desteklenen anahtar sözcüğü kullanın; örneğin, C# ' ta kullanmak `enum` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="1898d-134">**X DO NOT** derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="1898d-135">**X DO NOT** "Enum" veya "Bayrağı." soneki ekleyin</span><span class="sxs-lookup"><span data-stu-id="1898d-135">**X DO NOT** add the suffix "Enum" or "Flag."</span></span>|  
|`System.Exception`|<span data-ttu-id="1898d-136">**✓ DO** "Özel durum." soneki ekleyin</span><span class="sxs-lookup"><span data-stu-id="1898d-136">**✓ DO** add the suffix "Exception."</span></span>|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="1898d-137">**✓ DO** "Sözlük." soneki ekleyin</span><span class="sxs-lookup"><span data-stu-id="1898d-137">**✓ DO** add the suffix "Dictionary."</span></span> <span data-ttu-id="1898d-138">Unutmayın `IDictionary` belirli bir koleksiyon türüdür, ancak bu kılavuz aşağıdaki daha genel koleksiyonlar yönerge göre önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="1898d-138">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="1898d-139">**✓ DO** "Koleksiyonu." soneki ekleyin</span><span class="sxs-lookup"><span data-stu-id="1898d-139">**✓ DO** add the suffix "Collection."</span></span>|  
|`System.IO.Stream`|<span data-ttu-id="1898d-140">**✓ DO** "Akış" soneki ekleyin</span><span class="sxs-lookup"><span data-stu-id="1898d-140">**✓ DO** add the suffix "Stream."</span></span>|  
|`CodeAccessPermission IPermission`|<span data-ttu-id="1898d-141">**✓ DO** "İzni." soneki ekleyin</span><span class="sxs-lookup"><span data-stu-id="1898d-141">**✓ DO** add the suffix "Permission."</span></span>|  
  
## <a name="naming-enumerations"></a><span data-ttu-id="1898d-142">Adlandırma sabit listeleri</span><span class="sxs-lookup"><span data-stu-id="1898d-142">Naming Enumerations</span></span>  
 <span data-ttu-id="1898d-143">Numaralandırma türleri (numaralandırmalar olarak da bilinir) adlarını genel standart türü adlandırma kuralları (PascalCasing, vb.) izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="1898d-143">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="1898d-144">Ancak, özellikle numaralandırmalar için geçerli olan ek yönergeler de vardır.</span><span class="sxs-lookup"><span data-stu-id="1898d-144">However, there are additional guidelines that apply specifically to enums.</span></span>  
  
 <span data-ttu-id="1898d-145">**✓ DO** değerlerinin bit alanları olmadığı sürece bir sabit listesi için tekil tür adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="1898d-145">**✓ DO** use a singular type name for an enumeration unless its values are bit fields.</span></span>  
  
 <span data-ttu-id="1898d-146">**✓ DO** çoğul türü adı numaralandırması için bit alanları ile bayrakları enum olarak da bilinir değerler olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="1898d-146">**✓ DO** use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>  
  
 <span data-ttu-id="1898d-147">**X DO NOT** "Enum" soneki enum türü adları kullanın.</span><span class="sxs-lookup"><span data-stu-id="1898d-147">**X DO NOT** use an "Enum" suffix in enum type names.</span></span>  
  
 <span data-ttu-id="1898d-148">**X DO NOT** enum "Bayrakları" sonekleri adlarını yazın veya "Bayrak" kullanın.</span><span class="sxs-lookup"><span data-stu-id="1898d-148">**X DO NOT** use "Flag" or "Flags" suffixes in enum type names.</span></span>  
  
 <span data-ttu-id="1898d-149">**X DO NOT** bir önek numaralandırma değeri adları (örneğin, "ad" ADO numaralandırmalar için.), "rtf" zengin metin numaralandırmalar, vb. için kullanın.</span><span class="sxs-lookup"><span data-stu-id="1898d-149">**X DO NOT** use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>  
  
 <span data-ttu-id="1898d-150">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="1898d-150">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="1898d-151">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="1898d-151">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1898d-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1898d-152">See also</span></span>

- [<span data-ttu-id="1898d-153">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="1898d-153">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="1898d-154">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="1898d-154">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
