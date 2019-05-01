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
ms.openlocfilehash: ee4d884a0efbeb6e57ed727396bf3bcb39979774
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61811572"
---
# <a name="regular-expression-examples"></a><span data-ttu-id="3c1ca-102">Normal İfade Örnekleri</span><span class="sxs-lookup"><span data-stu-id="3c1ca-102">Regular Expression Examples</span></span>
<span data-ttu-id="3c1ca-103">Bu bölüm yaygın uygulamalar normal ifadeler kullanımını gösteren kod örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3c1ca-103">This section contains code examples that illustrate the use of regular expressions in common applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c1ca-104"><xref:System.Web.RegularExpressions> Ad alanı, HTML, XML ve ASP.NET belgelerden dizeleri ayrıştırma için önceden tanımlanmış bir normal ifade desenlerini uygulama normal ifade nesneleri sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="3c1ca-104">The <xref:System.Web.RegularExpressions> namespace contains a number of regular expression objects that implement predefined regular expression patterns for parsing strings from HTML, XML, and ASP.NET documents.</span></span> <span data-ttu-id="3c1ca-105">Örneğin, <xref:System.Web.RegularExpressions.TagRegex> sınıfı tanımlayan bir dizedeki başlangıç etiketleri ve <xref:System.Web.RegularExpressions.CommentRegex> sınıfı tanımlayan bir dize ASP.NET açıklamaları.</span><span class="sxs-lookup"><span data-stu-id="3c1ca-105">For example, the <xref:System.Web.RegularExpressions.TagRegex> class identifies start tags in a string and the <xref:System.Web.RegularExpressions.CommentRegex> class identifies ASP.NET comments in a string.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3c1ca-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3c1ca-106">In This Section</span></span>  
 [<span data-ttu-id="3c1ca-107">Örnek: Href tarama</span><span class="sxs-lookup"><span data-stu-id="3c1ca-107">Example: Scanning for HREFs</span></span>](../../../docs/standard/base-types/regular-expression-example-scanning-for-hrefs.md)  
 <span data-ttu-id="3c1ca-108">Bir Giriş dizesinin arar ve yazdırır veya href bir örnek sağlar = "..." değerler ve bunların konumları dize.</span><span class="sxs-lookup"><span data-stu-id="3c1ca-108">Provides an example that searches an input string and prints out all the href="…" values and their locations in the string.</span></span>  
  
 [<span data-ttu-id="3c1ca-109">Örnek: Tarih biçimlerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="3c1ca-109">Example: Changing Date Formats</span></span>](../../../docs/standard/base-types/regular-expression-example-changing-date-formats.md)  
 <span data-ttu-id="3c1ca-110">Form aa/gg/yy tarih gg-aa-yy form tarihleri ile değiştiren bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c1ca-110">Provides an example that replaces dates in the form mm/dd/yy with dates in the form dd-mm-yy.</span></span>  
  
 [<span data-ttu-id="3c1ca-111">Nasıl yapılır: Bir URL'den protokol ve bağlantı noktası numarası çıkarma</span><span class="sxs-lookup"><span data-stu-id="3c1ca-111">How to: Extract a Protocol and Port Number from a URL</span></span>](../../../docs/standard/base-types/how-to-extract-a-protocol-and-port-number-from-a-url.md)  
 <span data-ttu-id="3c1ca-112">Protokol ve bağlantı noktası numarası URL içeren bir dizeden ayıklar bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c1ca-112">Provides an example that extracts a protocol and port number from a string that contains a URL.</span></span> <span data-ttu-id="3c1ca-113">Örneğin, "http://www.contoso.com:8080/letters/readme.html" "http:8080" döndürür.</span><span class="sxs-lookup"><span data-stu-id="3c1ca-113">For example, "http://www.contoso.com:8080/letters/readme.html" returns "http:8080".</span></span>  
  
 [<span data-ttu-id="3c1ca-114">Nasıl yapılır: Şerit geçersiz karakterleri bir dizeden</span><span class="sxs-lookup"><span data-stu-id="3c1ca-114">How to: Strip Invalid Characters from a String</span></span>](../../../docs/standard/base-types/how-to-strip-invalid-characters-from-a-string.md)  
 <span data-ttu-id="3c1ca-115">Geçersiz alfasayısal olmayan karakterleri kaldırır bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c1ca-115">Provides an example that strips invalid non-alphanumeric characters from a string.</span></span>  
  
 [<span data-ttu-id="3c1ca-116">Nasıl yapılır: Dizelerin geçerli e-posta biçiminde olduğunu doğrulama</span><span class="sxs-lookup"><span data-stu-id="3c1ca-116">How to: Verify that Strings Are in Valid Email Format</span></span>](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)  
 <span data-ttu-id="3c1ca-117">Bir dize geçerli bir e-posta biçiminde olduğunu doğrulayan bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c1ca-117">Provides an example that verifies that a string is in valid email format.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3c1ca-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="3c1ca-118">Reference</span></span>  
 <xref:System.Text.RegularExpressions>  
 <span data-ttu-id="3c1ca-119">.NET sınıf kitaplığı başvuru bilgileri sağlar **System.Text.RegularExpressions** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="3c1ca-119">Provides class library reference information for the .NET **System.Text.RegularExpressions** namespace.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3c1ca-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="3c1ca-120">Related Sections</span></span>  
 [<span data-ttu-id="3c1ca-121">.NET normal ifadeler</span><span class="sxs-lookup"><span data-stu-id="3c1ca-121">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)  
 <span data-ttu-id="3c1ca-122">Programlama dili en boy normal ifadelerin genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c1ca-122">Provides an overview of the programming language aspect of regular expressions.</span></span>  
  
 [<span data-ttu-id="3c1ca-123">Normal İfade Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="3c1ca-123">The Regular Expression Object Model</span></span>](../../../docs/standard/base-types/the-regular-expression-object-model.md)  
 <span data-ttu-id="3c1ca-124">İçinde bulunan normal ifade sınıfları açıklar `System.Text.RegularExpression` ad alanı ve kullanım örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c1ca-124">Describes the regular expression classes contained in the `System.Text.RegularExpression` namespace and provides examples of their use.</span></span>  
  
 [<span data-ttu-id="3c1ca-125">Normal İfade Davranışının Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="3c1ca-125">Details of Regular Expression Behavior</span></span>](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)  
 <span data-ttu-id="3c1ca-126">.NET normal ifadelerin davranışı ve özellikleri hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c1ca-126">Provides information about the capabilities and behavior of .NET regular expressions.</span></span>  
  
 [<span data-ttu-id="3c1ca-127">Normal İfade Dili - Hızlı Başvuru</span><span class="sxs-lookup"><span data-stu-id="3c1ca-127">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 <span data-ttu-id="3c1ca-128">Normal ifadeler tanımlamak için kullanabileceğiniz karakterler, operatörler ve yapılar kümesi hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c1ca-128">Provides information on the set of characters, operators, and constructs that you can use to define regular expressions.</span></span>
