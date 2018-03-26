---
title: UriTemplate ve UriTemplateTable
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ac77fe2c83828d2cc9473417d2b29b2d2e540923
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="uritemplate-and-uritemplatetable"></a><span data-ttu-id="3ba80-102">UriTemplate ve UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="3ba80-102">UriTemplate and UriTemplateTable</span></span>
<span data-ttu-id="3ba80-103">Web geliştiricileri şekli ve kendi Hizmetleri yanıt URI düzeni tanımlamak için gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-103">Web developers require the ability to describe the shape and layout of the URIs that their services respond to.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="3ba80-104"> Geliştiriciler kendi URI'ler üzerinde denetime iki yeni sınıflar eklendi.</span><span class="sxs-lookup"><span data-stu-id="3ba80-104"> added two new classes to give developers control over their URIs.</span></span> <span data-ttu-id="3ba80-105"><xref:System.UriTemplate> ve <xref:System.UriTemplateTable> URI tabanlı gönderme altyapısında temelini [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3ba80-105"><xref:System.UriTemplate> and <xref:System.UriTemplateTable> form the basis of the URI-based dispatch engine in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="3ba80-106">Bu sınıfların de kendi izin geliştiricilere şablonları ve URI eşleme mekanizması uygulamadan yararlanmak için kullanılabilir bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="3ba80-106">These classes can also be used on their own, allowing developers to take advantage of templates and the URI mapping mechanism without implementing a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
## <a name="templates"></a><span data-ttu-id="3ba80-107">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="3ba80-107">Templates</span></span>  
 <span data-ttu-id="3ba80-108">Bir şablon göreli URI'ler kümesini tanımlamak için bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="3ba80-108">A template is a way to describe a set of relative URIs.</span></span> <span data-ttu-id="3ba80-109">Aşağıdaki tabloda URI şablonları kümesini çeşitli hava durumu bilgi türlerini alır. bir sistem nasıl tanımlanabilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-109">The set of URI templates in the following table shows how a system that retrieves various types of weather information might be defined.</span></span>  
  
|<span data-ttu-id="3ba80-110">Veri</span><span class="sxs-lookup"><span data-stu-id="3ba80-110">Data</span></span>|<span data-ttu-id="3ba80-111">Şablon</span><span class="sxs-lookup"><span data-stu-id="3ba80-111">Template</span></span>|  
|----------|--------------|  
|<span data-ttu-id="3ba80-112">Ulusal tahmin</span><span class="sxs-lookup"><span data-stu-id="3ba80-112">National Forecast</span></span>|<span data-ttu-id="3ba80-113">hava durumu/Ulusal</span><span class="sxs-lookup"><span data-stu-id="3ba80-113">weather/national</span></span>|  
|<span data-ttu-id="3ba80-114">Durum tahmin</span><span class="sxs-lookup"><span data-stu-id="3ba80-114">State Forecast</span></span>|<span data-ttu-id="3ba80-115">hava durumu / {state}</span><span class="sxs-lookup"><span data-stu-id="3ba80-115">weather/{state}</span></span>|  
|<span data-ttu-id="3ba80-116">Şehir tahmin</span><span class="sxs-lookup"><span data-stu-id="3ba80-116">City Forecast</span></span>|<span data-ttu-id="3ba80-117">hava durumu / {state} / {Şehir}</span><span class="sxs-lookup"><span data-stu-id="3ba80-117">weather/{state}/{city}</span></span>|  
|<span data-ttu-id="3ba80-118">Etkinlik tahmin</span><span class="sxs-lookup"><span data-stu-id="3ba80-118">Activity Forecast</span></span>|<span data-ttu-id="3ba80-119">hava durumu / {state} / {Şehir} / {etkinliği}</span><span class="sxs-lookup"><span data-stu-id="3ba80-119">weather/{state}/{city}/{activity}</span></span>|  
  
 <span data-ttu-id="3ba80-120">Bu tablo bir yapısal olarak benzer URI'ler açıklar.</span><span class="sxs-lookup"><span data-stu-id="3ba80-120">This table describes a set of structurally similar URIs.</span></span> <span data-ttu-id="3ba80-121">Her girişin bir URI şablonudur.</span><span class="sxs-lookup"><span data-stu-id="3ba80-121">Each entry is a URI template.</span></span> <span data-ttu-id="3ba80-122">Süslü ayraçlar segmentlerinde değişkenleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="3ba80-122">The segments in curly braces describe variables.</span></span> <span data-ttu-id="3ba80-123">Süslü ayraçlar içinde değil kesimleri değişmez değer dizeleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3ba80-123">The segments not in curly braces describe literal strings.</span></span> <span data-ttu-id="3ba80-124">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Şablon sınıfları, örneğin, "/ hava durumu/wa/seattle/dönüşüm", bir gelen URI alıp, açıklayan bir şablona eşleşen bir geliştirici izin ver "/weather/ {state} / {Şehir} / {etkinlik}".</span><span class="sxs-lookup"><span data-stu-id="3ba80-124">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] template classes allow a developer to take an incoming URI, for example, "/weather/wa/seattle/cycling", and match it to a template that describes it, "/weather/{state}/{city}/{activity}".</span></span>  
  
