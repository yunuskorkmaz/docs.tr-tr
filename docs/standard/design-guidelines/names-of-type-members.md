---
title: Tür üyeleri adları
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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575355"
---
# <a name="names-of-type-members"></a><span data-ttu-id="0c86d-102">Tür üyeleri adları</span><span class="sxs-lookup"><span data-stu-id="0c86d-102">Names of Type Members</span></span>
<span data-ttu-id="0c86d-103">Türleri üyeleri yapılır: yöntemler, özellikler, olaylar, Oluşturucular ve alanları.</span><span class="sxs-lookup"><span data-stu-id="0c86d-103">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="0c86d-104">Tür üyeleri adlandırma yönergeleri aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0c86d-104">The following sections describe guidelines for naming type members.</span></span>  
  
## <a name="names-of-methods"></a><span data-ttu-id="0c86d-105">Yöntemlerin adlarını</span><span class="sxs-lookup"><span data-stu-id="0c86d-105">Names of Methods</span></span>  
 <span data-ttu-id="0c86d-106">Yöntemleri eylemin gerçekleştirilmesi şekillerini olduğundan tasarım yönergeleri yöntem adları fiiller veya fiil cümleleri olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0c86d-106">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="0c86d-107">Bu kılavuz ayrıca aşağıdaki isim veya gelen tümcecikleri olan özellik türü adları ve, yöntem adlarını ayırt etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0c86d-107">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>  
  
 <span data-ttu-id="0c86d-108">**✓ YAPMAK** fiiller ya da fiil cümleleri yöntemleri adlar verin.</span><span class="sxs-lookup"><span data-stu-id="0c86d-108">**✓ DO** give methods names that are verbs or verb phrases.</span></span>  
  
```  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a><span data-ttu-id="0c86d-109">Özellik adlarını</span><span class="sxs-lookup"><span data-stu-id="0c86d-109">Names of Properties</span></span>  
 <span data-ttu-id="0c86d-110">Diğer üyeleri, isim tümcecik veya sıfat adları özellikleri verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="0c86d-110">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="0c86d-111">Bir özellik verilere başvuruda bulunmaktadır ve özelliğin adını yansıtır çünkü olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="0c86d-111">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="0c86d-112">PascalCasing özellik adları için her zaman kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0c86d-112">PascalCasing is always used for property names.</span></span>  
  
 <span data-ttu-id="0c86d-113">**✓ YAPMAK** isim, isim tümcecik veya gelen kullanarak özelliklerini olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="0c86d-113">**✓ DO** name properties using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="0c86d-114">**X yok** "Get" yöntem aşağıdaki örnekteki gibi adıyla aynı özelliklere sahip:</span><span class="sxs-lookup"><span data-stu-id="0c86d-114">**X DO NOT** have properties that match the name of "Get" methods as in the following example:</span></span>  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 <span data-ttu-id="0c86d-115">Bu deseni genelde özelliği gerçekten bir yöntemi olması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0c86d-115">This pattern typically indicates that the property should really be a method.</span></span>  
  
 <span data-ttu-id="0c86d-116">**✓ YAPMAK** Koleksiyon Özellikleri "List" veya "Koleksiyonu." gelmelidir tekil bir ifade kullanmak yerine koleksiyondaki öğelerin açıklayan bir çoğul deyimi adı</span><span class="sxs-lookup"><span data-stu-id="0c86d-116">**✓ DO** name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection."</span></span>  
  
 <span data-ttu-id="0c86d-117">**✓ YAPMAK** bir İleticiden olumlu bir ifade Boolean özelliklerle adı (`CanSeek` yerine `CantSeek`).</span><span class="sxs-lookup"><span data-stu-id="0c86d-117">**✓ DO** name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="0c86d-118">İsteğe bağlı olarak, aynı zamanda Boole özellikleri önek ", ancak değer ekler burada var" veya "İçin"Durumdayken,"".</span><span class="sxs-lookup"><span data-stu-id="0c86d-118">Optionally, you can also prefix Boolean properties with "Is," "Can," or "Has," but only where it adds value.</span></span>  
  
 <span data-ttu-id="0c86d-119">**✓ DÜŞÜNÜN** bir özellik türü aynı adı verip.</span><span class="sxs-lookup"><span data-stu-id="0c86d-119">**✓ CONSIDER** giving a property the same name as its type.</span></span>  
  
 <span data-ttu-id="0c86d-120">Örneğin, aşağıdaki özelliği doğru alır ve adlı bir enum değeri ayarlar `Color`, özellik adlı `Color`:</span><span class="sxs-lookup"><span data-stu-id="0c86d-120">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>  
  
```  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a><span data-ttu-id="0c86d-121">Olayların adları</span><span class="sxs-lookup"><span data-stu-id="0c86d-121">Names of Events</span></span>  
 <span data-ttu-id="0c86d-122">Olayları için oluşmasını olan bir ya da oluştu bir bazı eylemler her zaman başvurun.</span><span class="sxs-lookup"><span data-stu-id="0c86d-122">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="0c86d-123">Bu nedenle, yöntemleriyle olduğu gibi olayları fiiller ile adlandırılır ve fiil zamanın zaman olayının saat göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0c86d-123">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>  
  
 <span data-ttu-id="0c86d-124">**✓ YAPMAK** bir fiil veya bir fiil deyimi olaylarla olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="0c86d-124">**✓ DO** name events with a verb or a verb phrase.</span></span>  
  
 <span data-ttu-id="0c86d-125">Örnekler `Clicked`, `Painting`, `DroppedDown`ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="0c86d-125">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>  
  
 <span data-ttu-id="0c86d-126">**✓ YAPMAK** mevcut ve geçmiş zamanlarını kullanarak önce ve sonra bir kavramı ile olayları adlar verin.</span><span class="sxs-lookup"><span data-stu-id="0c86d-126">**✓ DO** give events names with a concept of before and after, using the present and past tenses.</span></span>  
  
 <span data-ttu-id="0c86d-127">Örneğin, bir pencere kapatılmadan önce bir kapatma olayı adlı `Closing`, ve bir pencere kapatıldıktan sonra tetiklenir çağrılabilir `Closed`.</span><span class="sxs-lookup"><span data-stu-id="0c86d-127">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>  
  
 <span data-ttu-id="0c86d-128">**X yok** "Önce" veya "Sonra" önekleri veya öncesi belirtmek için postfixes ve sonrası olayları kullanın.</span><span class="sxs-lookup"><span data-stu-id="0c86d-128">**X DO NOT** use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="0c86d-129">Kullanım mevcut ve geçmiş zamanlarını yalnızca tanımlandığı gibi.</span><span class="sxs-lookup"><span data-stu-id="0c86d-129">Use present and past tenses as just described.</span></span>  
  
 <span data-ttu-id="0c86d-130">**✓ YAPMAK** aşağıdaki örnekte gösterildiği gibi "EventHandler" soneki ile ad olay işleyicileri (olay türleri kullanılan temsilcileri):</span><span class="sxs-lookup"><span data-stu-id="0c86d-130">**✓ DO** name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 <span data-ttu-id="0c86d-131">**✓ YAPMAK** adlı iki parametre kullanmak `sender` ve `e` olay işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="0c86d-131">**✓ DO** use two parameters named `sender` and `e` in event handlers.</span></span>  
  
 <span data-ttu-id="0c86d-132">Gönderen parametresi olayı nesneyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0c86d-132">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="0c86d-133">Gönderen parametresi genellikle türünde `object`daha belirli bir tür kullanmayı mümkün olsa bile.</span><span class="sxs-lookup"><span data-stu-id="0c86d-133">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>  
  
 <span data-ttu-id="0c86d-134">**✓ YAPMAK** "EventArgs" sonek bağımsız değişkeni sınıflarıyla olay adı.</span><span class="sxs-lookup"><span data-stu-id="0c86d-134">**✓ DO** name event argument classes with the "EventArgs" suffix.</span></span>  
  
