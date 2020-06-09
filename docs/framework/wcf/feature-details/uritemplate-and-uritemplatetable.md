---
title: UriTemplate ve UriTemplateTable
ms.date: 03/30/2017
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
ms.openlocfilehash: 106ba21b58dabab96afbc8fb6db5cb305386f2fe
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595082"
---
# <a name="uritemplate-and-uritemplatetable"></a><span data-ttu-id="ce6e1-102">UriTemplate ve UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="ce6e1-102">UriTemplate and UriTemplateTable</span></span>
<span data-ttu-id="ce6e1-103">Web geliştiricileri, hizmetlerinin yanıt verdiği URI 'lerin şeklini ve yerleşimini betimleyebilme olanağı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-103">Web developers require the ability to describe the shape and layout of the URIs that their services respond to.</span></span> <span data-ttu-id="ce6e1-104">Windows Communication Foundation (WCF), geliştiricilerin URI 'lerinde denetim sağlamak için iki yeni sınıf ekledi.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-104">Windows Communication Foundation (WCF) added two new classes to give developers control over their URIs.</span></span> <span data-ttu-id="ce6e1-105"><xref:System.UriTemplate>ve <xref:System.UriTemplateTable> WCF 'de URI tabanlı dağıtım altyapısının temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-105"><xref:System.UriTemplate> and <xref:System.UriTemplateTable> form the basis of the URI-based dispatch engine in WCF.</span></span> <span data-ttu-id="ce6e1-106">Bu sınıflar kendi kendilerine de kullanılabilir, geliştiricilerin bir WCF hizmeti uygulamadan şablonlardan ve URI eşleme mekanizmasından yararlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-106">These classes can also be used on their own, allowing developers to take advantage of templates and the URI mapping mechanism without implementing a WCF service.</span></span>  
  
## <a name="templates"></a><span data-ttu-id="ce6e1-107">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="ce6e1-107">Templates</span></span>  
 <span data-ttu-id="ce6e1-108">Şablon, göreli URI 'lerin bir kümesini tanımlamaya yönelik bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-108">A template is a way to describe a set of relative URIs.</span></span> <span data-ttu-id="ce6e1-109">Aşağıdaki tabloda yer alan URI şablonları kümesi, çeşitli hava durumu bilgilerini alan bir sistemin nasıl tanımlanabilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-109">The set of URI templates in the following table shows how a system that retrieves various types of weather information might be defined.</span></span>  
  
|<span data-ttu-id="ce6e1-110">Veriler</span><span class="sxs-lookup"><span data-stu-id="ce6e1-110">Data</span></span>|<span data-ttu-id="ce6e1-111">Şablon</span><span class="sxs-lookup"><span data-stu-id="ce6e1-111">Template</span></span>|  
|----------|--------------|  
|<span data-ttu-id="ce6e1-112">Ulusal tahmin</span><span class="sxs-lookup"><span data-stu-id="ce6e1-112">National Forecast</span></span>|<span data-ttu-id="ce6e1-113">Hava durumu/Ulusal</span><span class="sxs-lookup"><span data-stu-id="ce6e1-113">weather/national</span></span>|  
|<span data-ttu-id="ce6e1-114">Durum tahmini</span><span class="sxs-lookup"><span data-stu-id="ce6e1-114">State Forecast</span></span>|<span data-ttu-id="ce6e1-115">Hava durumu/{State}</span><span class="sxs-lookup"><span data-stu-id="ce6e1-115">weather/{state}</span></span>|  
|<span data-ttu-id="ce6e1-116">Şehir tahmini</span><span class="sxs-lookup"><span data-stu-id="ce6e1-116">City Forecast</span></span>|<span data-ttu-id="ce6e1-117">Hava durumu/{State}/{City}</span><span class="sxs-lookup"><span data-stu-id="ce6e1-117">weather/{state}/{city}</span></span>|  
|<span data-ttu-id="ce6e1-118">Etkinlik tahmini</span><span class="sxs-lookup"><span data-stu-id="ce6e1-118">Activity Forecast</span></span>|<span data-ttu-id="ce6e1-119">Hava durumu/{State}/{City}/{Activity}</span><span class="sxs-lookup"><span data-stu-id="ce6e1-119">weather/{state}/{city}/{activity}</span></span>|  
  
 <span data-ttu-id="ce6e1-120">Bu tablo yapısal olarak benzer URI 'Ler kümesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-120">This table describes a set of structurally similar URIs.</span></span> <span data-ttu-id="ce6e1-121">Her giriş bir URI şablonudur.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-121">Each entry is a URI template.</span></span> <span data-ttu-id="ce6e1-122">Küme ayraçları içindeki segmentler değişkenleri anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-122">The segments in curly braces describe variables.</span></span> <span data-ttu-id="ce6e1-123">Küme ayraçları içinde olmayan kesimler, değişmez dizeleri tanımlıyor.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-123">The segments not in curly braces describe literal strings.</span></span> <span data-ttu-id="ce6e1-124">WCF şablon sınıfları, bir geliştiricinin gelen URI 'yi (örneğin, "/Weather/WA/Seattle/Cycling") alıp onu açıklayan bir şablonla eşleştirmek için "/dalgalı ther/{State}/{City}/{Activity}" sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-124">The WCF template classes allow a developer to take an incoming URI, for example, "/weather/wa/seattle/cycling", and match it to a template that describes it, "/weather/{state}/{city}/{activity}".</span></span>  
  