## <a name="uritemplate"></a><span data-ttu-id="3ba80-125">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="3ba80-125">UriTemplate</span></span>  
 <span data-ttu-id="3ba80-126"><xref:System.UriTemplate> bir URI şablonu kapsülleyen bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="3ba80-126"><xref:System.UriTemplate> is a class that encapsulates a URI template.</span></span> <span data-ttu-id="3ba80-127">Oluşturucusu şablon tanımlayan bir dize parametresi alan.</span><span class="sxs-lookup"><span data-stu-id="3ba80-127">The constructor takes a string parameter that defines the template.</span></span> <span data-ttu-id="3ba80-128">Bu dize sonraki bölümde açıklanan biçimde şablonu içerir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-128">This string contains the template in the format described in the next section.</span></span> <span data-ttu-id="3ba80-129"><xref:System.UriTemplate> Sınıfı sağlar izin yöntemleri eşleşen bir şablon için gelen bir URI, bir şablondan bir URI oluşturmayı, şablonda kullanılan değişken adları topluluğu almak, iki şablonları eşdeğerdir ve şablonun dönüş olup olmadığını belirler dize.</span><span class="sxs-lookup"><span data-stu-id="3ba80-129">The <xref:System.UriTemplate> class provides methods that allow you match an incoming URI to a template, generate a URI from a template, retrieve a collection of variable names used in the template, determine whether two templates are equivalent, and return the template's string.</span></span>  
  
 <span data-ttu-id="3ba80-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> taban adresi ve bir aday URI ve şablona URI'si eşleştirmeyi dener alır.</span><span class="sxs-lookup"><span data-stu-id="3ba80-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> takes a base address and a candidate URI and attempts to match the URI to the template.</span></span> <span data-ttu-id="3ba80-131">Eşleşme başarılı olursa bir <xref:System.UriTemplateMatch> örneği döndürülür.</span><span class="sxs-lookup"><span data-stu-id="3ba80-131">If the match is successful, a <xref:System.UriTemplateMatch> instance is returned.</span></span> <span data-ttu-id="3ba80-132"><xref:System.UriTemplateMatch> Nesnesini içeren temel bir URI, URI sorgu parametreleri, göreli yol kesimleri dizisi, bir ad/değer koleksiyonu eşleştirildiklerinden, değişkenlerin ad/değer koleksiyonu adayı <xref:System.UriTemplate> eşleştirme gerçekleştirmek için kullanılan örneği , URI (şablon bir joker karakter olduğunda kullanılır) adayı eşleşmeyen herhangi bir bölümünü içeren bir dize ve şablonuyla ilişkili bir nesne.</span><span class="sxs-lookup"><span data-stu-id="3ba80-132">The <xref:System.UriTemplateMatch> object contains a base URI, the candidate URI, a name/value collection of the query parameters, an array of the relative path segments, a name/value collection of variables that were matched, the <xref:System.UriTemplate> instance used to perform the match, a string that contains any unmatched portion of the candidate URI (used when the template has a wildcard), and an object that is associated with the template.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ba80-133"><xref:System.UriTemplate> Sınıfı bir şablona URI'si aday eşleştirirken düzeni ve bağlantı noktası numarası yok sayar.</span><span class="sxs-lookup"><span data-stu-id="3ba80-133">The <xref:System.UriTemplate> class ignores the scheme and port number when matching a candidate URI to a template.</span></span>  
  
 <span data-ttu-id="3ba80-134">Bir şablondan bir URI oluşturmayı sağlayan iki yöntem vardır <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> ve <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span><span class="sxs-lookup"><span data-stu-id="3ba80-134">There are two methods that allow you to generate a URI from a template, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> and <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span></span> <span data-ttu-id="3ba80-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> Temel adres ve parametreleri ad/değer koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="3ba80-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> takes a base address and a name/value collection of parameters.</span></span> <span data-ttu-id="3ba80-136">Şablon bağlandığında bu parametreler için değişkenleri yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3ba80-136">These parameters are substituted for variables when the template is bound.</span></span> <span data-ttu-id="3ba80-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> ad/değer çiftlerini alır ve bunları soldan sağa değiştirir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> takes the name/value pairs and substitutes them left to right.</span></span>  
  
 <span data-ttu-id="3ba80-138"><xref:System.UriTemplate.ToString> Şablon dizesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="3ba80-138"><xref:System.UriTemplate.ToString> returns the template string.</span></span>  
  
 <span data-ttu-id="3ba80-139"><xref:System.UriTemplate.PathSegmentVariableNames%2A> Özellik adları şablon dizesinde yol kesimleri içinde kullanılan değişkenlerinin koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-139">The <xref:System.UriTemplate.PathSegmentVariableNames%2A> property contains a collection of the names of the variables used within path segments in the template string.</span></span>  
  
 <span data-ttu-id="3ba80-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> alan bir <xref:System.UriTemplate> bir parametre olarak ve iki şablonları eşdeğer olup olmadığını belirten bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="3ba80-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> takes a <xref:System.UriTemplate> as a parameter and returns a Boolean value that specifies whether the two templates are equivalent.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="3ba80-141"> Bu konunun ilerleyen bölümlerinde şablon eşdeğer bölümü.</span><span class="sxs-lookup"><span data-stu-id="3ba80-141"> the Template Equivalence section later in this topic.</span></span>  
  
 <span data-ttu-id="3ba80-142"><xref:System.UriTemplate> HTTP URI dilbilgisi uyan herhangi bir URI şeması ile çalışmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3ba80-142"><xref:System.UriTemplate> is designed to work with any URI scheme that conforms to the HTTP URI grammar.</span></span> <span data-ttu-id="3ba80-143">Desteklenen URI şemaları örnekleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-143">The following are examples of supported URI schemes.</span></span>  
  
-   <span data-ttu-id="3ba80-144">http://</span><span class="sxs-lookup"><span data-stu-id="3ba80-144">http://</span></span>  
  
-   <span data-ttu-id="3ba80-145">https://</span><span class="sxs-lookup"><span data-stu-id="3ba80-145">https://</span></span>  
  
-   <span data-ttu-id="3ba80-146">net.tcp://</span><span class="sxs-lookup"><span data-stu-id="3ba80-146">net.tcp://</span></span>  
  
-   <span data-ttu-id="3ba80-147">net.pipe://</span><span class="sxs-lookup"><span data-stu-id="3ba80-147">net.pipe://</span></span>  
  
-   <span data-ttu-id="3ba80-148">sb://</span><span class="sxs-lookup"><span data-stu-id="3ba80-148">sb://</span></span>  
  
 <span data-ttu-id="3ba80-149">Düzenleri gibi file:// ve urn: / / değil HTTP URI dilbilgisi uygun ve URI şablonları ile kullanıldığında öngörülemeyen sonuçlara neden.</span><span class="sxs-lookup"><span data-stu-id="3ba80-149">Schemes like file:// and urn:// do not conform to the HTTP URI grammar and cause unpredictable results when used with URI templates.</span></span>  
  