## <a name="names-of-fields"></a><span data-ttu-id="0c86d-135">Alanların adlarını</span><span class="sxs-lookup"><span data-stu-id="0c86d-135">Names of Fields</span></span>  
 <span data-ttu-id="0c86d-136">Statik genel ve korumalı alanlarına alan adlandırma yönergeleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="0c86d-136">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="0c86d-137">İç ve özel alanlar yönergeleri tarafından kapsanmayan ve ortak veya korumalı örneği alanları tarafından izin verilmez [üye tasarım yönergeleri](../../../docs/standard/design-guidelines/member.md).</span><span class="sxs-lookup"><span data-stu-id="0c86d-137">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](../../../docs/standard/design-guidelines/member.md).</span></span>  
  
 <span data-ttu-id="0c86d-138">**✓ YAPMAK** PascalCasing alan adları kullanın.</span><span class="sxs-lookup"><span data-stu-id="0c86d-138">**✓ DO** use PascalCasing in field names.</span></span>  
  
 <span data-ttu-id="0c86d-139">**✓ YAPMAK** ad alanları bir isim, isim tümcecik veya gelen kullanarak.</span><span class="sxs-lookup"><span data-stu-id="0c86d-139">**✓ DO** name fields using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="0c86d-140">**X yok** alan adları için bir önek kullanın.</span><span class="sxs-lookup"><span data-stu-id="0c86d-140">**X DO NOT** use a prefix for field names.</span></span>  
  
 <span data-ttu-id="0c86d-141">Örneğin, "g_" veya "s_" statik alanları belirtmek için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="0c86d-141">For example, do not use "g_" or "s_" to indicate static fields.</span></span>  
  
 <span data-ttu-id="0c86d-142">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="0c86d-142">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="0c86d-143">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="0c86d-143">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c86d-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0c86d-144">See Also</span></span>  
 [<span data-ttu-id="0c86d-145">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="0c86d-145">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="0c86d-146">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="0c86d-146">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
