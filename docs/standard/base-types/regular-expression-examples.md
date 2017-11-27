---
title: "Normal İfade Örnekleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- regular expressions [.NET Framework], examples
- regular expressions [.NET Framework]
- strings [.NET Framework], regular expressions
ms.assetid: e9fd53f2-ed56-4b09-b2ea-e9bc9d65e6d6
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5d7fa8fe2bade9f20f71f846c717d79d6b6ffb36
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="regular-expression-examples"></a><span data-ttu-id="3a346-102">Normal İfade Örnekleri</span><span class="sxs-lookup"><span data-stu-id="3a346-102">Regular Expression Examples</span></span>
<span data-ttu-id="3a346-103">Bu bölüm, sık kullanılan uygulamalar normal ifadelerde kullanımını gösteren kod örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3a346-103">This section contains code examples that illustrate the use of regular expressions in common applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a346-104"><xref:System.Web.RegularExpressions> Ad alanı, HTML, XML ve ASP.NET belgelerden dizeleri ayrıştırma için önceden tanımlanmış normal ifade desenlerini uygulama normal ifade nesnelerin sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="3a346-104">The <xref:System.Web.RegularExpressions> namespace contains a number of regular expression objects that implement predefined regular expression patterns for parsing strings from HTML, XML, and ASP.NET documents.</span></span> <span data-ttu-id="3a346-105">Örneğin, <xref:System.Web.RegularExpressions.TagRegex> sınıfı tanımlayan bir dizedeki başlangıç etiketleri ve <xref:System.Web.RegularExpressions.CommentRegex> sınıfı tanımlayan bir dize ASP.NET açıklamaları.</span><span class="sxs-lookup"><span data-stu-id="3a346-105">For example, the <xref:System.Web.RegularExpressions.TagRegex> class identifies start tags in a string and the <xref:System.Web.RegularExpressions.CommentRegex> class identifies ASP.NET comments in a string.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3a346-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3a346-106">In This Section</span></span>  
 [<span data-ttu-id="3a346-107">Örnek: Href tarama</span><span class="sxs-lookup"><span data-stu-id="3a346-107">Example: Scanning for HREFs</span></span>](../../../docs/standard/base-types/regular-expression-example-scanning-for-hrefs.md)  
 <span data-ttu-id="3a346-108">Giriş dizesi arar ve tüm href yazdırır bir örnek sağlar = "..." değerlerini ve konumlarına dize.</span><span class="sxs-lookup"><span data-stu-id="3a346-108">Provides an example that searches an input string and prints out all the href="…" values and their locations in the string.</span></span>  
  
 [<span data-ttu-id="3a346-109">Örnek: Tarih biçimlerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="3a346-109">Example: Changing Date Formats</span></span>](../../../docs/standard/base-types/regular-expression-example-changing-date-formats.md)  
 <span data-ttu-id="3a346-110">Form gg/aa/yy tarih gg-aa-yy formu tarihlerle değiştiren bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a346-110">Provides an example that replaces dates in the form mm/dd/yy with dates in the form dd-mm-yy.</span></span>  
  
 [<span data-ttu-id="3a346-111">Nasıl yapılır: bir URL'den protokol ve bağlantı noktası numarası çıkarma</span><span class="sxs-lookup"><span data-stu-id="3a346-111">How to: Extract a Protocol and Port Number from a URL</span></span>](../../../docs/standard/base-types/how-to-extract-a-protocol-and-port-number-from-a-url.md)  
 <span data-ttu-id="3a346-112">Protokol ve bağlantı noktası numarası bir URL içeren bir dizeden ayıklar bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a346-112">Provides an example that extracts a protocol and port number from a string that contains a URL.</span></span> <span data-ttu-id="3a346-113">Örneğin, "http://www.contoso.com:8080/letters/readme.html", "http:8080" döndürür.</span><span class="sxs-lookup"><span data-stu-id="3a346-113">For example, "http://www.contoso.com:8080/letters/readme.html" returns "http:8080".</span></span>  
  
 [<span data-ttu-id="3a346-114">Nasıl yapılır: dizeden geçersiz karakterleri çıkartma</span><span class="sxs-lookup"><span data-stu-id="3a346-114">How to: Strip Invalid Characters from a String</span></span>](../../../docs/standard/base-types/how-to-strip-invalid-characters-from-a-string.md)  
 <span data-ttu-id="3a346-115">Bir dizeden geçersiz alfasayısal olmayan karakterler şeritler bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a346-115">Provides an example that strips invalid non-alphanumeric characters from a string.</span></span>  
  
 [<span data-ttu-id="3a346-116">Nasıl yapılır: dizelerin geçerli e-posta biçiminde olduğunu doğrulama</span><span class="sxs-lookup"><span data-stu-id="3a346-116">How to: Verify that Strings Are in Valid Email Format</span></span>](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)  
 <span data-ttu-id="3a346-117">Bir dize geçerli e-posta biçiminde olduğunu doğrulamak için kullanabileceğiniz bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a346-117">Provides an example that you can use to verify that a string is in valid email format.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3a346-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="3a346-118">Reference</span></span>  
 <xref:System.Text.RegularExpressions>  
 <span data-ttu-id="3a346-119">.NET için sınıf kitaplığı başvuru bilgileri sağlar **System.Text.RegularExpressions** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="3a346-119">Provides class library reference information for the .NET **System.Text.RegularExpressions** namespace.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3a346-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="3a346-120">Related Sections</span></span>  
 [<span data-ttu-id="3a346-121">.NET normal ifadeler</span><span class="sxs-lookup"><span data-stu-id="3a346-121">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)  
 <span data-ttu-id="3a346-122">Normal ifadeler programlama dili yönünü genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a346-122">Provides an overview of the programming language aspect of regular expressions.</span></span>  
  
 [<span data-ttu-id="3a346-123">Normal ifade nesnesi modeli</span><span class="sxs-lookup"><span data-stu-id="3a346-123">The Regular Expression Object Model</span></span>](../../../docs/standard/base-types/the-regular-expression-object-model.md)  
 <span data-ttu-id="3a346-124">İçinde yer alan normal ifade sınıfları açıklar `System.Text.RegularExpression` ad alanı ve kullanım örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a346-124">Describes the regular expression classes contained in the `System.Text.RegularExpression` namespace and provides examples of their use.</span></span>  
  
 [<span data-ttu-id="3a346-125">Normal ifade davranışının ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="3a346-125">Details of Regular Expression Behavior</span></span>](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)  
 <span data-ttu-id="3a346-126">.NET normal ifadeler davranışını ve özellikleri hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a346-126">Provides information about the capabilities and behavior of .NET regular expressions.</span></span>  
  
 [<span data-ttu-id="3a346-127">Normal ifade dili - hızlı başvuru</span><span class="sxs-lookup"><span data-stu-id="3a346-127">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 <span data-ttu-id="3a346-128">Normal ifadeler tanımlamak için kullanabileceğiniz karakterler, operatörler ve yapılar kümesi hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a346-128">Provides information on the set of characters, operators, and constructs that you can use to define regular expressions.</span></span>