### <a name="template-string-syntax"></a><span data-ttu-id="3ba80-150">Şablon dizesi söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3ba80-150">Template String Syntax</span></span>  
 <span data-ttu-id="3ba80-151">Bir şablon üç bölümden oluşur: bir yolu, isteğe bağlı bir sorgu ve isteğe bağlı bir parçası.</span><span class="sxs-lookup"><span data-stu-id="3ba80-151">A template has three parts: a path, an optional query, and an optional fragment.</span></span> <span data-ttu-id="3ba80-152">Örneğin, aşağıdaki şablonu bakın:</span><span class="sxs-lookup"><span data-stu-id="3ba80-152">For an example, see the following template:</span></span>  
  
```  
"/weather/{state}/{city}?forecast={length)#frag1  
```  
  
 <span data-ttu-id="3ba80-153">Yolun oluşan "/weather/ {state} / {Şehir}", sorgu oluşan"? Tahmin = {uzunluk} ve"#frag1"parça oluşur.</span><span class="sxs-lookup"><span data-stu-id="3ba80-153">The path consists of "/weather/{state}/{city}", the query consists of "?forecast={length}, and the fragment consists of "#frag1".</span></span>  
  
 <span data-ttu-id="3ba80-154">Baştaki ve sondaki eğik çizgi yol ifadesinde isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3ba80-154">Leading and trailing slashes are optional in the path expression.</span></span> <span data-ttu-id="3ba80-155">Sorgu ve parça ifadeleri tamamen atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-155">Both the query and fragment expressions can be omitted entirely.</span></span> <span data-ttu-id="3ba80-156">Bir yol kesimleri tarafından ayrılmış bir dizi oluşur '/', her segmentinde bir hazır değer, ({süslü ayraçlar içinde} yazılmış) bir değişken adı ya da bir joker karakter içerebilir (yazılmış olarak\*').</span><span class="sxs-lookup"><span data-stu-id="3ba80-156">A path consists of a series of segments delimited by '/', each segment can have a literal value, a variable name (written in {curly braces}), or a wildcard (written as '\*').</span></span> <span data-ttu-id="3ba80-157">Önceki şablondaki "\weather\ kesimi ise bir hazır değer değeri"{durumu}"ve"{Şehir}"olan değişkenler.</span><span class="sxs-lookup"><span data-stu-id="3ba80-157">In the previous template the "\weather\ segment is a literal value while "{state}" and "{city}" are variables.</span></span> <span data-ttu-id="3ba80-158">Değişkenleri alabilir, süslü ayraçlar içeriğini kendi adından ve oluşturmak için somut bir değer daha sonra değiştirilebilir bir *URI kapalı*.</span><span class="sxs-lookup"><span data-stu-id="3ba80-158">Variables take their name from the contents of their curly braces and they can later be replaced with a concrete value to create a *closed URI*.</span></span> <span data-ttu-id="3ba80-159">Joker karakter isteğe bağlıdır, ancak yalnızca, mantıksal olarak "yolu rest" eşleştiği URI, sonunda yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-159">The wildcard is optional, but can only appear at the end of the URI, where it logically matches "the rest of the path".</span></span>  
  
 <span data-ttu-id="3ba80-160">Sorgu ifadesi varsa, sırasız ad/değer çiftleri tarafından ayrılmış bir dizi belirtir '&'.</span><span class="sxs-lookup"><span data-stu-id="3ba80-160">The query expression, if present, specifies a series of unordered name/value pairs delimited by '&'.</span></span> <span data-ttu-id="3ba80-161">Sorgu ifadesi öğeleri ya da değişmez değer çiftleri olacak (x = 2) veya bir değişken çifti (x = {var}).</span><span class="sxs-lookup"><span data-stu-id="3ba80-161">Elements of the query expression can either be literal pairs (x=2) or a variable pair (x={var}).</span></span> <span data-ttu-id="3ba80-162">Sorguyu yalnızca sağ tarafındaki değişken bir ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-162">Only the right side of the query can have a variable expression.</span></span> <span data-ttu-id="3ba80-163">({birad} = {someValue} izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="3ba80-163">({someName} = {someValue} is not allowed.</span></span> <span data-ttu-id="3ba80-164">Değerleri eşlenmemiş (? x) izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="3ba80-164">Unpaired values (?x) are not permitted.</span></span> <span data-ttu-id="3ba80-165">Boş sorgu ifadesi ve yalnızca bir tek oluşan bir sorgu ifadesi arasında fark yoktur '?' (her ikisi de "herhangi bir sorgu" anlamına gelir).</span><span class="sxs-lookup"><span data-stu-id="3ba80-165">There is no difference between an empty query expression and a query expression consisting of just a single '?' (both mean "any query").</span></span>  
  
 <span data-ttu-id="3ba80-166">Parça ifadesi değişmez değer oluşabilir, değişken izin verilir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-166">The fragment expression can consist of a literal value, no variables are allowed.</span></span>  
  
 <span data-ttu-id="3ba80-167">Tüm şablon değişken adları şablon dize içinde benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3ba80-167">All template variable names within a template string must be unique.</span></span> <span data-ttu-id="3ba80-168">Şablon değişkeni adları büyük/küçük harfe duyarsızdır.</span><span class="sxs-lookup"><span data-stu-id="3ba80-168">Template variable names are case-insensitive.</span></span>  
  
 <span data-ttu-id="3ba80-169">Geçerli şablon dizesi örnekleri:</span><span class="sxs-lookup"><span data-stu-id="3ba80-169">Examples of valid template strings:</span></span>  
  
-   <span data-ttu-id="3ba80-170">""</span><span class="sxs-lookup"><span data-stu-id="3ba80-170">""</span></span>  
  
-   <span data-ttu-id="3ba80-171">"/ ayakkabı"</span><span class="sxs-lookup"><span data-stu-id="3ba80-171">"/shoe"</span></span>  
  
-   <span data-ttu-id="3ba80-172">"/ ayakkabı / \*"</span><span class="sxs-lookup"><span data-stu-id="3ba80-172">"/shoe/\*"</span></span>  
  
-   <span data-ttu-id="3ba80-173">"{ayakkabı} / bot"</span><span class="sxs-lookup"><span data-stu-id="3ba80-173">"{shoe}/boat"</span></span>  
  
-   <span data-ttu-id="3ba80-174">"{ayakkabı} / {{quilt} /bed/ bot}"</span><span class="sxs-lookup"><span data-stu-id="3ba80-174">"{shoe}/{boat}/bed/{quilt}"</span></span>  
  
-   <span data-ttu-id="3ba80-175">"ayakkabı / {bot}"</span><span class="sxs-lookup"><span data-stu-id="3ba80-175">"shoe/{boat}"</span></span>  
  
-   <span data-ttu-id="3ba80-176">"ayakkabı / {bot} / \*"</span><span class="sxs-lookup"><span data-stu-id="3ba80-176">"shoe/{boat}/\*"</span></span>  
  
-   <span data-ttu-id="3ba80-177">"shoe/boat?x=2"</span><span class="sxs-lookup"><span data-stu-id="3ba80-177">"shoe/boat?x=2"</span></span>  
  
-   <span data-ttu-id="3ba80-178">"shoe/{boat}?x={bed}"</span><span class="sxs-lookup"><span data-stu-id="3ba80-178">"shoe/{boat}?x={bed}"</span></span>  
  
-   <span data-ttu-id="3ba80-179">"ayakkabı / {bot}? = {yatak} & y x bant ="</span><span class="sxs-lookup"><span data-stu-id="3ba80-179">"shoe/{boat}?x={bed}&y=band"</span></span>  
  
-   <span data-ttu-id="3ba80-180">"?x={shoe}"</span><span class="sxs-lookup"><span data-stu-id="3ba80-180">"?x={shoe}"</span></span>  
  
-   <span data-ttu-id="3ba80-181">"shoe?x=3&y={var}</span><span class="sxs-lookup"><span data-stu-id="3ba80-181">"shoe?x=3&y={var}</span></span>  
  
 <span data-ttu-id="3ba80-182">Geçersiz şablon dizesi örnekleri:</span><span class="sxs-lookup"><span data-stu-id="3ba80-182">Examples of invalid template strings:</span></span>  
  
-   <span data-ttu-id="3ba80-183">"{ayakkabı} / {AYAKKABI} / x 2 =" – Yinelenen değişken adları.</span><span class="sxs-lookup"><span data-stu-id="3ba80-183">"{shoe}/{SHOE}/x=2" – Duplicate variable names.</span></span>  
  
-   <span data-ttu-id="3ba80-184">"{ayakkabı} /boat/? yatak {ayakkabı} =" – Yinelenen değişken adları.</span><span class="sxs-lookup"><span data-stu-id="3ba80-184">"{shoe}/boat/?bed={shoe}" – Duplicate variable names.</span></span>  
  
-   <span data-ttu-id="3ba80-185">"? x = 2 & x 3 =" – değişmez değerleri olsalar bile, ad/değer çiftleri bir sorgu dizesi içinde benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3ba80-185">"?x=2&x=3" – Name/value pairs within a query string must be unique, even if they are literals.</span></span>  
  
-   <span data-ttu-id="3ba80-186">"? x 2 = &" – sorgu dizesi hatalı biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="3ba80-186">"?x=2&" – Query string is malformed.</span></span>  
  
-   <span data-ttu-id="3ba80-187">"? 2 & x = {ayakkabı}" – sorgu dizesi, ad/değer çiftleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3ba80-187">"?2&x={shoe}" – Query string must be name/value pairs.</span></span>  
  
-   <span data-ttu-id="3ba80-188">"? y = 2 & & X = 3" – sorgu dizesi ad değer çifti olmalıdır, adları ile başlatamıyor '&'.</span><span class="sxs-lookup"><span data-stu-id="3ba80-188">"?y=2&&X=3" – Query string must be name value pairs, names cannot start with '&'.</span></span>  
  
### <a name="compound-path-segments"></a><span data-ttu-id="3ba80-189">Yol kesimleri bileşik</span><span class="sxs-lookup"><span data-stu-id="3ba80-189">Compound Path Segments</span></span>  
 <span data-ttu-id="3ba80-190">Bileşik yol kesimleri değişmez değerler ile birleştirilmiş değişkenlerinin yanı sıra birden çok değişkenleri içerecek şekilde tek bir URI yol kesimi izin verir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-190">Compound path segments allow a single URI path segment to contain multiple variables as well as variables combined with literals.</span></span> <span data-ttu-id="3ba80-191">Geçerli bileşik yol kesimleri örnekleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-191">The following are examples of valid compound path segments.</span></span>  
  
-   <span data-ttu-id="3ba80-192">/filename. {ext} /</span><span class="sxs-lookup"><span data-stu-id="3ba80-192">/filename.{ext}/</span></span>  
  
-   <span data-ttu-id="3ba80-193">/{filename}.jpg/</span><span class="sxs-lookup"><span data-stu-id="3ba80-193">/{filename}.jpg/</span></span>  
  
-   <span data-ttu-id="3ba80-194">/{filename}.{ext}/</span><span class="sxs-lookup"><span data-stu-id="3ba80-194">/{filename}.{ext}/</span></span>  
  
-   <span data-ttu-id="3ba80-195">/ {a}. {b}someLiteral{c}({d}) /</span><span class="sxs-lookup"><span data-stu-id="3ba80-195">/{a}.{b}someLiteral{c}({d})/</span></span>  
  
 <span data-ttu-id="3ba80-196">Geçersiz bir yol kesimleri örnekleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-196">The following are examples of invalid path segments.</span></span>  
  
-   <span data-ttu-id="3ba80-197">/{} - Değişkenleri şeklinde adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3ba80-197">/{} - Variables must be named.</span></span>  
  
-   <span data-ttu-id="3ba80-198">/ {ayakkabı} {bot} - değişkenleri bir hazır değer ile ayrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3ba80-198">/{shoe}{boat} - Variables must be separated by a literal.</span></span>  
  
### <a name="matching-and-compound-path-segments"></a><span data-ttu-id="3ba80-199">Eşleşen ve bileşik yol kesimleri</span><span class="sxs-lookup"><span data-stu-id="3ba80-199">Matching and Compound Path Segments</span></span>  
 <span data-ttu-id="3ba80-200">Bileşik yol kesimleri, tek bir yol kesimi içinde birden çok değişkenleri olan bir UriTemplate tanımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3ba80-200">Compound path segments allow you to define a UriTemplate that has multiple variables within a single path segment.</span></span> <span data-ttu-id="3ba80-201">Örneğin, aşağıdaki şablonu dizesinde: "adresleri / {state}. {Şehir} "(durumu ve şehir) iki değişken aynı kesim içinde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3ba80-201">For example, in the following template string: "Addresses/{state}.{city}" two variables (state and city) are defined within the same segment.</span></span> <span data-ttu-id="3ba80-202">Bu şablon bir URL gibi eşleşir "http://example.com/Washington.Redmond"ancak bir URL gibi eşleşir"http://example.com/Washington.Redmond.Microsoft".</span><span class="sxs-lookup"><span data-stu-id="3ba80-202">This template would match a URL such as "http://example.com/Washington.Redmond" but it will also match an URL like "http://example.com/Washington.Redmond.Microsoft".</span></span> <span data-ttu-id="3ba80-203">İkinci durumda, "Washington" durumu değişkenini içerir ve şehir değişkeni "Redmond.Microsoft" içerir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-203">In the latter case, the state variable will contain "Washington" and the city variable will contain "Redmond.Microsoft".</span></span> <span data-ttu-id="3ba80-204">Bu durumda herhangi bir metin (dışında '/') {Şehir} değişkeni ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-204">In this case any text (except ‘/’) will match the {city} variable.</span></span> <span data-ttu-id="3ba80-205">"Ek" metin eşleşmez bir şablon istiyorsanız, değişkeni ayrı bir şablon kesimdeki örneğin koyun: "adresleri / {state} / {şehir}.</span><span class="sxs-lookup"><span data-stu-id="3ba80-205">If you want a template that will not match the "extra" text, place the variable in a separate template segment, for example: "Addresses/{state}/{city}.</span></span>  
  
### <a name="named-wildcard-segments"></a><span data-ttu-id="3ba80-206">Adlandırılmış joker parçaları</span><span class="sxs-lookup"><span data-stu-id="3ba80-206">Named Wildcard Segments</span></span>  
 <span data-ttu-id="3ba80-207">Değişken adı joker karakteriyle başlayan yol değişken kesimi adlandırılmış joker kesimi ise ' \*'.</span><span class="sxs-lookup"><span data-stu-id="3ba80-207">A named wildcard segment is any path variable segment whose variable name begins with the wildcard character ‘\*’.</span></span> <span data-ttu-id="3ba80-208">Aşağıdaki şablonu dizesi "ayakkabı" adlı bir adlandırılmış joker karakter kesiminin içerir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-208">The following template string contains a named wildcard segment named "shoe".</span></span>  
  
```  
"literal/{*shoe}"  
```  
  
 <span data-ttu-id="3ba80-209">Joker karakter kesimleri aşağıdaki kurallara uymalıdır:</span><span class="sxs-lookup"><span data-stu-id="3ba80-209">Wildcard segments must follow the following rules:</span></span>  
  
-   <span data-ttu-id="3ba80-210">Olabilir en çok her şablon dize için bir adlandırılmış joker kesim.</span><span class="sxs-lookup"><span data-stu-id="3ba80-210">There can be at most one named wildcard segment for each template string.</span></span>  
  
-   <span data-ttu-id="3ba80-211">Bir adlandırılmış joker karakter kesiminin yolu en sağdaki kesimdeki adresindeki görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-211">A named wildcard segment must appear at the right-most segment in the path.</span></span>  
  
-   <span data-ttu-id="3ba80-212">Bir adlandırılmış joker karakter kesiminin aynı şablonu dizesi anonim joker Segmentte ile birlikte çalışamaz.</span><span class="sxs-lookup"><span data-stu-id="3ba80-212">A named wildcard segment cannot coexist with an anonymous wildcard segment within the same template string.</span></span>  
  
-   <span data-ttu-id="3ba80-213">Bir adlandırılmış joker karakter kesiminin adı benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3ba80-213">The name of a named wildcard segment must be unique.</span></span>  
  
-   <span data-ttu-id="3ba80-214">Joker karakter adlı kesimleri varsayılan değerlere sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="3ba80-214">Named wildcard segments cannot have default values.</span></span>  
  
-   <span data-ttu-id="3ba80-215">Adlandırılmış joker kesimleri ile bitemez "/".</span><span class="sxs-lookup"><span data-stu-id="3ba80-215">Named wildcard segments cannot end with "/".</span></span>  
  
### <a name="default-variable-values"></a><span data-ttu-id="3ba80-216">Varsayılan değişken değerleri</span><span class="sxs-lookup"><span data-stu-id="3ba80-216">Default Variable Values</span></span>  
 <span data-ttu-id="3ba80-217">Değişken değerleri varsayılan bir şablon içindeki değişkenleri için varsayılan değerleri belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3ba80-217">Default variable values allow you to specify default values for variables within a template.</span></span> <span data-ttu-id="3ba80-218">Bir koleksiyon veya değişkeni bildirme süslü ayraçlar olan varsayılan değişkenlerini belirtilebilir UriTemplate oluşturucuya geçirilen.</span><span class="sxs-lookup"><span data-stu-id="3ba80-218">Default variables can be specified with the curly braces that declare the variable or as a collection passed to the UriTemplate constructor.</span></span> <span data-ttu-id="3ba80-219">Aşağıdaki şablonu belirtmek için iki yolunu gösterir bir <xref:System.UriTemplate> varsayılan değerlerle değişkenleriyle.</span><span class="sxs-lookup"><span data-stu-id="3ba80-219">The following template shows two ways to specify a <xref:System.UriTemplate> with variables with default values.</span></span>  
  
```  
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 <span data-ttu-id="3ba80-220">Bu şablon adlı bir değişken bildiren `a` varsayılan değerini `1` ve adlı bir değişkende `b` varsayılan değerini `5`.</span><span class="sxs-lookup"><span data-stu-id="3ba80-220">This template declares a variable named `a` with a default value of `1` and a variable named `b` with a default value of `5`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ba80-221">Yalnızca yol kesimi değişkenleri varsayılan değerlere sahip olmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-221">Only path segment variables are allowed to have default values.</span></span> <span data-ttu-id="3ba80-222">Sorgu dizesi değişkenlerinin, bileşik kesim değişkenleri ve adlandırılmış joker değişkenleri varsayılan değerlere sahip izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="3ba80-222">Query string variables, compound segment variables, and named wildcard variables are not permitted to have default values.</span></span>  
  
 <span data-ttu-id="3ba80-223">Aşağıdaki kod bir aday URI eşleştirirken varsayılan değişken değerleri nasıl işleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-223">The following code shows how default variable values are handled when matching a candidate URI.</span></span>  
  
```  
Uri baseAddress = new Uri("http://localhost:800   
Dictionary<string,string> defVals = new Dictionary<string,string> {{"a","1"}, {"b", "5"}};  
UriTemplate t = new UriTemplate("/test/{a}/{b}", defVals);0");  
UriTemplate t = new UriTemplate("/{state=WA}/{city=Redmond}/", true);  
Uri candidate = new Uri("http://localhost:8000/OR");  
  
UriTemplateMatch m1 = t.Match(baseAddress, candidate);  
  
// Display contents of BoundVariables  
foreach (string key in m1.BoundVariables.AllKeys)  
{  
    Console.WriteLine("\t\t{0}={1}", key, m1.BoundVariables[key]);  
}  
// The output of the above code is  
// Template: /{state=WA}/{city=Redmond}/  
// Candidate URI: http://localhost:8000/OR  
// BoundVariables:  
//      STATE=OR  
//       CITY=Redmond  
```  
  
> [!NOTE]
>  <span data-ttu-id="3ba80-224">8000 / / / gibi bir URI şablonunu eşleşmiyor önceki kod, ancak listelenen 8000 gibi bir URI / yapar.</span><span class="sxs-lookup"><span data-stu-id="3ba80-224">A URI such as http://localhost:8000/// does not match the template listed in the preceding code, however a URI such as http://localhost:8000/ does.</span></span>  
  
 <span data-ttu-id="3ba80-225">Aşağıdaki kod, bir URI ile bir şablon oluştururken, varsayılan değişken değerleri nasıl işleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-225">The following code shows how default variable values are handled when creating a URI with a template.</span></span>  
  
```  
Uri baseAddress = new Uri("http://localhost:8000/");  
Dictionary<string,string> defVals = new Dictionary<string,string> {{"a","1"}, {"b", "5"}};  
UriTemplate t = new UriTemplate("/test/{a}/{b}", defVals);  
NameValueCollection vals = new NameValueCollection();  
vals.Add("a", "10");  
  
Uri boundUri = t.BindByName(baseAddress, vals);  
Console.WriteLine("BaseAddress: {0}", baseAddress);  
Console.WriteLine("Template: {0}", t.ToString());  
  
Console.WriteLine("Values: ");  
foreach (string key in vals.AllKeys)  
{  
    Console.WriteLine("\tKey = {0}, Value = {1}", key, vals[key]);  
}  
Console.WriteLine("Bound URI: {0}", boundUri);  
  
// The output of the preceding code is  
// BaseAddress: http://localhost:8000/  
// Template: /test/{a}/{b}  
// Values:  
//     Key = a, Value = 10  
// Bound URI: http://localhost:8000/test/10/5  
```  
  
 <span data-ttu-id="3ba80-226">Bir değişken varsayılan değerini verilen zaman `null` ek bazı kısıtlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="3ba80-226">When a variable is given a default value of `null` there are some additional constraints.</span></span> <span data-ttu-id="3ba80-227">Varsayılan değer olarak bir değişken olabilir `null` değişkeni şablonu dizesi sağ çoğu kesim içinde yer alıyorsa veya kesim sağındaki tüm parçaları varsayılan değerleri, varsa `null`.</span><span class="sxs-lookup"><span data-stu-id="3ba80-227">A variable can have a default value of `null` if the variable is contained within the right most segment of the template string or if all segments to the right of the segment have default values of `null`.</span></span> <span data-ttu-id="3ba80-228">Geçerli şablon dizelerdir varsayılan değerlerle aşağıdaki `null`:</span><span class="sxs-lookup"><span data-stu-id="3ba80-228">The following are valid template strings with default values of `null`:</span></span>  
  
-   ```  
    UriTemplate t = new UriTemplate("shoe/{boat=null}");  
    ```  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");  
    ```  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");  
    ```  
 <span data-ttu-id="3ba80-229">Aşağıdaki varsayılan değerlerle geçersiz şablon dizelerdir `null`:</span><span class="sxs-lookup"><span data-stu-id="3ba80-229">The following are invalid template strings with  default values of `null`:</span></span>  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment  
    ```  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value  
    ```  
### <a name="default-values-and-matching"></a><span data-ttu-id="3ba80-230">Varsayılan değerler ve eşleştirme</span><span class="sxs-lookup"><span data-stu-id="3ba80-230">Default Values and Matching</span></span>  
 <span data-ttu-id="3ba80-231">Aday URI varsayılan değerlerine sahip bir şablon ile eşleştirme yapılırken varsayılan değerleri yerleştirilir <xref:System.UriTemplateMatch.BoundVariables%2A> değerleri adayı URI belirtilmezse koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="3ba80-231">When matching a candidate URI with a template that has default values, the default values are placed in the <xref:System.UriTemplateMatch.BoundVariables%2A> collection if values are not specified in the candidate URI.</span></span>  
  
### <a name="template-equivalence"></a><span data-ttu-id="3ba80-232">Şablon eşdeğer</span><span class="sxs-lookup"><span data-stu-id="3ba80-232">Template Equivalence</span></span>  
 <span data-ttu-id="3ba80-233">İki şablonları olmasını denirse *yapısal olarak eşdeğer* zaman tüm şablonları değişmez değerleri eşleşmesi ve aynı segmentlerinde değişkenleriniz.</span><span class="sxs-lookup"><span data-stu-id="3ba80-233">Two templates are said to be *structurally equivalent* when all of the templates' literals match and they have variables in the same segments.</span></span> <span data-ttu-id="3ba80-234">Örneğin aşağıdaki şablonlardan yapısal olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="3ba80-234">For example the following templates are structurally equivalent:</span></span>  
  
-   <span data-ttu-id="3ba80-235">/a/{var1}/b b/{var2}?x=1&y=2</span><span class="sxs-lookup"><span data-stu-id="3ba80-235">/a/{var1}/b b/{var2}?x=1&y=2</span></span>  
  
-   <span data-ttu-id="3ba80-236">a/{x}/b%20b/{var1}?y=2&x=1</span><span class="sxs-lookup"><span data-stu-id="3ba80-236">a/{x}/b%20b/{var1}?y=2&x=1</span></span>  
  
-   <span data-ttu-id="3ba80-237">a/{y}/B%20B/{z}/?y=2&x=1</span><span class="sxs-lookup"><span data-stu-id="3ba80-237">a/{y}/B%20B/{z}/?y=2&x=1</span></span>  
  
 <span data-ttu-id="3ba80-238">Fark edilecek bazı noktalar:</span><span class="sxs-lookup"><span data-stu-id="3ba80-238">A few things to notice:</span></span>  
  
-   <span data-ttu-id="3ba80-239">Bir şablon başında bir eğik çizgi varsa, yalnızca ilk dizine göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-239">If a template contains leading slashes, only the first one is ignored.</span></span>  
  
-   <span data-ttu-id="3ba80-240">Yapısal eşdeğer şablon dizeleri karşılaştırma, çalışması için değişken adları yok sayılır ve yol kesimleri, sorgu dizeleri büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="3ba80-240">When comparing template strings for structural equivalence, case is ignored for variable names and path segments, query strings are case sensitive.</span></span>  
  
-   <span data-ttu-id="3ba80-241">Sorgu dizeleri sırasız.</span><span class="sxs-lookup"><span data-stu-id="3ba80-241">Query strings are unordered.</span></span>  
  
## <a name="uritemplatetable"></a><span data-ttu-id="3ba80-242">UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="3ba80-242">UriTemplateTable</span></span>  
 <span data-ttu-id="3ba80-243"><xref:System.UriTemplateTable> Sınıfı temsil eden bir ilişkilendirilebilir tablosu <xref:System.UriTemplate> bağlı nesneleri nesneyi geliştiricinin seçme.</span><span class="sxs-lookup"><span data-stu-id="3ba80-243">The <xref:System.UriTemplateTable> class represents an associative table of <xref:System.UriTemplate> objects bound to an object of the developer's choosing.</span></span> <span data-ttu-id="3ba80-244">A <xref:System.UriTemplateTable> en az birini içermelidir <xref:System.UriTemplate> çağrılmadan önce <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="3ba80-244">A <xref:System.UriTemplateTable> must contain at least one <xref:System.UriTemplate> prior to calling <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span> <span data-ttu-id="3ba80-245">İçeriği bir <xref:System.UriTemplateTable> kadar değiştirilebilir <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="3ba80-245">The contents of a <xref:System.UriTemplateTable> can be changed until <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="3ba80-246">Doğrulama gerçekleştirilir zaman <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="3ba80-246">Validation is performed when <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="3ba80-247">Değerin doğrulaması türüne bağlıdır `allowMultiple` parametresi <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="3ba80-247">The type of validation performed depends upon the value of the `allowMultiple` parameter to <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span>  
  
 <span data-ttu-id="3ba80-248">Zaman <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> tümleştirilmesidir adlı `false`, <xref:System.UriTemplateTable> tablosunda hiçbir şablon olduğundan emin olmak için denetler.</span><span class="sxs-lookup"><span data-stu-id="3ba80-248">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `false`, the <xref:System.UriTemplateTable> checks to make sure there are no templates in the table.</span></span> <span data-ttu-id="3ba80-249">Bu yapısal olarak eşdeğer şablonlardan bulunursa, bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3ba80-249">If it finds any structurally equivalent templates, it throws an exception.</span></span> <span data-ttu-id="3ba80-250">Bu ile birlikte kullanılır <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> yalnızca tek bir şablonda sağlamak istediğinizde bir gelen URI ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-250">This is used in conjunction with <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> when you want to ensure only one template matches an incoming URI.</span></span>  
  
 <span data-ttu-id="3ba80-251">Zaman <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> tümleştirilmesidir adlı `true`, <xref:System.UriTemplateTable> birden çok, yapısal olarak eşdeğer şablonları içerilmesini bir <xref:System.UriTemplateTable>.</span><span class="sxs-lookup"><span data-stu-id="3ba80-251">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `true`, <xref:System.UriTemplateTable> allows multiple, structurally-equivalent templates to be contained within a <xref:System.UriTemplateTable>.</span></span>  
  
 <span data-ttu-id="3ba80-252">Bir dizi <xref:System.UriTemplate> eklenen nesneleri bir <xref:System.UriTemplateTable> bunlar olmamalıdır belirsiz sorgu dizeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-252">If a set of <xref:System.UriTemplate> objects added to a <xref:System.UriTemplateTable> contain query strings they must not be ambiguous.</span></span> <span data-ttu-id="3ba80-253">Aynı sorgu dizelerine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-253">Identical query strings are allowed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ba80-254">Sırada <xref:System.UriTemplateTable> temel adresleri, kullanım düzenleri HTTP, düzeni dışındaki ve bağlantı noktası numarası yok sayılır adayı URI'ler şablonlarına eşleştirirken sağlar.</span><span class="sxs-lookup"><span data-stu-id="3ba80-254">While the <xref:System.UriTemplateTable> allows base addresses that use schemes other than HTTP, the scheme and port number are ignored when matching candidate URIs to templates.</span></span>  
  
### <a name="query-string-ambiguity"></a><span data-ttu-id="3ba80-255">Sorgu dizesi belirsizlik</span><span class="sxs-lookup"><span data-stu-id="3ba80-255">Query String Ambiguity</span></span>  
 <span data-ttu-id="3ba80-256">Birden fazla şablon eşleşen bir URI ise paylaşımına eşdeğer bir yol şablonları belirsiz sorgu dizeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-256">Templates that share an equivalent path contain ambiguous query strings if there is a URI that matches more than one template.</span></span>  
  
 <span data-ttu-id="3ba80-257">Aşağıdaki sorgu dizeleri kendilerini içinde anlaşılır şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3ba80-257">The following sets of query strings are unambiguous within themselves:</span></span>  
  
-   <span data-ttu-id="3ba80-258">?x=1</span><span class="sxs-lookup"><span data-stu-id="3ba80-258">?x=1</span></span>  
  
-   <span data-ttu-id="3ba80-259">?x=2</span><span class="sxs-lookup"><span data-stu-id="3ba80-259">?x=2</span></span>  
  
-   <span data-ttu-id="3ba80-260">?x=3</span><span class="sxs-lookup"><span data-stu-id="3ba80-260">?x=3</span></span>  
  
-   <span data-ttu-id="3ba80-261">?x=1&y={var}</span><span class="sxs-lookup"><span data-stu-id="3ba80-261">?x=1&y={var}</span></span>  
  
-   <span data-ttu-id="3ba80-262">?x=2&z={var}</span><span class="sxs-lookup"><span data-stu-id="3ba80-262">?x=2&z={var}</span></span>  
  
-   <span data-ttu-id="3ba80-263">?x=3</span><span class="sxs-lookup"><span data-stu-id="3ba80-263">?x=3</span></span>  
  
-   <span data-ttu-id="3ba80-264">?x=1</span><span class="sxs-lookup"><span data-stu-id="3ba80-264">?x=1</span></span>  
  
-   <span data-ttu-id="3ba80-265">?</span><span class="sxs-lookup"><span data-stu-id="3ba80-265">?</span></span>  
  
-   <span data-ttu-id="3ba80-266">?</span><span class="sxs-lookup"><span data-stu-id="3ba80-266">?</span></span> <span data-ttu-id="3ba80-267">x={var}</span><span class="sxs-lookup"><span data-stu-id="3ba80-267">x={var}</span></span>  
  
-   <span data-ttu-id="3ba80-268">?</span><span class="sxs-lookup"><span data-stu-id="3ba80-268">?</span></span>  
  
-   <span data-ttu-id="3ba80-269">?m=get&c=rss</span><span class="sxs-lookup"><span data-stu-id="3ba80-269">?m=get&c=rss</span></span>  
  
-   <span data-ttu-id="3ba80-270">?m=put&c=rss</span><span class="sxs-lookup"><span data-stu-id="3ba80-270">?m=put&c=rss</span></span>  
  
-   <span data-ttu-id="3ba80-271">?m=get&c=atom</span><span class="sxs-lookup"><span data-stu-id="3ba80-271">?m=get&c=atom</span></span>  
  
-   <span data-ttu-id="3ba80-272">?m=put&c=atom</span><span class="sxs-lookup"><span data-stu-id="3ba80-272">?m=put&c=atom</span></span>  
  
 <span data-ttu-id="3ba80-273">Aşağıdaki sorgu dizesi şablonları kendilerini içinde belirsiz şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3ba80-273">The following sets of query string templates are ambiguous within themselves:</span></span>  
  
-   <span data-ttu-id="3ba80-274">?x=1</span><span class="sxs-lookup"><span data-stu-id="3ba80-274">?x=1</span></span>  
  
-   <span data-ttu-id="3ba80-275">?x={var}</span><span class="sxs-lookup"><span data-stu-id="3ba80-275">?x={var}</span></span>  
  
 <span data-ttu-id="3ba80-276">"x 1 ="-iki şablonları ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-276">"x=1" - Matches both templates.</span></span>  
  
-   <span data-ttu-id="3ba80-277">?x=1</span><span class="sxs-lookup"><span data-stu-id="3ba80-277">?x=1</span></span>  
  
-   <span data-ttu-id="3ba80-278">?y=2</span><span class="sxs-lookup"><span data-stu-id="3ba80-278">?y=2</span></span>  
  
 <span data-ttu-id="3ba80-279">"x 1 & y = 2 =" her iki şablonları ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-279">"x=1&y=2" matches both templates.</span></span> <span data-ttu-id="3ba80-280">Eşleşen şablonu sonra daha fazla sorgu dizesi değişkenlerinin bir sorgu dizesi içerebilir olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="3ba80-280">This is because a query string may contain more query string variables then the template it matches.</span></span>  
  
-   <span data-ttu-id="3ba80-281">?x=1</span><span class="sxs-lookup"><span data-stu-id="3ba80-281">?x=1</span></span>  
  
-   <span data-ttu-id="3ba80-282">?x=1&y={var}</span><span class="sxs-lookup"><span data-stu-id="3ba80-282">?x=1&y={var}</span></span>  
  
 <span data-ttu-id="3ba80-283">"x 1 & y = 3 =" her iki şablonları ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="3ba80-283">"x=1&y=3" matches both templates.</span></span>  
  
-   <span data-ttu-id="3ba80-284">?x=3&y=4</span><span class="sxs-lookup"><span data-stu-id="3ba80-284">?x=3&y=4</span></span>  
  
-   <span data-ttu-id="3ba80-285">?x=3&z=5</span><span class="sxs-lookup"><span data-stu-id="3ba80-285">?x=3&z=5</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ba80-286">Karakter á ve Á bir URI yolu bir parçası olarak görüntülendiğinde farklı karakter olduğu kabul edilir veya <xref:System.UriTemplate> yol kesimi değişmez değer (ancak karakterler a ve A aynı olduğu varsayılır).</span><span class="sxs-lookup"><span data-stu-id="3ba80-286">The characters á and Á are considered to be different characters when they appear as part of a URI path or <xref:System.UriTemplate> path segment literal (but the characters a and A are considered to be the same).</span></span> <span data-ttu-id="3ba80-287">Karakter á ve Á bir parçası olarak görüntülendiğinde aynı karakterler olduğu kabul edilir <xref:System.UriTemplate> {variableName} veya bir sorgu dizesi (ve a ve bir de değerlendirilir aynı karakter olmalı).</span><span class="sxs-lookup"><span data-stu-id="3ba80-287">The characters á and Á are considered to be the same characters when they appear as part of a <xref:System.UriTemplate> {variableName} or a query string (and a and A are also considered to be the same characters).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ba80-288">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3ba80-288">See Also</span></span>  
 [<span data-ttu-id="3ba80-289">WCF Web HTTP Programlama Modeli Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3ba80-289">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)  
 [<span data-ttu-id="3ba80-290">WCF Web HTTP Programlama Nesnesi Modeli</span><span class="sxs-lookup"><span data-stu-id="3ba80-290">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)  
 [<span data-ttu-id="3ba80-291">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="3ba80-291">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)  
 [<span data-ttu-id="3ba80-292">UriTemplate Tablosu</span><span class="sxs-lookup"><span data-stu-id="3ba80-292">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [<span data-ttu-id="3ba80-293">UriTemplate Tablosu Dağıtıcısı</span><span class="sxs-lookup"><span data-stu-id="3ba80-293">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
