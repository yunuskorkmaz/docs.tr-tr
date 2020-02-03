---
title: Büyük/Küçük Harf Kuralları
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
ms.openlocfilehash: 8af4a15e1e5b34c38b14c6b547cf44801bbf13e6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741763"
---
# <a name="capitalization-conventions"></a><span data-ttu-id="9ede8-102">Büyük/Küçük Harf Kuralları</span><span class="sxs-lookup"><span data-stu-id="9ede8-102">Capitalization Conventions</span></span>
<span data-ttu-id="9ede8-103">Bu bölümdeki yönergeler, tutarlı bir şekilde uygulandığında, türler, Üyeler ve parametreler için tanımlayıcıların kolay okunmasını sağlamak üzere basit bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ede8-103">The guidelines in this chapter lay out a simple method for using case that, when applied consistently, make identifiers for types, members, and parameters easy to read.</span></span>

## <a name="capitalization-rules-for-identifiers"></a><span data-ttu-id="9ede8-104">Tanımlayıcılar için büyük harfe dönüştürme kuralları</span><span class="sxs-lookup"><span data-stu-id="9ede8-104">Capitalization Rules for Identifiers</span></span>
 <span data-ttu-id="9ede8-105">Bir Tanımlayıcıdaki sözcükleri ayırt etmek için, Tanımlayıcıdaki her sözcüğün ilk harfini büyük harfle yapın.</span><span class="sxs-lookup"><span data-stu-id="9ede8-105">To differentiate words in an identifier, capitalize the first letter of each word in the identifier.</span></span> <span data-ttu-id="9ede8-106">Sözcükleri ayırt etmek için alt çizgi kullanmayın veya bu konuyla ilgili olarak tanımlayıcılardan herhangi bir yerde.</span><span class="sxs-lookup"><span data-stu-id="9ede8-106">Do not use underscores to differentiate words, or for that matter, anywhere in identifiers.</span></span> <span data-ttu-id="9ede8-107">Tanımlayıcının kullanılmasına bağlı olarak, tanımlayıcıları büyük harfle almanın iki uygun yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="9ede8-107">There are two appropriate ways to capitalize identifiers, depending on the use of the identifier:</span></span>

- <span data-ttu-id="9ede8-108">Pascalbüyük harf</span><span class="sxs-lookup"><span data-stu-id="9ede8-108">PascalCasing</span></span>

- <span data-ttu-id="9ede8-109">Camelbüyük harf</span><span class="sxs-lookup"><span data-stu-id="9ede8-109">camelCasing</span></span>

 <span data-ttu-id="9ede8-110">Parametre adları hariç tüm tanımlayıcılar için kullanılan Pascalas kuralı, aşağıdaki örneklerde gösterildiği gibi her sözcüğün ilk karakterini (uzunluğunun iki harfli kısaltmalarla birlikte) büyük harfe dönüştürür:</span><span class="sxs-lookup"><span data-stu-id="9ede8-110">The PascalCasing convention, used for all identifiers except parameter names, capitalizes the first character of each word (including acronyms over two letters in length), as shown in the following examples:</span></span>

 `PropertyDescriptor`
 `HtmlTag`

 <span data-ttu-id="9ede8-111">Aşağıdaki tanımlayıcıda gösterildiği gibi, iki harfli kısaltmalar için her iki harf de büyük harfli olan özel bir durum yapılır:</span><span class="sxs-lookup"><span data-stu-id="9ede8-111">A special case is made for two-letter acronyms in which both letters are capitalized, as shown in the following identifier:</span></span>

 `IOStream`

 <span data-ttu-id="9ede8-112">Yalnızca parametre adları için kullanılan Camelas kuralı, aşağıdaki örneklerde gösterildiği gibi ilk sözcük hariç her sözcüğün ilk karakterini büyük harfe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="9ede8-112">The camelCasing convention, used only for parameter names, capitalizes the first character of each word except the first word, as shown in the following examples.</span></span> <span data-ttu-id="9ede8-113">Örnekte de gösterildiği gibi, Camel bir tanımlayıcıya başlayan iki harfli kısaltmalar her ikisi de küçük harftir.</span><span class="sxs-lookup"><span data-stu-id="9ede8-113">As the example also shows, two-letter acronyms that begin a camel-cased identifier are both lowercase.</span></span>

 `propertyDescriptor`
 `ioStream`
 `htmlTag`

 <span data-ttu-id="9ede8-114">✔️, birden çok sözcükten oluşan tüm ortak üye, tür ve ad alanı adları için Pascalbüyük harfleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="9ede8-114">✔️ DO use PascalCasing for all public member, type, and namespace names consisting of multiple words.</span></span>

 <span data-ttu-id="9ede8-115">✔️ parametre adları için Camelum kullanın.</span><span class="sxs-lookup"><span data-stu-id="9ede8-115">✔️ DO use camelCasing for parameter names.</span></span>

 <span data-ttu-id="9ede8-116">Aşağıdaki tabloda, farklı türlerde tanımlayıcılar için büyük/küçük harf kuralları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9ede8-116">The following table describes the capitalization rules for different types of identifiers.</span></span>

