---
description: 'Daha fazla bilgi edinin: UriTemplate ve UriTemplateTable'
title: UriTemplate ve UriTemplateTable
ms.date: 03/30/2017
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
ms.openlocfilehash: 7abcf0125108e4f48e392e8bb817dda77dfedd38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632418"
---
# <a name="uritemplate-and-uritemplatetable"></a><span data-ttu-id="757cc-103">UriTemplate ve UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="757cc-103">UriTemplate and UriTemplateTable</span></span>

<span data-ttu-id="757cc-104">Web geliştiricileri, hizmetlerinin yanıt verdiği URI 'lerin şeklini ve yerleşimini betimleyebilme olanağı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="757cc-104">Web developers require the ability to describe the shape and layout of the URIs that their services respond to.</span></span> <span data-ttu-id="757cc-105">Windows Communication Foundation (WCF), geliştiricilerin URI 'lerinde denetim sağlamak için iki yeni sınıf ekledi.</span><span class="sxs-lookup"><span data-stu-id="757cc-105">Windows Communication Foundation (WCF) added two new classes to give developers control over their URIs.</span></span> <span data-ttu-id="757cc-106"><xref:System.UriTemplate> ve <xref:System.UriTemplateTable> WCF 'de URI tabanlı dağıtım altyapısının temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="757cc-106"><xref:System.UriTemplate> and <xref:System.UriTemplateTable> form the basis of the URI-based dispatch engine in WCF.</span></span> <span data-ttu-id="757cc-107">Bu sınıflar kendi kendilerine de kullanılabilir, geliştiricilerin bir WCF hizmeti uygulamadan şablonlardan ve URI eşleme mekanizmasından yararlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="757cc-107">These classes can also be used on their own, allowing developers to take advantage of templates and the URI mapping mechanism without implementing a WCF service.</span></span>  
  
## <a name="templates"></a><span data-ttu-id="757cc-108">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="757cc-108">Templates</span></span>  

 <span data-ttu-id="757cc-109">Şablon, göreli URI 'lerin bir kümesini tanımlamaya yönelik bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="757cc-109">A template is a way to describe a set of relative URIs.</span></span> <span data-ttu-id="757cc-110">Aşağıdaki tabloda yer alan URI şablonları kümesi, çeşitli hava durumu bilgilerini alan bir sistemin nasıl tanımlanabilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="757cc-110">The set of URI templates in the following table shows how a system that retrieves various types of weather information might be defined.</span></span>  
  
|<span data-ttu-id="757cc-111">Veriler</span><span class="sxs-lookup"><span data-stu-id="757cc-111">Data</span></span>|<span data-ttu-id="757cc-112">Şablon</span><span class="sxs-lookup"><span data-stu-id="757cc-112">Template</span></span>|  
|----------|--------------|  
|<span data-ttu-id="757cc-113">Ulusal tahmin</span><span class="sxs-lookup"><span data-stu-id="757cc-113">National Forecast</span></span>|<span data-ttu-id="757cc-114">Hava durumu/Ulusal</span><span class="sxs-lookup"><span data-stu-id="757cc-114">weather/national</span></span>|  
|<span data-ttu-id="757cc-115">Durum tahmini</span><span class="sxs-lookup"><span data-stu-id="757cc-115">State Forecast</span></span>|<span data-ttu-id="757cc-116">Hava durumu/{State}</span><span class="sxs-lookup"><span data-stu-id="757cc-116">weather/{state}</span></span>|  
|<span data-ttu-id="757cc-117">Şehir tahmini</span><span class="sxs-lookup"><span data-stu-id="757cc-117">City Forecast</span></span>|<span data-ttu-id="757cc-118">Hava durumu/{State}/{City}</span><span class="sxs-lookup"><span data-stu-id="757cc-118">weather/{state}/{city}</span></span>|  
|<span data-ttu-id="757cc-119">Etkinlik tahmini</span><span class="sxs-lookup"><span data-stu-id="757cc-119">Activity Forecast</span></span>|<span data-ttu-id="757cc-120">Hava durumu/{State}/{City}/{Activity}</span><span class="sxs-lookup"><span data-stu-id="757cc-120">weather/{state}/{city}/{activity}</span></span>|  
  
 <span data-ttu-id="757cc-121">Bu tablo yapısal olarak benzer URI 'Ler kümesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="757cc-121">This table describes a set of structurally similar URIs.</span></span> <span data-ttu-id="757cc-122">Her giriş bir URI şablonudur.</span><span class="sxs-lookup"><span data-stu-id="757cc-122">Each entry is a URI template.</span></span> <span data-ttu-id="757cc-123">Küme ayraçları içindeki segmentler değişkenleri anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="757cc-123">The segments in curly braces describe variables.</span></span> <span data-ttu-id="757cc-124">Küme ayraçları içinde olmayan kesimler, değişmez dizeleri tanımlıyor.</span><span class="sxs-lookup"><span data-stu-id="757cc-124">The segments not in curly braces describe literal strings.</span></span> <span data-ttu-id="757cc-125">WCF şablon sınıfları, bir geliştiricinin gelen URI 'yi (örneğin, "/Weather/WA/Seattle/Cycling") alıp onu açıklayan bir şablonla eşleştirmek için "/dalgalı ther/{State}/{City}/{Activity}" sağlar.</span><span class="sxs-lookup"><span data-stu-id="757cc-125">The WCF template classes allow a developer to take an incoming URI, for example, "/weather/wa/seattle/cycling", and match it to a template that describes it, "/weather/{state}/{city}/{activity}".</span></span>  
  
