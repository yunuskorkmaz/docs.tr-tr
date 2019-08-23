---
title: Normal İfade Örnekleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- regular expressions [.NET Framework], examples
- regular expressions [.NET Framework]
- strings [.NET Framework], regular expressions
ms.assetid: e9fd53f2-ed56-4b09-b2ea-e9bc9d65e6d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc62fffe3ca51acf0f2098d2975665b91b052992
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930888"
---
# <a name="regular-expression-examples"></a><span data-ttu-id="ac29f-102">Normal İfade Örnekleri</span><span class="sxs-lookup"><span data-stu-id="ac29f-102">Regular Expression Examples</span></span>
<span data-ttu-id="ac29f-103">Bu bölüm ortak uygulamalarda normal ifadelerin kullanımını gösteren kod örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ac29f-103">This section contains code examples that illustrate the use of regular expressions in common applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ac29f-104">Ad <xref:System.Web.RegularExpressions> alanı, HTML, XML ve ASP.net belgelerinden dizeleri ayrıştırmak için önceden tanımlanmış normal ifade desenleri uygulayan bir dizi normal ifade nesnesi içerir.</span><span class="sxs-lookup"><span data-stu-id="ac29f-104">The <xref:System.Web.RegularExpressions> namespace contains a number of regular expression objects that implement predefined regular expression patterns for parsing strings from HTML, XML, and ASP.NET documents.</span></span> <span data-ttu-id="ac29f-105">Örneğin, <xref:System.Web.RegularExpressions.TagRegex> sınıfı bir dizedeki başlangıç etiketlerini tanımlar <xref:System.Web.RegularExpressions.CommentRegex> ve sınıf ASP.net açıklamalarını bir dizede tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ac29f-105">For example, the <xref:System.Web.RegularExpressions.TagRegex> class identifies start tags in a string and the <xref:System.Web.RegularExpressions.CommentRegex> class identifies ASP.NET comments in a string.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ac29f-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ac29f-106">In This Section</span></span>  
 [<span data-ttu-id="ac29f-107">Örnek: HREFs taranıyor</span><span class="sxs-lookup"><span data-stu-id="ac29f-107">Example: Scanning for HREFs</span></span>](../../../docs/standard/base-types/regular-expression-example-scanning-for-hrefs.md)  
 <span data-ttu-id="ac29f-108">Bir giriş dizesini arayan ve tüm href = "..." öğesini yazdıran bir örnek sağlar değerler ve dizedeki konumları.</span><span class="sxs-lookup"><span data-stu-id="ac29f-108">Provides an example that searches an input string and prints out all the href="…" values and their locations in the string.</span></span>  
  
 [<span data-ttu-id="ac29f-109">Örnek: Tarih biçimlerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="ac29f-109">Example: Changing Date Formats</span></span>](../../../docs/standard/base-types/regular-expression-example-changing-date-formats.md)  
 <span data-ttu-id="ac29f-110">Aa/gg/yy biçimindeki tarihleri gg-aa-yy biçimindeki tarihlerle değiştiren bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac29f-110">Provides an example that replaces dates in the form mm/dd/yy with dates in the form dd-mm-yy.</span></span>  
  
 [<span data-ttu-id="ac29f-111">Nasıl yapılır: Bir URL 'den protokol ve bağlantı noktası numarası Ayıkla</span><span class="sxs-lookup"><span data-stu-id="ac29f-111">How to: Extract a Protocol and Port Number from a URL</span></span>](../../../docs/standard/base-types/how-to-extract-a-protocol-and-port-number-from-a-url.md)  
 <span data-ttu-id="ac29f-112">URL içeren bir dizeden protokol ve bağlantı noktası numarası çıkaran bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac29f-112">Provides an example that extracts a protocol and port number from a string that contains a URL.</span></span> <span data-ttu-id="ac29f-113">Örneğin, "http://www.contoso.com:8080/letters/readme.html", "http: 8080" döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac29f-113">For example, "http://www.contoso.com:8080/letters/readme.html" returns "http:8080".</span></span>  
  
 [<span data-ttu-id="ac29f-114">Nasıl yapılır: Dizeden geçersiz karakterleri şerit</span><span class="sxs-lookup"><span data-stu-id="ac29f-114">How to: Strip Invalid Characters from a String</span></span>](../../../docs/standard/base-types/how-to-strip-invalid-characters-from-a-string.md)  
 <span data-ttu-id="ac29f-115">Bir dizeden geçersiz alfasayısal olmayan karakter şeritleri sağlayan bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac29f-115">Provides an example that strips invalid non-alphanumeric characters from a string.</span></span>  
  
 [<span data-ttu-id="ac29f-116">Nasıl yapılır: Dizelerin geçerli e-posta biçiminde olduğunu doğrulama</span><span class="sxs-lookup"><span data-stu-id="ac29f-116">How to: Verify that Strings Are in Valid Email Format</span></span>](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)  
 <span data-ttu-id="ac29f-117">Bir dizenin geçerli e-posta biçiminde olduğunu doğrulayan bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac29f-117">Provides an example that verifies that a string is in valid email format.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ac29f-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="ac29f-118">Reference</span></span>  
 <xref:System.Text.RegularExpressions>  
 <span data-ttu-id="ac29f-119">.NET **System. Text. RegularExpressions** ad alanı için sınıf kitaplığı başvuru bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac29f-119">Provides class library reference information for the .NET **System.Text.RegularExpressions** namespace.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ac29f-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="ac29f-120">Related Sections</span></span>  
 [<span data-ttu-id="ac29f-121">.NET normal Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="ac29f-121">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)  
 <span data-ttu-id="ac29f-122">Normal ifadelerin programlama diline ilişkin bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac29f-122">Provides an overview of the programming language aspect of regular expressions.</span></span>  
  
 [<span data-ttu-id="ac29f-123">Normal İfade Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="ac29f-123">The Regular Expression Object Model</span></span>](../../../docs/standard/base-types/the-regular-expression-object-model.md)  
 <span data-ttu-id="ac29f-124">`System.Text.RegularExpression` Ad alanında bulunan normal ifade sınıflarını açıklar ve kullanımları örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac29f-124">Describes the regular expression classes contained in the `System.Text.RegularExpression` namespace and provides examples of their use.</span></span>  
  
 [<span data-ttu-id="ac29f-125">Normal İfade Davranışının Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="ac29f-125">Details of Regular Expression Behavior</span></span>](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)  
 <span data-ttu-id="ac29f-126">.NET normal ifadelerinin özellikleri ve davranışları hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac29f-126">Provides information about the capabilities and behavior of .NET regular expressions.</span></span>  
  
 [<span data-ttu-id="ac29f-127">Normal İfade Dili - Hızlı Başvuru</span><span class="sxs-lookup"><span data-stu-id="ac29f-127">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 <span data-ttu-id="ac29f-128">Normal ifadeler tanımlamak için kullanabileceğiniz karakterler, operatörler ve yapılar kümesi hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac29f-128">Provides information on the set of characters, operators, and constructs that you can use to define regular expressions.</span></span>
