---
title: Büyük/küçük harf kuralları
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ef7913a2601c3a791cb028b4074ce37b9e9421b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575290"
---
# <a name="capitalization-conventions"></a><span data-ttu-id="59ffe-102">Büyük/küçük harf kuralları</span><span class="sxs-lookup"><span data-stu-id="59ffe-102">Capitalization Conventions</span></span>
<span data-ttu-id="59ffe-103">Bu bölüm yerleşim kullanmak için basit bir yöntem çıkışı yönergeleri, sürekli türleri, üyeleri ve parametreleri okumak kolay yapma tanımlayıcıları uygulandığında durumda.</span><span class="sxs-lookup"><span data-stu-id="59ffe-103">The guidelines in this chapter lay out a simple method for using case that, when applied consistently, make identifiers for types, members, and parameters easy to read.</span></span>  
  
## <a name="capitalization-rules-for-identifiers"></a><span data-ttu-id="59ffe-104">Tanımlayıcılar için büyük/küçük harf kuralları</span><span class="sxs-lookup"><span data-stu-id="59ffe-104">Capitalization Rules for Identifiers</span></span>  
 <span data-ttu-id="59ffe-105">Tanımlayıcı sözcükleri ayırt etmek için tanımlayıcı her sözcüğün ilk harfini büyük harf.</span><span class="sxs-lookup"><span data-stu-id="59ffe-105">To differentiate words in an identifier, capitalize the first letter of each word in the identifier.</span></span> <span data-ttu-id="59ffe-106">Alt çizgi sözcükleri ayırt etmek için kullanmayın veya tanımlayıcıları başka bir yerindeki Bu konular için.</span><span class="sxs-lookup"><span data-stu-id="59ffe-106">Do not use underscores to differentiate words, or for that matter, anywhere in identifiers.</span></span> <span data-ttu-id="59ffe-107">Tanımlayıcı kullanılmasına bağlı olarak tanımlayıcıları sağladığınızdan uygun iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="59ffe-107">There are two appropriate ways to capitalize identifiers, depending on the use of the identifier:</span></span>  
  
-   <span data-ttu-id="59ffe-108">PascalCasing</span><span class="sxs-lookup"><span data-stu-id="59ffe-108">PascalCasing</span></span>  
  
-   <span data-ttu-id="59ffe-109">camelCasing</span><span class="sxs-lookup"><span data-stu-id="59ffe-109">camelCasing</span></span>  
  
 <span data-ttu-id="59ffe-110">Parametre adları dışındaki tüm tanımlayıcılar için kullanılan PascalCasing kuralı (iki harf uzunluğu üzerinden kısaltmalar dahil) her sözcüğün ilk karakteri aşağıdaki örneklerde gösterildiği gibi büyük harfe çevirir:</span><span class="sxs-lookup"><span data-stu-id="59ffe-110">The PascalCasing convention, used for all identifiers except parameter names, capitalizes the first character of each word (including acronyms over two letters in length), as shown in the following examples:</span></span>  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 <span data-ttu-id="59ffe-111">Özel bir durum içinde her iki harf olduğundan, iki harfli kısaltmalar için aşağıdaki tanımlayıcıda gösterildiği gibi yapılır:</span><span class="sxs-lookup"><span data-stu-id="59ffe-111">A special case is made for two-letter acronyms in which both letters are capitalized, as shown in the following identifier:</span></span>  
  
 `IOStream`  
  
 <span data-ttu-id="59ffe-112">Parametre adları için yalnızca kullanılan camelCasing kuralı ilk word dışında her sözcüğün ilk karakteri aşağıdaki örneklerde gösterildiği gibi büyük harfe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="59ffe-112">The camelCasing convention, used only for parameter names, capitalizes the first character of each word except the first word, as shown in the following examples.</span></span> <span data-ttu-id="59ffe-113">Örnekte de görüldüğü gibi bir başlamalıdır tanımlayıcı başlamak iki harfli kısaltmalar küçük hem de ' dir.</span><span class="sxs-lookup"><span data-stu-id="59ffe-113">As the example also shows, two-letter acronyms that begin a camel-cased identifier are both lowercase.</span></span>  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 <span data-ttu-id="59ffe-114">**✓ DO** PascalCasing birden çok sözcüklük oluşan tüm ortak üye, türü ve ad alanı adları için kullanın.</span><span class="sxs-lookup"><span data-stu-id="59ffe-114">**✓ DO** use PascalCasing for all public member, type, and namespace names consisting of multiple words.</span></span>  
  
 <span data-ttu-id="59ffe-115">**✓ DO** camelCasing parametre adları için kullanın.</span><span class="sxs-lookup"><span data-stu-id="59ffe-115">**✓ DO** use camelCasing for parameter names.</span></span>  
  
 <span data-ttu-id="59ffe-116">Aşağıdaki tabloda, farklı türlerdeki tanımlayıcıları için büyük/küçük harf kurallar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="59ffe-116">The following table describes the capitalization rules for different types of identifiers.</span></span>  
  