## <a name="uritemplate"></a><span data-ttu-id="757cc-126">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="757cc-126">UriTemplate</span></span>  

 <span data-ttu-id="757cc-127"><xref:System.UriTemplate> , bir URI şablonunu kapsülleyen bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="757cc-127"><xref:System.UriTemplate> is a class that encapsulates a URI template.</span></span> <span data-ttu-id="757cc-128">Oluşturucu, şablonu tanımlayan bir dize parametresi alır.</span><span class="sxs-lookup"><span data-stu-id="757cc-128">The constructor takes a string parameter that defines the template.</span></span> <span data-ttu-id="757cc-129">Bu dize, sonraki bölümde açıklanan biçimdeki şablonu içerir.</span><span class="sxs-lookup"><span data-stu-id="757cc-129">This string contains the template in the format described in the next section.</span></span> <span data-ttu-id="757cc-130">Sınıfı, bir <xref:System.UriTemplate> şablon için gelen URI 'yi eşleştirmek, bir ŞABLONDAN URI oluşturmak, şablonda kullanılan değişken adlarından oluşan bir koleksiyonu almak, iki şablonun eşdeğer olup olmadığını tespit etmek ve şablonun dizesini döndürmeksizin yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="757cc-130">The <xref:System.UriTemplate> class provides methods that allow you match an incoming URI to a template, generate a URI from a template, retrieve a collection of variable names used in the template, determine whether two templates are equivalent, and return the template's string.</span></span>  
  
 <span data-ttu-id="757cc-131"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> temel bir adresi ve aday URI 'yi alır ve URI 'yi şablonla eşleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="757cc-131"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> takes a base address and a candidate URI and attempts to match the URI to the template.</span></span> <span data-ttu-id="757cc-132">Eşleşme başarılı olursa bir <xref:System.UriTemplateMatch> örnek döndürülür.</span><span class="sxs-lookup"><span data-stu-id="757cc-132">If the match is successful, a <xref:System.UriTemplateMatch> instance is returned.</span></span> <span data-ttu-id="757cc-133"><xref:System.UriTemplateMatch>Nesne bir temel URI içerir, aday URI, sorgu parametrelerinin ad/değer koleksiyonu, göreli yol segmentlerinin bir dizisi, eşleşen değişkenlerin bir adı/değer koleksiyonu, <xref:System.UriTemplate> karşılamanın yerine getirmek için kullanılan örnek, aday URI 'sinin eşleşmeyen herhangi bir bölümünü (şablon bir joker karakter olduğunda kullanılır) ve şablonla ilişkili bir nesneyi içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="757cc-133">The <xref:System.UriTemplateMatch> object contains a base URI, the candidate URI, a name/value collection of the query parameters, an array of the relative path segments, a name/value collection of variables that were matched, the <xref:System.UriTemplate> instance used to perform the match, a string that contains any unmatched portion of the candidate URI (used when the template has a wildcard), and an object that is associated with the template.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="757cc-134"><xref:System.UriTemplate>Sınıf, bir aday URI 'yi bir şablonla eşleştirirken düzen ve bağlantı noktası numarasını yoksayar.</span><span class="sxs-lookup"><span data-stu-id="757cc-134">The <xref:System.UriTemplate> class ignores the scheme and port number when matching a candidate URI to a template.</span></span>  
  
 <span data-ttu-id="757cc-135">Bir şablondan URI oluşturmanıza izin veren iki yöntem vardır <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> ve <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> .</span><span class="sxs-lookup"><span data-stu-id="757cc-135">There are two methods that allow you to generate a URI from a template, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> and <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span></span> <span data-ttu-id="757cc-136"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> bir taban adresi ve parametrelerin ad/değer koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="757cc-136"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> takes a base address and a name/value collection of parameters.</span></span> <span data-ttu-id="757cc-137">Bu parametreler, şablon bağlandığında değişkenler için değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="757cc-137">These parameters are substituted for variables when the template is bound.</span></span> <span data-ttu-id="757cc-138"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> ad/değer çiftlerini alır ve bunları soldan sağa koyar.</span><span class="sxs-lookup"><span data-stu-id="757cc-138"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> takes the name/value pairs and substitutes them left to right.</span></span>  
  
 <span data-ttu-id="757cc-139"><xref:System.UriTemplate.ToString> Şablon dizesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="757cc-139"><xref:System.UriTemplate.ToString> returns the template string.</span></span>  
  
 <span data-ttu-id="757cc-140"><xref:System.UriTemplate.PathSegmentVariableNames%2A>Özelliği, şablon dizesindeki yol kesimleri içinde kullanılan değişkenlerin adlarının bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="757cc-140">The <xref:System.UriTemplate.PathSegmentVariableNames%2A> property contains a collection of the names of the variables used within path segments in the template string.</span></span>  
  
 <span data-ttu-id="757cc-141"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> bir <xref:System.UriTemplate> parametresini parametre olarak alır ve iki şablonun eşdeğer olup olmadığını belirten bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="757cc-141"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> takes a <xref:System.UriTemplate> as a parameter and returns a Boolean value that specifies whether the two templates are equivalent.</span></span> <span data-ttu-id="757cc-142">Daha fazla bilgi için bu konunun ilerleyen kısımlarında yer alarak şablon denklik bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="757cc-142">For more information, see the Template Equivalence section later in this topic.</span></span>  
  
 <span data-ttu-id="757cc-143"><xref:System.UriTemplate> , HTTP URI dilbilgisine uygun herhangi bir URI şeması ile çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="757cc-143"><xref:System.UriTemplate> is designed to work with any URI scheme that conforms to the HTTP URI grammar.</span></span> <span data-ttu-id="757cc-144">Aşağıda desteklenen URI düzenlerinin örnekleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="757cc-144">The following are examples of supported URI schemes.</span></span>  
  
- `http://`  
  
- `https://`  
  
- `net.tcp://`  
  
- `net.pipe://`  
  
- `sb://`  
  
 <span data-ttu-id="757cc-145">File://ve urn://gibi düzenler HTTP URI dilbilgisine uymuyor ve URI şablonlarıyla birlikte kullanıldığında öngörülemeyen sonuçlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="757cc-145">Schemes like file:// and urn:// do not conform to the HTTP URI grammar and cause unpredictable results when used with URI templates.</span></span>  
  