|<span data-ttu-id="9ede8-117">Tanımlayıcı</span><span class="sxs-lookup"><span data-stu-id="9ede8-117">Identifier</span></span>|<span data-ttu-id="9ede8-118">Büyük/küçük harf kullanımı</span><span class="sxs-lookup"><span data-stu-id="9ede8-118">Casing</span></span>|<span data-ttu-id="9ede8-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="9ede8-119">Example</span></span>|
|----------------|------------|-------------|
|<span data-ttu-id="9ede8-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="9ede8-120">Namespace</span></span>|<span data-ttu-id="9ede8-121">Pascal</span><span class="sxs-lookup"><span data-stu-id="9ede8-121">Pascal</span></span>|`namespace System.Security { ... }`|
|<span data-ttu-id="9ede8-122">Tür</span><span class="sxs-lookup"><span data-stu-id="9ede8-122">Type</span></span>|<span data-ttu-id="9ede8-123">Pascal</span><span class="sxs-lookup"><span data-stu-id="9ede8-123">Pascal</span></span>|`public class StreamReader { ... }`|
|<span data-ttu-id="9ede8-124">Arabirim</span><span class="sxs-lookup"><span data-stu-id="9ede8-124">Interface</span></span>|<span data-ttu-id="9ede8-125">Pascal</span><span class="sxs-lookup"><span data-stu-id="9ede8-125">Pascal</span></span>|`public interface IEnumerable { ... }`|
|<span data-ttu-id="9ede8-126">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9ede8-126">Method</span></span>|<span data-ttu-id="9ede8-127">Pascal</span><span class="sxs-lookup"><span data-stu-id="9ede8-127">Pascal</span></span>|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|
|<span data-ttu-id="9ede8-128">Özellik</span><span class="sxs-lookup"><span data-stu-id="9ede8-128">Property</span></span>|<span data-ttu-id="9ede8-129">Pascal</span><span class="sxs-lookup"><span data-stu-id="9ede8-129">Pascal</span></span>|`public class String {` <br />  `public int Length { get; }` <br /> `}`|
|<span data-ttu-id="9ede8-130">Olay</span><span class="sxs-lookup"><span data-stu-id="9ede8-130">Event</span></span>|<span data-ttu-id="9ede8-131">Pascal</span><span class="sxs-lookup"><span data-stu-id="9ede8-131">Pascal</span></span>|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|
|<span data-ttu-id="9ede8-132">Alan</span><span class="sxs-lookup"><span data-stu-id="9ede8-132">Field</span></span>|<span data-ttu-id="9ede8-133">Pascal</span><span class="sxs-lookup"><span data-stu-id="9ede8-133">Pascal</span></span>|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|
|<span data-ttu-id="9ede8-134">Sabit listesi değeri</span><span class="sxs-lookup"><span data-stu-id="9ede8-134">Enum value</span></span>|<span data-ttu-id="9ede8-135">Pascal</span><span class="sxs-lookup"><span data-stu-id="9ede8-135">Pascal</span></span>|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|
|<span data-ttu-id="9ede8-136">Parametre</span><span class="sxs-lookup"><span data-stu-id="9ede8-136">Parameter</span></span>|<span data-ttu-id="9ede8-137">Ortası büyük harf</span><span class="sxs-lookup"><span data-stu-id="9ede8-137">Camel</span></span>|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|

