---
title: Tür üyelerinin adları
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25fe93b63c518f54ee72300f26dfcb3f3ad21d76
ms.sourcegitcommit: b6baf91310f6867223f0f32d596b451592b917b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/31/2018
ms.locfileid: "33575355"
---
# <a name="names-of-type-members"></a><span data-ttu-id="591c3-102">Tür üyelerinin adları</span><span class="sxs-lookup"><span data-stu-id="591c3-102">Names of Type Members</span></span>
<span data-ttu-id="591c3-103">Üyeleri türlerine yapılan: yöntemler, özellikler, olaylar, Oluşturucular ve alanları.</span><span class="sxs-lookup"><span data-stu-id="591c3-103">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="591c3-104">Aşağıdaki bölümlerde, tür üyeleri adlandırmak için yönergeler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="591c3-104">The following sections describe guidelines for naming type members.</span></span>  
  
## <a name="names-of-methods"></a><span data-ttu-id="591c3-105">Yöntemlerin adları</span><span class="sxs-lookup"><span data-stu-id="591c3-105">Names of Methods</span></span>  
 <span data-ttu-id="591c3-106">Yöntemleri eylemde toplanabilmesini olduğundan, tasarım yönergeleri yöntem adları fiilleri ya da tümcelere fiili olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="591c3-106">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="591c3-107">Bu kılavuz ayrıca aşağıdaki isim veya sıfat tümcecikleri olan özellik ve tür adları, yöntem adlarını ayırt etmek için hizmet verir.</span><span class="sxs-lookup"><span data-stu-id="591c3-107">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>  
  
 <span data-ttu-id="591c3-108">**✓ DO** fiilleri ya da fiili tümcecikleri yöntemleri adlar verin.</span><span class="sxs-lookup"><span data-stu-id="591c3-108">**✓ DO** give methods names that are verbs or verb phrases.</span></span>  
  
```  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a><span data-ttu-id="591c3-109">Özelliklerin adları</span><span class="sxs-lookup"><span data-stu-id="591c3-109">Names of Properties</span></span>  
 <span data-ttu-id="591c3-110">Diğer üyeleri özellikleri isim ifade veya sıfat adları verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="591c3-110">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="591c3-111">Bir özellik verileri ifade eder ve özellik adını yansıtılan çünkü olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="591c3-111">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="591c3-112">PascalCasing her zaman özellik adları için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="591c3-112">PascalCasing is always used for property names.</span></span>  
  
 <span data-ttu-id="591c3-113">**✓ DO** adı bir isim, isim sözcük veya sıfat kullanarak özellikleri.</span><span class="sxs-lookup"><span data-stu-id="591c3-113">**✓ DO** name properties using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="591c3-114">**X DO NOT** aşağıdaki örnekte olduğu gibi "Get" yöntemlerinin adıyla aynı özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="591c3-114">**X DO NOT** have properties that match the name of "Get" methods as in the following example:</span></span>  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 <span data-ttu-id="591c3-115">Bu düzen, genellikle özelliği bir yöntem gerçekten gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="591c3-115">This pattern typically indicates that the property should really be a method.</span></span>  
  
 <span data-ttu-id="591c3-116">**✓ DO** koleksiyon özellikleri ardından "List" veya "Koleksiyonu." tekil bir ifade kullanmak yerine koleksiyondaki öğeleri açıklayan çoğul tümcecik adı</span><span class="sxs-lookup"><span data-stu-id="591c3-116">**✓ DO** name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection."</span></span>  
  
 <span data-ttu-id="591c3-117">**✓ DO** olumlu bir ifade ile Boole özellikleri adlandırın (`CanSeek` yerine `CantSeek`).</span><span class="sxs-lookup"><span data-stu-id="591c3-117">**✓ DO** name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="591c3-118">İsteğe bağlı olarak ayrıca Boole özellikleri öneki "İçin"Olan,"" veya ", ancak yalnızca değer kazandıran burada sahip".</span><span class="sxs-lookup"><span data-stu-id="591c3-118">Optionally, you can also prefix Boolean properties with "Is," "Can," or "Has," but only where it adds value.</span></span>  
  
 <span data-ttu-id="591c3-119">**✓ CONSIDER** özellik türü olarak aynı adı vererek.</span><span class="sxs-lookup"><span data-stu-id="591c3-119">**✓ CONSIDER** giving a property the same name as its type.</span></span>  
  
 <span data-ttu-id="591c3-120">Örneğin, aşağıdaki özelliği doğru alır ve bir enum değeri ayarlar `Color`, özellik adlı `Color`:</span><span class="sxs-lookup"><span data-stu-id="591c3-120">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>  
  
```  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a><span data-ttu-id="591c3-121">Olayların adları</span><span class="sxs-lookup"><span data-stu-id="591c3-121">Names of Events</span></span>  
 <span data-ttu-id="591c3-122">Olayları için gerçekleşmesini olan bir ya da gerçekleşen bir bazı eylemler her zaman bakın.</span><span class="sxs-lookup"><span data-stu-id="591c3-122">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="591c3-123">Bu nedenle, yöntemleriyle yönteminde olduğu gibi olayları fiiller ile adlandırılır ve fiili şimdiki zaman olayı zaman belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="591c3-123">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>  
  
 <span data-ttu-id="591c3-124">**✓ DO** fiil veya fiili tümcecik olaylarlaA adı.</span><span class="sxs-lookup"><span data-stu-id="591c3-124">**✓ DO** name events with a verb or a verb phrase.</span></span>  
  
 <span data-ttu-id="591c3-125">Örnekler `Clicked`, `Painting`, `DroppedDown`ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="591c3-125">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>  
  
 <span data-ttu-id="591c3-126">**✓ DO** mevcut ve geçmiş zamanlarını kullanarak önce ve sonra bir kavramı ile olayları adlar verin.</span><span class="sxs-lookup"><span data-stu-id="591c3-126">**✓ DO** give events names with a concept of before and after, using the present and past tenses.</span></span>  
  
 <span data-ttu-id="591c3-127">Örneğin, bir pencere kapatılmadan hemen önce bir kapatma olayı adlı `Closing`, ve penceresi kapatıldıktan sonra başlatan bir çağrılabilir `Closed`.</span><span class="sxs-lookup"><span data-stu-id="591c3-127">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>  
  
 <span data-ttu-id="591c3-128">**X DO NOT** "Önce" veya "Sonra" ön ekleri veya öncesi belirtmek için postfixes ve sonrası olayları kullanın.</span><span class="sxs-lookup"><span data-stu-id="591c3-128">**X DO NOT** use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="591c3-129">Kullanımı mevcut ve geçmiş zamanlarını yalnızca tanımlandığı gibi.</span><span class="sxs-lookup"><span data-stu-id="591c3-129">Use present and past tenses as just described.</span></span>  
  
 <span data-ttu-id="591c3-130">**✓ DO** aşağıdaki örnekte gösterildiği gibi "EventHandler" soneki ile ad olay işleyicileri (temsilcileri olay türleri kullanılan):</span><span class="sxs-lookup"><span data-stu-id="591c3-130">**✓ DO** name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 <span data-ttu-id="591c3-131">**✓ DO** adlı iki parametre kullanmak `sender` ve `e` olay işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="591c3-131">**✓ DO** use two parameters named `sender` and `e` in event handlers.</span></span>  
  
 <span data-ttu-id="591c3-132">Gönderen parametresi olayı tetikleyen nesne temsil eder.</span><span class="sxs-lookup"><span data-stu-id="591c3-132">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="591c3-133">Gönderen parametresi genellikle türüdür `object`bile daha belirli bir tür kullanmak istemiyorsunuz mümkündür.</span><span class="sxs-lookup"><span data-stu-id="591c3-133">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>  
  
 <span data-ttu-id="591c3-134">**✓ DO** "EventArgs" sonek bağımsız değişkeni sınıflarıyla olay adı.</span><span class="sxs-lookup"><span data-stu-id="591c3-134">**✓ DO** name event argument classes with the "EventArgs" suffix.</span></span>  
  