### <a name="template-string-syntax"></a><span data-ttu-id="757cc-146">Şablon dizesi sözdizimi</span><span class="sxs-lookup"><span data-stu-id="757cc-146">Template String Syntax</span></span>  

 <span data-ttu-id="757cc-147">Şablon üç bölümden oluşur: yol, isteğe bağlı sorgu ve isteğe bağlı bir parça.</span><span class="sxs-lookup"><span data-stu-id="757cc-147">A template has three parts: a path, an optional query, and an optional fragment.</span></span> <span data-ttu-id="757cc-148">Bir örnek için, aşağıdaki şablona bakın:</span><span class="sxs-lookup"><span data-stu-id="757cc-148">For an example, see the following template:</span></span>  
  
`"/weather/{state}/{city}?forecast={length)#frag1`  
  
 <span data-ttu-id="757cc-149">Yol "/dalgalı ther/{State}/{City}" bilgisinden oluşur, sorgu "? tahmine = {length} ve parça" #frag1 "bilgisinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="757cc-149">The path consists of "/weather/{state}/{city}", the query consists of "?forecast={length}, and the fragment consists of "#frag1".</span></span>  
  
 <span data-ttu-id="757cc-150">Yol ifadesinde öndeki ve sondaki eğik çizgiler isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="757cc-150">Leading and trailing slashes are optional in the path expression.</span></span> <span data-ttu-id="757cc-151">Hem sorgu hem de parça ifadeleri tamamen atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="757cc-151">Both the query and fragment expressions can be omitted entirely.</span></span> <span data-ttu-id="757cc-152">Bir yol, '/' ile ayrılmış bir dizi kesimden oluşur, her segment bir sabit değer, değişken adı ({küme ayraçları} içinde yazılmış) veya joker karakter (' ' olarak yazılmış \* ) olabilir.</span><span class="sxs-lookup"><span data-stu-id="757cc-152">A path consists of a series of segments delimited by '/', each segment can have a literal value, a variable name (written in {curly braces}), or a wildcard (written as '\*').</span></span> <span data-ttu-id="757cc-153">Önceki şablonda, "{State}" ve "{City}" değişkenleri olan "\dalgalı ther\ segmenti değişmez değer değeridir.</span><span class="sxs-lookup"><span data-stu-id="757cc-153">In the previous template the "\weather\ segment is a literal value while "{state}" and "{city}" are variables.</span></span> <span data-ttu-id="757cc-154">Değişkenler, bunların adlarını kendi küme ayraçları içeriğinden alır ve daha sonra *kapalı bır URI* oluşturmak için somut bir değer ile değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="757cc-154">Variables take their name from the contents of their curly braces and they can later be replaced with a concrete value to create a *closed URI*.</span></span> <span data-ttu-id="757cc-155">Joker karakter isteğe bağlıdır, ancak yalnızca URI sonunda görünebilir, burada "yolun geri kalanı" ile mantıksal olarak eşleşir.</span><span class="sxs-lookup"><span data-stu-id="757cc-155">The wildcard is optional, but can only appear at the end of the URI, where it logically matches "the rest of the path".</span></span>  
  
 <span data-ttu-id="757cc-156">Sorgu ifadesi varsa, ' & ' ile ayrılmış bir sıralı ad/değer çiftleri serisi belirtir.</span><span class="sxs-lookup"><span data-stu-id="757cc-156">The query expression, if present, specifies a series of unordered name/value pairs delimited by '&'.</span></span> <span data-ttu-id="757cc-157">Sorgu ifadesinin öğeleri, sabit değer çiftleri (x = 2) veya bir değişken çifti (x = {var}) olabilir.</span><span class="sxs-lookup"><span data-stu-id="757cc-157">Elements of the query expression can either be literal pairs (x=2) or a variable pair (x={var}).</span></span> <span data-ttu-id="757cc-158">Sorgunun yalnızca sağ tarafında bir değişken ifadesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="757cc-158">Only the right side of the query can have a variable expression.</span></span> <span data-ttu-id="757cc-159">({someName} = {someValue} öğesine izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="757cc-159">({someName} = {someValue} is not allowed.</span></span> <span data-ttu-id="757cc-160">Eşlenmemiş değerlere (? x) izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="757cc-160">Unpaired values (?x) are not permitted.</span></span> <span data-ttu-id="757cc-161">Boş bir sorgu ifadesi ve yalnızca tek bir '? ' içeren bir sorgu ifadesi arasında fark yoktur (her ikisi de "herhangi bir sorgu").</span><span class="sxs-lookup"><span data-stu-id="757cc-161">There is no difference between an empty query expression and a query expression consisting of just a single '?' (both mean "any query").</span></span>  
  
 <span data-ttu-id="757cc-162">Parça ifadesi bir değişmez değerden oluşabilir, hiçbir değişkene izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="757cc-162">The fragment expression can consist of a literal value, no variables are allowed.</span></span>  
  
 <span data-ttu-id="757cc-163">Bir şablon dizesi içindeki tüm şablon değişken adları benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="757cc-163">All template variable names within a template string must be unique.</span></span> <span data-ttu-id="757cc-164">Şablon değişken adları büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="757cc-164">Template variable names are case-insensitive.</span></span>  
  
 <span data-ttu-id="757cc-165">Geçerli şablon dizeleri örnekleri:</span><span class="sxs-lookup"><span data-stu-id="757cc-165">Examples of valid template strings:</span></span>  
  
- <span data-ttu-id="757cc-166">""</span><span class="sxs-lookup"><span data-stu-id="757cc-166">""</span></span>  
  
- <span data-ttu-id="757cc-167">"/Shoe"</span><span class="sxs-lookup"><span data-stu-id="757cc-167">"/shoe"</span></span>  
  
- <span data-ttu-id="757cc-168">"/Shoe/ \* "</span><span class="sxs-lookup"><span data-stu-id="757cc-168">"/shoe/\*"</span></span>  
  
- <span data-ttu-id="757cc-169">"{Shoe}/bot"</span><span class="sxs-lookup"><span data-stu-id="757cc-169">"{shoe}/boat"</span></span>  
  
- <span data-ttu-id="757cc-170">"{Shoe}/{Boat}/Bed/{Quilt}"</span><span class="sxs-lookup"><span data-stu-id="757cc-170">"{shoe}/{boat}/bed/{quilt}"</span></span>  
  
- <span data-ttu-id="757cc-171">"Shoe/{bot}"</span><span class="sxs-lookup"><span data-stu-id="757cc-171">"shoe/{boat}"</span></span>  
  
- <span data-ttu-id="757cc-172">"Shoe/{bot}/ \* "</span><span class="sxs-lookup"><span data-stu-id="757cc-172">"shoe/{boat}/\*"</span></span>  
  
- <span data-ttu-id="757cc-173">"Shoe/bot? x = 2"</span><span class="sxs-lookup"><span data-stu-id="757cc-173">"shoe/boat?x=2"</span></span>  
  
- <span data-ttu-id="757cc-174">"Shoe/{bot}? x = {yatak}"</span><span class="sxs-lookup"><span data-stu-id="757cc-174">"shoe/{boat}?x={bed}"</span></span>  
  
- <span data-ttu-id="757cc-175">"Shoe/{bot}? x = {yatak} &y = bant"</span><span class="sxs-lookup"><span data-stu-id="757cc-175">"shoe/{boat}?x={bed}&y=band"</span></span>  
  
- <span data-ttu-id="757cc-176">"? x = {Shoe}"</span><span class="sxs-lookup"><span data-stu-id="757cc-176">"?x={shoe}"</span></span>  
  
- <span data-ttu-id="757cc-177">"Shoe? x = 3&y = {var}</span><span class="sxs-lookup"><span data-stu-id="757cc-177">"shoe?x=3&y={var}</span></span>  
  
 <span data-ttu-id="757cc-178">Geçersiz şablon dizeleri örnekleri:</span><span class="sxs-lookup"><span data-stu-id="757cc-178">Examples of invalid template strings:</span></span>  
  
- <span data-ttu-id="757cc-179">"{Shoe}/{SHOE}/x = 2" – yinelenen değişken adları.</span><span class="sxs-lookup"><span data-stu-id="757cc-179">"{shoe}/{SHOE}/x=2" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="757cc-180">"{Shoe}/Boat/? yatak = {Shoe}"-yinelenen değişken adları.</span><span class="sxs-lookup"><span data-stu-id="757cc-180">"{shoe}/boat/?bed={shoe}" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="757cc-181">"? x = 2&x = 3" – bir sorgu dizesi içindeki ad/değer çiftleri, değişmez değerler olsa bile benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="757cc-181">"?x=2&x=3" – Name/value pairs within a query string must be unique, even if they are literals.</span></span>  
  
- <span data-ttu-id="757cc-182">"? x = 2&" – sorgu dizesi hatalı biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="757cc-182">"?x=2&" – Query string is malformed.</span></span>  
  
- <span data-ttu-id="757cc-183">"? 2&x = {Shoe}" – sorgu dizesi ad/değer çiftleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="757cc-183">"?2&x={shoe}" – Query string must be name/value pairs.</span></span>  
  
- <span data-ttu-id="757cc-184">"? y = 2&&X = 3" – sorgu dizesi ad değer çiftleri olmalıdır, adlar ' & ' ile başlayamaz.</span><span class="sxs-lookup"><span data-stu-id="757cc-184">"?y=2&&X=3" – Query string must be name value pairs, names cannot start with '&'.</span></span>  
  
### <a name="compound-path-segments"></a><span data-ttu-id="757cc-185">Bileşik yol kesimleri</span><span class="sxs-lookup"><span data-stu-id="757cc-185">Compound Path Segments</span></span>  

 <span data-ttu-id="757cc-186">Bileşik yol kesimleri, tek bir URI yol segmentinin birden çok değişken ve değişmez değerler ile birleştirilmiş değişkenler içermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="757cc-186">Compound path segments allow a single URI path segment to contain multiple variables as well as variables combined with literals.</span></span> <span data-ttu-id="757cc-187">Aşağıda geçerli bileşik yol segmentlerinin örnekleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="757cc-187">The following are examples of valid compound path segments.</span></span>  
  
- <span data-ttu-id="757cc-188">kısaltın. {ext}/</span><span class="sxs-lookup"><span data-stu-id="757cc-188">/filename.{ext}/</span></span>  
  
- <span data-ttu-id="757cc-189">/{filename}.exe jpg/</span><span class="sxs-lookup"><span data-stu-id="757cc-189">/{filename}.jpg/</span></span>  
  
- <span data-ttu-id="757cc-190">kısaltın. {ext}/</span><span class="sxs-lookup"><span data-stu-id="757cc-190">/{filename}.{ext}/</span></span>  
  
- <span data-ttu-id="757cc-191">a. {b} someLiteral {c} ({d})/</span><span class="sxs-lookup"><span data-stu-id="757cc-191">/{a}.{b}someLiteral{c}({d})/</span></span>  
  
 <span data-ttu-id="757cc-192">Aşağıda geçersiz yol kesimlerinin örnekleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="757cc-192">The following are examples of invalid path segments.</span></span>  
  
- <span data-ttu-id="757cc-193">/ {} -Değişkenlerin adlandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="757cc-193">/{} - Variables must be named.</span></span>  
  
- <span data-ttu-id="757cc-194">/{Shoe}{Boat}-değişkenlerin bir sabit değer ile ayrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="757cc-194">/{shoe}{boat} - Variables must be separated by a literal.</span></span>  
  
### <a name="matching-and-compound-path-segments"></a><span data-ttu-id="757cc-195">Eşleşen ve bileşik yol kesimleri</span><span class="sxs-lookup"><span data-stu-id="757cc-195">Matching and Compound Path Segments</span></span>  

 <span data-ttu-id="757cc-196">Bileşik yol kesimleri, tek bir yol segmentinde birden çok değişken içeren bir UriTemplate tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="757cc-196">Compound path segments allow you to define a UriTemplate that has multiple variables within a single path segment.</span></span> <span data-ttu-id="757cc-197">Örneğin, şu şablon dizesinde: "adresler/{State}. {City} "iki değişken (eyalet ve şehir) aynı segment içinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="757cc-197">For example, in the following template string: "Addresses/{state}.{city}" two variables (state and city) are defined within the same segment.</span></span> <span data-ttu-id="757cc-198">Bu şablon gibi bir URL ile eşleşir `http://example.com/Washington.Redmond` , ancak aynı zamanda gibi BIR URL ile eşleşir `http://example.com/Washington.Redmond.Microsoft` .</span><span class="sxs-lookup"><span data-stu-id="757cc-198">This template would match a URL such as `http://example.com/Washington.Redmond` but it will also match an URL like `http://example.com/Washington.Redmond.Microsoft`.</span></span> <span data-ttu-id="757cc-199">İkinci durumda, durum değişkeni "Washington" ve City değişkeni "Redmond. Microsoft" içerecektir.</span><span class="sxs-lookup"><span data-stu-id="757cc-199">In the latter case, the state variable will contain "Washington" and the city variable will contain "Redmond.Microsoft".</span></span> <span data-ttu-id="757cc-200">Bu durumda, herhangi bir metin ('/' hariç) {City} değişkeniyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="757cc-200">In this case any text (except ‘/’) will match the {city} variable.</span></span> <span data-ttu-id="757cc-201">"Ekstra" metinle eşleşmeyen bir şablon istiyorsanız, değişkeni ayrı bir şablon kesimine yerleştirin, örneğin: "adresler/{State}/{City}.</span><span class="sxs-lookup"><span data-stu-id="757cc-201">If you want a template that will not match the "extra" text, place the variable in a separate template segment, for example: "Addresses/{state}/{city}.</span></span>  
  
### <a name="named-wildcard-segments"></a><span data-ttu-id="757cc-202">Adlandırılmış joker kesimleri</span><span class="sxs-lookup"><span data-stu-id="757cc-202">Named Wildcard Segments</span></span>  

 <span data-ttu-id="757cc-203">Adlandırılmış joker karakter segmenti, değişken adı ' ' joker karakteriyle başlayan herhangi bir yol değişkeni segmentdir \* .</span><span class="sxs-lookup"><span data-stu-id="757cc-203">A named wildcard segment is any path variable segment whose variable name begins with the wildcard character ‘\*’.</span></span> <span data-ttu-id="757cc-204">Aşağıdaki şablon dizesi "Shoe" adlı adlandırılmış bir joker karakter segmentini içerir.</span><span class="sxs-lookup"><span data-stu-id="757cc-204">The following template string contains a named wildcard segment named "shoe".</span></span>  
  
`"literal/{*shoe}"`  
  
 <span data-ttu-id="757cc-205">Joker karakter kesimleri aşağıdaki kurallara uymalıdır:</span><span class="sxs-lookup"><span data-stu-id="757cc-205">Wildcard segments must follow the following rules:</span></span>  
  
- <span data-ttu-id="757cc-206">Her bir şablon dizesi için en fazla bir adlandırılmış joker karakter segmenti olabilir.</span><span class="sxs-lookup"><span data-stu-id="757cc-206">There can be at most one named wildcard segment for each template string.</span></span>  
  
- <span data-ttu-id="757cc-207">Adlandırılmış bir joker karakter segmenti, yoldaki en sağ kesimde görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="757cc-207">A named wildcard segment must appear at the right-most segment in the path.</span></span>  
  
- <span data-ttu-id="757cc-208">Adlandırılmış bir joker karakter segmenti aynı şablon dizesinde anonim bir joker karakterle birlikte bulunamaz.</span><span class="sxs-lookup"><span data-stu-id="757cc-208">A named wildcard segment cannot coexist with an anonymous wildcard segment within the same template string.</span></span>  
  
- <span data-ttu-id="757cc-209">Adlandırılmış bir joker karakter kesiminin adı benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="757cc-209">The name of a named wildcard segment must be unique.</span></span>  
  
- <span data-ttu-id="757cc-210">Adlandırılmış joker karakter kesimleri varsayılan değerlere sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="757cc-210">Named wildcard segments cannot have default values.</span></span>  
  
- <span data-ttu-id="757cc-211">Adlandırılmış joker kesimleri "/" ile bitemez.</span><span class="sxs-lookup"><span data-stu-id="757cc-211">Named wildcard segments cannot end with "/".</span></span>  
  
### <a name="default-variable-values"></a><span data-ttu-id="757cc-212">Varsayılan değişken değerleri</span><span class="sxs-lookup"><span data-stu-id="757cc-212">Default Variable Values</span></span>  

 <span data-ttu-id="757cc-213">Varsayılan değişken değerleri bir şablon içindeki değişkenler için varsayılan değerleri belirtmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="757cc-213">Default variable values allow you to specify default values for variables within a template.</span></span> <span data-ttu-id="757cc-214">Varsayılan değişkenler, değişkeni bildiren küme ayraçları ile veya UriTemplate oluşturucusuna geçirilen bir koleksiyon olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="757cc-214">Default variables can be specified with the curly braces that declare the variable or as a collection passed to the UriTemplate constructor.</span></span> <span data-ttu-id="757cc-215">Aşağıdaki şablonda, <xref:System.UriTemplate> varsayılan değerleri olan değişkenleri içeren bir belirtmek için iki yol gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="757cc-215">The following template shows two ways to specify a <xref:System.UriTemplate> with variables with default values.</span></span>  
  
```csharp
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 <span data-ttu-id="757cc-216">Bu şablon, varsayılan değeri olan adlı bir değişken `a` `1` ve `b` varsayılan değeri olan adlı bir değişken bildirir `5` .</span><span class="sxs-lookup"><span data-stu-id="757cc-216">This template declares a variable named `a` with a default value of `1` and a variable named `b` with a default value of `5`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="757cc-217">Yalnızca yol kesimi değişkenlerinin varsayılan değerlere sahip olmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="757cc-217">Only path segment variables are allowed to have default values.</span></span> <span data-ttu-id="757cc-218">Sorgu dizesi değişkenleri, bileşik kesim değişkenleri ve adlandırılmış joker dizeler varsayılan değerlere sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="757cc-218">Query string variables, compound segment variables, and named wildcard variables are not permitted to have default values.</span></span>  
  
 <span data-ttu-id="757cc-219">Aşağıdaki kod, bir aday URI ile eşleştirilirken varsayılan değişken değerlerinin nasıl işlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="757cc-219">The following code shows how default variable values are handled when matching a candidate URI.</span></span>  
  
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
> <span data-ttu-id="757cc-220">Gibi bir URI `http://localhost:8000///` , önceki kodda listelenen şablonla eşleşmez, ancak gibi BIR URI `http://localhost:8000/` .</span><span class="sxs-lookup"><span data-stu-id="757cc-220">A URI such as `http://localhost:8000///` does not match the template listed in the preceding code, however a URI such as `http://localhost:8000/` does.</span></span>  
  
 <span data-ttu-id="757cc-221">Aşağıdaki kod, bir şablon ile URI oluştururken varsayılan değişken değerlerinin nasıl işlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="757cc-221">The following code shows how default variable values are handled when creating a URI with a template.</span></span>  
  
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
  
<span data-ttu-id="757cc-222">Bir değişkene varsayılan değer verildiğinde, `null` bazı ek kısıtlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="757cc-222">When a variable is given a default value of `null` there are some additional constraints.</span></span> <span data-ttu-id="757cc-223">Değişken, `null` şablon dizesinin en sağ alt segmentinde yer alıyorsa veya segmentin sağ tarafındaki tüm segmentlerin varsayılan değerleri içeriyorsa, bir değişken varsayılan değeri olabilir `null` .</span><span class="sxs-lookup"><span data-stu-id="757cc-223">A variable can have a default value of `null` if the variable is contained within the right most segment of the template string or if all segments to the right of the segment have default values of `null`.</span></span> <span data-ttu-id="757cc-224">Aşağıda varsayılan değerleri olan geçerli şablon dizeleri verilmiştir `null` :</span><span class="sxs-lookup"><span data-stu-id="757cc-224">The following are valid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("shoe/{boat=null}");`

- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");`
  
- `UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");`

 <span data-ttu-id="757cc-225">Varsayılan değerleri geçersiz olan şablon dizeleri aşağıda verilmiştir `null` :</span><span class="sxs-lookup"><span data-stu-id="757cc-225">The following are invalid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment`
  
- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value`

### <a name="default-values-and-matching"></a><span data-ttu-id="757cc-226">Varsayılan değerler ve eşleştirme</span><span class="sxs-lookup"><span data-stu-id="757cc-226">Default Values and Matching</span></span>  

 <span data-ttu-id="757cc-227">Bir aday URI 'yi varsayılan değerlere sahip bir şablonla eşleştirirken, <xref:System.UriTemplateMatch.BoundVariables%2A> aday URI 'sinde değerler belirtilmemişse varsayılan değerler koleksiyona yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="757cc-227">When matching a candidate URI with a template that has default values, the default values are placed in the <xref:System.UriTemplateMatch.BoundVariables%2A> collection if values are not specified in the candidate URI.</span></span>  
  
### <a name="template-equivalence"></a><span data-ttu-id="757cc-228">Şablon denklik</span><span class="sxs-lookup"><span data-stu-id="757cc-228">Template Equivalence</span></span>  

 <span data-ttu-id="757cc-229">Tüm şablonların sabit değerleri eşleşiyorsa ve aynı kesimlerde değişkenler olduğunda, iki şablon *yapısal olarak eşdeğer* olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="757cc-229">Two templates are said to be *structurally equivalent* when all of the templates' literals match and they have variables in the same segments.</span></span> <span data-ttu-id="757cc-230">Örneğin, aşağıdaki şablonlar yapısal olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="757cc-230">For example the following templates are structurally equivalent:</span></span>  
  
- <span data-ttu-id="757cc-231">/a/{var1}/b b/{var2}? x = 1&y = 2</span><span class="sxs-lookup"><span data-stu-id="757cc-231">/a/{var1}/b b/{var2}?x=1&y=2</span></span>  
  
- <span data-ttu-id="757cc-232">a/{x}/b% 20B/{var1}? y = 2&x = 1</span><span class="sxs-lookup"><span data-stu-id="757cc-232">a/{x}/b%20b/{var1}?y=2&x=1</span></span>  
  
- <span data-ttu-id="757cc-233">a/{y}/B% 20B/{z}/? y = 2&x = 1</span><span class="sxs-lookup"><span data-stu-id="757cc-233">a/{y}/B%20B/{z}/?y=2&x=1</span></span>  
  
 <span data-ttu-id="757cc-234">Dikkat etmeniz gereken birkaç nokta vardır:</span><span class="sxs-lookup"><span data-stu-id="757cc-234">A few things to notice:</span></span>  
  
- <span data-ttu-id="757cc-235">Bir şablon önünde eğik çizgi içeriyorsa, yalnızca ilki yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="757cc-235">If a template contains leading slashes, only the first one is ignored.</span></span>  
  
- <span data-ttu-id="757cc-236">Yapısal denklik için şablon dizelerini karşılaştırırken, değişken adları ve yol kesimleri için durum yoksayıldı, sorgu dizeleri büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="757cc-236">When comparing template strings for structural equivalence, case is ignored for variable names and path segments, query strings are case sensitive.</span></span>  
  
- <span data-ttu-id="757cc-237">Sorgu dizeleri sırasız.</span><span class="sxs-lookup"><span data-stu-id="757cc-237">Query strings are unordered.</span></span>  
  
## <a name="uritemplatetable"></a><span data-ttu-id="757cc-238">UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="757cc-238">UriTemplateTable</span></span>  

 <span data-ttu-id="757cc-239"><xref:System.UriTemplateTable>Sınıfı, <xref:System.UriTemplate> geliştiricinin seçme nesnesine bağlantılı nesnelerin ilişkilendirilebilir tablosunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="757cc-239">The <xref:System.UriTemplateTable> class represents an associative table of <xref:System.UriTemplate> objects bound to an object of the developer's choosing.</span></span> <span data-ttu-id="757cc-240">' Nin <xref:System.UriTemplateTable> çağrılmadan önce en az bir tane içermesi gerekir <xref:System.UriTemplate> <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> .</span><span class="sxs-lookup"><span data-stu-id="757cc-240">A <xref:System.UriTemplateTable> must contain at least one <xref:System.UriTemplate> prior to calling <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span> <span data-ttu-id="757cc-241">Bir öğesinin içeriği <xref:System.UriTemplateTable> <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> çağrılana kadar değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="757cc-241">The contents of a <xref:System.UriTemplateTable> can be changed until <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="757cc-242">Çağrıldığında doğrulama gerçekleştirilir <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> .</span><span class="sxs-lookup"><span data-stu-id="757cc-242">Validation is performed when <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="757cc-243">Gerçekleştirilen doğrulamanın türü, parametresinin değerine bağlıdır `allowMultiple` <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> .</span><span class="sxs-lookup"><span data-stu-id="757cc-243">The type of validation performed depends upon the value of the `allowMultiple` parameter to <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span>  
  
 <span data-ttu-id="757cc-244"><xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>İçinde geçirme çağrıldığında, `false` <xref:System.UriTemplateTable> tabloda hiçbir şablon olmadığından emin olmak için kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="757cc-244">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `false`, the <xref:System.UriTemplateTable> checks to make sure there are no templates in the table.</span></span> <span data-ttu-id="757cc-245">Yapısal olarak eşdeğer şablonlar bulursa, bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="757cc-245">If it finds any structurally equivalent templates, it throws an exception.</span></span> <span data-ttu-id="757cc-246">Bu, bir <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> gelen URI ile eşleşen yalnızca bir şablonun olduğundan emin olmak istediğiniz zaman ile birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="757cc-246">This is used in conjunction with <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> when you want to ensure only one template matches an incoming URI.</span></span>  
  
 <span data-ttu-id="757cc-247"><xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>İçinde geçirme çağrıldığında `true` , <xref:System.UriTemplateTable> birden çok, yapısal olarak denk şablonların bir içinde yer almasına izin verir <xref:System.UriTemplateTable> .</span><span class="sxs-lookup"><span data-stu-id="757cc-247">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `true`, <xref:System.UriTemplateTable> allows multiple, structurally-equivalent templates to be contained within a <xref:System.UriTemplateTable>.</span></span>  
  
 <span data-ttu-id="757cc-248"><xref:System.UriTemplate>Bir nesne kümesine eklenen bir <xref:System.UriTemplateTable> sorgu dizesi varsa, bunların belirsiz olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="757cc-248">If a set of <xref:System.UriTemplate> objects added to a <xref:System.UriTemplateTable> contain query strings they must not be ambiguous.</span></span> <span data-ttu-id="757cc-249">Özdeş sorgu dizelerine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="757cc-249">Identical query strings are allowed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="757cc-250">HTTP dışındaki <xref:System.UriTemplateTable> şemaları kullanan temel adreslere izin verdiğinden, aday URI 'leri şablonlarla eşleştirilirken düzen ve bağlantı noktası numarası yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="757cc-250">While the <xref:System.UriTemplateTable> allows base addresses that use schemes other than HTTP, the scheme and port number are ignored when matching candidate URIs to templates.</span></span>  
  
### <a name="query-string-ambiguity"></a><span data-ttu-id="757cc-251">Sorgu dizesi belirsizlik</span><span class="sxs-lookup"><span data-stu-id="757cc-251">Query String Ambiguity</span></span>  

 <span data-ttu-id="757cc-252">Bir eşdeğer yolu paylaşan şablonlar, birden fazla şablonla eşleşen bir URI varsa belirsiz sorgu dizeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="757cc-252">Templates that share an equivalent path contain ambiguous query strings if there is a URI that matches more than one template.</span></span>  
  
 <span data-ttu-id="757cc-253">Aşağıdaki sorgu dizeleri kümeleri kendi içinde belirsiz:</span><span class="sxs-lookup"><span data-stu-id="757cc-253">The following sets of query strings are unambiguous within themselves:</span></span>  
  
- <span data-ttu-id="757cc-254">? x = 1</span><span class="sxs-lookup"><span data-stu-id="757cc-254">?x=1</span></span>  
  
- <span data-ttu-id="757cc-255">? x = 2</span><span class="sxs-lookup"><span data-stu-id="757cc-255">?x=2</span></span>  
  
- <span data-ttu-id="757cc-256">? x = 3</span><span class="sxs-lookup"><span data-stu-id="757cc-256">?x=3</span></span>  
  
- <span data-ttu-id="757cc-257">? x = 1&y = {var}</span><span class="sxs-lookup"><span data-stu-id="757cc-257">?x=1&y={var}</span></span>  
  
- <span data-ttu-id="757cc-258">? x = 2&z = {var}</span><span class="sxs-lookup"><span data-stu-id="757cc-258">?x=2&z={var}</span></span>  
  
- <span data-ttu-id="757cc-259">? x = 3</span><span class="sxs-lookup"><span data-stu-id="757cc-259">?x=3</span></span>  
  
- <span data-ttu-id="757cc-260">? x = 1</span><span class="sxs-lookup"><span data-stu-id="757cc-260">?x=1</span></span>  
  
- <span data-ttu-id="757cc-261">?</span><span class="sxs-lookup"><span data-stu-id="757cc-261">?</span></span>  
  
- <span data-ttu-id="757cc-262">?</span><span class="sxs-lookup"><span data-stu-id="757cc-262">?</span></span> <span data-ttu-id="757cc-263">x = {var}</span><span class="sxs-lookup"><span data-stu-id="757cc-263">x={var}</span></span>  
  
- <span data-ttu-id="757cc-264">?</span><span class="sxs-lookup"><span data-stu-id="757cc-264">?</span></span>  
  
- <span data-ttu-id="757cc-265">? m = Get&c = RSS</span><span class="sxs-lookup"><span data-stu-id="757cc-265">?m=get&c=rss</span></span>  
  
- <span data-ttu-id="757cc-266">? m = put&c = RSS</span><span class="sxs-lookup"><span data-stu-id="757cc-266">?m=put&c=rss</span></span>  
  
- <span data-ttu-id="757cc-267">? m = Get&c = atom</span><span class="sxs-lookup"><span data-stu-id="757cc-267">?m=get&c=atom</span></span>  
  
- <span data-ttu-id="757cc-268">? m = put&c = atom</span><span class="sxs-lookup"><span data-stu-id="757cc-268">?m=put&c=atom</span></span>  
  
 <span data-ttu-id="757cc-269">Aşağıdaki sorgu dizesi şablonları kümeleri kendileri içinde belirsizdir:</span><span class="sxs-lookup"><span data-stu-id="757cc-269">The following sets of query string templates are ambiguous within themselves:</span></span>  
  
- <span data-ttu-id="757cc-270">? x = 1</span><span class="sxs-lookup"><span data-stu-id="757cc-270">?x=1</span></span>  
  
- <span data-ttu-id="757cc-271">? x = {var}</span><span class="sxs-lookup"><span data-stu-id="757cc-271">?x={var}</span></span>  
  
 <span data-ttu-id="757cc-272">"x = 1"-her iki şablon da eşleşir.</span><span class="sxs-lookup"><span data-stu-id="757cc-272">"x=1" - Matches both templates.</span></span>  
  
- <span data-ttu-id="757cc-273">? x = 1</span><span class="sxs-lookup"><span data-stu-id="757cc-273">?x=1</span></span>  
  
- <span data-ttu-id="757cc-274">? y = 2</span><span class="sxs-lookup"><span data-stu-id="757cc-274">?y=2</span></span>  
  
 <span data-ttu-id="757cc-275">"x = 1&y = 2", her iki şablonlarla de eşleşir.</span><span class="sxs-lookup"><span data-stu-id="757cc-275">"x=1&y=2" matches both templates.</span></span> <span data-ttu-id="757cc-276">Bunun nedeni, bir sorgu dizesinin daha fazla sorgu dizesi değişkeni içermesi olabilir ve bundan sonra eşleşen şablondur.</span><span class="sxs-lookup"><span data-stu-id="757cc-276">This is because a query string may contain more query string variables then the template it matches.</span></span>  
  
- <span data-ttu-id="757cc-277">? x = 1</span><span class="sxs-lookup"><span data-stu-id="757cc-277">?x=1</span></span>  
  
- <span data-ttu-id="757cc-278">? x = 1&y = {var}</span><span class="sxs-lookup"><span data-stu-id="757cc-278">?x=1&y={var}</span></span>  
  
 <span data-ttu-id="757cc-279">"x = 1&y = 3" her iki şablonlarla de eşleşir.</span><span class="sxs-lookup"><span data-stu-id="757cc-279">"x=1&y=3" matches both templates.</span></span>  
  
- <span data-ttu-id="757cc-280">? x = 3&y = 4</span><span class="sxs-lookup"><span data-stu-id="757cc-280">?x=3&y=4</span></span>  
  
- <span data-ttu-id="757cc-281">? x = 3&z = 5</span><span class="sxs-lookup"><span data-stu-id="757cc-281">?x=3&z=5</span></span>  
  
> [!NOTE]
> <span data-ttu-id="757cc-282">Á ve Á karakterleri, bir URI yolu veya yol segmenti değişmez değerinin bir parçası olarak görüntülendiklerinde farklı karakterler olarak değerlendirilir <xref:System.UriTemplate> (ancak a ve a karakterleri aynı olduğu kabul edilir).</span><span class="sxs-lookup"><span data-stu-id="757cc-282">The characters á and Á are considered to be different characters when they appear as part of a URI path or <xref:System.UriTemplate> path segment literal (but the characters a and A are considered to be the same).</span></span> <span data-ttu-id="757cc-283">Á ve Á karakterleri, bir <xref:System.UriTemplate> {VariableName} veya bir sorgu dizesinin (ve ' de aynı karakterler olarak kabul edilir) bir parçası olarak göründükleri karakterlerle aynı karakterler olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="757cc-283">The characters á and Á are considered to be the same characters when they appear as part of a <xref:System.UriTemplate> {variableName} or a query string (and a and A are also considered to be the same characters).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="757cc-284">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="757cc-284">See also</span></span>

- [<span data-ttu-id="757cc-285">WCF Web HTTP Programlama Modeli Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="757cc-285">WCF Web HTTP Programming Model Overview</span></span>](wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="757cc-286">WCF Web HTTP Programlama Nesnesi Modeli</span><span class="sxs-lookup"><span data-stu-id="757cc-286">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)
- [<span data-ttu-id="757cc-287">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="757cc-287">UriTemplate</span></span>](../samples/uritemplate-sample.md)
- [<span data-ttu-id="757cc-288">UriTemplate Tablosu</span><span class="sxs-lookup"><span data-stu-id="757cc-288">UriTemplate Table</span></span>](../samples/uritemplate-table-sample.md)
- [<span data-ttu-id="757cc-289">UriTemplate Tablosu Dağıtıcısı</span><span class="sxs-lookup"><span data-stu-id="757cc-289">UriTemplate Table Dispatcher</span></span>](../samples/uritemplate-table-dispatcher-sample.md)