## <a name="uritemplate"></a><span data-ttu-id="ce6e1-125">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="ce6e1-125">UriTemplate</span></span>  
 <span data-ttu-id="ce6e1-126"><xref:System.UriTemplate>, bir URI şablonunu kapsülleyen bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-126"><xref:System.UriTemplate> is a class that encapsulates a URI template.</span></span> <span data-ttu-id="ce6e1-127">Oluşturucu, şablonu tanımlayan bir dize parametresi alır.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-127">The constructor takes a string parameter that defines the template.</span></span> <span data-ttu-id="ce6e1-128">Bu dize, sonraki bölümde açıklanan biçimdeki şablonu içerir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-128">This string contains the template in the format described in the next section.</span></span> <span data-ttu-id="ce6e1-129">Sınıfı, bir <xref:System.UriTemplate> şablon için gelen URI 'yi eşleştirmek, bir ŞABLONDAN URI oluşturmak, şablonda kullanılan değişken adlarından oluşan bir koleksiyonu almak, iki şablonun eşdeğer olup olmadığını tespit etmek ve şablonun dizesini döndürmeksizin yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-129">The <xref:System.UriTemplate> class provides methods that allow you match an incoming URI to a template, generate a URI from a template, retrieve a collection of variable names used in the template, determine whether two templates are equivalent, and return the template's string.</span></span>  
  
 <span data-ttu-id="ce6e1-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29>temel bir adresi ve aday URI 'yi alır ve URI 'yi şablonla eşleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> takes a base address and a candidate URI and attempts to match the URI to the template.</span></span> <span data-ttu-id="ce6e1-131">Eşleşme başarılı olursa bir <xref:System.UriTemplateMatch> örnek döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-131">If the match is successful, a <xref:System.UriTemplateMatch> instance is returned.</span></span> <span data-ttu-id="ce6e1-132"><xref:System.UriTemplateMatch>Nesne bir temel URI içerir, aday URI, sorgu parametrelerinin ad/değer koleksiyonu, göreli yol segmentlerinin bir dizisi, eşleşen değişkenlerin bir adı/değer koleksiyonu, <xref:System.UriTemplate> karşılamanın yerine getirmek için kullanılan örnek, aday URI 'sinin eşleşmeyen herhangi bir bölümünü (şablon bir joker karakter olduğunda kullanılır) ve şablonla ilişkili bir nesneyi içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-132">The <xref:System.UriTemplateMatch> object contains a base URI, the candidate URI, a name/value collection of the query parameters, an array of the relative path segments, a name/value collection of variables that were matched, the <xref:System.UriTemplate> instance used to perform the match, a string that contains any unmatched portion of the candidate URI (used when the template has a wildcard), and an object that is associated with the template.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce6e1-133"><xref:System.UriTemplate>Sınıf, bir aday URI 'yi bir şablonla eşleştirirken düzen ve bağlantı noktası numarasını yoksayar.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-133">The <xref:System.UriTemplate> class ignores the scheme and port number when matching a candidate URI to a template.</span></span>  
  
 <span data-ttu-id="ce6e1-134">Bir şablondan URI oluşturmanıza izin veren iki yöntem vardır <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> ve <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> .</span><span class="sxs-lookup"><span data-stu-id="ce6e1-134">There are two methods that allow you to generate a URI from a template, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> and <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span></span> <span data-ttu-id="ce6e1-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29>bir taban adresi ve parametrelerin ad/değer koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> takes a base address and a name/value collection of parameters.</span></span> <span data-ttu-id="ce6e1-136">Bu parametreler, şablon bağlandığında değişkenler için değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-136">These parameters are substituted for variables when the template is bound.</span></span> <span data-ttu-id="ce6e1-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>ad/değer çiftlerini alır ve bunları soldan sağa koyar.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> takes the name/value pairs and substitutes them left to right.</span></span>  
  
 <span data-ttu-id="ce6e1-138"><xref:System.UriTemplate.ToString>Şablon dizesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-138"><xref:System.UriTemplate.ToString> returns the template string.</span></span>  
  
 <span data-ttu-id="ce6e1-139"><xref:System.UriTemplate.PathSegmentVariableNames%2A>Özelliği, şablon dizesindeki yol kesimleri içinde kullanılan değişkenlerin adlarının bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-139">The <xref:System.UriTemplate.PathSegmentVariableNames%2A> property contains a collection of the names of the variables used within path segments in the template string.</span></span>  
  
 <span data-ttu-id="ce6e1-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29>bir <xref:System.UriTemplate> parametresini parametre olarak alır ve iki şablonun eşdeğer olup olmadığını belirten bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> takes a <xref:System.UriTemplate> as a parameter and returns a Boolean value that specifies whether the two templates are equivalent.</span></span> <span data-ttu-id="ce6e1-141">Daha fazla bilgi için bu konunun ilerleyen kısımlarında yer alarak şablon denklik bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-141">For more information, see the Template Equivalence section later in this topic.</span></span>  
  
 <span data-ttu-id="ce6e1-142"><xref:System.UriTemplate>, HTTP URI dilbilgisine uygun herhangi bir URI şeması ile çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-142"><xref:System.UriTemplate> is designed to work with any URI scheme that conforms to the HTTP URI grammar.</span></span> <span data-ttu-id="ce6e1-143">Aşağıda desteklenen URI düzenlerinin örnekleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-143">The following are examples of supported URI schemes.</span></span>  
  
- `http://`  
  
- `https://`  
  
- `net.tcp://`  
  
- `net.pipe://`  
  
- `sb://`  
  
 <span data-ttu-id="ce6e1-144">File://ve urn://gibi düzenler HTTP URI dilbilgisine uymuyor ve URI şablonlarıyla birlikte kullanıldığında öngörülemeyen sonuçlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-144">Schemes like file:// and urn:// do not conform to the HTTP URI grammar and cause unpredictable results when used with URI templates.</span></span>  
  
