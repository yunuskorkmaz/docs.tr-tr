---
title: UriTemplate ve UriTemplateTable
ms.date: 03/30/2017
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
ms.openlocfilehash: f51d6fa5c78d97cf11a3c0005be7656013b30e90
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955277"
---
# <a name="uritemplate-and-uritemplatetable"></a><span data-ttu-id="82065-102">UriTemplate ve UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="82065-102">UriTemplate and UriTemplateTable</span></span>
<span data-ttu-id="82065-103">Web geliştiricileri, hizmetlerinin yanıt verdiği URI 'lerin şeklini ve yerleşimini betimleyebilme olanağı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="82065-103">Web developers require the ability to describe the shape and layout of the URIs that their services respond to.</span></span> <span data-ttu-id="82065-104">Windows Communication Foundation (WCF), geliştiricilerin URI 'lerinde denetim sağlamak için iki yeni sınıf ekledi.</span><span class="sxs-lookup"><span data-stu-id="82065-104">Windows Communication Foundation (WCF) added two new classes to give developers control over their URIs.</span></span> <span data-ttu-id="82065-105"><xref:System.UriTemplate>ve <xref:System.UriTemplateTable> WCF 'de URI tabanlı dağıtım altyapısının temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="82065-105"><xref:System.UriTemplate> and <xref:System.UriTemplateTable> form the basis of the URI-based dispatch engine in WCF.</span></span> <span data-ttu-id="82065-106">Bu sınıflar kendi kendilerine de kullanılabilir, geliştiricilerin bir WCF hizmeti uygulamadan şablonlardan ve URI eşleme mekanizmasından yararlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="82065-106">These classes can also be used on their own, allowing developers to take advantage of templates and the URI mapping mechanism without implementing a WCF service.</span></span>  
  
## <a name="templates"></a><span data-ttu-id="82065-107">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="82065-107">Templates</span></span>  
 <span data-ttu-id="82065-108">Şablon, göreli URI 'lerin bir kümesini tanımlamaya yönelik bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="82065-108">A template is a way to describe a set of relative URIs.</span></span> <span data-ttu-id="82065-109">Aşağıdaki tabloda yer alan URI şablonları kümesi, çeşitli hava durumu bilgilerini alan bir sistemin nasıl tanımlanabilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="82065-109">The set of URI templates in the following table shows how a system that retrieves various types of weather information might be defined.</span></span>  
  
|<span data-ttu-id="82065-110">Veri</span><span class="sxs-lookup"><span data-stu-id="82065-110">Data</span></span>|<span data-ttu-id="82065-111">Şablon</span><span class="sxs-lookup"><span data-stu-id="82065-111">Template</span></span>|  
|----------|--------------|  
|<span data-ttu-id="82065-112">Ulusal tahmin</span><span class="sxs-lookup"><span data-stu-id="82065-112">National Forecast</span></span>|<span data-ttu-id="82065-113">Hava durumu/Ulusal</span><span class="sxs-lookup"><span data-stu-id="82065-113">weather/national</span></span>|  
|<span data-ttu-id="82065-114">Durum tahmini</span><span class="sxs-lookup"><span data-stu-id="82065-114">State Forecast</span></span>|<span data-ttu-id="82065-115">Hava durumu/{State}</span><span class="sxs-lookup"><span data-stu-id="82065-115">weather/{state}</span></span>|  
|<span data-ttu-id="82065-116">Şehir tahmini</span><span class="sxs-lookup"><span data-stu-id="82065-116">City Forecast</span></span>|<span data-ttu-id="82065-117">Hava durumu/{State}/{City}</span><span class="sxs-lookup"><span data-stu-id="82065-117">weather/{state}/{city}</span></span>|  
|<span data-ttu-id="82065-118">Etkinlik tahmini</span><span class="sxs-lookup"><span data-stu-id="82065-118">Activity Forecast</span></span>|<span data-ttu-id="82065-119">Hava durumu/{State}/{City}/{Activity}</span><span class="sxs-lookup"><span data-stu-id="82065-119">weather/{state}/{city}/{activity}</span></span>|  
  
 <span data-ttu-id="82065-120">Bu tablo yapısal olarak benzer URI 'Ler kümesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="82065-120">This table describes a set of structurally similar URIs.</span></span> <span data-ttu-id="82065-121">Her giriş bir URI şablonudur.</span><span class="sxs-lookup"><span data-stu-id="82065-121">Each entry is a URI template.</span></span> <span data-ttu-id="82065-122">Küme ayraçları içindeki segmentler değişkenleri anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="82065-122">The segments in curly braces describe variables.</span></span> <span data-ttu-id="82065-123">Küme ayraçları içinde olmayan kesimler, değişmez dizeleri tanımlıyor.</span><span class="sxs-lookup"><span data-stu-id="82065-123">The segments not in curly braces describe literal strings.</span></span> <span data-ttu-id="82065-124">WCF şablon sınıfları, bir geliştiricinin gelen URI 'yi (örneğin, "/Weather/WA/Seattle/Cycling") alıp onu açıklayan bir şablonla eşleştirmek için "/dalgalı ther/{State}/{City}/{Activity}" sağlar.</span><span class="sxs-lookup"><span data-stu-id="82065-124">The WCF template classes allow a developer to take an incoming URI, for example, "/weather/wa/seattle/cycling", and match it to a template that describes it, "/weather/{state}/{city}/{activity}".</span></span>  
  