## <a name="capitalizing-compound-words-and-common-terms"></a><span data-ttu-id="9ede8-138">Bileşik sözcüklerin ve ortak koşulların büyük bir olması</span><span class="sxs-lookup"><span data-stu-id="9ede8-138">Capitalizing Compound Words and Common Terms</span></span>
 <span data-ttu-id="9ede8-139">Çoğu bileşik terim, büyük küçük harf amaçlarıyla tek sözcük olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9ede8-139">Most compound terms are treated as single words for purposes of capitalization.</span></span>

 <span data-ttu-id="9ede8-140">❌, kapalı biçimli bileşik sözcükler olarak adlandırılan her sözcük için büyük harf KULLANMAYıN.</span><span class="sxs-lookup"><span data-stu-id="9ede8-140">❌ DO NOT capitalize each word in so-called closed-form compound words.</span></span>

 <span data-ttu-id="9ede8-141">Bunlar, uç nokta gibi tek bir kelime olarak yazılmış olan Birleşik sözcüklerdir.</span><span class="sxs-lookup"><span data-stu-id="9ede8-141">These are compound words written as a single word, such as endpoint.</span></span> <span data-ttu-id="9ede8-142">Büyük/küçük harf yönergeleri için kapalı biçimli bir bileşik sözcüğü tek bir sözcük olarak değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="9ede8-142">For the purpose of casing guidelines, treat a closed-form compound word as a single word.</span></span> <span data-ttu-id="9ede8-143">Bileşik bir sözcüğün kapalı biçimde yazılıp yazılmadığını öğrenmek için geçerli bir sözlük kullanın.</span><span class="sxs-lookup"><span data-stu-id="9ede8-143">Use a current dictionary to determine if a compound word is written in closed form.</span></span>

|<span data-ttu-id="9ede8-144">Pascal</span><span class="sxs-lookup"><span data-stu-id="9ede8-144">Pascal</span></span>|<span data-ttu-id="9ede8-145">Ortası büyük harf</span><span class="sxs-lookup"><span data-stu-id="9ede8-145">Camel</span></span>|<span data-ttu-id="9ede8-146">Not</span><span class="sxs-lookup"><span data-stu-id="9ede8-146">Not</span></span>|
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

## <a name="case-sensitivity"></a><span data-ttu-id="9ede8-147">Büyük/küçük harf duyarlılığı</span><span class="sxs-lookup"><span data-stu-id="9ede8-147">Case Sensitivity</span></span>
 <span data-ttu-id="9ede8-148">CLR üzerinde çalışabilen dillerin, büyük/küçük harf duyarlılığı desteklemek için gerekli değildir, ancak bazıları.</span><span class="sxs-lookup"><span data-stu-id="9ede8-148">Languages that can run on the CLR are not required to support case-sensitivity, although some do.</span></span> <span data-ttu-id="9ede8-149">Diliniz destekliyorsa bile, çerçeve'nize erişebilen diğer diller değildir.</span><span class="sxs-lookup"><span data-stu-id="9ede8-149">Even if your language supports it, other languages that might access your framework do not.</span></span> <span data-ttu-id="9ede8-150">Bu nedenle dışarıdan erişilebilen tüm API 'Ler, aynı bağlamdaki iki ad arasında ayrım yapmak için tek başına bir durum kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="9ede8-150">Any APIs that are externally accessible, therefore, cannot rely on case alone to distinguish between two names in the same context.</span></span>

 <span data-ttu-id="9ede8-151">❌ tüm programlama dillerinin büyük/küçük harfe duyarlı olduğunu varsaymaz.</span><span class="sxs-lookup"><span data-stu-id="9ede8-151">❌ DO NOT assume that all programming languages are case sensitive.</span></span> <span data-ttu-id="9ede8-152">Bunlar değildir.</span><span class="sxs-lookup"><span data-stu-id="9ede8-152">They are not.</span></span> <span data-ttu-id="9ede8-153">Adlar tek başına büyük/küçük harf bakımından farklı olamaz.</span><span class="sxs-lookup"><span data-stu-id="9ede8-153">Names cannot differ by case alone.</span></span>

 <span data-ttu-id="9ede8-154">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="9ede8-154">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="9ede8-155">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="9ede8-155">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="9ede8-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ede8-156">See also</span></span>

- [<span data-ttu-id="9ede8-157">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="9ede8-157">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="9ede8-158">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="9ede8-158">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
