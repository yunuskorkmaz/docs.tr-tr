---
title: "Sınıflar, yapılar ve arabirimleri adları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7c76fccec77454cb4551e427e254fe84d9a60299
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="090a0-102">Sınıflar, yapılar ve arabirimleri adları</span><span class="sxs-lookup"><span data-stu-id="090a0-102">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="090a0-103">Genel bir tür adlandırma için izleyin adlandırma yönergeleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="090a0-103">The naming guidelines that follow apply to general type naming.</span></span>  
  
 <span data-ttu-id="090a0-104">**✓ YAPMAK** sınıflar ve yapılar isimleri veya PascalCasing kullanarak isim deyimlere ile ad.</span><span class="sxs-lookup"><span data-stu-id="090a0-104">**✓ DO** name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>  
  
 <span data-ttu-id="090a0-105">Bu tür adları fiil tümcecikleri adlı yöntemlerden ayırır.</span><span class="sxs-lookup"><span data-stu-id="090a0-105">This distinguishes type names from methods, which are named with verb phrases.</span></span>  
  
 <span data-ttu-id="090a0-106">**✓ YAPMAK** ad arabirimleri sıfat tümcecikleri veya bazen isimleri veya isim deyimleri ile.</span><span class="sxs-lookup"><span data-stu-id="090a0-106">**✓ DO** name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>  
  
 <span data-ttu-id="090a0-107">Nadiren isimleri ve isim tümcecikleri kullanılmalıdır ve türü soyut bir sınıf ve bir arabirim olmalıdır gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="090a0-107">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>  
  
 <span data-ttu-id="090a0-108">**X yok** bir önek (örneğin, "C") sınıfı adlar verin.</span><span class="sxs-lookup"><span data-stu-id="090a0-108">**X DO NOT** give class names a prefix (e.g., "C").</span></span>  
  
 <span data-ttu-id="090a0-109">**✓ DÜŞÜNÜN** adını bitiş türetilmiş adıyla sınıflar temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="090a0-109">**✓ CONSIDER** ending the name of derived classes with the name of the base class.</span></span>  
  
 <span data-ttu-id="090a0-110">Bu çok okunabilir ve ilişkiyi açıkça açıklar.</span><span class="sxs-lookup"><span data-stu-id="090a0-110">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="090a0-111">Bu kod bazı örnekleri şunlardır: `ArgumentOutOfRangeException`, bir tür olduğu, `Exception`, ve `SerializableAttribute`, bir tür olduğu, `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="090a0-111">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="090a0-112">Ancak, bu kılavuz uygulamada makul karar kullanmak önemlidir; Örneğin, `Button` sınıfı, bir tür, `Control` olay, ancak `Control` adını görünmüyor.</span><span class="sxs-lookup"><span data-stu-id="090a0-112">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>  
  
 <span data-ttu-id="090a0-113">**✓ YAPMAK** öneki arabirimi adları harfle türü bir arabirim olduğunu belirtmek için ediyorum.</span><span class="sxs-lookup"><span data-stu-id="090a0-113">**✓ DO** prefix interface names with the letter I, to indicate that the type is an interface.</span></span>  
  
 <span data-ttu-id="090a0-114">Örneğin, `IComponent` (tanımlayıcı bir isim), `ICustomAttributeProvider` (isim tümcecik) ve `IPersistable` (gelen) uygun arabirimi adlardır.</span><span class="sxs-lookup"><span data-stu-id="090a0-114">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="090a0-115">Diğer tür adları olduğu gibi ile kısaltmalar kaçının.</span><span class="sxs-lookup"><span data-stu-id="090a0-115">As with other type names, avoid abbreviations.</span></span>  
  
 <span data-ttu-id="090a0-116">**✓ YAPMAK** göre "t" arabirimi adı öneki burada sınıfıdır arabirimi standart uygulaması bir sınıf – arabirim çifti tanımlarken yalnızca adları farklı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="090a0-116">**✓ DO** ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>  
  
## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="090a0-117">Genel tür parametreleri adları</span><span class="sxs-lookup"><span data-stu-id="090a0-117">Names of Generic Type Parameters</span></span>  
 <span data-ttu-id="090a0-118">Genel türler için .NET Framework 2.0 eklendi.</span><span class="sxs-lookup"><span data-stu-id="090a0-118">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="090a0-119">Tanımlayıcı adlı yeni bir tür özellik sunulmuştur *tür parametresi*.</span><span class="sxs-lookup"><span data-stu-id="090a0-119">The feature introduced a new kind of identifier called *type parameter*.</span></span>  
  
 <span data-ttu-id="090a0-120">**✓ YAPMAK** tamamen kendinden açıklamalıdır tek harfli adıdır ve açıklayıcı bir ad, değer Ekle değil sürece genel tür parametreleri ile açıklayıcı adlar adı.</span><span class="sxs-lookup"><span data-stu-id="090a0-120">**✓ DO** name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>  
  
 <span data-ttu-id="090a0-121">**✓ DÜŞÜNÜN** kullanarak `T` tek tek harfli tür parametresi türleriyle türü parametre adı olarak.</span><span class="sxs-lookup"><span data-stu-id="090a0-121">**✓ CONSIDER** using `T` as the type parameter name for types with one single-letter type parameter.</span></span>  
  
```  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 <span data-ttu-id="090a0-122">**✓ YAPMAK** önek tanımlayıcı türü parametre adları ile `T`.</span><span class="sxs-lookup"><span data-stu-id="090a0-122">**✓ DO** prefix descriptive type parameter names with `T`.</span></span>  
  