## <a name="uritemplate"></a><span data-ttu-id="82065-125">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="82065-125">UriTemplate</span></span>  
 <span data-ttu-id="82065-126"><xref:System.UriTemplate>, bir URI şablonunu kapsülleyen bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="82065-126"><xref:System.UriTemplate> is a class that encapsulates a URI template.</span></span> <span data-ttu-id="82065-127">Oluşturucu, şablonu tanımlayan bir dize parametresi alır.</span><span class="sxs-lookup"><span data-stu-id="82065-127">The constructor takes a string parameter that defines the template.</span></span> <span data-ttu-id="82065-128">Bu dize, sonraki bölümde açıklanan biçimdeki şablonu içerir.</span><span class="sxs-lookup"><span data-stu-id="82065-128">This string contains the template in the format described in the next section.</span></span> <span data-ttu-id="82065-129"><xref:System.UriTemplate> Sınıfı, bir şablon için gelen URI 'yi eşleştirmek, şablondan URI oluşturmak, şablonda kullanılan değişken adlarından oluşan bir koleksiyonu almak, iki şablonun eşdeğer olup olmadığını tespit etmek ve şablonu geri döndürmeksizin dizisinde.</span><span class="sxs-lookup"><span data-stu-id="82065-129">The <xref:System.UriTemplate> class provides methods that allow you match an incoming URI to a template, generate a URI from a template, retrieve a collection of variable names used in the template, determine whether two templates are equivalent, and return the template's string.</span></span>  
  
 <span data-ttu-id="82065-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29>temel bir adresi ve aday URI 'yi alır ve URI 'yi şablonla eşleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="82065-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> takes a base address and a candidate URI and attempts to match the URI to the template.</span></span> <span data-ttu-id="82065-131">Eşleşme başarılı olursa bir <xref:System.UriTemplateMatch> örnek döndürülür.</span><span class="sxs-lookup"><span data-stu-id="82065-131">If the match is successful, a <xref:System.UriTemplateMatch> instance is returned.</span></span> <span data-ttu-id="82065-132">Nesne, temel bir URI, aday URI, sorgu parametrelerinin bir ad/değer koleksiyonu, göreli yol segmentlerinin bir dizisi, eşleşen <xref:System.UriTemplate> değişkenlerin bir ad/değer koleksiyonu, eşleşme gerçekleştirmek için kullanılan örnek <xref:System.UriTemplateMatch> , aday URI 'nin eşleşmeyen bir kısmını (şablon bir joker karakter olduğunda kullanılır) ve şablonuyla ilişkili bir nesneyi içeren bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="82065-132">The <xref:System.UriTemplateMatch> object contains a base URI, the candidate URI, a name/value collection of the query parameters, an array of the relative path segments, a name/value collection of variables that were matched, the <xref:System.UriTemplate> instance used to perform the match, a string that contains any unmatched portion of the candidate URI (used when the template has a wildcard), and an object that is associated with the template.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82065-133"><xref:System.UriTemplate> Sınıf, bir aday URI 'yi bir şablonla eşleştirirken düzen ve bağlantı noktası numarasını yoksayar.</span><span class="sxs-lookup"><span data-stu-id="82065-133">The <xref:System.UriTemplate> class ignores the scheme and port number when matching a candidate URI to a template.</span></span>  
  
 <span data-ttu-id="82065-134">Bir şablondan <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> URI oluşturmanıza izin veren iki yöntem vardır ve <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span><span class="sxs-lookup"><span data-stu-id="82065-134">There are two methods that allow you to generate a URI from a template, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> and <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span></span> <span data-ttu-id="82065-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29>bir taban adresi ve parametrelerin ad/değer koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="82065-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> takes a base address and a name/value collection of parameters.</span></span> <span data-ttu-id="82065-136">Bu parametreler, şablon bağlandığında değişkenler için değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="82065-136">These parameters are substituted for variables when the template is bound.</span></span> <span data-ttu-id="82065-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>ad/değer çiftlerini alır ve bunları soldan sağa koyar.</span><span class="sxs-lookup"><span data-stu-id="82065-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> takes the name/value pairs and substitutes them left to right.</span></span>  
  
 <span data-ttu-id="82065-138"><xref:System.UriTemplate.ToString>Şablon dizesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="82065-138"><xref:System.UriTemplate.ToString> returns the template string.</span></span>  
  
 <span data-ttu-id="82065-139"><xref:System.UriTemplate.PathSegmentVariableNames%2A> Özelliği, şablon dizesindeki yol kesimleri içinde kullanılan değişkenlerin adlarının bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="82065-139">The <xref:System.UriTemplate.PathSegmentVariableNames%2A> property contains a collection of the names of the variables used within path segments in the template string.</span></span>  
  
 <span data-ttu-id="82065-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29>bir <xref:System.UriTemplate> parametresini parametre olarak alır ve iki şablonun eşdeğer olup olmadığını belirten bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="82065-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> takes a <xref:System.UriTemplate> as a parameter and returns a Boolean value that specifies whether the two templates are equivalent.</span></span> <span data-ttu-id="82065-141">Daha fazla bilgi için bu konunun ilerleyen kısımlarında yer alarak şablon denklik bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="82065-141">For more information, see the Template Equivalence section later in this topic.</span></span>  
  
 <span data-ttu-id="82065-142"><xref:System.UriTemplate>, HTTP URI dilbilgisine uygun herhangi bir URI şeması ile çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="82065-142"><xref:System.UriTemplate> is designed to work with any URI scheme that conforms to the HTTP URI grammar.</span></span> <span data-ttu-id="82065-143">Aşağıda desteklenen URI düzenlerinin örnekleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="82065-143">The following are examples of supported URI schemes.</span></span>  
  
- <span data-ttu-id="82065-144">http://</span><span class="sxs-lookup"><span data-stu-id="82065-144">http://</span></span>  
  
- <span data-ttu-id="82065-145">https://</span><span class="sxs-lookup"><span data-stu-id="82065-145">https://</span></span>  
  
- <span data-ttu-id="82065-146">net.tcp://</span><span class="sxs-lookup"><span data-stu-id="82065-146">net.tcp://</span></span>  
  