### <a name="template-string-syntax"></a><span data-ttu-id="ce6e1-145">Şablon dizesi sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce6e1-145">Template String Syntax</span></span>  
 <span data-ttu-id="ce6e1-146">Şablon üç bölümden oluşur: yol, isteğe bağlı sorgu ve isteğe bağlı bir parça.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-146">A template has three parts: a path, an optional query, and an optional fragment.</span></span> <span data-ttu-id="ce6e1-147">Bir örnek için, aşağıdaki şablona bakın:</span><span class="sxs-lookup"><span data-stu-id="ce6e1-147">For an example, see the following template:</span></span>  
  
`"/weather/{state}/{city}?forecast={length)#frag1`  
  
 <span data-ttu-id="ce6e1-148">Yol "/dalgalı ther/{State}/{City}" bilgisinden oluşur, sorgu "? tahmine = {length} ve parça" #frag1 "bilgisinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-148">The path consists of "/weather/{state}/{city}", the query consists of "?forecast={length}, and the fragment consists of "#frag1".</span></span>  
  
 <span data-ttu-id="ce6e1-149">Yol ifadesinde öndeki ve sondaki eğik çizgiler isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-149">Leading and trailing slashes are optional in the path expression.</span></span> <span data-ttu-id="ce6e1-150">Hem sorgu hem de parça ifadeleri tamamen atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-150">Both the query and fragment expressions can be omitted entirely.</span></span> <span data-ttu-id="ce6e1-151">Bir yol, '/' ile ayrılmış bir dizi kesimden oluşur, her segment bir sabit değer, değişken adı ({küme ayraçları} içinde yazılmış) veya joker karakter (' ' olarak yazılmış \* ) olabilir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-151">A path consists of a series of segments delimited by '/', each segment can have a literal value, a variable name (written in {curly braces}), or a wildcard (written as '\*').</span></span> <span data-ttu-id="ce6e1-152">Önceki şablonda, "{State}" ve "{City}" değişkenleri olan "\dalgalı ther\ segmenti değişmez değer değeridir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-152">In the previous template the "\weather\ segment is a literal value while "{state}" and "{city}" are variables.</span></span> <span data-ttu-id="ce6e1-153">Değişkenler, bunların adlarını kendi küme ayraçları içeriğinden alır ve daha sonra *kapalı bır URI*oluşturmak için somut bir değer ile değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-153">Variables take their name from the contents of their curly braces and they can later be replaced with a concrete value to create a *closed URI*.</span></span> <span data-ttu-id="ce6e1-154">Joker karakter isteğe bağlıdır, ancak yalnızca URI sonunda görünebilir, burada "yolun geri kalanı" ile mantıksal olarak eşleşir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-154">The wildcard is optional, but can only appear at the end of the URI, where it logically matches "the rest of the path".</span></span>  
  
 <span data-ttu-id="ce6e1-155">Sorgu ifadesi varsa, ' & ' ile ayrılmış bir sıralı ad/değer çiftleri serisi belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-155">The query expression, if present, specifies a series of unordered name/value pairs delimited by '&'.</span></span> <span data-ttu-id="ce6e1-156">Sorgu ifadesinin öğeleri, sabit değer çiftleri (x = 2) veya bir değişken çifti (x = {var}) olabilir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-156">Elements of the query expression can either be literal pairs (x=2) or a variable pair (x={var}).</span></span> <span data-ttu-id="ce6e1-157">Sorgunun yalnızca sağ tarafında bir değişken ifadesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-157">Only the right side of the query can have a variable expression.</span></span> <span data-ttu-id="ce6e1-158">({someName} = {someValue} öğesine izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-158">({someName} = {someValue} is not allowed.</span></span> <span data-ttu-id="ce6e1-159">Eşlenmemiş değerlere (? x) izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-159">Unpaired values (?x) are not permitted.</span></span> <span data-ttu-id="ce6e1-160">Boş bir sorgu ifadesi ve yalnızca tek bir '? ' içeren bir sorgu ifadesi arasında fark yoktur (her ikisi de "herhangi bir sorgu").</span><span class="sxs-lookup"><span data-stu-id="ce6e1-160">There is no difference between an empty query expression and a query expression consisting of just a single '?' (both mean "any query").</span></span>  
  
 <span data-ttu-id="ce6e1-161">Parça ifadesi bir değişmez değerden oluşabilir, hiçbir değişkene izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-161">The fragment expression can consist of a literal value, no variables are allowed.</span></span>  
  
 <span data-ttu-id="ce6e1-162">Bir şablon dizesi içindeki tüm şablon değişken adları benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-162">All template variable names within a template string must be unique.</span></span> <span data-ttu-id="ce6e1-163">Şablon değişken adları büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-163">Template variable names are case-insensitive.</span></span>  
  
 <span data-ttu-id="ce6e1-164">Geçerli şablon dizeleri örnekleri:</span><span class="sxs-lookup"><span data-stu-id="ce6e1-164">Examples of valid template strings:</span></span>  
  
- <span data-ttu-id="ce6e1-165">""</span><span class="sxs-lookup"><span data-stu-id="ce6e1-165">""</span></span>  
  
- <span data-ttu-id="ce6e1-166">"/Shoe"</span><span class="sxs-lookup"><span data-stu-id="ce6e1-166">"/shoe"</span></span>  
  
- <span data-ttu-id="ce6e1-167">"/Shoe/ \* "</span><span class="sxs-lookup"><span data-stu-id="ce6e1-167">"/shoe/\*"</span></span>  
  
- <span data-ttu-id="ce6e1-168">"{Shoe}/bot"</span><span class="sxs-lookup"><span data-stu-id="ce6e1-168">"{shoe}/boat"</span></span>  
  
- <span data-ttu-id="ce6e1-169">"{Shoe}/{Boat}/Bed/{Quilt}"</span><span class="sxs-lookup"><span data-stu-id="ce6e1-169">"{shoe}/{boat}/bed/{quilt}"</span></span>  
  
- <span data-ttu-id="ce6e1-170">"Shoe/{bot}"</span><span class="sxs-lookup"><span data-stu-id="ce6e1-170">"shoe/{boat}"</span></span>  
  
- <span data-ttu-id="ce6e1-171">"Shoe/{bot}/ \* "</span><span class="sxs-lookup"><span data-stu-id="ce6e1-171">"shoe/{boat}/\*"</span></span>  
  
- <span data-ttu-id="ce6e1-172">"Shoe/bot? x = 2"</span><span class="sxs-lookup"><span data-stu-id="ce6e1-172">"shoe/boat?x=2"</span></span>  
  
- <span data-ttu-id="ce6e1-173">"Shoe/{bot}? x = {yatak}"</span><span class="sxs-lookup"><span data-stu-id="ce6e1-173">"shoe/{boat}?x={bed}"</span></span>  
  
- <span data-ttu-id="ce6e1-174">"Shoe/{bot}? x = {yatak} &y = bant"</span><span class="sxs-lookup"><span data-stu-id="ce6e1-174">"shoe/{boat}?x={bed}&y=band"</span></span>  
  
- <span data-ttu-id="ce6e1-175">"? x = {Shoe}"</span><span class="sxs-lookup"><span data-stu-id="ce6e1-175">"?x={shoe}"</span></span>  
  
- <span data-ttu-id="ce6e1-176">"Shoe? x = 3&y = {var}</span><span class="sxs-lookup"><span data-stu-id="ce6e1-176">"shoe?x=3&y={var}</span></span>  
  
 <span data-ttu-id="ce6e1-177">Geçersiz şablon dizeleri örnekleri:</span><span class="sxs-lookup"><span data-stu-id="ce6e1-177">Examples of invalid template strings:</span></span>  
  
- <span data-ttu-id="ce6e1-178">"{Shoe}/{SHOE}/x = 2" – yinelenen değişken adları.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-178">"{shoe}/{SHOE}/x=2" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="ce6e1-179">"{Shoe}/Boat/? yatak = {Shoe}"-yinelenen değişken adları.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-179">"{shoe}/boat/?bed={shoe}" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="ce6e1-180">"? x = 2&x = 3" – bir sorgu dizesi içindeki ad/değer çiftleri, değişmez değerler olsa bile benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-180">"?x=2&x=3" – Name/value pairs within a query string must be unique, even if they are literals.</span></span>  
  
- <span data-ttu-id="ce6e1-181">"? x = 2&" – sorgu dizesi hatalı biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-181">"?x=2&" – Query string is malformed.</span></span>  
  
- <span data-ttu-id="ce6e1-182">"? 2&x = {Shoe}" – sorgu dizesi ad/değer çiftleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-182">"?2&x={shoe}" – Query string must be name/value pairs.</span></span>  
  
- <span data-ttu-id="ce6e1-183">"? y = 2&&X = 3" – sorgu dizesi ad değer çiftleri olmalıdır, adlar ' & ' ile başlayamaz.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-183">"?y=2&&X=3" – Query string must be name value pairs, names cannot start with '&'.</span></span>  
  
### <a name="compound-path-segments"></a><span data-ttu-id="ce6e1-184">Bileşik yol kesimleri</span><span class="sxs-lookup"><span data-stu-id="ce6e1-184">Compound Path Segments</span></span>  
 <span data-ttu-id="ce6e1-185">Bileşik yol kesimleri, tek bir URI yol segmentinin birden çok değişken ve değişmez değerler ile birleştirilmiş değişkenler içermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-185">Compound path segments allow a single URI path segment to contain multiple variables as well as variables combined with literals.</span></span> <span data-ttu-id="ce6e1-186">Aşağıda geçerli bileşik yol segmentlerinin örnekleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-186">The following are examples of valid compound path segments.</span></span>  
  
- <span data-ttu-id="ce6e1-187">kısaltın. {ext}/</span><span class="sxs-lookup"><span data-stu-id="ce6e1-187">/filename.{ext}/</span></span>  
  
- <span data-ttu-id="ce6e1-188">/{filename}.exe jpg/</span><span class="sxs-lookup"><span data-stu-id="ce6e1-188">/{filename}.jpg/</span></span>  
  
- <span data-ttu-id="ce6e1-189">kısaltın. {ext}/</span><span class="sxs-lookup"><span data-stu-id="ce6e1-189">/{filename}.{ext}/</span></span>  
  
- <span data-ttu-id="ce6e1-190">a. {b} someLiteral {c} ({d})/</span><span class="sxs-lookup"><span data-stu-id="ce6e1-190">/{a}.{b}someLiteral{c}({d})/</span></span>  
  
 <span data-ttu-id="ce6e1-191">Aşağıda geçersiz yol kesimlerinin örnekleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-191">The following are examples of invalid path segments.</span></span>  
  
- <span data-ttu-id="ce6e1-192">/ {} -Değişkenlerin adlandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-192">/{} - Variables must be named.</span></span>  
  
- <span data-ttu-id="ce6e1-193">/{Shoe}{Boat}-değişkenlerin bir sabit değer ile ayrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-193">/{shoe}{boat} - Variables must be separated by a literal.</span></span>  
  
### <a name="matching-and-compound-path-segments"></a><span data-ttu-id="ce6e1-194">Eşleşen ve bileşik yol kesimleri</span><span class="sxs-lookup"><span data-stu-id="ce6e1-194">Matching and Compound Path Segments</span></span>  
 <span data-ttu-id="ce6e1-195">Bileşik yol kesimleri, tek bir yol segmentinde birden çok değişken içeren bir UriTemplate tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-195">Compound path segments allow you to define a UriTemplate that has multiple variables within a single path segment.</span></span> <span data-ttu-id="ce6e1-196">Örneğin, şu şablon dizesinde: "adresler/{State}. {City} "iki değişken (eyalet ve şehir) aynı segment içinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-196">For example, in the following template string: "Addresses/{state}.{city}" two variables (state and city) are defined within the same segment.</span></span> <span data-ttu-id="ce6e1-197">Bu şablon gibi bir URL ile eşleşir `http://example.com/Washington.Redmond` , ancak aynı zamanda gibi BIR URL ile eşleşir `http://example.com/Washington.Redmond.Microsoft` .</span><span class="sxs-lookup"><span data-stu-id="ce6e1-197">This template would match a URL such as `http://example.com/Washington.Redmond` but it will also match an URL like `http://example.com/Washington.Redmond.Microsoft`.</span></span> <span data-ttu-id="ce6e1-198">İkinci durumda, durum değişkeni "Washington" ve City değişkeni "Redmond. Microsoft" içerecektir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-198">In the latter case, the state variable will contain "Washington" and the city variable will contain "Redmond.Microsoft".</span></span> <span data-ttu-id="ce6e1-199">Bu durumda, herhangi bir metin ('/' hariç) {City} değişkeniyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-199">In this case any text (except ‘/’) will match the {city} variable.</span></span> <span data-ttu-id="ce6e1-200">"Ekstra" metinle eşleşmeyen bir şablon istiyorsanız, değişkeni ayrı bir şablon kesimine yerleştirin, örneğin: "adresler/{State}/{City}.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-200">If you want a template that will not match the "extra" text, place the variable in a separate template segment, for example: "Addresses/{state}/{city}.</span></span>  
  
### <a name="named-wildcard-segments"></a><span data-ttu-id="ce6e1-201">Adlandırılmış joker kesimleri</span><span class="sxs-lookup"><span data-stu-id="ce6e1-201">Named Wildcard Segments</span></span>  
 <span data-ttu-id="ce6e1-202">Adlandırılmış joker karakter segmenti, değişken adı ' ' joker karakteriyle başlayan herhangi bir yol değişkeni segmentdir \* .</span><span class="sxs-lookup"><span data-stu-id="ce6e1-202">A named wildcard segment is any path variable segment whose variable name begins with the wildcard character ‘\*’.</span></span> <span data-ttu-id="ce6e1-203">Aşağıdaki şablon dizesi "Shoe" adlı adlandırılmış bir joker karakter segmentini içerir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-203">The following template string contains a named wildcard segment named "shoe".</span></span>  
  
`"literal/{*shoe}"`  
  
 <span data-ttu-id="ce6e1-204">Joker karakter kesimleri aşağıdaki kurallara uymalıdır:</span><span class="sxs-lookup"><span data-stu-id="ce6e1-204">Wildcard segments must follow the following rules:</span></span>  
  
- <span data-ttu-id="ce6e1-205">Her bir şablon dizesi için en fazla bir adlandırılmış joker karakter segmenti olabilir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-205">There can be at most one named wildcard segment for each template string.</span></span>  
  
- <span data-ttu-id="ce6e1-206">Adlandırılmış bir joker karakter segmenti, yoldaki en sağ kesimde görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-206">A named wildcard segment must appear at the right-most segment in the path.</span></span>  
  
- <span data-ttu-id="ce6e1-207">Adlandırılmış bir joker karakter segmenti aynı şablon dizesinde anonim bir joker karakterle birlikte bulunamaz.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-207">A named wildcard segment cannot coexist with an anonymous wildcard segment within the same template string.</span></span>  
  
- <span data-ttu-id="ce6e1-208">Adlandırılmış bir joker karakter kesiminin adı benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-208">The name of a named wildcard segment must be unique.</span></span>  
  
- <span data-ttu-id="ce6e1-209">Adlandırılmış joker karakter kesimleri varsayılan değerlere sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-209">Named wildcard segments cannot have default values.</span></span>  
  
- <span data-ttu-id="ce6e1-210">Adlandırılmış joker kesimleri "/" ile bitemez.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-210">Named wildcard segments cannot end with "/".</span></span>  
  
### <a name="default-variable-values"></a><span data-ttu-id="ce6e1-211">Varsayılan değişken değerleri</span><span class="sxs-lookup"><span data-stu-id="ce6e1-211">Default Variable Values</span></span>  
 <span data-ttu-id="ce6e1-212">Varsayılan değişken değerleri bir şablon içindeki değişkenler için varsayılan değerleri belirtmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-212">Default variable values allow you to specify default values for variables within a template.</span></span> <span data-ttu-id="ce6e1-213">Varsayılan değişkenler, değişkeni bildiren küme ayraçları ile veya UriTemplate oluşturucusuna geçirilen bir koleksiyon olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-213">Default variables can be specified with the curly braces that declare the variable or as a collection passed to the UriTemplate constructor.</span></span> <span data-ttu-id="ce6e1-214">Aşağıdaki şablonda, <xref:System.UriTemplate> varsayılan değerleri olan değişkenleri içeren bir belirtmek için iki yol gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-214">The following template shows two ways to specify a <xref:System.UriTemplate> with variables with default values.</span></span>  
  
```csharp
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 <span data-ttu-id="ce6e1-215">Bu şablon, varsayılan değeri olan adlı bir değişken `a` `1` ve `b` varsayılan değeri olan adlı bir değişken bildirir `5` .</span><span class="sxs-lookup"><span data-stu-id="ce6e1-215">This template declares a variable named `a` with a default value of `1` and a variable named `b` with a default value of `5`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce6e1-216">Yalnızca yol kesimi değişkenlerinin varsayılan değerlere sahip olmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-216">Only path segment variables are allowed to have default values.</span></span> <span data-ttu-id="ce6e1-217">Sorgu dizesi değişkenleri, bileşik kesim değişkenleri ve adlandırılmış joker dizeler varsayılan değerlere sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-217">Query string variables, compound segment variables, and named wildcard variables are not permitted to have default values.</span></span>  
  
 <span data-ttu-id="ce6e1-218">Aşağıdaki kod, bir aday URI ile eşleştirilirken varsayılan değişken değerlerinin nasıl işlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-218">The following code shows how default variable values are handled when matching a candidate URI.</span></span>  
  
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
> <span data-ttu-id="ce6e1-219">Gibi bir URI `http://localhost:8000///` , önceki kodda listelenen şablonla eşleşmez, ancak gibi BIR URI `http://localhost:8000/` .</span><span class="sxs-lookup"><span data-stu-id="ce6e1-219">A URI such as `http://localhost:8000///` does not match the template listed in the preceding code, however a URI such as `http://localhost:8000/` does.</span></span>  
  
 <span data-ttu-id="ce6e1-220">Aşağıdaki kod, bir şablon ile URI oluştururken varsayılan değişken değerlerinin nasıl işlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-220">The following code shows how default variable values are handled when creating a URI with a template.</span></span>  
  
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
  
<span data-ttu-id="ce6e1-221">Bir değişkene varsayılan değer verildiğinde, `null` bazı ek kısıtlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-221">When a variable is given a default value of `null` there are some additional constraints.</span></span> <span data-ttu-id="ce6e1-222">Değişken, `null` şablon dizesinin en sağ alt segmentinde yer alıyorsa veya segmentin sağ tarafındaki tüm segmentlerin varsayılan değerleri içeriyorsa, bir değişken varsayılan değeri olabilir `null` .</span><span class="sxs-lookup"><span data-stu-id="ce6e1-222">A variable can have a default value of `null` if the variable is contained within the right most segment of the template string or if all segments to the right of the segment have default values of `null`.</span></span> <span data-ttu-id="ce6e1-223">Aşağıda varsayılan değerleri olan geçerli şablon dizeleri verilmiştir `null` :</span><span class="sxs-lookup"><span data-stu-id="ce6e1-223">The following are valid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("shoe/{boat=null}");`

- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");`
  
- `UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");`

 <span data-ttu-id="ce6e1-224">Varsayılan değerleri geçersiz olan şablon dizeleri aşağıda verilmiştir `null` :</span><span class="sxs-lookup"><span data-stu-id="ce6e1-224">The following are invalid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment`
  
- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value`

### <a name="default-values-and-matching"></a><span data-ttu-id="ce6e1-225">Varsayılan değerler ve eşleştirme</span><span class="sxs-lookup"><span data-stu-id="ce6e1-225">Default Values and Matching</span></span>  
 <span data-ttu-id="ce6e1-226">Bir aday URI 'yi varsayılan değerlere sahip bir şablonla eşleştirirken, <xref:System.UriTemplateMatch.BoundVariables%2A> aday URI 'sinde değerler belirtilmemişse varsayılan değerler koleksiyona yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-226">When matching a candidate URI with a template that has default values, the default values are placed in the <xref:System.UriTemplateMatch.BoundVariables%2A> collection if values are not specified in the candidate URI.</span></span>  
  
### <a name="template-equivalence"></a><span data-ttu-id="ce6e1-227">Şablon denklik</span><span class="sxs-lookup"><span data-stu-id="ce6e1-227">Template Equivalence</span></span>  
 <span data-ttu-id="ce6e1-228">Tüm şablonların sabit değerleri eşleşiyorsa ve aynı kesimlerde değişkenler olduğunda, iki şablon *yapısal olarak eşdeğer* olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-228">Two templates are said to be *structurally equivalent* when all of the templates' literals match and they have variables in the same segments.</span></span> <span data-ttu-id="ce6e1-229">Örneğin, aşağıdaki şablonlar yapısal olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="ce6e1-229">For example the following templates are structurally equivalent:</span></span>  
  
- <span data-ttu-id="ce6e1-230">/a/{var1}/b b/{var2}? x = 1&y = 2</span><span class="sxs-lookup"><span data-stu-id="ce6e1-230">/a/{var1}/b b/{var2}?x=1&y=2</span></span>  
  
- <span data-ttu-id="ce6e1-231">a/{x}/b% 20B/{var1}? y = 2&x = 1</span><span class="sxs-lookup"><span data-stu-id="ce6e1-231">a/{x}/b%20b/{var1}?y=2&x=1</span></span>  
  
- <span data-ttu-id="ce6e1-232">a/{y}/B% 20B/{z}/? y = 2&x = 1</span><span class="sxs-lookup"><span data-stu-id="ce6e1-232">a/{y}/B%20B/{z}/?y=2&x=1</span></span>  
  
 <span data-ttu-id="ce6e1-233">Dikkat etmeniz gereken birkaç nokta vardır:</span><span class="sxs-lookup"><span data-stu-id="ce6e1-233">A few things to notice:</span></span>  
  
- <span data-ttu-id="ce6e1-234">Bir şablon önünde eğik çizgi içeriyorsa, yalnızca ilki yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-234">If a template contains leading slashes, only the first one is ignored.</span></span>  
  
- <span data-ttu-id="ce6e1-235">Yapısal denklik için şablon dizelerini karşılaştırırken, değişken adları ve yol kesimleri için durum yoksayıldı, sorgu dizeleri büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-235">When comparing template strings for structural equivalence, case is ignored for variable names and path segments, query strings are case sensitive.</span></span>  
  
- <span data-ttu-id="ce6e1-236">Sorgu dizeleri sırasız.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-236">Query strings are unordered.</span></span>  
  
## <a name="uritemplatetable"></a><span data-ttu-id="ce6e1-237">UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="ce6e1-237">UriTemplateTable</span></span>  
 <span data-ttu-id="ce6e1-238"><xref:System.UriTemplateTable>Sınıfı, <xref:System.UriTemplate> geliştiricinin seçme nesnesine bağlantılı nesnelerin ilişkilendirilebilir tablosunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-238">The <xref:System.UriTemplateTable> class represents an associative table of <xref:System.UriTemplate> objects bound to an object of the developer's choosing.</span></span> <span data-ttu-id="ce6e1-239">' Nin <xref:System.UriTemplateTable> çağrılmadan önce en az bir tane içermesi gerekir <xref:System.UriTemplate> <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> .</span><span class="sxs-lookup"><span data-stu-id="ce6e1-239">A <xref:System.UriTemplateTable> must contain at least one <xref:System.UriTemplate> prior to calling <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span> <span data-ttu-id="ce6e1-240">Bir öğesinin içeriği <xref:System.UriTemplateTable> <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> çağrılana kadar değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-240">The contents of a <xref:System.UriTemplateTable> can be changed until <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="ce6e1-241">Çağrıldığında doğrulama gerçekleştirilir <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> .</span><span class="sxs-lookup"><span data-stu-id="ce6e1-241">Validation is performed when <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="ce6e1-242">Gerçekleştirilen doğrulamanın türü, parametresinin değerine bağlıdır `allowMultiple` <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> .</span><span class="sxs-lookup"><span data-stu-id="ce6e1-242">The type of validation performed depends upon the value of the `allowMultiple` parameter to <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span>  
  
 <span data-ttu-id="ce6e1-243"><xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>İçinde geçirme çağrıldığında, `false` <xref:System.UriTemplateTable> tabloda hiçbir şablon olmadığından emin olmak için kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-243">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `false`, the <xref:System.UriTemplateTable> checks to make sure there are no templates in the table.</span></span> <span data-ttu-id="ce6e1-244">Yapısal olarak eşdeğer şablonlar bulursa, bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-244">If it finds any structurally equivalent templates, it throws an exception.</span></span> <span data-ttu-id="ce6e1-245">Bu, bir <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> gelen URI ile eşleşen yalnızca bir şablonun olduğundan emin olmak istediğiniz zaman ile birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-245">This is used in conjunction with <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> when you want to ensure only one template matches an incoming URI.</span></span>  
  
 <span data-ttu-id="ce6e1-246"><xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>İçinde geçirme çağrıldığında `true` , <xref:System.UriTemplateTable> birden çok, yapısal olarak denk şablonların bir içinde yer almasına izin verir <xref:System.UriTemplateTable> .</span><span class="sxs-lookup"><span data-stu-id="ce6e1-246">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `true`, <xref:System.UriTemplateTable> allows multiple, structurally-equivalent templates to be contained within a <xref:System.UriTemplateTable>.</span></span>  
  
 <span data-ttu-id="ce6e1-247"><xref:System.UriTemplate>Bir nesne kümesine eklenen bir <xref:System.UriTemplateTable> sorgu dizesi varsa, bunların belirsiz olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-247">If a set of <xref:System.UriTemplate> objects added to a <xref:System.UriTemplateTable> contain query strings they must not be ambiguous.</span></span> <span data-ttu-id="ce6e1-248">Özdeş sorgu dizelerine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-248">Identical query strings are allowed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce6e1-249">HTTP dışındaki <xref:System.UriTemplateTable> şemaları kullanan temel adreslere izin verdiğinden, aday URI 'leri şablonlarla eşleştirilirken düzen ve bağlantı noktası numarası yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-249">While the <xref:System.UriTemplateTable> allows base addresses that use schemes other than HTTP, the scheme and port number are ignored when matching candidate URIs to templates.</span></span>  
  
### <a name="query-string-ambiguity"></a><span data-ttu-id="ce6e1-250">Sorgu dizesi belirsizlik</span><span class="sxs-lookup"><span data-stu-id="ce6e1-250">Query String Ambiguity</span></span>  
 <span data-ttu-id="ce6e1-251">Bir eşdeğer yolu paylaşan şablonlar, birden fazla şablonla eşleşen bir URI varsa belirsiz sorgu dizeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-251">Templates that share an equivalent path contain ambiguous query strings if there is a URI that matches more than one template.</span></span>  
  
 <span data-ttu-id="ce6e1-252">Aşağıdaki sorgu dizeleri kümeleri kendi içinde belirsiz:</span><span class="sxs-lookup"><span data-stu-id="ce6e1-252">The following sets of query strings are unambiguous within themselves:</span></span>  
  
- <span data-ttu-id="ce6e1-253">? x = 1</span><span class="sxs-lookup"><span data-stu-id="ce6e1-253">?x=1</span></span>  
  
- <span data-ttu-id="ce6e1-254">? x = 2</span><span class="sxs-lookup"><span data-stu-id="ce6e1-254">?x=2</span></span>  
  
- <span data-ttu-id="ce6e1-255">? x = 3</span><span class="sxs-lookup"><span data-stu-id="ce6e1-255">?x=3</span></span>  
  
- <span data-ttu-id="ce6e1-256">? x = 1&y = {var}</span><span class="sxs-lookup"><span data-stu-id="ce6e1-256">?x=1&y={var}</span></span>  
  
- <span data-ttu-id="ce6e1-257">? x = 2&z = {var}</span><span class="sxs-lookup"><span data-stu-id="ce6e1-257">?x=2&z={var}</span></span>  
  
- <span data-ttu-id="ce6e1-258">? x = 3</span><span class="sxs-lookup"><span data-stu-id="ce6e1-258">?x=3</span></span>  
  
- <span data-ttu-id="ce6e1-259">? x = 1</span><span class="sxs-lookup"><span data-stu-id="ce6e1-259">?x=1</span></span>  
  
- <span data-ttu-id="ce6e1-260">?</span><span class="sxs-lookup"><span data-stu-id="ce6e1-260">?</span></span>  
  
- <span data-ttu-id="ce6e1-261">?</span><span class="sxs-lookup"><span data-stu-id="ce6e1-261">?</span></span> <span data-ttu-id="ce6e1-262">x = {var}</span><span class="sxs-lookup"><span data-stu-id="ce6e1-262">x={var}</span></span>  
  
- <span data-ttu-id="ce6e1-263">?</span><span class="sxs-lookup"><span data-stu-id="ce6e1-263">?</span></span>  
  
- <span data-ttu-id="ce6e1-264">? m = Get&c = RSS</span><span class="sxs-lookup"><span data-stu-id="ce6e1-264">?m=get&c=rss</span></span>  
  
- <span data-ttu-id="ce6e1-265">? m = put&c = RSS</span><span class="sxs-lookup"><span data-stu-id="ce6e1-265">?m=put&c=rss</span></span>  
  
- <span data-ttu-id="ce6e1-266">? m = Get&c = atom</span><span class="sxs-lookup"><span data-stu-id="ce6e1-266">?m=get&c=atom</span></span>  
  
- <span data-ttu-id="ce6e1-267">? m = put&c = atom</span><span class="sxs-lookup"><span data-stu-id="ce6e1-267">?m=put&c=atom</span></span>  
  
 <span data-ttu-id="ce6e1-268">Aşağıdaki sorgu dizesi şablonları kümeleri kendileri içinde belirsizdir:</span><span class="sxs-lookup"><span data-stu-id="ce6e1-268">The following sets of query string templates are ambiguous within themselves:</span></span>  
  
- <span data-ttu-id="ce6e1-269">? x = 1</span><span class="sxs-lookup"><span data-stu-id="ce6e1-269">?x=1</span></span>  
  
- <span data-ttu-id="ce6e1-270">? x = {var}</span><span class="sxs-lookup"><span data-stu-id="ce6e1-270">?x={var}</span></span>  
  
 <span data-ttu-id="ce6e1-271">"x = 1"-her iki şablon da eşleşir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-271">"x=1" - Matches both templates.</span></span>  
  
- <span data-ttu-id="ce6e1-272">? x = 1</span><span class="sxs-lookup"><span data-stu-id="ce6e1-272">?x=1</span></span>  
  
- <span data-ttu-id="ce6e1-273">? y = 2</span><span class="sxs-lookup"><span data-stu-id="ce6e1-273">?y=2</span></span>  
  
 <span data-ttu-id="ce6e1-274">"x = 1&y = 2", her iki şablonlarla de eşleşir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-274">"x=1&y=2" matches both templates.</span></span> <span data-ttu-id="ce6e1-275">Bunun nedeni, bir sorgu dizesinin daha fazla sorgu dizesi değişkeni içermesi olabilir ve bundan sonra eşleşen şablondur.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-275">This is because a query string may contain more query string variables then the template it matches.</span></span>  
  
- <span data-ttu-id="ce6e1-276">? x = 1</span><span class="sxs-lookup"><span data-stu-id="ce6e1-276">?x=1</span></span>  
  
- <span data-ttu-id="ce6e1-277">? x = 1&y = {var}</span><span class="sxs-lookup"><span data-stu-id="ce6e1-277">?x=1&y={var}</span></span>  
  
 <span data-ttu-id="ce6e1-278">"x = 1&y = 3" her iki şablonlarla de eşleşir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-278">"x=1&y=3" matches both templates.</span></span>  
  
- <span data-ttu-id="ce6e1-279">? x = 3&y = 4</span><span class="sxs-lookup"><span data-stu-id="ce6e1-279">?x=3&y=4</span></span>  
  
- <span data-ttu-id="ce6e1-280">? x = 3&z = 5</span><span class="sxs-lookup"><span data-stu-id="ce6e1-280">?x=3&z=5</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce6e1-281">Á ve Á karakterleri, bir URI yolu veya yol segmenti değişmez değerinin bir parçası olarak görüntülendiklerinde farklı karakterler olarak değerlendirilir <xref:System.UriTemplate> (ancak a ve a karakterleri aynı olduğu kabul edilir).</span><span class="sxs-lookup"><span data-stu-id="ce6e1-281">The characters á and Á are considered to be different characters when they appear as part of a URI path or <xref:System.UriTemplate> path segment literal (but the characters a and A are considered to be the same).</span></span> <span data-ttu-id="ce6e1-282">Á ve Á karakterleri, bir <xref:System.UriTemplate> {VariableName} veya bir sorgu dizesinin (ve ' de aynı karakterler olarak kabul edilir) bir parçası olarak göründükleri karakterlerle aynı karakterler olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-282">The characters á and Á are considered to be the same characters when they appear as part of a <xref:System.UriTemplate> {variableName} or a query string (and a and A are also considered to be the same characters).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce6e1-283">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce6e1-283">See also</span></span>

- [<span data-ttu-id="ce6e1-284">WCF Web HTTP Programlama Modeli Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ce6e1-284">WCF Web HTTP Programming Model Overview</span></span>](wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="ce6e1-285">WCF Web HTTP Programlama Nesnesi Modeli</span><span class="sxs-lookup"><span data-stu-id="ce6e1-285">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)
- [<span data-ttu-id="ce6e1-286">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="ce6e1-286">UriTemplate</span></span>](../samples/uritemplate-sample.md)
- [<span data-ttu-id="ce6e1-287">UriTemplate Tablosu</span><span class="sxs-lookup"><span data-stu-id="ce6e1-287">UriTemplate Table</span></span>](../samples/uritemplate-table-sample.md)
- [<span data-ttu-id="ce6e1-288">UriTemplate Tablosu Dağıtıcısı</span><span class="sxs-lookup"><span data-stu-id="ce6e1-288">UriTemplate Table Dispatcher</span></span>](../samples/uritemplate-table-dispatcher-sample.md)
