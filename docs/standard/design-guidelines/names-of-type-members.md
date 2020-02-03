---
title: Tür Üyelerinin Adları
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
ms.openlocfilehash: 81c837bd045992043208a59f6ee16803c1d6eb3c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744186"
---
# <a name="names-of-type-members"></a><span data-ttu-id="bafe7-102">Tür Üyelerinin Adları</span><span class="sxs-lookup"><span data-stu-id="bafe7-102">Names of Type Members</span></span>
<span data-ttu-id="bafe7-103">Üyeleri türlerine yapılan: yöntemler, özellikler, olaylar, Oluşturucular ve alanları.</span><span class="sxs-lookup"><span data-stu-id="bafe7-103">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="bafe7-104">Aşağıdaki bölümlerde, tür üyeleri adlandırmak için yönergeler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bafe7-104">The following sections describe guidelines for naming type members.</span></span>

## <a name="names-of-methods"></a><span data-ttu-id="bafe7-105">Yöntemlerin adları</span><span class="sxs-lookup"><span data-stu-id="bafe7-105">Names of Methods</span></span>
 <span data-ttu-id="bafe7-106">Yöntemleri eylemde toplanabilmesini olduğundan, tasarım yönergeleri yöntem adları fiilleri ya da tümcelere fiili olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bafe7-106">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="bafe7-107">Bu kılavuz ayrıca aşağıdaki isim veya sıfat tümcecikleri olan özellik ve tür adları, yöntem adlarını ayırt etmek için hizmet verir.</span><span class="sxs-lookup"><span data-stu-id="bafe7-107">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>

 <span data-ttu-id="bafe7-108">✔️ fiiller veya fiil tümceleri olan yöntem adlarını verir.</span><span class="sxs-lookup"><span data-stu-id="bafe7-108">✔️ DO give methods names that are verbs or verb phrases.</span></span>

```csharp
public class String {
    public int CompareTo(...);
    public string[] Split(...);
    public string Trim();
}
```

## <a name="names-of-properties"></a><span data-ttu-id="bafe7-109">Özelliklerin adları</span><span class="sxs-lookup"><span data-stu-id="bafe7-109">Names of Properties</span></span>
 <span data-ttu-id="bafe7-110">Diğer üyeleri özellikleri isim ifade veya sıfat adları verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="bafe7-110">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="bafe7-111">Bir özellik verileri ifade eder ve özellik adını yansıtılan çünkü olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="bafe7-111">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="bafe7-112">PascalCasing her zaman özellik adları için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bafe7-112">PascalCasing is always used for property names.</span></span>

 <span data-ttu-id="bafe7-113">✔️ adı, isim tümceciğini veya sıfatıcı kullanarak ad özellikleri YAPıN.</span><span class="sxs-lookup"><span data-stu-id="bafe7-113">✔️ DO name properties using a noun, noun phrase, or adjective.</span></span>

 <span data-ttu-id="bafe7-114">❌, aşağıdaki örnekte olduğu gibi "Get" yöntemlerinin adıyla eşleşen özelliklere sahip DEĞILDIR:</span><span class="sxs-lookup"><span data-stu-id="bafe7-114">❌ DO NOT have properties that match the name of "Get" methods as in the following example:</span></span>

 <span data-ttu-id="bafe7-115">`public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`</span><span class="sxs-lookup"><span data-stu-id="bafe7-115">`public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`</span></span>

 <span data-ttu-id="bafe7-116">Bu düzen, genellikle özelliği bir yöntem gerçekten gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bafe7-116">This pattern typically indicates that the property should really be a method.</span></span>

 <span data-ttu-id="bafe7-117">✔️ koleksiyon özelliklerini, tekil bir tümceciği, ardından "List" veya "Collection" yerine, koleksiyondaki öğeleri açıklayan bir plural ifadesi ile YAPıN.</span><span class="sxs-lookup"><span data-stu-id="bafe7-117">✔️ DO name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection".</span></span>

 <span data-ttu-id="bafe7-118">✔️ Boolean özelliklerini, bir belirleyici ifade (`CantSeek`yerine`CanSeek`) ile adlandırın.</span><span class="sxs-lookup"><span data-stu-id="bafe7-118">✔️ DO name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="bafe7-119">İsteğe bağlı olarak, Boolean özelliklerinin önüne "dir", "can" veya "sahip" de önek olarak önek ekleyebilirsiniz, ancak yalnızca değer ekler.</span><span class="sxs-lookup"><span data-stu-id="bafe7-119">Optionally, you can also prefix Boolean properties with "Is", "Can", or "Has", but only where it adds value.</span></span>

 <span data-ttu-id="bafe7-120">✔️ bir özelliği türüyle aynı ada vermeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="bafe7-120">✔️ CONSIDER giving a property the same name as its type.</span></span>

 <span data-ttu-id="bafe7-121">Örneğin, aşağıdaki özellik, `Color`adlı bir sabit listesi değerini doğru bir şekilde alır ve ayarlar. bu nedenle, özelliğin adı `Color`olur:</span><span class="sxs-lookup"><span data-stu-id="bafe7-121">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>

```csharp
public enum Color {...}
public class Control {
    public Color Color { get {...} set {...} }
}
```