- <span data-ttu-id="82065-147">net.pipe://</span><span class="sxs-lookup"><span data-stu-id="82065-147">net.pipe://</span></span>  
  
- <span data-ttu-id="82065-148">sb://</span><span class="sxs-lookup"><span data-stu-id="82065-148">sb://</span></span>  
  
 <span data-ttu-id="82065-149">File://ve urn://gibi düzenler HTTP URI dilbilgisine uymuyor ve URI şablonlarıyla birlikte kullanıldığında öngörülemeyen sonuçlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="82065-149">Schemes like file:// and urn:// do not conform to the HTTP URI grammar and cause unpredictable results when used with URI templates.</span></span>  
  
### <a name="template-string-syntax"></a><span data-ttu-id="82065-150">Şablon dizesi sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82065-150">Template String Syntax</span></span>  
 <span data-ttu-id="82065-151">Şablon üç bölümden oluşur: yol, isteğe bağlı sorgu ve isteğe bağlı bir parça.</span><span class="sxs-lookup"><span data-stu-id="82065-151">A template has three parts: a path, an optional query, and an optional fragment.</span></span> <span data-ttu-id="82065-152">Bir örnek için, aşağıdaki şablona bakın:</span><span class="sxs-lookup"><span data-stu-id="82065-152">For an example, see the following template:</span></span>  
  