## <a name="names-of-fields"></a><span data-ttu-id="591c3-135">Alanların adlarını</span><span class="sxs-lookup"><span data-stu-id="591c3-135">Names of Fields</span></span>  
 <span data-ttu-id="591c3-136">Statik genel ve korumalı alanlar için alan adlandırma yönergeleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="591c3-136">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="591c3-137">İç ve özel alanları yönergeleri tarafından kapsanmayan ve ortak veya korumalı örnek alanları tarafından izin verilmez [üye tasarımı yönergeleri](../../../docs/standard/design-guidelines/member.md).</span><span class="sxs-lookup"><span data-stu-id="591c3-137">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](../../../docs/standard/design-guidelines/member.md).</span></span>  
  
 <span data-ttu-id="591c3-138">**✓ DO** PascalCasing alan adları kullanın.</span><span class="sxs-lookup"><span data-stu-id="591c3-138">**✓ DO** use PascalCasing in field names.</span></span>  
  
 <span data-ttu-id="591c3-139">**✓ DO** ad alanları bir isim, isim tümceciği veya sıfat kullanarak.</span><span class="sxs-lookup"><span data-stu-id="591c3-139">**✓ DO** name fields using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="591c3-140">**X DO NOT** alan adları için önek kullanın.</span><span class="sxs-lookup"><span data-stu-id="591c3-140">**X DO NOT** use a prefix for field names.</span></span>  
  
 <span data-ttu-id="591c3-141">Örneğin, "g_" veya "kendisinin" statik alanları göstermek için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="591c3-141">For example, do not use "g_" or "s_" to indicate static fields.</span></span>  
  
 <span data-ttu-id="591c3-142">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="591c3-142">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="591c3-143">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="591c3-143">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="591c3-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="591c3-144">See Also</span></span>  
 [<span data-ttu-id="591c3-145">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="591c3-145">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="591c3-146">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="591c3-146">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
