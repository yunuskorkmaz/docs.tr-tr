---
title: Yapı Tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
ms.openlocfilehash: b6d06bc8a1e8535f1452af0726138abaebfd4951
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743603"
---
# <a name="struct-design"></a><span data-ttu-id="2dc08-102">Yapı Tasarımı</span><span class="sxs-lookup"><span data-stu-id="2dc08-102">Struct Design</span></span>
<span data-ttu-id="2dc08-103">Genel amaçlı değer türü, genellikle bir struct, C# anahtar kelimesi olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2dc08-103">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="2dc08-104">Bu bölüm, genel yapı tasarımı için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2dc08-104">This section provides guidelines for general struct design.</span></span>

 <span data-ttu-id="2dc08-105">❌ yapı için parametresiz bir Oluşturucu sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="2dc08-105">❌ DO NOT provide a parameterless constructor for a struct.</span></span>

 <span data-ttu-id="2dc08-106">Bu kılavuzdan sonra, dizinin her öğesinde oluşturucuyu çalıştırmak zorunda kalmadan yapıların dizilerinin oluşturulmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="2dc08-106">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="2dc08-107">Yapıların parametresiz C# oluşturuculara sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="2dc08-107">Notice that C# does not allow structs to have parameterless constructors.</span></span>

 <span data-ttu-id="2dc08-108">❌ kesilebilir değer türlerini tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="2dc08-108">❌ DO NOT define mutable value types.</span></span>

 <span data-ttu-id="2dc08-109">Kesilebilir değer türlerinde birçok sorun vardır.</span><span class="sxs-lookup"><span data-stu-id="2dc08-109">Mutable value types have several problems.</span></span> <span data-ttu-id="2dc08-110">Örneğin, bir özellik alıcısı bir değer türü döndürdüğünde, çağıran bir kopyasını alır.</span><span class="sxs-lookup"><span data-stu-id="2dc08-110">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="2dc08-111">Kopya örtük olarak oluşturulduğundan, geliştiriciler özgün değeri değil, kopyayı değiştirmez gibi farkında olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="2dc08-111">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="2dc08-112">Ayrıca, bazı dillerin (özellikle de dinamik diller) değişebilir değer türlerini kullanarak sorunlar vardır, çünkü başvuru yapıldığında yerel değişkenler de bir kopyanın oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="2dc08-112">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>

 <span data-ttu-id="2dc08-113">✔️ Tüm örnek verilerinin sıfıra, yanlış veya null (uygun şekilde) olarak ayarlandığı bir durumun geçerli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="2dc08-113">✔️ DO ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>

 <span data-ttu-id="2dc08-114">Bu, yapıların bir dizisi oluşturulduğunda geçersiz örneklerin yanlışlıkla oluşturulmasını önler.</span><span class="sxs-lookup"><span data-stu-id="2dc08-114">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>

 <span data-ttu-id="2dc08-115">✔️ değer türlerinde <xref:System.IEquatable%601> uygulayın.</span><span class="sxs-lookup"><span data-stu-id="2dc08-115">✔️ DO implement <xref:System.IEquatable%601> on value types.</span></span>

 <span data-ttu-id="2dc08-116">Değer türlerinde <xref:System.Object.Equals%2A?displayProperty=nameWithType> yöntemi kutulama sağlar ve yansıma kullandığından, varsayılan uygulama çok verimli değildir.</span><span class="sxs-lookup"><span data-stu-id="2dc08-116">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="2dc08-117"><xref:System.IEquatable%601.Equals%2A> çok daha iyi bir performansa sahip olabilir ve bu, kutulamayı neden olmayacak şekilde uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="2dc08-117"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>

 <span data-ttu-id="2dc08-118">❌, <xref:System.ValueType>açıkça genişletmez.</span><span class="sxs-lookup"><span data-stu-id="2dc08-118">❌ DO NOT explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="2dc08-119">Aslında çoğu dil bunu engeller.</span><span class="sxs-lookup"><span data-stu-id="2dc08-119">In fact, most languages prevent this.</span></span>

 <span data-ttu-id="2dc08-120">Genel olarak, yapılar çok faydalı olabilir, ancak yalnızca sık kutulanmamış küçük, tek, sabit değerler için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2dc08-120">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>

 <span data-ttu-id="2dc08-121">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="2dc08-121">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="2dc08-122">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="2dc08-122">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="2dc08-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2dc08-123">See also</span></span>

- [<span data-ttu-id="2dc08-124">Tür Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2dc08-124">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="2dc08-125">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2dc08-125">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="2dc08-126">Sınıf ile Yapı Arasında Seçim Yapma</span><span class="sxs-lookup"><span data-stu-id="2dc08-126">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