```  
"/weather/{state}/{city}?forecast={length)#frag1  
```  
  
 <span data-ttu-id="82065-153">Yol "/dalgalı ther/{State}/{City}" bilgisinden oluşur, sorgu "? tahmine = {length} ve parça" #frag1 "bilgisinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="82065-153">The path consists of "/weather/{state}/{city}", the query consists of "?forecast={length}, and the fragment consists of "#frag1".</span></span>  
  
 <span data-ttu-id="82065-154">Yol ifadesinde öndeki ve sondaki eğik çizgiler isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="82065-154">Leading and trailing slashes are optional in the path expression.</span></span> <span data-ttu-id="82065-155">Hem sorgu hem de parça ifadeleri tamamen atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="82065-155">Both the query and fragment expressions can be omitted entirely.</span></span> <span data-ttu-id="82065-156">Bir yol, '/' ile ayrılmış bir dizi kesimden oluşur, her segment bir sabit değer, değişken adı ({küme ayraçları} içinde yazılmış) veya joker karakter ('\*' olarak yazılmış) olabilir.</span><span class="sxs-lookup"><span data-stu-id="82065-156">A path consists of a series of segments delimited by '/', each segment can have a literal value, a variable name (written in {curly braces}), or a wildcard (written as '\*').</span></span> <span data-ttu-id="82065-157">Önceki şablonda, "{State}" ve "{City}" değişkenleri olan "\dalgalı ther\ segmenti değişmez değer değeridir.</span><span class="sxs-lookup"><span data-stu-id="82065-157">In the previous template the "\weather\ segment is a literal value while "{state}" and "{city}" are variables.</span></span> <span data-ttu-id="82065-158">Değişkenler, bunların adlarını kendi küme ayraçları içeriğinden alır ve daha sonra *kapalı bır URI*oluşturmak için somut bir değer ile değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="82065-158">Variables take their name from the contents of their curly braces and they can later be replaced with a concrete value to create a *closed URI*.</span></span> <span data-ttu-id="82065-159">Joker karakter isteğe bağlıdır, ancak yalnızca URI sonunda görünebilir, burada "yolun geri kalanı" ile mantıksal olarak eşleşir.</span><span class="sxs-lookup"><span data-stu-id="82065-159">The wildcard is optional, but can only appear at the end of the URI, where it logically matches "the rest of the path".</span></span>  
  
 <span data-ttu-id="82065-160">Sorgu ifadesi varsa, ' & ' ile ayrılmış bir sıralı ad/değer çiftleri serisi belirtir.</span><span class="sxs-lookup"><span data-stu-id="82065-160">The query expression, if present, specifies a series of unordered name/value pairs delimited by '&'.</span></span> <span data-ttu-id="82065-161">Sorgu ifadesinin öğeleri, sabit değer çiftleri (x = 2) veya bir değişken çifti (x = {var}) olabilir.</span><span class="sxs-lookup"><span data-stu-id="82065-161">Elements of the query expression can either be literal pairs (x=2) or a variable pair (x={var}).</span></span> <span data-ttu-id="82065-162">Sorgunun yalnızca sağ tarafında bir değişken ifadesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="82065-162">Only the right side of the query can have a variable expression.</span></span> <span data-ttu-id="82065-163">({someName} = {someValue} öğesine izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="82065-163">({someName} = {someValue} is not allowed.</span></span> <span data-ttu-id="82065-164">Eşlenmemiş değerlere (? x) izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="82065-164">Unpaired values (?x) are not permitted.</span></span> <span data-ttu-id="82065-165">Boş bir sorgu ifadesi ve yalnızca tek bir '? ' içeren bir sorgu ifadesi arasında fark yoktur (her ikisi de "herhangi bir sorgu").</span><span class="sxs-lookup"><span data-stu-id="82065-165">There is no difference between an empty query expression and a query expression consisting of just a single '?' (both mean "any query").</span></span>  
  
 <span data-ttu-id="82065-166">Parça ifadesi bir değişmez değerden oluşabilir, hiçbir değişkene izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="82065-166">The fragment expression can consist of a literal value, no variables are allowed.</span></span>  
  
 <span data-ttu-id="82065-167">Bir şablon dizesi içindeki tüm şablon değişken adları benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="82065-167">All template variable names within a template string must be unique.</span></span> <span data-ttu-id="82065-168">Şablon değişken adları büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="82065-168">Template variable names are case-insensitive.</span></span>  
  
 <span data-ttu-id="82065-169">Geçerli şablon dizeleri örnekleri:</span><span class="sxs-lookup"><span data-stu-id="82065-169">Examples of valid template strings:</span></span>  
  
- <span data-ttu-id="82065-170">""</span><span class="sxs-lookup"><span data-stu-id="82065-170">""</span></span>  
  
- <span data-ttu-id="82065-171">"/Shoe"</span><span class="sxs-lookup"><span data-stu-id="82065-171">"/shoe"</span></span>  
  
- <span data-ttu-id="82065-172">"/Shoe/\*"</span><span class="sxs-lookup"><span data-stu-id="82065-172">"/shoe/\*"</span></span>  
  
- <span data-ttu-id="82065-173">"{Shoe}/bot"</span><span class="sxs-lookup"><span data-stu-id="82065-173">"{shoe}/boat"</span></span>  
  
- <span data-ttu-id="82065-174">"{Shoe}/{Boat}/Bed/{Quilt}"</span><span class="sxs-lookup"><span data-stu-id="82065-174">"{shoe}/{boat}/bed/{quilt}"</span></span>  
  
- <span data-ttu-id="82065-175">"Shoe/{bot}"</span><span class="sxs-lookup"><span data-stu-id="82065-175">"shoe/{boat}"</span></span>  
  
- <span data-ttu-id="82065-176">"Shoe/{bot}/\*"</span><span class="sxs-lookup"><span data-stu-id="82065-176">"shoe/{boat}/\*"</span></span>  
  
- <span data-ttu-id="82065-177">"Shoe/bot? x = 2"</span><span class="sxs-lookup"><span data-stu-id="82065-177">"shoe/boat?x=2"</span></span>  
  
- <span data-ttu-id="82065-178">"Shoe/{bot}? x = {yatak}"</span><span class="sxs-lookup"><span data-stu-id="82065-178">"shoe/{boat}?x={bed}"</span></span>  
  
- <span data-ttu-id="82065-179">"Shoe/{bot}? x = {yatak} & y = bant"</span><span class="sxs-lookup"><span data-stu-id="82065-179">"shoe/{boat}?x={bed}&y=band"</span></span>  
  
- <span data-ttu-id="82065-180">"? x = {Shoe}"</span><span class="sxs-lookup"><span data-stu-id="82065-180">"?x={shoe}"</span></span>  
  
- <span data-ttu-id="82065-181">"Shoe? x = 3 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="82065-181">"shoe?x=3&y={var}</span></span>  
  
 <span data-ttu-id="82065-182">Geçersiz şablon dizeleri örnekleri:</span><span class="sxs-lookup"><span data-stu-id="82065-182">Examples of invalid template strings:</span></span>  
  
- <span data-ttu-id="82065-183">"{Shoe}/{SHOE}/x = 2" – yinelenen değişken adları.</span><span class="sxs-lookup"><span data-stu-id="82065-183">"{shoe}/{SHOE}/x=2" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="82065-184">"{Shoe}/Boat/? yatak = {Shoe}"-yinelenen değişken adları.</span><span class="sxs-lookup"><span data-stu-id="82065-184">"{shoe}/boat/?bed={shoe}" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="82065-185">"? x = 2 & x = 3" – bir sorgu dizesi içindeki ad/değer çiftleri, değişmez değerler olsa bile benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="82065-185">"?x=2&x=3" – Name/value pairs within a query string must be unique, even if they are literals.</span></span>  
  
- <span data-ttu-id="82065-186">"? x = 2 &" – sorgu dizesi hatalı biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="82065-186">"?x=2&" – Query string is malformed.</span></span>  
  
- <span data-ttu-id="82065-187">"? 2 & x = {Shoe}" – sorgu dizesi ad/değer çiftleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="82065-187">"?2&x={shoe}" – Query string must be name/value pairs.</span></span>  
  
- <span data-ttu-id="82065-188">"? y = 2 & & X = 3" – sorgu dizesi ad değer çiftleri olmalıdır, adlar ' & ' ile başlayamaz.</span><span class="sxs-lookup"><span data-stu-id="82065-188">"?y=2&&X=3" – Query string must be name value pairs, names cannot start with '&'.</span></span>  
  
### <a name="compound-path-segments"></a><span data-ttu-id="82065-189">Bileşik yol kesimleri</span><span class="sxs-lookup"><span data-stu-id="82065-189">Compound Path Segments</span></span>  
 <span data-ttu-id="82065-190">Bileşik yol kesimleri, tek bir URI yol segmentinin birden çok değişken ve değişmez değerler ile birleştirilmiş değişkenler içermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="82065-190">Compound path segments allow a single URI path segment to contain multiple variables as well as variables combined with literals.</span></span> <span data-ttu-id="82065-191">Aşağıda geçerli bileşik yol segmentlerinin örnekleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="82065-191">The following are examples of valid compound path segments.</span></span>  
  
- <span data-ttu-id="82065-192">kısaltın. {ext}/</span><span class="sxs-lookup"><span data-stu-id="82065-192">/filename.{ext}/</span></span>  
  
- <span data-ttu-id="82065-193">/{filename}.exe jpg/</span><span class="sxs-lookup"><span data-stu-id="82065-193">/{filename}.jpg/</span></span>  
  
- <span data-ttu-id="82065-194">kısaltın. {ext}/</span><span class="sxs-lookup"><span data-stu-id="82065-194">/{filename}.{ext}/</span></span>  
  
- <span data-ttu-id="82065-195">a. {b} someLiteral {c} ({d})/</span><span class="sxs-lookup"><span data-stu-id="82065-195">/{a}.{b}someLiteral{c}({d})/</span></span>  
  
 <span data-ttu-id="82065-196">Aşağıda geçersiz yol kesimlerinin örnekleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="82065-196">The following are examples of invalid path segments.</span></span>  
  
- <span data-ttu-id="82065-197">/{} -Değişkenlerin adlandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="82065-197">/{} - Variables must be named.</span></span>  
  
- <span data-ttu-id="82065-198">/{Shoe}{Boat}-değişkenlerin bir sabit değer ile ayrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="82065-198">/{shoe}{boat} - Variables must be separated by a literal.</span></span>  
  
### <a name="matching-and-compound-path-segments"></a><span data-ttu-id="82065-199">Eşleşen ve bileşik yol kesimleri</span><span class="sxs-lookup"><span data-stu-id="82065-199">Matching and Compound Path Segments</span></span>  
 <span data-ttu-id="82065-200">Bileşik yol kesimleri, tek bir yol segmentinde birden çok değişken içeren bir UriTemplate tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="82065-200">Compound path segments allow you to define a UriTemplate that has multiple variables within a single path segment.</span></span> <span data-ttu-id="82065-201">Örneğin, aşağıdaki şablon dizesinde: "Adresler/{State}. {City} "iki değişken (eyalet ve şehir) aynı segment içinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="82065-201">For example, in the following template string: "Addresses/{state}.{city}" two variables (state and city) are defined within the same segment.</span></span> <span data-ttu-id="82065-202">Bu şablon gibi bir URL `http://example.com/Washington.Redmond` ile eşleşir, ancak aynı zamanda gibi bir `http://example.com/Washington.Redmond.Microsoft`URL ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="82065-202">This template would match a URL such as `http://example.com/Washington.Redmond` but it will also match an URL like `http://example.com/Washington.Redmond.Microsoft`.</span></span> <span data-ttu-id="82065-203">İkinci durumda, durum değişkeni "Washington" ve City değişkeni "Redmond. Microsoft" içerecektir.</span><span class="sxs-lookup"><span data-stu-id="82065-203">In the latter case, the state variable will contain "Washington" and the city variable will contain "Redmond.Microsoft".</span></span> <span data-ttu-id="82065-204">Bu durumda, herhangi bir metin ('/' hariç) {City} değişkeniyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="82065-204">In this case any text (except ‘/’) will match the {city} variable.</span></span> <span data-ttu-id="82065-205">"Ekstra" metinle eşleşmeyen bir şablon istiyorsanız, değişkeni ayrı bir şablon segmentine yerleştirin, örneğin: "Adresler/{State}/{City}.</span><span class="sxs-lookup"><span data-stu-id="82065-205">If you want a template that will not match the "extra" text, place the variable in a separate template segment, for example: "Addresses/{state}/{city}.</span></span>  
  
### <a name="named-wildcard-segments"></a><span data-ttu-id="82065-206">Adlandırılmış joker kesimleri</span><span class="sxs-lookup"><span data-stu-id="82065-206">Named Wildcard Segments</span></span>  
 <span data-ttu-id="82065-207">Adlandırılmış joker karakter segmenti, değişken adı '\*' joker karakteriyle başlayan herhangi bir yol değişkeni segmentdir.</span><span class="sxs-lookup"><span data-stu-id="82065-207">A named wildcard segment is any path variable segment whose variable name begins with the wildcard character ‘\*’.</span></span> <span data-ttu-id="82065-208">Aşağıdaki şablon dizesi "Shoe" adlı adlandırılmış bir joker karakter segmentini içerir.</span><span class="sxs-lookup"><span data-stu-id="82065-208">The following template string contains a named wildcard segment named "shoe".</span></span>  
  
```  
"literal/{*shoe}"  
```  
  
 <span data-ttu-id="82065-209">Joker karakter kesimleri aşağıdaki kurallara uymalıdır:</span><span class="sxs-lookup"><span data-stu-id="82065-209">Wildcard segments must follow the following rules:</span></span>  
  
- <span data-ttu-id="82065-210">Her bir şablon dizesi için en fazla bir adlandırılmış joker karakter segmenti olabilir.</span><span class="sxs-lookup"><span data-stu-id="82065-210">There can be at most one named wildcard segment for each template string.</span></span>  
  
- <span data-ttu-id="82065-211">Adlandırılmış bir joker karakter segmenti, yoldaki en sağ kesimde görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="82065-211">A named wildcard segment must appear at the right-most segment in the path.</span></span>  
  
- <span data-ttu-id="82065-212">Adlandırılmış bir joker karakter segmenti aynı şablon dizesinde anonim bir joker karakterle birlikte bulunamaz.</span><span class="sxs-lookup"><span data-stu-id="82065-212">A named wildcard segment cannot coexist with an anonymous wildcard segment within the same template string.</span></span>  
  
- <span data-ttu-id="82065-213">Adlandırılmış bir joker karakter kesiminin adı benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="82065-213">The name of a named wildcard segment must be unique.</span></span>  
  
- <span data-ttu-id="82065-214">Adlandırılmış joker karakter kesimleri varsayılan değerlere sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="82065-214">Named wildcard segments cannot have default values.</span></span>  
  
- <span data-ttu-id="82065-215">Adlandırılmış joker kesimleri "/" ile bitemez.</span><span class="sxs-lookup"><span data-stu-id="82065-215">Named wildcard segments cannot end with "/".</span></span>  
  
### <a name="default-variable-values"></a><span data-ttu-id="82065-216">Varsayılan değişken değerleri</span><span class="sxs-lookup"><span data-stu-id="82065-216">Default Variable Values</span></span>  
 <span data-ttu-id="82065-217">Varsayılan değişken değerleri bir şablon içindeki değişkenler için varsayılan değerleri belirtmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="82065-217">Default variable values allow you to specify default values for variables within a template.</span></span> <span data-ttu-id="82065-218">Varsayılan değişkenler, değişkeni bildiren küme ayraçları ile veya UriTemplate oluşturucusuna geçirilen bir koleksiyon olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="82065-218">Default variables can be specified with the curly braces that declare the variable or as a collection passed to the UriTemplate constructor.</span></span> <span data-ttu-id="82065-219">Aşağıdaki şablonda, varsayılan değerleri olan değişkenleri içeren bir <xref:System.UriTemplate> belirtmek için iki yol gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="82065-219">The following template shows two ways to specify a <xref:System.UriTemplate> with variables with default values.</span></span>  
  
```csharp
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 <span data-ttu-id="82065-220">`a` Bu şablon, varsayılan `1` değeri olan adlı bir değişken ve varsayılan değeri `5`olan adlı `b` bir değişken bildirir.</span><span class="sxs-lookup"><span data-stu-id="82065-220">This template declares a variable named `a` with a default value of `1` and a variable named `b` with a default value of `5`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82065-221">Yalnızca yol kesimi değişkenlerinin varsayılan değerlere sahip olmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="82065-221">Only path segment variables are allowed to have default values.</span></span> <span data-ttu-id="82065-222">Sorgu dizesi değişkenleri, bileşik kesim değişkenleri ve adlandırılmış joker dizeler varsayılan değerlere sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="82065-222">Query string variables, compound segment variables, and named wildcard variables are not permitted to have default values.</span></span>  
  
 <span data-ttu-id="82065-223">Aşağıdaki kod, bir aday URI ile eşleştirilirken varsayılan değişken değerlerinin nasıl işlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="82065-223">The following code shows how default variable values are handled when matching a candidate URI.</span></span>  
  
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
> <span data-ttu-id="82065-224">Gibi bir URI `http://localhost:8000///` , önceki kodda listelenen şablonla eşleşmez, ancak gibi bir URI `http://localhost:8000/` .</span><span class="sxs-lookup"><span data-stu-id="82065-224">A URI such as `http://localhost:8000///` does not match the template listed in the preceding code, however a URI such as `http://localhost:8000/` does.</span></span>  
  
 <span data-ttu-id="82065-225">Aşağıdaki kod, bir şablon ile URI oluştururken varsayılan değişken değerlerinin nasıl işlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="82065-225">The following code shows how default variable values are handled when creating a URI with a template.</span></span>  
  
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
  
<span data-ttu-id="82065-226">Bir değişkene varsayılan değer `null` verildiğinde, bazı ek kısıtlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="82065-226">When a variable is given a default value of `null` there are some additional constraints.</span></span> <span data-ttu-id="82065-227">Değişken, şablon dizesinin en sağ alt segmentinde yer alıyorsa veya segmentin sağ tarafındaki tüm segmentlerin varsayılan `null` `null`değerleri içeriyorsa, bir değişken varsayılan değeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="82065-227">A variable can have a default value of `null` if the variable is contained within the right most segment of the template string or if all segments to the right of the segment have default values of `null`.</span></span> <span data-ttu-id="82065-228">Aşağıda varsayılan değerleri `null`olan geçerli şablon dizeleri verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="82065-228">The following are valid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("shoe/{boat=null}");`

- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");`
  
- `UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");`

 <span data-ttu-id="82065-229">Varsayılan değerleri `null`geçersiz olan şablon dizeleri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="82065-229">The following are invalid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment`
  
- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value`

### <a name="default-values-and-matching"></a><span data-ttu-id="82065-230">Varsayılan değerler ve eşleştirme</span><span class="sxs-lookup"><span data-stu-id="82065-230">Default Values and Matching</span></span>  
 <span data-ttu-id="82065-231">Bir aday URI 'yi varsayılan değerlere sahip bir şablonla eşleştirirken, aday URI 'sinde değerler belirtilmemişse varsayılan değerler <xref:System.UriTemplateMatch.BoundVariables%2A> koleksiyona yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="82065-231">When matching a candidate URI with a template that has default values, the default values are placed in the <xref:System.UriTemplateMatch.BoundVariables%2A> collection if values are not specified in the candidate URI.</span></span>  
  
### <a name="template-equivalence"></a><span data-ttu-id="82065-232">Şablon denklik</span><span class="sxs-lookup"><span data-stu-id="82065-232">Template Equivalence</span></span>  
 <span data-ttu-id="82065-233">Tüm şablonların sabit değerleri eşleşiyorsa ve aynı kesimlerde değişkenler olduğunda, iki şablon *yapısal olarak eşdeğer* olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="82065-233">Two templates are said to be *structurally equivalent* when all of the templates' literals match and they have variables in the same segments.</span></span> <span data-ttu-id="82065-234">Örneğin, aşağıdaki şablonlar yapısal olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="82065-234">For example the following templates are structurally equivalent:</span></span>  
  
- <span data-ttu-id="82065-235">/a/{var1}/b b/{var2}? x = 1 & y = 2</span><span class="sxs-lookup"><span data-stu-id="82065-235">/a/{var1}/b b/{var2}?x=1&y=2</span></span>  
  
- <span data-ttu-id="82065-236">a/{x}/b%20b/{var1}?y=2&x=1</span><span class="sxs-lookup"><span data-stu-id="82065-236">a/{x}/b%20b/{var1}?y=2&x=1</span></span>  
  
- <span data-ttu-id="82065-237">a/{y}/B% 20B/{z}/? y = 2 & x = 1</span><span class="sxs-lookup"><span data-stu-id="82065-237">a/{y}/B%20B/{z}/?y=2&x=1</span></span>  
  
 <span data-ttu-id="82065-238">Dikkat etmeniz gereken birkaç nokta vardır:</span><span class="sxs-lookup"><span data-stu-id="82065-238">A few things to notice:</span></span>  
  
- <span data-ttu-id="82065-239">Bir şablon önünde eğik çizgi içeriyorsa, yalnızca ilki yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="82065-239">If a template contains leading slashes, only the first one is ignored.</span></span>  
  
- <span data-ttu-id="82065-240">Yapısal denklik için şablon dizelerini karşılaştırırken, değişken adları ve yol kesimleri için durum yoksayıldı, sorgu dizeleri büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="82065-240">When comparing template strings for structural equivalence, case is ignored for variable names and path segments, query strings are case sensitive.</span></span>  
  
- <span data-ttu-id="82065-241">Sorgu dizeleri sırasız.</span><span class="sxs-lookup"><span data-stu-id="82065-241">Query strings are unordered.</span></span>  
  
## <a name="uritemplatetable"></a><span data-ttu-id="82065-242">UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="82065-242">UriTemplateTable</span></span>  
 <span data-ttu-id="82065-243">Sınıfı, geliştiricinin seçme nesnesine bağlantılı <xref:System.UriTemplate> nesnelerin ilişkilendirilebilir tablosunu temsil eder. <xref:System.UriTemplateTable></span><span class="sxs-lookup"><span data-stu-id="82065-243">The <xref:System.UriTemplateTable> class represents an associative table of <xref:System.UriTemplate> objects bound to an object of the developer's choosing.</span></span> <span data-ttu-id="82065-244">' Nin çağrılmadan <xref:System.UriTemplate> <xref:System.UriTemplateTable> önceenazbir<xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>tane içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="82065-244">A <xref:System.UriTemplateTable> must contain at least one <xref:System.UriTemplate> prior to calling <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span> <span data-ttu-id="82065-245">Bir <xref:System.UriTemplateTable> öğesinin içeriği çağrılana kadar <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="82065-245">The contents of a <xref:System.UriTemplateTable> can be changed until <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="82065-246">Çağrıldığında doğrulama gerçekleştirilir <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> .</span><span class="sxs-lookup"><span data-stu-id="82065-246">Validation is performed when <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="82065-247">Gerçekleştirilen doğrulamanın türü, `allowMultiple` <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>parametresinin değerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="82065-247">The type of validation performed depends upon the value of the `allowMultiple` parameter to <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span>  
  
 <span data-ttu-id="82065-248"><xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> İçinde`false`geçirmeçağrıldığında, tabloda hiçbir şablon olmadığından emin olmak için kontroleder.<xref:System.UriTemplateTable></span><span class="sxs-lookup"><span data-stu-id="82065-248">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `false`, the <xref:System.UriTemplateTable> checks to make sure there are no templates in the table.</span></span> <span data-ttu-id="82065-249">Yapısal olarak eşdeğer şablonlar bulursa, bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="82065-249">If it finds any structurally equivalent templates, it throws an exception.</span></span> <span data-ttu-id="82065-250">Bu, bir gelen URI ile <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> eşleşen yalnızca bir şablonun olduğundan emin olmak istediğiniz zaman ile birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="82065-250">This is used in conjunction with <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> when you want to ensure only one template matches an incoming URI.</span></span>  
  
 <span data-ttu-id="82065-251">İçinde geçirme çağrıldığında ,<xref:System.UriTemplateTable> birden çok, yapısal olarak denk şablonların bir <xref:System.UriTemplateTable>içinde yer almasına izin verir. `true` <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29></span><span class="sxs-lookup"><span data-stu-id="82065-251">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `true`, <xref:System.UriTemplateTable> allows multiple, structurally-equivalent templates to be contained within a <xref:System.UriTemplateTable>.</span></span>  
  
 <span data-ttu-id="82065-252"><xref:System.UriTemplate> Bir<xref:System.UriTemplateTable> nesne kümesine eklenen bir sorgu dizesi varsa, bunların belirsiz olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="82065-252">If a set of <xref:System.UriTemplate> objects added to a <xref:System.UriTemplateTable> contain query strings they must not be ambiguous.</span></span> <span data-ttu-id="82065-253">Özdeş sorgu dizelerine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="82065-253">Identical query strings are allowed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82065-254">HTTP dışındaki şemaları kullanan temel adreslere izinverdiğinden,adayURI'lerişablonlarlaeşleştirilirkendüzenvebağlantınoktasınumarasıyoksayılır.<xref:System.UriTemplateTable></span><span class="sxs-lookup"><span data-stu-id="82065-254">While the <xref:System.UriTemplateTable> allows base addresses that use schemes other than HTTP, the scheme and port number are ignored when matching candidate URIs to templates.</span></span>  
  
### <a name="query-string-ambiguity"></a><span data-ttu-id="82065-255">Sorgu dizesi belirsizlik</span><span class="sxs-lookup"><span data-stu-id="82065-255">Query String Ambiguity</span></span>  
 <span data-ttu-id="82065-256">Bir eşdeğer yolu paylaşan şablonlar, birden fazla şablonla eşleşen bir URI varsa belirsiz sorgu dizeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="82065-256">Templates that share an equivalent path contain ambiguous query strings if there is a URI that matches more than one template.</span></span>  
  
 <span data-ttu-id="82065-257">Aşağıdaki sorgu dizeleri kümeleri kendi içinde belirsiz:</span><span class="sxs-lookup"><span data-stu-id="82065-257">The following sets of query strings are unambiguous within themselves:</span></span>  
  
- <span data-ttu-id="82065-258">?x=1</span><span class="sxs-lookup"><span data-stu-id="82065-258">?x=1</span></span>  
  
- <span data-ttu-id="82065-259">?x=2</span><span class="sxs-lookup"><span data-stu-id="82065-259">?x=2</span></span>  
  
- <span data-ttu-id="82065-260">?x=3</span><span class="sxs-lookup"><span data-stu-id="82065-260">?x=3</span></span>  
  
- <span data-ttu-id="82065-261">? x = 1 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="82065-261">?x=1&y={var}</span></span>  
  
- <span data-ttu-id="82065-262">?x=2&z={var}</span><span class="sxs-lookup"><span data-stu-id="82065-262">?x=2&z={var}</span></span>  
  
- <span data-ttu-id="82065-263">?x=3</span><span class="sxs-lookup"><span data-stu-id="82065-263">?x=3</span></span>  
  
- <span data-ttu-id="82065-264">?x=1</span><span class="sxs-lookup"><span data-stu-id="82065-264">?x=1</span></span>  
  
- <span data-ttu-id="82065-265">?</span><span class="sxs-lookup"><span data-stu-id="82065-265">?</span></span>  
  
- <span data-ttu-id="82065-266">?</span><span class="sxs-lookup"><span data-stu-id="82065-266">?</span></span> <span data-ttu-id="82065-267">x={var}</span><span class="sxs-lookup"><span data-stu-id="82065-267">x={var}</span></span>  
  
- <span data-ttu-id="82065-268">?</span><span class="sxs-lookup"><span data-stu-id="82065-268">?</span></span>  
  
- <span data-ttu-id="82065-269">? m = get & c = RSS</span><span class="sxs-lookup"><span data-stu-id="82065-269">?m=get&c=rss</span></span>  
  
- <span data-ttu-id="82065-270">? m = put & c = RSS</span><span class="sxs-lookup"><span data-stu-id="82065-270">?m=put&c=rss</span></span>  
  
- <span data-ttu-id="82065-271">? m = get & c = atom</span><span class="sxs-lookup"><span data-stu-id="82065-271">?m=get&c=atom</span></span>  
  
- <span data-ttu-id="82065-272">? m = put & c = atom</span><span class="sxs-lookup"><span data-stu-id="82065-272">?m=put&c=atom</span></span>  
  
 <span data-ttu-id="82065-273">Aşağıdaki sorgu dizesi şablonları kümeleri kendileri içinde belirsizdir:</span><span class="sxs-lookup"><span data-stu-id="82065-273">The following sets of query string templates are ambiguous within themselves:</span></span>  
  
- <span data-ttu-id="82065-274">?x=1</span><span class="sxs-lookup"><span data-stu-id="82065-274">?x=1</span></span>  
  
- <span data-ttu-id="82065-275">?x={var}</span><span class="sxs-lookup"><span data-stu-id="82065-275">?x={var}</span></span>  
  
 <span data-ttu-id="82065-276">"x = 1"-her iki şablon da eşleşir.</span><span class="sxs-lookup"><span data-stu-id="82065-276">"x=1" - Matches both templates.</span></span>  
  
- <span data-ttu-id="82065-277">?x=1</span><span class="sxs-lookup"><span data-stu-id="82065-277">?x=1</span></span>  
  
- <span data-ttu-id="82065-278">? y = 2</span><span class="sxs-lookup"><span data-stu-id="82065-278">?y=2</span></span>  
  
 <span data-ttu-id="82065-279">"x = 1 & y = 2", her iki şablonlarla de eşleşir.</span><span class="sxs-lookup"><span data-stu-id="82065-279">"x=1&y=2" matches both templates.</span></span> <span data-ttu-id="82065-280">Bunun nedeni, bir sorgu dizesinin daha fazla sorgu dizesi değişkeni içermesi olabilir ve bundan sonra eşleşen şablondur.</span><span class="sxs-lookup"><span data-stu-id="82065-280">This is because a query string may contain more query string variables then the template it matches.</span></span>  
  
- <span data-ttu-id="82065-281">?x=1</span><span class="sxs-lookup"><span data-stu-id="82065-281">?x=1</span></span>  
  
- <span data-ttu-id="82065-282">? x = 1 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="82065-282">?x=1&y={var}</span></span>  
  
 <span data-ttu-id="82065-283">"x = 1 & y = 3" her iki şablonlarla de eşleşir.</span><span class="sxs-lookup"><span data-stu-id="82065-283">"x=1&y=3" matches both templates.</span></span>  
  
- <span data-ttu-id="82065-284">? x = 3 & y = 4</span><span class="sxs-lookup"><span data-stu-id="82065-284">?x=3&y=4</span></span>  
  
- <span data-ttu-id="82065-285">?x=3&z=5</span><span class="sxs-lookup"><span data-stu-id="82065-285">?x=3&z=5</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82065-286">Á ve á karakterleri, bir URI yolu veya <xref:System.UriTemplate> yol segmenti değişmez değerinin bir parçası olarak görüntülendiklerinde farklı karakterler olarak değerlendirilir (ancak a ve a karakterleri aynı olduğu kabul edilir).</span><span class="sxs-lookup"><span data-stu-id="82065-286">The characters á and Á are considered to be different characters when they appear as part of a URI path or <xref:System.UriTemplate> path segment literal (but the characters a and A are considered to be the same).</span></span> <span data-ttu-id="82065-287">Á ve á karakterleri, bir <xref:System.UriTemplate> {VariableName} veya bir sorgu dizesinin (ve ' de aynı karakterler olarak kabul edilir) bir parçası olarak göründükleri karakterlerle aynı karakterler olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="82065-287">The characters á and Á are considered to be the same characters when they appear as part of a <xref:System.UriTemplate> {variableName} or a query string (and a and A are also considered to be the same characters).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82065-288">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82065-288">See also</span></span>

- [<span data-ttu-id="82065-289">WCF Web HTTP Programlama Modeli Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="82065-289">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="82065-290">WCF Web HTTP Programlama Nesnesi Modeli</span><span class="sxs-lookup"><span data-stu-id="82065-290">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [<span data-ttu-id="82065-291">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="82065-291">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
- [<span data-ttu-id="82065-292">UriTemplate Tablosu</span><span class="sxs-lookup"><span data-stu-id="82065-292">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="82065-293">UriTemplate Tablosu Dağıtıcısı</span><span class="sxs-lookup"><span data-stu-id="82065-293">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