|<span data-ttu-id="59ffe-117">Tanımlayıcı</span><span class="sxs-lookup"><span data-stu-id="59ffe-117">Identifier</span></span>|<span data-ttu-id="59ffe-118">Büyük/küçük harf kullanımı</span><span class="sxs-lookup"><span data-stu-id="59ffe-118">Casing</span></span>|<span data-ttu-id="59ffe-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="59ffe-119">Example</span></span>|  
|----------------|------------|-------------|  
|<span data-ttu-id="59ffe-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="59ffe-120">Namespace</span></span>|<span data-ttu-id="59ffe-121">Pascal</span><span class="sxs-lookup"><span data-stu-id="59ffe-121">Pascal</span></span>|`namespace System.Security { ... }`|  
|<span data-ttu-id="59ffe-122">Tür</span><span class="sxs-lookup"><span data-stu-id="59ffe-122">Type</span></span>|<span data-ttu-id="59ffe-123">Pascal</span><span class="sxs-lookup"><span data-stu-id="59ffe-123">Pascal</span></span>|`public class StreamReader { ... }`|  
|<span data-ttu-id="59ffe-124">Arabirim</span><span class="sxs-lookup"><span data-stu-id="59ffe-124">Interface</span></span>|<span data-ttu-id="59ffe-125">Pascal</span><span class="sxs-lookup"><span data-stu-id="59ffe-125">Pascal</span></span>|`public interface IEnumerable { ... }`|  
|<span data-ttu-id="59ffe-126">Yöntem</span><span class="sxs-lookup"><span data-stu-id="59ffe-126">Method</span></span>|<span data-ttu-id="59ffe-127">Pascal</span><span class="sxs-lookup"><span data-stu-id="59ffe-127">Pascal</span></span>|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|<span data-ttu-id="59ffe-128">Özellik</span><span class="sxs-lookup"><span data-stu-id="59ffe-128">Property</span></span>|<span data-ttu-id="59ffe-129">Pascal</span><span class="sxs-lookup"><span data-stu-id="59ffe-129">Pascal</span></span>|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|<span data-ttu-id="59ffe-130">Olay</span><span class="sxs-lookup"><span data-stu-id="59ffe-130">Event</span></span>|<span data-ttu-id="59ffe-131">Pascal</span><span class="sxs-lookup"><span data-stu-id="59ffe-131">Pascal</span></span>|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|<span data-ttu-id="59ffe-132">Alan</span><span class="sxs-lookup"><span data-stu-id="59ffe-132">Field</span></span>|<span data-ttu-id="59ffe-133">Pascal</span><span class="sxs-lookup"><span data-stu-id="59ffe-133">Pascal</span></span>|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|<span data-ttu-id="59ffe-134">Enum değeri</span><span class="sxs-lookup"><span data-stu-id="59ffe-134">Enum value</span></span>|<span data-ttu-id="59ffe-135">Pascal</span><span class="sxs-lookup"><span data-stu-id="59ffe-135">Pascal</span></span>|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|<span data-ttu-id="59ffe-136">Parametre</span><span class="sxs-lookup"><span data-stu-id="59ffe-136">Parameter</span></span>|<span data-ttu-id="59ffe-137">Ortası büyük</span><span class="sxs-lookup"><span data-stu-id="59ffe-137">Camel</span></span>|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a><span data-ttu-id="59ffe-138">Bileşik sözcüklerin ve Ortak terimleri büyük harfe dönüştürme</span><span class="sxs-lookup"><span data-stu-id="59ffe-138">Capitalizing Compound Words and Common Terms</span></span>  
 <span data-ttu-id="59ffe-139">Çoğu bileşik koşulları büyük/küçük harf amaçları için tek sözcük olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="59ffe-139">Most compound terms are treated as single words for purposes of capitalization.</span></span>  
  
 <span data-ttu-id="59ffe-140">**X DO NOT** sözde kapalı form bileşik sözcüklerin her sözcüğün büyük harfe çevirme.</span><span class="sxs-lookup"><span data-stu-id="59ffe-140">**X DO NOT** capitalize each word in so-called closed-form compound words.</span></span>  
  
 <span data-ttu-id="59ffe-141">Bu uç nokta gibi tek bir sözcük olarak yazılmış bileşik sözcüklerdir.</span><span class="sxs-lookup"><span data-stu-id="59ffe-141">These are compound words written as a single word, such as endpoint.</span></span> <span data-ttu-id="59ffe-142">Büyük/küçük harf yönergeleri amacıyla kapalı form bileşik word tek bir sözcük kabul eder.</span><span class="sxs-lookup"><span data-stu-id="59ffe-142">For the purpose of casing guidelines, treat a closed-form compound word as a single word.</span></span> <span data-ttu-id="59ffe-143">Geçerli bir sözlük, bileşik bir sözcük kapalı formunda yazılırsa belirlemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="59ffe-143">Use a current dictionary to determine if a compound word is written in closed form.</span></span>  
  
