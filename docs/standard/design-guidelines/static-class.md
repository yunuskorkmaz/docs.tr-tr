---
title: Statik Sınıf Tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
ms.openlocfilehash: c906502ed071e8515f101996ec42a04772f72b12
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291935"
---
# <a name="static-class-design"></a><span data-ttu-id="faa1d-102">Statik Sınıf Tasarımı</span><span class="sxs-lookup"><span data-stu-id="faa1d-102">Static Class Design</span></span>
<span data-ttu-id="faa1d-103">Statik bir sınıf, yalnızca statik Üyeler ( <xref:System.Object?displayProperty=nameWithType> ve büyük olasılıkla özel bir Oluşturucu) içeren bir sınıf olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="faa1d-103">A static class is defined as a class that contains only static members (of course besides the instance members inherited from <xref:System.Object?displayProperty=nameWithType> and possibly a private constructor).</span></span> <span data-ttu-id="faa1d-104">Bazı diller statik sınıflar için yerleşik destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="faa1d-104">Some languages provide built-in support for static classes.</span></span> <span data-ttu-id="faa1d-105">C# 2,0 ve üzeri sürümlerde, bir sınıf statik olarak bildirildiğinde, mühürlenmiş, soyut ve herhangi bir örnek üyesi geçersiz kılınmaz veya bildirilebilecek.</span><span class="sxs-lookup"><span data-stu-id="faa1d-105">In C# 2.0 and later, when a class is declared to be static, it is sealed, abstract, and no instance members can be overridden or declared.</span></span>

 <span data-ttu-id="faa1d-106">Statik sınıflar saf nesne odaklı tasarım ve basitlik arasında bir uzlaşdır.</span><span class="sxs-lookup"><span data-stu-id="faa1d-106">Static classes are a compromise between pure object-oriented design and simplicity.</span></span> <span data-ttu-id="faa1d-107">Bunlar genellikle diğer işlemlere (gibi) kısayollar sağlamak için kullanılır (örneğin <xref:System.IO.File?displayProperty=nameWithType> ), uzantı yöntemlerinin sahipleri veya tam bir nesne odaklı sarmalayıcının izin verilmeyen bir sarmalayıcı (gibi <xref:System.Environment?displayProperty=nameWithType> ).</span><span class="sxs-lookup"><span data-stu-id="faa1d-107">They are commonly used to provide shortcuts to other operations (such as <xref:System.IO.File?displayProperty=nameWithType>), holders of extension methods, or functionality for which a full object-oriented wrapper is unwarranted (such as <xref:System.Environment?displayProperty=nameWithType>).</span></span>

 <span data-ttu-id="faa1d-108">✔️ statik sınıfları gelişigüzel bir şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="faa1d-108">✔️ DO use static classes sparingly.</span></span>

 <span data-ttu-id="faa1d-109">Statik sınıflar yalnızca çerçevenin nesne odaklı çekirdeği için destekleme sınıfları olarak kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="faa1d-109">Static classes should be used only as supporting classes for the object-oriented core of the framework.</span></span>

 <span data-ttu-id="faa1d-110">❌Statik sınıfları çeşitli demet olarak değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="faa1d-110">❌ DO NOT treat static classes as a miscellaneous bucket.</span></span>

 <span data-ttu-id="faa1d-111">❌Statik sınıflarda örnek üyelerini bildirme veya geçersiz kılma.</span><span class="sxs-lookup"><span data-stu-id="faa1d-111">❌ DO NOT declare or override instance members in static classes.</span></span>

 <span data-ttu-id="faa1d-112">✔️ statik sınıfları korumalı, soyut olarak bildirir ve programlama dilinizin statik sınıflar için yerleşik desteği yoksa özel bir örnek oluşturucu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="faa1d-112">✔️ DO declare static classes as sealed, abstract, and add a private instance constructor if your programming language does not have built-in support for static classes.</span></span>

 <span data-ttu-id="faa1d-113">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="faa1d-113">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="faa1d-114">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="faa1d-114">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="faa1d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="faa1d-115">See also</span></span>

- [<span data-ttu-id="faa1d-116">Tür tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="faa1d-116">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="faa1d-117">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="faa1d-117">Framework Design Guidelines</span></span>](index.md)
