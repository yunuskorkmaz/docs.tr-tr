---
title: UriTemplate ve UriTemplateTable
ms.date: 03/30/2017
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
ms.openlocfilehash: b0dc3b2b747bc08da239490db7db3ba77d1e7ed8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130253"
---
# <a name="uritemplate-and-uritemplatetable"></a><span data-ttu-id="205b7-102">UriTemplate ve UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="205b7-102">UriTemplate and UriTemplateTable</span></span>
<span data-ttu-id="205b7-103">Web geliştiricileri şekil ve hizmetlerini yanıt bir URI'leri düzenini açıklayan olanağına sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="205b7-103">Web developers require the ability to describe the shape and layout of the URIs that their services respond to.</span></span> <span data-ttu-id="205b7-104">Windows Communication Foundation (WCF), geliştiricilerin kendi bir URI'leri denetiminin kendilerinde olmasına iki yeni sınıflar eklendi.</span><span class="sxs-lookup"><span data-stu-id="205b7-104">Windows Communication Foundation (WCF) added two new classes to give developers control over their URIs.</span></span> <xref:System.UriTemplate> <span data-ttu-id="205b7-105">ve <xref:System.UriTemplateTable> URI tabanlı dağıtım altyapısı WCF'de temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="205b7-105">and <xref:System.UriTemplateTable> form the basis of the URI-based dispatch engine in WCF.</span></span> <span data-ttu-id="205b7-106">Bu sınıflar, bir WCF Hizmeti uygulamadan kendi şablonlarını ve URI yararlanmak geliştiricilerin eşleme mekanizmasını de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="205b7-106">These classes can also be used on their own, allowing developers to take advantage of templates and the URI mapping mechanism without implementing a WCF service.</span></span>  
  
## <a name="templates"></a><span data-ttu-id="205b7-107">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="205b7-107">Templates</span></span>  
 <span data-ttu-id="205b7-108">Şablon, göreli bir URI'leri bir kümesini tanımlamak için kullanılan bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="205b7-108">A template is a way to describe a set of relative URIs.</span></span> <span data-ttu-id="205b7-109">Dizi URI şablonu aşağıdaki tabloda yer alan çeşitli türlerde hava durumu bilgileri sistem nasıl tanımlanabilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="205b7-109">The set of URI templates in the following table shows how a system that retrieves various types of weather information might be defined.</span></span>  
  
|<span data-ttu-id="205b7-110">Veri</span><span class="sxs-lookup"><span data-stu-id="205b7-110">Data</span></span>|<span data-ttu-id="205b7-111">Şablon</span><span class="sxs-lookup"><span data-stu-id="205b7-111">Template</span></span>|  
|----------|--------------|  
|<span data-ttu-id="205b7-112">Ulusal tahmin</span><span class="sxs-lookup"><span data-stu-id="205b7-112">National Forecast</span></span>|<span data-ttu-id="205b7-113">hava durumu/Ulusal</span><span class="sxs-lookup"><span data-stu-id="205b7-113">weather/national</span></span>|  
|<span data-ttu-id="205b7-114">Durum tahmin</span><span class="sxs-lookup"><span data-stu-id="205b7-114">State Forecast</span></span>|<span data-ttu-id="205b7-115">hava durumu / {state}</span><span class="sxs-lookup"><span data-stu-id="205b7-115">weather/{state}</span></span>|  
|<span data-ttu-id="205b7-116">Şehir tahmin</span><span class="sxs-lookup"><span data-stu-id="205b7-116">City Forecast</span></span>|<span data-ttu-id="205b7-117">hava durumu / {state} / {Şehir}</span><span class="sxs-lookup"><span data-stu-id="205b7-117">weather/{state}/{city}</span></span>|  
|<span data-ttu-id="205b7-118">Etkinlik tahmin</span><span class="sxs-lookup"><span data-stu-id="205b7-118">Activity Forecast</span></span>|<span data-ttu-id="205b7-119">hava durumu / {state} / {Şehir} / {etkinliği}</span><span class="sxs-lookup"><span data-stu-id="205b7-119">weather/{state}/{city}/{activity}</span></span>|  
  
 <span data-ttu-id="205b7-120">Bu tablo, yapısal olarak benzer bir URI'leri kümesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="205b7-120">This table describes a set of structurally similar URIs.</span></span> <span data-ttu-id="205b7-121">Her girişin bir URI Şablonu ' dir.</span><span class="sxs-lookup"><span data-stu-id="205b7-121">Each entry is a URI template.</span></span> <span data-ttu-id="205b7-122">Küme ayracı segmentler değişkenleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="205b7-122">The segments in curly braces describe variables.</span></span> <span data-ttu-id="205b7-123">Segment kaşlı ayraçlar içinde değil, değişmez değer dizeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="205b7-123">The segments not in curly braces describe literal strings.</span></span> <span data-ttu-id="205b7-124">WCF şablon sınıfları, örneğin, "/ hava durumu/wa/seattle/dönüşüm", gelen bir URI olması ve onu tanımlayan bir şablon eşleştirmek bir geliştirici izin ver "/weather/ {state} / {Şehir} / {etkinlik}".</span><span class="sxs-lookup"><span data-stu-id="205b7-124">The WCF template classes allow a developer to take an incoming URI, for example, "/weather/wa/seattle/cycling", and match it to a template that describes it, "/weather/{state}/{city}/{activity}".</span></span>  
  
