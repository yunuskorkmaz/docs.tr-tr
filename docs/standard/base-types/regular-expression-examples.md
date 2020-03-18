---
title: Normal İfade Örnekleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- regular expressions [.NET Framework], examples
- regular expressions [.NET Framework]
- strings [.NET Framework], regular expressions
ms.assetid: e9fd53f2-ed56-4b09-b2ea-e9bc9d65e6d6
ms.openlocfilehash: 788fa2a6793e14189def4c30a0baf0d4a5cf6b0a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73128089"
---
# <a name="regular-expression-examples"></a><span data-ttu-id="3627a-102">Normal İfade Örnekleri</span><span class="sxs-lookup"><span data-stu-id="3627a-102">Regular Expression Examples</span></span>
<span data-ttu-id="3627a-103">Bu bölümde, ortak uygulamalarda normal ifadelerin kullanımını gösteren kod örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3627a-103">This section contains code examples that illustrate the use of regular expressions in common applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3627a-104">Ad <xref:System.Web.RegularExpressions> alanı, dizeleri HTML, XML ve ASP.NET belgelerden ayrıştırma için önceden tanımlanmış normal ifade desenleri uygulayan bir dizi normal ifade nesnesi içerir.</span><span class="sxs-lookup"><span data-stu-id="3627a-104">The <xref:System.Web.RegularExpressions> namespace contains a number of regular expression objects that implement predefined regular expression patterns for parsing strings from HTML, XML, and ASP.NET documents.</span></span> <span data-ttu-id="3627a-105">Örneğin, <xref:System.Web.RegularExpressions.TagRegex> sınıf bir dizedeki başlangıç <xref:System.Web.RegularExpressions.CommentRegex> etiketlerini tanımlar ve sınıf bir dizedeki ASP.NET açıklamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3627a-105">For example, the <xref:System.Web.RegularExpressions.TagRegex> class identifies start tags in a string and the <xref:System.Web.RegularExpressions.CommentRegex> class identifies ASP.NET comments in a string.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3627a-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3627a-106">In This Section</span></span>  
 [<span data-ttu-id="3627a-107">Örnek: HREF Tarama</span><span class="sxs-lookup"><span data-stu-id="3627a-107">Example: Scanning for HREFs</span></span>](../../../docs/standard/base-types/regular-expression-example-scanning-for-hrefs.md)  
 <span data-ttu-id="3627a-108">Giriş dizesini arayan ve tüm href="..." yazdıran bir örnek sağlar. değerleri ve konumlarını dize.</span><span class="sxs-lookup"><span data-stu-id="3627a-108">Provides an example that searches an input string and prints out all the href="…" values and their locations in the string.</span></span>  
  
 [<span data-ttu-id="3627a-109">Örnek: Tarih Biçimlerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="3627a-109">Example: Changing Date Formats</span></span>](../../../docs/standard/base-types/regular-expression-example-changing-date-formats.md)  
 <span data-ttu-id="3627a-110">mm/dd/yy formundaki tarihleri dd-mm-yy formundaki tarihlerle değiştiren bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="3627a-110">Provides an example that replaces dates in the form mm/dd/yy with dates in the form dd-mm-yy.</span></span>  
  
 [<span data-ttu-id="3627a-111">Nasıl yapılır: Bir URL'den Protokol ve Bağlantı Noktası Numarası Çıkarma</span><span class="sxs-lookup"><span data-stu-id="3627a-111">How to: Extract a Protocol and Port Number from a URL</span></span>](../../../docs/standard/base-types/how-to-extract-a-protocol-and-port-number-from-a-url.md)  
 <span data-ttu-id="3627a-112">URL içeren bir dizeden bir iletişim kuralı ve bağlantı noktası numarası ayıklayan bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="3627a-112">Provides an example that extracts a protocol and port number from a string that contains a URL.</span></span> <span data-ttu-id="3627a-113">Örneğin, "http://www.contoso.com:8080/letters/readme.html" "http:8080" döndürür.</span><span class="sxs-lookup"><span data-stu-id="3627a-113">For example, "http://www.contoso.com:8080/letters/readme.html" returns "http:8080".</span></span>  
  
 [<span data-ttu-id="3627a-114">Nasıl yapılır: Dizeden Geçersiz Karakterleri Çıkartma</span><span class="sxs-lookup"><span data-stu-id="3627a-114">How to: Strip Invalid Characters from a String</span></span>](../../../docs/standard/base-types/how-to-strip-invalid-characters-from-a-string.md)  
 <span data-ttu-id="3627a-115">Geçersiz alfanümerik olmayan karakterleri bir dizeden şeritlere örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="3627a-115">Provides an example that strips invalid non-alphanumeric characters from a string.</span></span>  
  
 [<span data-ttu-id="3627a-116">Nasıl yapılır: Dizelerin Geçerli E-Posta Biçiminde Olduğunu Doğrulama</span><span class="sxs-lookup"><span data-stu-id="3627a-116">How to: Verify that Strings Are in Valid Email Format</span></span>](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)  
 <span data-ttu-id="3627a-117">Dize geçerli e-posta biçiminde olduğunu doğrulayan bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="3627a-117">Provides an example that verifies that a string is in valid email format.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3627a-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="3627a-118">Reference</span></span>  
 <xref:System.Text.RegularExpressions>  
 <span data-ttu-id="3627a-119">.NET **System.Text.RegularExpressions** ad alanı için sınıf kitaplığı başvuru bilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3627a-119">Provides class library reference information for the .NET **System.Text.RegularExpressions** namespace.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3627a-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="3627a-120">Related Sections</span></span>  
 [<span data-ttu-id="3627a-121">.NET Düzenli İfadeler</span><span class="sxs-lookup"><span data-stu-id="3627a-121">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)  
 <span data-ttu-id="3627a-122">Normal ifadelerin programlama dili boyutuna genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="3627a-122">Provides an overview of the programming language aspect of regular expressions.</span></span>  
  
 [<span data-ttu-id="3627a-123">Normal İfade Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="3627a-123">The Regular Expression Object Model</span></span>](../../../docs/standard/base-types/the-regular-expression-object-model.md)  
 <span data-ttu-id="3627a-124">`System.Text.RegularExpression` Ad alanında bulunan normal ifade sınıflarını açıklar ve bunların kullanımına örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3627a-124">Describes the regular expression classes contained in the `System.Text.RegularExpression` namespace and provides examples of their use.</span></span>  
  
 [<span data-ttu-id="3627a-125">Normal İfade Davranışının Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="3627a-125">Details of Regular Expression Behavior</span></span>](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)  
 <span data-ttu-id="3627a-126">.NET düzenli ifadelerin yetenekleri ve davranışları hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3627a-126">Provides information about the capabilities and behavior of .NET regular expressions.</span></span>  
  
 [<span data-ttu-id="3627a-127">Normal İfade Dili - Hızlı Başvuru</span><span class="sxs-lookup"><span data-stu-id="3627a-127">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 <span data-ttu-id="3627a-128">Normal ifadeler tanımlamak için kullanabileceğiniz karakterler, operatörler ve yapılar kümesi hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3627a-128">Provides information on the set of characters, operators, and constructs that you can use to define regular expressions.</span></span>