|<span data-ttu-id="59ffe-144">Pascal</span><span class="sxs-lookup"><span data-stu-id="59ffe-144">Pascal</span></span>|<span data-ttu-id="59ffe-145">Ortası büyük</span><span class="sxs-lookup"><span data-stu-id="59ffe-145">Camel</span></span>|<span data-ttu-id="59ffe-146">değil</span><span class="sxs-lookup"><span data-stu-id="59ffe-146">Not</span></span>|  
|------------|-----------|---------|  
|`BitFlag`|`bitFlag`|`Bitflag`|  
|`Callback`|`callback`|`CallBack`|  
|`Canceled`|`canceled`|`Cancelled`|  
|`DoNot`|`doNot`|`Don't`|  
|`Email`|`email`|`EMail`|  
|`Endpoint`|`endpoint`|`EndPoint`|  
|`FileName`|`fileName`|`Filename`|  
|`Gridline`|`gridline`|`GridLine`|  
|`Hashtable`|`hashtable`|`HashTable`|  
|`Id`|`id`|`ID`|  
|`Indexes`|`indexes`|`Indices`|  
|`LogOff`|`logOff`|`LogOut`|  
|`LogOn`|`logOn`|`LogIn`|  
|`Metadata`|`metadata`|`MetaData, metaData`|  
|`Multipanel`|`multipanel`|`MultiPanel`|  
|`Multiview`|`multiview`|`MultiView`|  
|`Namespace`|`namespace`|`NameSpace`|  
|`Ok`|`ok`|`OK`|  
|`Pi`|`pi`|`PI`|  
|`Placeholder`|`placeholder`|`PlaceHolder`|  
|`SignIn`|`signIn`|`SignOn`|  
|`SignOut`|`signOut`|`SignOff`|  
|`UserName`|`userName`|`Username`|  
|`WhiteSpace`|`whiteSpace`|`Whitespace`|  
|`Writable`|`writable`|`Writeable`|  
  
## <a name="case-sensitivity"></a><span data-ttu-id="59ffe-147">Büyük/küçük harfe duyarlılık</span><span class="sxs-lookup"><span data-stu-id="59ffe-147">Case Sensitivity</span></span>  
 <span data-ttu-id="59ffe-148">Bazı yapmak rağmen üzerinde CLR çalıştırabilirsiniz dilleri büyük küçük harf duyarlılığı, desteklemek için gereken değil.</span><span class="sxs-lookup"><span data-stu-id="59ffe-148">Languages that can run on the CLR are not required to support case-sensitivity, although some do.</span></span> <span data-ttu-id="59ffe-149">Dilinizi desteklediği olsa bile, framework erişebilir diğer diller yoktur.</span><span class="sxs-lookup"><span data-stu-id="59ffe-149">Even if your language supports it, other languages that might access your framework do not.</span></span> <span data-ttu-id="59ffe-150">Harici olarak erişilebilir olan tüm API'ları bu nedenle, tek başına aynı bağlamda iki ad arasında ayrım yapmak için durumu güvenir olamaz.</span><span class="sxs-lookup"><span data-stu-id="59ffe-150">Any APIs that are externally accessible, therefore, cannot rely on case alone to distinguish between two names in the same context.</span></span>  
  
 <span data-ttu-id="59ffe-151">**X DO NOT** tüm programlama dilleriyle büyük küçük harfe duyarlı olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="59ffe-151">**X DO NOT** assume that all programming languages are case sensitive.</span></span> <span data-ttu-id="59ffe-152">Bunlar değildir.</span><span class="sxs-lookup"><span data-stu-id="59ffe-152">They are not.</span></span> <span data-ttu-id="59ffe-153">Adları örneği tarafından tek başına farklı olamaz.</span><span class="sxs-lookup"><span data-stu-id="59ffe-153">Names cannot differ by case alone.</span></span>  
  
 <span data-ttu-id="59ffe-154">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="59ffe-154">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="59ffe-155">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="59ffe-155">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59ffe-156">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="59ffe-156">See Also</span></span>  
 [<span data-ttu-id="59ffe-157">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="59ffe-157">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="59ffe-158">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="59ffe-158">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
