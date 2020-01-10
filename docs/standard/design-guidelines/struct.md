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
ms.openlocfilehash: 8841a30f1dd0420b2ea45740b1e33bde5199c3f9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709055"
---
# <a name="struct-design"></a><span data-ttu-id="ae742-102">Yapı Tasarımı</span><span class="sxs-lookup"><span data-stu-id="ae742-102">Struct Design</span></span>
<span data-ttu-id="ae742-103">Genel amaçlı değer türü, genellikle bir struct, C# anahtar kelimesi olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ae742-103">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="ae742-104">Bu bölüm, genel yapı tasarımı için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ae742-104">This section provides guidelines for general struct design.</span></span>  
  
 <span data-ttu-id="ae742-105">**X** bir struct için parametresiz bir Oluşturucu sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="ae742-105">**X DO NOT** provide a parameterless constructor for a struct.</span></span>  
  
 <span data-ttu-id="ae742-106">Bu kılavuzdan sonra, dizinin her öğesinde oluşturucuyu çalıştırmak zorunda kalmadan yapıların dizilerinin oluşturulmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="ae742-106">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="ae742-107">Yapıların parametresiz C# oluşturuculara sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="ae742-107">Notice that C# does not allow structs to have parameterless constructors.</span></span>  
  
 <span data-ttu-id="ae742-108">**X DO NOT** değişmez değer türleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="ae742-108">**X DO NOT** define mutable value types.</span></span>  
  
 <span data-ttu-id="ae742-109">Kesilebilir değer türlerinde birçok sorun vardır.</span><span class="sxs-lookup"><span data-stu-id="ae742-109">Mutable value types have several problems.</span></span> <span data-ttu-id="ae742-110">Örneğin, bir özellik alıcısı bir değer türü döndürdüğünde, çağıran bir kopyasını alır.</span><span class="sxs-lookup"><span data-stu-id="ae742-110">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="ae742-111">Kopya örtük olarak oluşturulduğundan, geliştiriciler özgün değeri değil, kopyayı değiştirmez gibi farkında olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="ae742-111">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="ae742-112">Ayrıca, bazı dillerin (özellikle de dinamik diller) değişebilir değer türlerini kullanarak sorunlar vardır, çünkü başvuru yapıldığında yerel değişkenler de bir kopyanın oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="ae742-112">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>  
  
 <span data-ttu-id="ae742-113">**✓ DO** veri tüm örnek olduğu bir duruma sıfıra ayarlanır ve yanlış veya boş (hangisi uygunsa) geçerli olduğundan emin.</span><span class="sxs-lookup"><span data-stu-id="ae742-113">**✓ DO** ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>  
  
 <span data-ttu-id="ae742-114">Bu, yapıların bir dizisi oluşturulduğunda geçersiz örneklerin yanlışlıkla oluşturulmasını önler.</span><span class="sxs-lookup"><span data-stu-id="ae742-114">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>  
  
 <span data-ttu-id="ae742-115">**✓ DO** uygulamak <xref:System.IEquatable%601> değer türleri üzerinde.</span><span class="sxs-lookup"><span data-stu-id="ae742-115">**✓ DO** implement <xref:System.IEquatable%601> on value types.</span></span>  
  
 <span data-ttu-id="ae742-116">Değer türlerinde <xref:System.Object.Equals%2A?displayProperty=nameWithType> yöntemi kutulama sağlar ve yansıma kullandığından, varsayılan uygulama çok verimli değildir.</span><span class="sxs-lookup"><span data-stu-id="ae742-116">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="ae742-117"><xref:System.IEquatable%601.Equals%2A> çok daha iyi bir performansa sahip olabilir ve bu, kutulamayı neden olmayacak şekilde uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="ae742-117"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>  
  
 <span data-ttu-id="ae742-118">**X DO NOT** açıkça genişletmek <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="ae742-118">**X DO NOT** explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="ae742-119">Aslında çoğu dil bunu engeller.</span><span class="sxs-lookup"><span data-stu-id="ae742-119">In fact, most languages prevent this.</span></span>  
  
 <span data-ttu-id="ae742-120">Genel olarak, yapılar çok faydalı olabilir, ancak yalnızca sık kutulanmamış küçük, tek, sabit değerler için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ae742-120">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>  
  
 <span data-ttu-id="ae742-121">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="ae742-121">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="ae742-122">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="ae742-122">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae742-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae742-123">See also</span></span>

- [<span data-ttu-id="ae742-124">Tür Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ae742-124">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="ae742-125">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ae742-125">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="ae742-126">Sınıf ile Yapı Arasında Seçim Yapma</span><span class="sxs-lookup"><span data-stu-id="ae742-126">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