```  
public interface ISessionChannel<TSession> where TSession : ISession{  
    TSession Session { get; }  
}  
```  
  
 <span data-ttu-id="090a0-123">**✓ DÜŞÜNÜN** kısıtlamaları belirten yerleştirilen bir tür parametresi parametresi adına üzerinde.</span><span class="sxs-lookup"><span data-stu-id="090a0-123">**✓ CONSIDER** indicating constraints placed on a type parameter in the name of the parameter.</span></span>  
  
 <span data-ttu-id="090a0-124">Örneğin, bir parametre kısıtlı için `ISession` olarak adlandırılabilir `TSession`.</span><span class="sxs-lookup"><span data-stu-id="090a0-124">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>  
  
## <a name="names-of-common-types"></a><span data-ttu-id="090a0-125">Adları genel türleri</span><span class="sxs-lookup"><span data-stu-id="090a0-125">Names of Common Types</span></span>  
 <span data-ttu-id="090a0-126">**✓ YAPMAK** türetilmiş veya belirli .NET Framework türleri uygulama türleri adlandırırken aşağıdaki tabloda açıklanan yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="090a0-126">**✓ DO** follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>  
  
|<span data-ttu-id="090a0-127">Temel tür</span><span class="sxs-lookup"><span data-stu-id="090a0-127">Base Type</span></span>|<span data-ttu-id="090a0-128">Türetilmiş ve uygulama türü Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="090a0-128">Derived/Implementing Type Guideline</span></span>|  
|---------------|------------------------------------------|  
|`System.Attribute`|<span data-ttu-id="090a0-129">**✓ YAPMAK** özel öznitelik sınıfları adlarına "Özniteliği" soneki ekleyin.</span><span class="sxs-lookup"><span data-stu-id="090a0-129">**✓ DO** add the suffix "Attribute" to names of custom attribute classes.</span></span>|  
|`System.Delegate`|<span data-ttu-id="090a0-130">**✓ YAPMAK** olayları kullanılan temsilciler adlarını "EventHandler" soneki ekleyin.</span><span class="sxs-lookup"><span data-stu-id="090a0-130">**✓ DO** add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="090a0-131">**✓ YAPMAK** olay işleyicileri olarak kullanılanların dışındaki "Geri çağırma" adlarına temsilcileri soneki ekleyin.</span><span class="sxs-lookup"><span data-stu-id="090a0-131">**✓ DO** add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="090a0-132">**X yok** temsilciye "Temsilci" soneki ekleyin.</span><span class="sxs-lookup"><span data-stu-id="090a0-132">**X DO NOT** add the suffix "Delegate" to a delegate.</span></span>|  
|`System.EventArgs`|<span data-ttu-id="090a0-133">**✓ YAPMAK** "EventArgs." soneki ekleyin</span><span class="sxs-lookup"><span data-stu-id="090a0-133">**✓ DO** add the suffix "EventArgs."</span></span>|  
|`System.Enum`|<span data-ttu-id="090a0-134">**X yok** bu sınıftan türeyen; bunun yerine, dili tarafından desteklenen anahtar sözcüğü kullanın; örneğin, C# ' ta kullanmak `enum` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="090a0-134">**X DO NOT** derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="090a0-135">**X yok** "Enum" veya "Bayrağı." soneki ekleyin</span><span class="sxs-lookup"><span data-stu-id="090a0-135">**X DO NOT** add the suffix "Enum" or "Flag."</span></span>|  
|`System.Exception`|<span data-ttu-id="090a0-136">**✓ YAPMAK** "Özel durum." soneki ekleyin</span><span class="sxs-lookup"><span data-stu-id="090a0-136">**✓ DO** add the suffix "Exception."</span></span>|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="090a0-137">**✓ YAPMAK** "Sözlük." soneki ekleyin</span><span class="sxs-lookup"><span data-stu-id="090a0-137">**✓ DO** add the suffix "Dictionary."</span></span> <span data-ttu-id="090a0-138">Unutmayın `IDictionary` koleksiyonu belirli bir türde değil, ancak bu kılavuz aşağıdaki daha genel koleksiyonları kural göre önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="090a0-138">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="090a0-139">**✓ YAPMAK** "Koleksiyonu." soneki ekleyin</span><span class="sxs-lookup"><span data-stu-id="090a0-139">**✓ DO** add the suffix "Collection."</span></span>|  
|`System.IO.Stream`|<span data-ttu-id="090a0-140">**✓ YAPMAK** "Akış" soneki ekleyin</span><span class="sxs-lookup"><span data-stu-id="090a0-140">**✓ DO** add the suffix "Stream."</span></span>|  
|`CodeAccessPermission IPermission`|<span data-ttu-id="090a0-141">**✓ YAPMAK** "İzni." soneki ekleyin</span><span class="sxs-lookup"><span data-stu-id="090a0-141">**✓ DO** add the suffix "Permission."</span></span>|  
  
