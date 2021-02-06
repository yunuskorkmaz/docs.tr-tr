---
description: 'Daha fazla bilgi edinin: yapı tasarımı'
title: Yapı Tasarımı
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
ms.openlocfilehash: a28dd3e452d22e61d95ec521fdbde6539e38ed78
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641908"
---
# <a name="struct-design"></a><span data-ttu-id="6f4d8-103">Yapı Tasarımı</span><span class="sxs-lookup"><span data-stu-id="6f4d8-103">Struct Design</span></span>

<span data-ttu-id="6f4d8-104">Genel amaçlı değer türü genellikle struct, C# anahtar sözcüğü olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="6f4d8-104">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="6f4d8-105">Bu bölüm, genel yapı tasarımı için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f4d8-105">This section provides guidelines for general struct design.</span></span>

 <span data-ttu-id="6f4d8-106">❌ Struct için parametresiz bir Oluşturucu sağlamakmayın.</span><span class="sxs-lookup"><span data-stu-id="6f4d8-106">❌ DO NOT provide a parameterless constructor for a struct.</span></span>

 <span data-ttu-id="6f4d8-107">Bu kılavuzdan sonra, dizinin her öğesinde oluşturucuyu çalıştırmak zorunda kalmadan yapıların dizilerinin oluşturulmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="6f4d8-107">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="6f4d8-108">C# ' nin yapıların parametresiz oluşturuculara sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="6f4d8-108">Notice that C# does not allow structs to have parameterless constructors.</span></span>

 <span data-ttu-id="6f4d8-109">❌ Kesilebilir değer türlerini tanımlamayın.</span><span class="sxs-lookup"><span data-stu-id="6f4d8-109">❌ DO NOT define mutable value types.</span></span>

 <span data-ttu-id="6f4d8-110">Kesilebilir değer türlerinde birçok sorun vardır.</span><span class="sxs-lookup"><span data-stu-id="6f4d8-110">Mutable value types have several problems.</span></span> <span data-ttu-id="6f4d8-111">Örneğin, bir özellik alıcısı bir değer türü döndürdüğünde, çağıran bir kopyasını alır.</span><span class="sxs-lookup"><span data-stu-id="6f4d8-111">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="6f4d8-112">Kopya örtük olarak oluşturulduğundan, geliştiriciler özgün değeri değil, kopyayı değiştirmez gibi farkında olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="6f4d8-112">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="6f4d8-113">Ayrıca, bazı dillerin (özellikle de dinamik diller) değişebilir değer türlerini kullanarak sorunlar vardır, çünkü başvuru yapıldığında yerel değişkenler de bir kopyanın oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="6f4d8-113">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>

 <span data-ttu-id="6f4d8-114">✔️ Tüm örnek verilerinin sıfıra, yanlış veya null (uygun şekilde) olarak ayarlandığı bir durumun geçerli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="6f4d8-114">✔️ DO ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>

 <span data-ttu-id="6f4d8-115">Bu, yapıların bir dizisi oluşturulduğunda geçersiz örneklerin yanlışlıkla oluşturulmasını önler.</span><span class="sxs-lookup"><span data-stu-id="6f4d8-115">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>

 <span data-ttu-id="6f4d8-116"><xref:System.IEquatable%601>değer türlerinde uygulama ✔️.</span><span class="sxs-lookup"><span data-stu-id="6f4d8-116">✔️ DO implement <xref:System.IEquatable%601> on value types.</span></span>

 <span data-ttu-id="6f4d8-117"><xref:System.Object.Equals%2A?displayProperty=nameWithType>Değer türlerindeki yöntemi kutulama sağlar ve yansıma kullandığından, varsayılan uygulama çok verimli değildir.</span><span class="sxs-lookup"><span data-stu-id="6f4d8-117">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="6f4d8-118"><xref:System.IEquatable%601.Equals%2A> çok daha iyi performansa sahip olabilir ve bu, kutulamayı neden olmayacak şekilde uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="6f4d8-118"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>

 <span data-ttu-id="6f4d8-119">❌ Açıkça genişlemeyin <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="6f4d8-119">❌ DO NOT explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="6f4d8-120">Aslında çoğu dil bunu engeller.</span><span class="sxs-lookup"><span data-stu-id="6f4d8-120">In fact, most languages prevent this.</span></span>

 <span data-ttu-id="6f4d8-121">Genel olarak, yapılar çok faydalı olabilir, ancak yalnızca sık kutulanmamış küçük, tek, sabit değerler için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6f4d8-121">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>

 <span data-ttu-id="6f4d8-122">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="6f4d8-122">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="6f4d8-123">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="6f4d8-123">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="6f4d8-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f4d8-124">See also</span></span>

- [<span data-ttu-id="6f4d8-125">Tür tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="6f4d8-125">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="6f4d8-126">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="6f4d8-126">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="6f4d8-127">Sınıf ile Yapı Arasında Seçim Yapma</span><span class="sxs-lookup"><span data-stu-id="6f4d8-127">Choosing Between Class and Struct</span></span>](choosing-between-class-and-struct.md)