## <a name="uritemplate"></a><span data-ttu-id="205b7-125">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="205b7-125">UriTemplate</span></span>  
 <xref:System.UriTemplate> <span data-ttu-id="205b7-126">bir URI şablonu kapsülleyen bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="205b7-126">is a class that encapsulates a URI template.</span></span> <span data-ttu-id="205b7-127">Oluşturucusu şablon tanımlayan bir dize parametresi alır.</span><span class="sxs-lookup"><span data-stu-id="205b7-127">The constructor takes a string parameter that defines the template.</span></span> <span data-ttu-id="205b7-128">Bu dize sonraki bölümde açıklanan biçimde şablonu içerir.</span><span class="sxs-lookup"><span data-stu-id="205b7-128">This string contains the template in the format described in the next section.</span></span> <span data-ttu-id="205b7-129"><xref:System.UriTemplate> SAX olanak sağlayan yöntemleri eşleşen bir şablon için gelen bir URI, bir şablondan bir URI oluşturmayı, değişken adı şablonda kullanılan koleksiyonu alma, iki şablonu eşdeğerdir ve şablonun dönüş olup olmadığını belirlemek dize.</span><span class="sxs-lookup"><span data-stu-id="205b7-129">The <xref:System.UriTemplate> class provides methods that allow you match an incoming URI to a template, generate a URI from a template, retrieve a collection of variable names used in the template, determine whether two templates are equivalent, and return the template's string.</span></span>  
  
 <xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> <span data-ttu-id="205b7-130">Temel adres ve bir aday URI ve şablon URI'si eşleşmeyi dener alır.</span><span class="sxs-lookup"><span data-stu-id="205b7-130">takes a base address and a candidate URI and attempts to match the URI to the template.</span></span> <span data-ttu-id="205b7-131">Eşleşmenin başarılı olması durumunda bir <xref:System.UriTemplateMatch> örneği döndürülür.</span><span class="sxs-lookup"><span data-stu-id="205b7-131">If the match is successful, a <xref:System.UriTemplateMatch> instance is returned.</span></span> <span data-ttu-id="205b7-132"><xref:System.UriTemplateMatch> Nesnesini içeren temel bir URI, URI sorgu parametreleri, bir dizi göreli yol parçalarının, eşleştirilmiş olan değişkenler ad/değer koleksiyonu ad/değer koleksiyonunu aday <xref:System.UriTemplate> eşleştirme uygulamak için kullanılan örneği , URI (şablon bir joker karakter varsa kullanılır) aday eşleşmeyen herhangi bir bölümünü içeren bir dize ve şablonu ile ilişkili bir nesne.</span><span class="sxs-lookup"><span data-stu-id="205b7-132">The <xref:System.UriTemplateMatch> object contains a base URI, the candidate URI, a name/value collection of the query parameters, an array of the relative path segments, a name/value collection of variables that were matched, the <xref:System.UriTemplate> instance used to perform the match, a string that contains any unmatched portion of the candidate URI (used when the template has a wildcard), and an object that is associated with the template.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="205b7-133"><xref:System.UriTemplate> Sınıfı bir şablon için bir aday URI eşleştirirken düzenini ve bağlantı noktası numarası yok sayar.</span><span class="sxs-lookup"><span data-stu-id="205b7-133">The <xref:System.UriTemplate> class ignores the scheme and port number when matching a candidate URI to a template.</span></span>  
  
 <span data-ttu-id="205b7-134">Bir şablondan bir URI oluşturmayı sağlayan iki farklı yöntemle <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> ve <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span><span class="sxs-lookup"><span data-stu-id="205b7-134">There are two methods that allow you to generate a URI from a template, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> and <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span></span> <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> <span data-ttu-id="205b7-135">Temel adres ve parametrelerin ad/değer koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="205b7-135">takes a base address and a name/value collection of parameters.</span></span> <span data-ttu-id="205b7-136">Şablon bağlandığında bu parametreler için değişkenleri yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="205b7-136">These parameters are substituted for variables when the template is bound.</span></span> <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> <span data-ttu-id="205b7-137">ad/değer çiftlerini alır ve bunları soldan sağa yerini alır.</span><span class="sxs-lookup"><span data-stu-id="205b7-137">takes the name/value pairs and substitutes them left to right.</span></span>  
  
 <xref:System.UriTemplate.ToString> <span data-ttu-id="205b7-138">Şablon dizeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="205b7-138">returns the template string.</span></span>  
  
 <span data-ttu-id="205b7-139"><xref:System.UriTemplate.PathSegmentVariableNames%2A> Özelliği, şablonu dizedeki yol kesimleri içinde kullanılan değişkenlerin adlarını koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="205b7-139">The <xref:System.UriTemplate.PathSegmentVariableNames%2A> property contains a collection of the names of the variables used within path segments in the template string.</span></span>  
  
 <xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> <span data-ttu-id="205b7-140">alan bir <xref:System.UriTemplate> bir parametre olarak ve iki şablon eşdeğer olup olmadığını belirten bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="205b7-140">takes a <xref:System.UriTemplate> as a parameter and returns a Boolean value that specifies whether the two templates are equivalent.</span></span> <span data-ttu-id="205b7-141">Daha fazla bilgi için bu konunun ilerleyen bölümlerinde şablon denkliği bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="205b7-141">For more information, see the Template Equivalence section later in this topic.</span></span>  
  
 <xref:System.UriTemplate> <span data-ttu-id="205b7-142">HTTP URI dilbilgisi uyan herhangi bir URI şeması ile çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="205b7-142">is designed to work with any URI scheme that conforms to the HTTP URI grammar.</span></span> <span data-ttu-id="205b7-143">Desteklenen URI düzenleri örnekleri aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="205b7-143">The following are examples of supported URI schemes.</span></span>  
  
- <span data-ttu-id="205b7-144">http://</span><span class="sxs-lookup"><span data-stu-id="205b7-144">http://</span></span>  
  
- <span data-ttu-id="205b7-145">https://</span><span class="sxs-lookup"><span data-stu-id="205b7-145">https://</span></span>  
  
- <span data-ttu-id="205b7-146">net.tcp://</span><span class="sxs-lookup"><span data-stu-id="205b7-146">net.tcp://</span></span>  
  
- <span data-ttu-id="205b7-147">net.pipe://</span><span class="sxs-lookup"><span data-stu-id="205b7-147">net.pipe://</span></span>  
  
- <span data-ttu-id="205b7-148">sb://</span><span class="sxs-lookup"><span data-stu-id="205b7-148">sb://</span></span>  
  
 <span data-ttu-id="205b7-149">Düzenleri gibi file:// ve urn: / / değil HTTP URI dilbilgisi uygun ve URI şablonları ile kullanıldığında öngörülemeyen sonuçlara neden.</span><span class="sxs-lookup"><span data-stu-id="205b7-149">Schemes like file:// and urn:// do not conform to the HTTP URI grammar and cause unpredictable results when used with URI templates.</span></span>  
  