## <a name="names-of-events"></a><span data-ttu-id="bafe7-122">Olayların adları</span><span class="sxs-lookup"><span data-stu-id="bafe7-122">Names of Events</span></span>
 <span data-ttu-id="bafe7-123">Olayları için gerçekleşmesini olan bir ya da gerçekleşen bir bazı eylemler her zaman bakın.</span><span class="sxs-lookup"><span data-stu-id="bafe7-123">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="bafe7-124">Bu nedenle, yöntemleriyle yönteminde olduğu gibi olayları fiiller ile adlandırılır ve fiili şimdiki zaman olayı zaman belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bafe7-124">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>

 <span data-ttu-id="bafe7-125">bir fiil veya fiil ifadesi ile ad olayları ✔️.</span><span class="sxs-lookup"><span data-stu-id="bafe7-125">✔️ DO name events with a verb or a verb phrase.</span></span>

 <span data-ttu-id="bafe7-126">Örnekler şunlardır `Clicked`, `Painting`, `DroppedDown`ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="bafe7-126">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>

 <span data-ttu-id="bafe7-127">✔️, var olan ve son kullanılan kullanımı kullanarak olay adlarını önceden ve sonra bir kavram olarak verir.</span><span class="sxs-lookup"><span data-stu-id="bafe7-127">✔️ DO give events names with a concept of before and after, using the present and past tenses.</span></span>

 <span data-ttu-id="bafe7-128">Örneğin, bir pencere kapatılmadan önce oluşturulan bir Close olayı `Closing`çağrılır ve pencere kapatıldıktan sonra oluşturulan bir kapatma olayı `Closed`çağırılır.</span><span class="sxs-lookup"><span data-stu-id="bafe7-128">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>

 <span data-ttu-id="bafe7-129">❌ ön ve son olayları belirtmek için "önce" veya "After" öneklerini veya postdüzeltmelerinizi kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="bafe7-129">❌ DO NOT use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="bafe7-130">Kullanımı mevcut ve geçmiş zamanlarını yalnızca tanımlandığı gibi.</span><span class="sxs-lookup"><span data-stu-id="bafe7-130">Use present and past tenses as just described.</span></span>

 <span data-ttu-id="bafe7-131">Aşağıdaki örnekte gösterildiği gibi, ad olay işleyicilerini (olay türleri olarak kullanılan temsilciler) "EventHandler" sonekiyle birlikte ✔️:</span><span class="sxs-lookup"><span data-stu-id="bafe7-131">✔️ DO name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>

 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`

 <span data-ttu-id="bafe7-132">✔️, olay işleyicilerinde `sender` ve `e` adında iki parametre kullanır.</span><span class="sxs-lookup"><span data-stu-id="bafe7-132">✔️ DO use two parameters named `sender` and `e` in event handlers.</span></span>

 <span data-ttu-id="bafe7-133">Gönderen parametresi olayı tetikleyen nesne temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bafe7-133">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="bafe7-134">Gönderen parametresi, daha belirli bir tür kullanmak mümkün olsa bile, genellikle `object`türüdür.</span><span class="sxs-lookup"><span data-stu-id="bafe7-134">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>

 <span data-ttu-id="bafe7-135">✔️ olay bağımsız değişkeni sınıflarını "EventArgs" sonekiyle birlikte adlandırın.</span><span class="sxs-lookup"><span data-stu-id="bafe7-135">✔️ DO name event argument classes with the "EventArgs" suffix.</span></span>

## <a name="names-of-fields"></a><span data-ttu-id="bafe7-136">Alanların adlarını</span><span class="sxs-lookup"><span data-stu-id="bafe7-136">Names of Fields</span></span>
 <span data-ttu-id="bafe7-137">Statik genel ve korumalı alanlar için alan adlandırma yönergeleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="bafe7-137">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="bafe7-138">İç ve özel alanlar yönergeler kapsamında değildir ve ortak veya korumalı örnek alanlarına [üye tasarım yönergeleri](../../../docs/standard/design-guidelines/member.md)tarafından izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="bafe7-138">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](../../../docs/standard/design-guidelines/member.md).</span></span>

 <span data-ttu-id="bafe7-139">✔️, alan adlarında Pascalbüyük harfleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="bafe7-139">✔️ DO use PascalCasing in field names.</span></span>

 <span data-ttu-id="bafe7-140">ad alanlarını bir isim, isim tümceciği veya sıfatıcı kullanarak ✔️.</span><span class="sxs-lookup"><span data-stu-id="bafe7-140">✔️ DO name fields using a noun, noun phrase, or adjective.</span></span>

 <span data-ttu-id="bafe7-141">❌ alan adları için bir önek kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="bafe7-141">❌ DO NOT use a prefix for field names.</span></span>

 <span data-ttu-id="bafe7-142">Örneğin, "g_" veya "kendisinin" statik alanları göstermek için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="bafe7-142">For example, do not use "g_" or "s_" to indicate static fields.</span></span>

 <span data-ttu-id="bafe7-143">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="bafe7-143">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="bafe7-144">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="bafe7-144">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="bafe7-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bafe7-145">See also</span></span>

- [<span data-ttu-id="bafe7-146">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="bafe7-146">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="bafe7-147">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="bafe7-147">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