## <a name="naming-enumerations"></a><span data-ttu-id="090a0-142">Numaralandırmalar adlandırma</span><span class="sxs-lookup"><span data-stu-id="090a0-142">Naming Enumerations</span></span>  
 <span data-ttu-id="090a0-143">Numaralandırma türleri (numaralandırmaları olarak da bilinir) adlarını genel standart türü adlandırma kuralları (PascalCasing, vb.) izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="090a0-143">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="090a0-144">Ancak, özellikle numaralandırmaları uygulamak ek yönergeler vardır.</span><span class="sxs-lookup"><span data-stu-id="090a0-144">However, there are additional guidelines that apply specifically to enums.</span></span>  
  
 <span data-ttu-id="090a0-145">**✓ YAPMAK** değerlerinin bit alanları olmadığı sürece bir sabit listesi için tekil tür adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="090a0-145">**✓ DO** use a singular type name for an enumeration unless its values are bit fields.</span></span>  
  
 <span data-ttu-id="090a0-146">**✓ YAPMAK** çoğul türü adı numaralandırması için bit alanları ile bayrakları enum olarak da bilinir değerler olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="090a0-146">**✓ DO** use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>  
  
 <span data-ttu-id="090a0-147">**X yok** "Enum" soneki enum türü adları kullanın.</span><span class="sxs-lookup"><span data-stu-id="090a0-147">**X DO NOT** use an "Enum" suffix in enum type names.</span></span>  
  
 <span data-ttu-id="090a0-148">**X yok** enum "Bayrakları" sonekleri adlarını yazın veya "Bayrak" kullanın.</span><span class="sxs-lookup"><span data-stu-id="090a0-148">**X DO NOT** use "Flag" or "Flags" suffixes in enum type names.</span></span>  
  
 <span data-ttu-id="090a0-149">**X yok** bir önek numaralandırma değeri adları (örneğin, "ad" ADO numaralandırmalar için.), "rtf" zengin metin numaralandırmalar, vb. için kullanın.</span><span class="sxs-lookup"><span data-stu-id="090a0-149">**X DO NOT** use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>  
  
 <span data-ttu-id="090a0-150">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="090a0-150">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="090a0-151">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="090a0-151">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="090a0-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="090a0-152">See Also</span></span>  
 [<span data-ttu-id="090a0-153">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="090a0-153">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="090a0-154">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="090a0-154">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