### <a name="template-string-syntax"></a><span data-ttu-id="205b7-150">Şablon dizesi söz dizimi</span><span class="sxs-lookup"><span data-stu-id="205b7-150">Template String Syntax</span></span>  
 <span data-ttu-id="205b7-151">Bir şablon üç bölümden oluşur: bir yol, isteğe bağlı bir sorgu ve isteğe bağlı bir parçası.</span><span class="sxs-lookup"><span data-stu-id="205b7-151">A template has three parts: a path, an optional query, and an optional fragment.</span></span> <span data-ttu-id="205b7-152">Örneğin, aşağıdaki şablonu bakın:</span><span class="sxs-lookup"><span data-stu-id="205b7-152">For an example, see the following template:</span></span>  
  
```  
"/weather/{state}/{city}?forecast={length)#frag1  
```  
  
 <span data-ttu-id="205b7-153">Yolun oluşan "/weather/ {state} / {Şehir}", sorgu oluşan"? tahmini {length} ="#frag1"parça oluşur.</span><span class="sxs-lookup"><span data-stu-id="205b7-153">The path consists of "/weather/{state}/{city}", the query consists of "?forecast={length}, and the fragment consists of "#frag1".</span></span>  
  
 <span data-ttu-id="205b7-154">Baştaki ve sondaki eğik çizgi yolu ifade isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="205b7-154">Leading and trailing slashes are optional in the path expression.</span></span> <span data-ttu-id="205b7-155">Sorgu ve parça ifadeler tamamen atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="205b7-155">Both the query and fragment expressions can be omitted entirely.</span></span> <span data-ttu-id="205b7-156">Segment tarafından ayrılmış bir dizi yol oluşan '/', her bir kesim değişmez değer, bir değişken adı ({küme ayraçları içine} yazılmış) veya bir joker karakter olabilir (yazılmış olarak\*').</span><span class="sxs-lookup"><span data-stu-id="205b7-156">A path consists of a series of segments delimited by '/', each segment can have a literal value, a variable name (written in {curly braces}), or a wildcard (written as '\*').</span></span> <span data-ttu-id="205b7-157">Önceki şablonda "\weather\ segmenttir bir değişmez değer"{state}"ve"{city}"olan değişkenler.</span><span class="sxs-lookup"><span data-stu-id="205b7-157">In the previous template the "\weather\ segment is a literal value while "{state}" and "{city}" are variables.</span></span> <span data-ttu-id="205b7-158">Değişkenleri alabilir, küme ayracı içeriğini kendi adından ve oluşturmak için somut bir değer daha sonra değiştirilebilir bir *URI kapalı*.</span><span class="sxs-lookup"><span data-stu-id="205b7-158">Variables take their name from the contents of their curly braces and they can later be replaced with a concrete value to create a *closed URI*.</span></span> <span data-ttu-id="205b7-159">Joker karakter isteğe bağlıdır, ancak yalnızca burada "yolun rest" mantıksal olarak eşleşen bir URI sonunda görünebilir.</span><span class="sxs-lookup"><span data-stu-id="205b7-159">The wildcard is optional, but can only appear at the end of the URI, where it logically matches "the rest of the path".</span></span>  
  
 <span data-ttu-id="205b7-160">Sırasız ad/değer çiftleri tarafından ayrılmış bir dizi varsa, sorgu ifadesi belirtir '&'.</span><span class="sxs-lookup"><span data-stu-id="205b7-160">The query expression, if present, specifies a series of unordered name/value pairs delimited by '&'.</span></span> <span data-ttu-id="205b7-161">Sorgu ifadesinin öğeleri değişmez değer çifti olabilir (x = 2) veya bir değişken çifti (x = {var}).</span><span class="sxs-lookup"><span data-stu-id="205b7-161">Elements of the query expression can either be literal pairs (x=2) or a variable pair (x={var}).</span></span> <span data-ttu-id="205b7-162">Sorgu yalnızca sağ tarafında bir değişken bir ifadeye sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="205b7-162">Only the right side of the query can have a variable expression.</span></span> <span data-ttu-id="205b7-163">({birad} = {in değeri Birdeğer} izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="205b7-163">({someName} = {someValue} is not allowed.</span></span> <span data-ttu-id="205b7-164">Değerleri bitiştirilen (? x) izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="205b7-164">Unpaired values (?x) are not permitted.</span></span> <span data-ttu-id="205b7-165">Boş sorgu ifadesi yalnızca bir tek oluşan bir sorgu ifadesi arasındaki fark yoktur '?' (her ikisi de "herhangi bir sorgu" anlamına gelir).</span><span class="sxs-lookup"><span data-stu-id="205b7-165">There is no difference between an empty query expression and a query expression consisting of just a single '?' (both mean "any query").</span></span>  
  
 <span data-ttu-id="205b7-166">Parça ifadesi değişmez değer oluşabilir, değişken izin verilir.</span><span class="sxs-lookup"><span data-stu-id="205b7-166">The fragment expression can consist of a literal value, no variables are allowed.</span></span>  
  
 <span data-ttu-id="205b7-167">Bir şablon dize içindeki tüm şablon değişken adları benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="205b7-167">All template variable names within a template string must be unique.</span></span> <span data-ttu-id="205b7-168">Şablon değişkeni adları büyük/küçük harfe duyarsızdır.</span><span class="sxs-lookup"><span data-stu-id="205b7-168">Template variable names are case-insensitive.</span></span>  
  
 <span data-ttu-id="205b7-169">Geçerli şablon dizeleri örnekleri:</span><span class="sxs-lookup"><span data-stu-id="205b7-169">Examples of valid template strings:</span></span>  
  
- <span data-ttu-id="205b7-170">""</span><span class="sxs-lookup"><span data-stu-id="205b7-170">""</span></span>  
  
- <span data-ttu-id="205b7-171">"/shoe"</span><span class="sxs-lookup"><span data-stu-id="205b7-171">"/shoe"</span></span>  
  
- <span data-ttu-id="205b7-172">"/shoe/\*"</span><span class="sxs-lookup"><span data-stu-id="205b7-172">"/shoe/\*"</span></span>  
  
- <span data-ttu-id="205b7-173">"{ayakkabı} / bot"</span><span class="sxs-lookup"><span data-stu-id="205b7-173">"{shoe}/boat"</span></span>  
  
- <span data-ttu-id="205b7-174">"{ayakkabı} / {{quilt} /bed/ bot}"</span><span class="sxs-lookup"><span data-stu-id="205b7-174">"{shoe}/{boat}/bed/{quilt}"</span></span>  
  
- <span data-ttu-id="205b7-175">"ayakkabı / {bot}"</span><span class="sxs-lookup"><span data-stu-id="205b7-175">"shoe/{boat}"</span></span>  
  
- <span data-ttu-id="205b7-176">"ayakkabı / {bot} /\*"</span><span class="sxs-lookup"><span data-stu-id="205b7-176">"shoe/{boat}/\*"</span></span>  
  
- <span data-ttu-id="205b7-177">"shoe/boat?x=2"</span><span class="sxs-lookup"><span data-stu-id="205b7-177">"shoe/boat?x=2"</span></span>  
  
- <span data-ttu-id="205b7-178">"shoe/{boat}?x={bed}"</span><span class="sxs-lookup"><span data-stu-id="205b7-178">"shoe/{boat}?x={bed}"</span></span>  
  
- <span data-ttu-id="205b7-179">"ayakkabı / {bot}? = {yatak} & y x bant ="</span><span class="sxs-lookup"><span data-stu-id="205b7-179">"shoe/{boat}?x={bed}&y=band"</span></span>  
  
- <span data-ttu-id="205b7-180">"?x={shoe}"</span><span class="sxs-lookup"><span data-stu-id="205b7-180">"?x={shoe}"</span></span>  
  
- <span data-ttu-id="205b7-181">"shoe?x=3&y={var}</span><span class="sxs-lookup"><span data-stu-id="205b7-181">"shoe?x=3&y={var}</span></span>  
  
 <span data-ttu-id="205b7-182">Geçersiz şablon dizeleri örnekleri:</span><span class="sxs-lookup"><span data-stu-id="205b7-182">Examples of invalid template strings:</span></span>  
  
- <span data-ttu-id="205b7-183">"{ayakkabı} / {AYAKKABI} / x 2 =" – Yinelenen değişken adları.</span><span class="sxs-lookup"><span data-stu-id="205b7-183">"{shoe}/{SHOE}/x=2" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="205b7-184">"{ayakkabı} /boat/? yatak {ayakkabı} =" – Yinelenen değişken adları.</span><span class="sxs-lookup"><span data-stu-id="205b7-184">"{shoe}/boat/?bed={shoe}" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="205b7-185">"? x = 2 & x 3 =" – değişmez değerleri olsalar bile bir sorgu dizesi içinde ad/değer çiftleri benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="205b7-185">"?x=2&x=3" – Name/value pairs within a query string must be unique, even if they are literals.</span></span>  
  
- <span data-ttu-id="205b7-186">"? x 2 = &" – sorgu dizesi yanlış biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="205b7-186">"?x=2&" – Query string is malformed.</span></span>  
  
- <span data-ttu-id="205b7-187">"? 2 & x = {ayakkabı}" – ad/değer çiftleri sorgu dizesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="205b7-187">"?2&x={shoe}" – Query string must be name/value pairs.</span></span>  
  
- <span data-ttu-id="205b7-188">"? y = 2 & & X = 3" – adları ile başlayamaz, sorgu dizesi olmalıdır ad değer çiftleri '&'.</span><span class="sxs-lookup"><span data-stu-id="205b7-188">"?y=2&&X=3" – Query string must be name value pairs, names cannot start with '&'.</span></span>  
  
### <a name="compound-path-segments"></a><span data-ttu-id="205b7-189">Bileşik yol kesimleri</span><span class="sxs-lookup"><span data-stu-id="205b7-189">Compound Path Segments</span></span>  
 <span data-ttu-id="205b7-190">Bileşik yol kesimleri değişmez değerler ile birleştirilmiş değişkenleri yanı sıra birden çok değişkenleri içerecek şekilde tek bir URI yol kesimi izin verir.</span><span class="sxs-lookup"><span data-stu-id="205b7-190">Compound path segments allow a single URI path segment to contain multiple variables as well as variables combined with literals.</span></span> <span data-ttu-id="205b7-191">Geçerli bir bileşik yol kesimleri örnekleri aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="205b7-191">The following are examples of valid compound path segments.</span></span>  
  
- <span data-ttu-id="205b7-192">/filename. {ext} /</span><span class="sxs-lookup"><span data-stu-id="205b7-192">/filename.{ext}/</span></span>  
  
- <span data-ttu-id="205b7-193">/{filename}.jpg/</span><span class="sxs-lookup"><span data-stu-id="205b7-193">/{filename}.jpg/</span></span>  
  
- <span data-ttu-id="205b7-194">/ {filename}. {ext} /</span><span class="sxs-lookup"><span data-stu-id="205b7-194">/{filename}.{ext}/</span></span>  
  
- <span data-ttu-id="205b7-195">/ {bir}. {b}someLiteral{c}({d}) /</span><span class="sxs-lookup"><span data-stu-id="205b7-195">/{a}.{b}someLiteral{c}({d})/</span></span>  
  
 <span data-ttu-id="205b7-196">Geçersiz yol kesimleri örnekleri aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="205b7-196">The following are examples of invalid path segments.</span></span>  
  
- <span data-ttu-id="205b7-197">/{} -Değişkenler adlandırılmış.</span><span class="sxs-lookup"><span data-stu-id="205b7-197">/{} - Variables must be named.</span></span>  
  
- <span data-ttu-id="205b7-198">/ {ayakkabı} {bot} - değişkenleri, bir sabit değer ayrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="205b7-198">/{shoe}{boat} - Variables must be separated by a literal.</span></span>  
  
### <a name="matching-and-compound-path-segments"></a><span data-ttu-id="205b7-199">Eşleşen ve bileşik yol kesimleri</span><span class="sxs-lookup"><span data-stu-id="205b7-199">Matching and Compound Path Segments</span></span>  
 <span data-ttu-id="205b7-200">Bileşik yol kesimleri tek bir yol kesimi içinde birden fazla değişken olan UriTemplate tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="205b7-200">Compound path segments allow you to define a UriTemplate that has multiple variables within a single path segment.</span></span> <span data-ttu-id="205b7-201">Örneğin, aşağıdaki şablonu dizesi: "Adresleri / {state}. {Şehir} "(durumu ve şehir) iki değişken aynı kesim içinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="205b7-201">For example, in the following template string: "Addresses/{state}.{city}" two variables (state and city) are defined within the same segment.</span></span> <span data-ttu-id="205b7-202">Bu şablon bir URL gibi BC `http://example.com/Washington.Redmond` ancak gibi bir URL eşleşecektir `http://example.com/Washington.Redmond.Microsoft`.</span><span class="sxs-lookup"><span data-stu-id="205b7-202">This template would match a URL such as `http://example.com/Washington.Redmond` but it will also match an URL like `http://example.com/Washington.Redmond.Microsoft`.</span></span> <span data-ttu-id="205b7-203">İkinci durumda, "Washington" durumu değişkenini içerir ve "Redmond.Microsoft" Şehir değişkeni içerir.</span><span class="sxs-lookup"><span data-stu-id="205b7-203">In the latter case, the state variable will contain "Washington" and the city variable will contain "Redmond.Microsoft".</span></span> <span data-ttu-id="205b7-204">Bu durumda herhangi bir metin (dışında '/') {Şehir} değişkeni eşleşir.</span><span class="sxs-lookup"><span data-stu-id="205b7-204">In this case any text (except ‘/’) will match the {city} variable.</span></span> <span data-ttu-id="205b7-205">"Ek" metin eşleşmeyeceği bir şablon istiyorsanız, değişken içinde ayrı bir şablon segment, örneğin yerleştirin: "Adresleri / {state} / {şehir}.</span><span class="sxs-lookup"><span data-stu-id="205b7-205">If you want a template that will not match the "extra" text, place the variable in a separate template segment, for example: "Addresses/{state}/{city}.</span></span>  
  
### <a name="named-wildcard-segments"></a><span data-ttu-id="205b7-206">Adlandırılmış bir joker karakter segmentleri</span><span class="sxs-lookup"><span data-stu-id="205b7-206">Named Wildcard Segments</span></span>  
 <span data-ttu-id="205b7-207">Değişken adı joker karakteri ile başlayan yol değişkeni kesimini bir adlandırılmış joker segmenttir '\*'.</span><span class="sxs-lookup"><span data-stu-id="205b7-207">A named wildcard segment is any path variable segment whose variable name begins with the wildcard character ‘\*’.</span></span> <span data-ttu-id="205b7-208">Aşağıdaki şablonu dizesi "ayakkabı" adlı bir adlandırılmış bir joker karakter segmenti içerir.</span><span class="sxs-lookup"><span data-stu-id="205b7-208">The following template string contains a named wildcard segment named "shoe".</span></span>  
  
```  
"literal/{*shoe}"  
```  
  
 <span data-ttu-id="205b7-209">Joker karakter kesimleri, aşağıdaki kurallara uymalıdır:</span><span class="sxs-lookup"><span data-stu-id="205b7-209">Wildcard segments must follow the following rules:</span></span>  
  
- <span data-ttu-id="205b7-210">En fazla olabilir her şablon dizesi için bir adlandırılmış bir joker karakter segmenti.</span><span class="sxs-lookup"><span data-stu-id="205b7-210">There can be at most one named wildcard segment for each template string.</span></span>  
  
- <span data-ttu-id="205b7-211">Bir adlandırılmış bir joker karakter segmenti yolun en sağdaki kesimi sırasında yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="205b7-211">A named wildcard segment must appear at the right-most segment in the path.</span></span>  
  
- <span data-ttu-id="205b7-212">Bir adlandırılmış bir joker karakter segmenti aynı şablon dize içindeki bir anonim bir joker karakter segmenti ile bir arada bulunamaz.</span><span class="sxs-lookup"><span data-stu-id="205b7-212">A named wildcard segment cannot coexist with an anonymous wildcard segment within the same template string.</span></span>  
  
- <span data-ttu-id="205b7-213">Bir adlandırılmış bir joker karakter segmenti adı benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="205b7-213">The name of a named wildcard segment must be unique.</span></span>  
  
- <span data-ttu-id="205b7-214">Joker adlı segmentleri varsayılan değerlere sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="205b7-214">Named wildcard segments cannot have default values.</span></span>  
  
- <span data-ttu-id="205b7-215">Adlandırılmış bir joker karakter kesimleri ile bitemez "/".</span><span class="sxs-lookup"><span data-stu-id="205b7-215">Named wildcard segments cannot end with "/".</span></span>  
  
### <a name="default-variable-values"></a><span data-ttu-id="205b7-216">Varsayılan değişken değerleri</span><span class="sxs-lookup"><span data-stu-id="205b7-216">Default Variable Values</span></span>  
 <span data-ttu-id="205b7-217">Değişken değerleri varsayılan şablonu içindeki değişkenleri için varsayılan değerlere belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="205b7-217">Default variable values allow you to specify default values for variables within a template.</span></span> <span data-ttu-id="205b7-218">Varsayılan değişkenleri değişkenini tanımlamak ve küme ayraçlarının veya bir koleksiyon olarak belirtilebilir UriTemplate oluşturucuya geçirilen.</span><span class="sxs-lookup"><span data-stu-id="205b7-218">Default variables can be specified with the curly braces that declare the variable or as a collection passed to the UriTemplate constructor.</span></span> <span data-ttu-id="205b7-219">Aşağıdaki şablonu belirlemek için iki yolunu gösterir bir <xref:System.UriTemplate> varsayılan değerlerle değişkenleriyle.</span><span class="sxs-lookup"><span data-stu-id="205b7-219">The following template shows two ways to specify a <xref:System.UriTemplate> with variables with default values.</span></span>  
  
```csharp
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 <span data-ttu-id="205b7-220">Bu şablon adında bir değişken bildirir `a` varsayılan değerini `1` ve adlı bir değişken `b` varsayılan değerini `5`.</span><span class="sxs-lookup"><span data-stu-id="205b7-220">This template declares a variable named `a` with a default value of `1` and a variable named `b` with a default value of `5`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="205b7-221">Yalnızca yol kesimi değişkenleri varsayılan değerlere sahip izin verilir.</span><span class="sxs-lookup"><span data-stu-id="205b7-221">Only path segment variables are allowed to have default values.</span></span> <span data-ttu-id="205b7-222">Sorgu dizesi değişkenlerinin, bileşik bir segment değişkenleri ve adlandırılmış joker değişkenleri varsayılan değerlere sahip izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="205b7-222">Query string variables, compound segment variables, and named wildcard variables are not permitted to have default values.</span></span>  
  
 <span data-ttu-id="205b7-223">Aşağıdaki kod, bir aday URI eşleştirirken varsayılan değişken değerleri nasıl işleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="205b7-223">The following code shows how default variable values are handled when matching a candidate URI.</span></span>  
  
```csharp
Uri baseAddress = new Uri("http://localhost:8000/");

UriTemplate t = new UriTemplate("/{state=WA}/{city=Redmond}/", true);
Uri candidate = new Uri("http://localhost:8000/OR");

UriTemplateMatch m1 = t.Match(baseAddress, candidate);

Console.WriteLine($"Template: {t}");
Console.WriteLine($"Candidate URI: {candidate}");

// Display contents of BoundVariables
Console.WriteLine("BoundVariables:");
foreach (string key in m1.BoundVariables.AllKeys)
{
    Console.WriteLine($"\t{key}={m1.BoundVariables[key]}");
}
// The output of the above code is  
// Template: /{state=WA}/{city=Redmond}/
// Candidate URI: http://localhost:8000/OR
// BoundVariables:
//         STATE=OR
//         CITY=Redmond
```  
  
> [!NOTE]
> <span data-ttu-id="205b7-224">Bir URI gibi `http://localhost:8000///` önceki kodda, ancak listelenen şablonu eşleşmiyor gibi bir URI `http://localhost:8000/` yapar.</span><span class="sxs-lookup"><span data-stu-id="205b7-224">A URI such as `http://localhost:8000///` does not match the template listed in the preceding code, however a URI such as `http://localhost:8000/` does.</span></span>  
  
 <span data-ttu-id="205b7-225">Aşağıdaki kod, bir URI ile bir şablon oluştururken varsayılan değişken değerleri nasıl işleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="205b7-225">The following code shows how default variable values are handled when creating a URI with a template.</span></span>  
  
```csharp
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
  
<span data-ttu-id="205b7-226">Ne zaman bir değişkeni verilir varsayılan değerini `null` bazı ek kısıtlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="205b7-226">When a variable is given a default value of `null` there are some additional constraints.</span></span> <span data-ttu-id="205b7-227">Bir değişken varsayılan değerine sahip olabilir `null` değişken şablon dizesi doğru çoğu Segmentte içeriyorsa veya segment sağındaki tüm parçaları varsayılan değerleri varsa `null`.</span><span class="sxs-lookup"><span data-stu-id="205b7-227">A variable can have a default value of `null` if the variable is contained within the right most segment of the template string or if all segments to the right of the segment have default values of `null`.</span></span> <span data-ttu-id="205b7-228">Varsayılan değerleri ile geçerli şablon dizeleri şunlardır `null`:</span><span class="sxs-lookup"><span data-stu-id="205b7-228">The following are valid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("shoe/{boat=null}");`

- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");`
  
- `UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");`

 <span data-ttu-id="205b7-229">Varsayılan değerler ile geçersiz şablon dizeleri şunlardır `null`:</span><span class="sxs-lookup"><span data-stu-id="205b7-229">The following are invalid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment`
  
- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value`

### <a name="default-values-and-matching"></a><span data-ttu-id="205b7-230">Varsayılan değerleri ve eşleştirme</span><span class="sxs-lookup"><span data-stu-id="205b7-230">Default Values and Matching</span></span>  
 <span data-ttu-id="205b7-231">Bir aday URI varsayılan değerlere sahip bir şablon ile eşleştirme yapılırken varsayılan değerleri yerleştirilir <xref:System.UriTemplateMatch.BoundVariables%2A> değerleri adayı URI'nda belirtilmezse koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="205b7-231">When matching a candidate URI with a template that has default values, the default values are placed in the <xref:System.UriTemplateMatch.BoundVariables%2A> collection if values are not specified in the candidate URI.</span></span>  
  
### <a name="template-equivalence"></a><span data-ttu-id="205b7-232">Şablon eşdeğerlik</span><span class="sxs-lookup"><span data-stu-id="205b7-232">Template Equivalence</span></span>  
 <span data-ttu-id="205b7-233">İki şablon söylediğiniz olmasını *yapısal olarak eşdeğer* aynı segmentler değişkenleriniz ve ne zaman tüm şablonları değişmez değerleri eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="205b7-233">Two templates are said to be *structurally equivalent* when all of the templates' literals match and they have variables in the same segments.</span></span> <span data-ttu-id="205b7-234">Örneğin aşağıdaki şablonlardan yapısal olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="205b7-234">For example the following templates are structurally equivalent:</span></span>  
  
- <span data-ttu-id="205b7-235">/b b /a/ {var1} / {var2}? x = 1 & y = 2</span><span class="sxs-lookup"><span data-stu-id="205b7-235">/a/{var1}/b b/{var2}?x=1&y=2</span></span>  
  
- <span data-ttu-id="205b7-236">a/{x}/b%20b/{var1}?y=2&x=1</span><span class="sxs-lookup"><span data-stu-id="205b7-236">a/{x}/b%20b/{var1}?y=2&x=1</span></span>  
  
- <span data-ttu-id="205b7-237">a/{y}/B%20B/{z}/?y=2&x=1</span><span class="sxs-lookup"><span data-stu-id="205b7-237">a/{y}/B%20B/{z}/?y=2&x=1</span></span>  
  
 <span data-ttu-id="205b7-238">Fark gereken bazı noktalar:</span><span class="sxs-lookup"><span data-stu-id="205b7-238">A few things to notice:</span></span>  
  
- <span data-ttu-id="205b7-239">Bir şablon önde gelen eğik çizgiler içeriyorsa, yalnızca ilki göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="205b7-239">If a template contains leading slashes, only the first one is ignored.</span></span>  
  
- <span data-ttu-id="205b7-240">Yapısal denklik için şablon dizeleri karşılaştırırken çalışması için değişken adları yok sayılır ve yol kesimleri, sorgu dizeleri büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="205b7-240">When comparing template strings for structural equivalence, case is ignored for variable names and path segments, query strings are case sensitive.</span></span>  
  
- <span data-ttu-id="205b7-241">Sorgu dizeleri, sırasız.</span><span class="sxs-lookup"><span data-stu-id="205b7-241">Query strings are unordered.</span></span>  
  
## <a name="uritemplatetable"></a><span data-ttu-id="205b7-242">UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="205b7-242">UriTemplateTable</span></span>  
 <span data-ttu-id="205b7-243"><xref:System.UriTemplateTable> Sınıfı temsil eder, ilişkili bir tablosu <xref:System.UriTemplate> bağlı olan nesneleri geliştirici bir nesne seçme.</span><span class="sxs-lookup"><span data-stu-id="205b7-243">The <xref:System.UriTemplateTable> class represents an associative table of <xref:System.UriTemplate> objects bound to an object of the developer's choosing.</span></span> <span data-ttu-id="205b7-244">A <xref:System.UriTemplateTable> en az bir içeren <xref:System.UriTemplate> çağrılmadan önce <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="205b7-244">A <xref:System.UriTemplateTable> must contain at least one <xref:System.UriTemplate> prior to calling <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span> <span data-ttu-id="205b7-245">İçeriği bir <xref:System.UriTemplateTable> kadar değiştirilebilir <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> çağrılır.</span><span class="sxs-lookup"><span data-stu-id="205b7-245">The contents of a <xref:System.UriTemplateTable> can be changed until <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="205b7-246">Doğrulama işlemi gerçekleştirildiğinde, <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> çağrılır.</span><span class="sxs-lookup"><span data-stu-id="205b7-246">Validation is performed when <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="205b7-247">Değerin doğrulaması türüne bağlıdır `allowMultiple` parametresi <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="205b7-247">The type of validation performed depends upon the value of the `allowMultiple` parameter to <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span>  
  
 <span data-ttu-id="205b7-248">Zaman <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> tümleştirilmesidir adlı `false`, <xref:System.UriTemplateTable> denetler tablosunda hiçbir şablon olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="205b7-248">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `false`, the <xref:System.UriTemplateTable> checks to make sure there are no templates in the table.</span></span> <span data-ttu-id="205b7-249">Bu yapısal olarak eşdeğer herhangi bir şablon bulunursa, bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="205b7-249">If it finds any structurally equivalent templates, it throws an exception.</span></span> <span data-ttu-id="205b7-250">Bu ile birlikte kullanılan <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> yalnızca tek bir şablonda sağlamak istediğinizde bir gelen URI ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="205b7-250">This is used in conjunction with <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> when you want to ensure only one template matches an incoming URI.</span></span>  
  
 <span data-ttu-id="205b7-251">Zaman <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> tümleştirilmesidir adlı `true`, <xref:System.UriTemplateTable> birden çok, yapısal olarak eşdeğer şablonlarını kapsamında yer alan bir <xref:System.UriTemplateTable>.</span><span class="sxs-lookup"><span data-stu-id="205b7-251">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `true`, <xref:System.UriTemplateTable> allows multiple, structurally-equivalent templates to be contained within a <xref:System.UriTemplateTable>.</span></span>  
  
 <span data-ttu-id="205b7-252">Bir dizi <xref:System.UriTemplate> eklenen nesneleri bir <xref:System.UriTemplateTable> bunlar olmamalıdır belirsiz sorgu dizelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="205b7-252">If a set of <xref:System.UriTemplate> objects added to a <xref:System.UriTemplateTable> contain query strings they must not be ambiguous.</span></span> <span data-ttu-id="205b7-253">Aynı sorgu dizelerine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="205b7-253">Identical query strings are allowed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="205b7-254">Sırada <xref:System.UriTemplateTable> temel adreslerinin dışındaki HTTP düzenini, kullanım düzenleri ve bağlantı noktası numarası yok sayılır şablonları için aday URI'ler eşleştirirken sağlar.</span><span class="sxs-lookup"><span data-stu-id="205b7-254">While the <xref:System.UriTemplateTable> allows base addresses that use schemes other than HTTP, the scheme and port number are ignored when matching candidate URIs to templates.</span></span>  
  
### <a name="query-string-ambiguity"></a><span data-ttu-id="205b7-255">Sorgu dizesi belirsizlik</span><span class="sxs-lookup"><span data-stu-id="205b7-255">Query String Ambiguity</span></span>  
 <span data-ttu-id="205b7-256">Birden fazla şablon eşleşen bir URI ise paylaşımına eşdeğer bir yol şablonları belirsiz sorgu dizelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="205b7-256">Templates that share an equivalent path contain ambiguous query strings if there is a URI that matches more than one template.</span></span>  
  
 <span data-ttu-id="205b7-257">Sorgu dizeleri aşağıdaki kümesi içinde kendilerini durumdaysalar:</span><span class="sxs-lookup"><span data-stu-id="205b7-257">The following sets of query strings are unambiguous within themselves:</span></span>  
  
- <span data-ttu-id="205b7-258">?x=1</span><span class="sxs-lookup"><span data-stu-id="205b7-258">?x=1</span></span>  
  
- <span data-ttu-id="205b7-259">?x=2</span><span class="sxs-lookup"><span data-stu-id="205b7-259">?x=2</span></span>  
  
- <span data-ttu-id="205b7-260">?x=3</span><span class="sxs-lookup"><span data-stu-id="205b7-260">?x=3</span></span>  
  
- <span data-ttu-id="205b7-261">?x=1&y={var}</span><span class="sxs-lookup"><span data-stu-id="205b7-261">?x=1&y={var}</span></span>  
  
- <span data-ttu-id="205b7-262">?x=2&z={var}</span><span class="sxs-lookup"><span data-stu-id="205b7-262">?x=2&z={var}</span></span>  
  
- <span data-ttu-id="205b7-263">?x=3</span><span class="sxs-lookup"><span data-stu-id="205b7-263">?x=3</span></span>  
  
- <span data-ttu-id="205b7-264">?x=1</span><span class="sxs-lookup"><span data-stu-id="205b7-264">?x=1</span></span>  
  
- <span data-ttu-id="205b7-265">?</span><span class="sxs-lookup"><span data-stu-id="205b7-265">?</span></span>  
  
- <span data-ttu-id="205b7-266">?</span><span class="sxs-lookup"><span data-stu-id="205b7-266">?</span></span> <span data-ttu-id="205b7-267">x={var}</span><span class="sxs-lookup"><span data-stu-id="205b7-267">x={var}</span></span>  
  
- <span data-ttu-id="205b7-268">?</span><span class="sxs-lookup"><span data-stu-id="205b7-268">?</span></span>  
  
- <span data-ttu-id="205b7-269">? m = get & c rss =</span><span class="sxs-lookup"><span data-stu-id="205b7-269">?m=get&c=rss</span></span>  
  
- <span data-ttu-id="205b7-270">? m = put & c rss =</span><span class="sxs-lookup"><span data-stu-id="205b7-270">?m=put&c=rss</span></span>  
  
- <span data-ttu-id="205b7-271">? m = get & c atom =</span><span class="sxs-lookup"><span data-stu-id="205b7-271">?m=get&c=atom</span></span>  
  
- <span data-ttu-id="205b7-272">? m = put & c atom =</span><span class="sxs-lookup"><span data-stu-id="205b7-272">?m=put&c=atom</span></span>  
  
 <span data-ttu-id="205b7-273">Aşağıdaki sorgu dizesi şablonları kümesi içinde kendilerini belirsizdir:</span><span class="sxs-lookup"><span data-stu-id="205b7-273">The following sets of query string templates are ambiguous within themselves:</span></span>  
  
- <span data-ttu-id="205b7-274">?x=1</span><span class="sxs-lookup"><span data-stu-id="205b7-274">?x=1</span></span>  
  
- <span data-ttu-id="205b7-275">?x={var}</span><span class="sxs-lookup"><span data-stu-id="205b7-275">?x={var}</span></span>  
  
 <span data-ttu-id="205b7-276">"x = 1"-iki şablon eşleşir.</span><span class="sxs-lookup"><span data-stu-id="205b7-276">"x=1" - Matches both templates.</span></span>  
  
- <span data-ttu-id="205b7-277">?x=1</span><span class="sxs-lookup"><span data-stu-id="205b7-277">?x=1</span></span>  
  
- <span data-ttu-id="205b7-278">? y = 2</span><span class="sxs-lookup"><span data-stu-id="205b7-278">?y=2</span></span>  
  
 <span data-ttu-id="205b7-279">"x = 1 & y = 2" iki şablon eşleşir.</span><span class="sxs-lookup"><span data-stu-id="205b7-279">"x=1&y=2" matches both templates.</span></span> <span data-ttu-id="205b7-280">Şablon ile eşleşen sonra daha fazla sorgu dizesi değişkenlerinin bir sorgu dizesi içerebilir olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="205b7-280">This is because a query string may contain more query string variables then the template it matches.</span></span>  
  
- <span data-ttu-id="205b7-281">?x=1</span><span class="sxs-lookup"><span data-stu-id="205b7-281">?x=1</span></span>  
  
- <span data-ttu-id="205b7-282">?x=1&y={var}</span><span class="sxs-lookup"><span data-stu-id="205b7-282">?x=1&y={var}</span></span>  
  
 <span data-ttu-id="205b7-283">"x = 1 & y 3 =" iki şablon eşleşir.</span><span class="sxs-lookup"><span data-stu-id="205b7-283">"x=1&y=3" matches both templates.</span></span>  
  
- <span data-ttu-id="205b7-284">?x=3&y=4</span><span class="sxs-lookup"><span data-stu-id="205b7-284">?x=3&y=4</span></span>  
  
- <span data-ttu-id="205b7-285">?x=3&z=5</span><span class="sxs-lookup"><span data-stu-id="205b7-285">?x=3&z=5</span></span>  
  
> [!NOTE]
> <span data-ttu-id="205b7-286">Karakter á ve Á bir URI yolu bir parçası olarak görünürler, farklı karakterler olarak değerlendirilir veya <xref:System.UriTemplate> yol kesimi değişmez değer (ancak karakterler a ve A ile aynı olarak kabul edilir).</span><span class="sxs-lookup"><span data-stu-id="205b7-286">The characters á and Á are considered to be different characters when they appear as part of a URI path or <xref:System.UriTemplate> path segment literal (but the characters a and A are considered to be the same).</span></span> <span data-ttu-id="205b7-287">Karakter á ve Á bir parçası olarak görünürler, aynı karakterler olarak değerlendirilir <xref:System.UriTemplate> {variableName} ya da bir sorgu dizesi (ve a ve bir de kabul edilir aynı karakterler olabilir).</span><span class="sxs-lookup"><span data-stu-id="205b7-287">The characters á and Á are considered to be the same characters when they appear as part of a <xref:System.UriTemplate> {variableName} or a query string (and a and A are also considered to be the same characters).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="205b7-288">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="205b7-288">See also</span></span>

- [<span data-ttu-id="205b7-289">WCF Web HTTP Programlama Modeli Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="205b7-289">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="205b7-290">WCF Web HTTP Programlama Nesnesi Modeli</span><span class="sxs-lookup"><span data-stu-id="205b7-290">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [<span data-ttu-id="205b7-291">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="205b7-291">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
- [<span data-ttu-id="205b7-292">UriTemplate Tablosu</span><span class="sxs-lookup"><span data-stu-id="205b7-292">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="205b7-293">UriTemplate Tablosu Dağıtıcısı</span><span class="sxs-lookup"><span data-stu-id="205b7-293">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
