---
title: Yapı tasarımı
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3879dc3f0270a56132b44882a74c50d05914ff89
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44268870"
---
# <a name="struct-design"></a><span data-ttu-id="6f68e-102">Yapı tasarımı</span><span class="sxs-lookup"><span data-stu-id="6f68e-102">Struct Design</span></span>
<span data-ttu-id="6f68e-103">Genel amaçlı bir değer türü, genellikle kendi C# anahtar sözcüğü bir yapı da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="6f68e-103">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="6f68e-104">Bu bölümde, genel yapı tasarımı için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f68e-104">This section provides guidelines for general struct design.</span></span>  
  
 <span data-ttu-id="6f68e-105">**X DO NOT** yapısı için varsayılan bir oluşturucu sağlayın.</span><span class="sxs-lookup"><span data-stu-id="6f68e-105">**X DO NOT** provide a default constructor for a struct.</span></span>  
  
 <span data-ttu-id="6f68e-106">Bu kılavuz aşağıdaki dizinin her öğesinde Oluşturucusu çalıştırmak zorunda kalmadan oluşturulacak yapı dizileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f68e-106">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="6f68e-107">C# varsayılan oluşturucular yapılar izin vermediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6f68e-107">Notice that C# does not allow structs to have default constructors.</span></span>  
  
 <span data-ttu-id="6f68e-108">**X DO NOT** değişmez değer türleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="6f68e-108">**X DO NOT** define mutable value types.</span></span>  
  
 <span data-ttu-id="6f68e-109">Değişmez değer türleri, bazı sorunlar vardır.</span><span class="sxs-lookup"><span data-stu-id="6f68e-109">Mutable value types have several problems.</span></span> <span data-ttu-id="6f68e-110">Örneğin, bir değer türü özellik alıcısı geri döndüğünde, çağıran bir kopyasını alır.</span><span class="sxs-lookup"><span data-stu-id="6f68e-110">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="6f68e-111">Geliştiriciler, kopya örtük olarak oluşturulduğundan, bunlar kopya ve özgün değeri diziyi emin haberdar olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="6f68e-111">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="6f68e-112">Ayrıca, bazı diller (özellikle dinamik dilleri) yerel değişkenler, başvurusu kaldırıldığında bile, bir kopyalama yapılacak neden değişmez değer türleri kullanarak sorunları vardır.</span><span class="sxs-lookup"><span data-stu-id="6f68e-112">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>  
  
 <span data-ttu-id="6f68e-113">**✓ DO** veri tüm örnek olduğu bir duruma sıfıra ayarlanır ve yanlış veya boş (hangisi uygunsa) geçerli olduğundan emin.</span><span class="sxs-lookup"><span data-stu-id="6f68e-113">**✓ DO** ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>  
  
 <span data-ttu-id="6f68e-114">Struct'ın bir dizi oluşturulduğunda bu geçersiz örnekleri yanlışlıkla oluşturulmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="6f68e-114">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>  
  
 <span data-ttu-id="6f68e-115">**✓ DO** uygulamak <xref:System.IEquatable%601> değer türleri üzerinde.</span><span class="sxs-lookup"><span data-stu-id="6f68e-115">**✓ DO** implement <xref:System.IEquatable%601> on value types.</span></span>  
  
 <span data-ttu-id="6f68e-116"><xref:System.Object.Equals%2A?displayProperty=nameWithType> Yöntemi değer türleri üzerinde kutulama neden olur ve yansıma kullandığından, varsayılan uygulama çok verimli değildir.</span><span class="sxs-lookup"><span data-stu-id="6f68e-116">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="6f68e-117"><xref:System.IEquatable%601.Equals%2A> çok daha iyi performans sahip olabilir ve böylece kutulama açmayacağını uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="6f68e-117"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>  
  
 <span data-ttu-id="6f68e-118">**X DO NOT** açıkça genişletmek <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="6f68e-118">**X DO NOT** explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="6f68e-119">Aslında, çoğu dil bu engeller.</span><span class="sxs-lookup"><span data-stu-id="6f68e-119">In fact, most languages prevent this.</span></span>  
  
 <span data-ttu-id="6f68e-120">Genel olarak, yapılar çok kullanışlı olabilir, ancak yalnızca sık Kutulu değil küçük, tek, sabit değerler kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6f68e-120">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>  
  
 <span data-ttu-id="6f68e-121">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="6f68e-121">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="6f68e-122">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="6f68e-122">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f68e-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f68e-123">See also</span></span>

- [<span data-ttu-id="6f68e-124">Tür Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="6f68e-124">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
- [<span data-ttu-id="6f68e-125">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="6f68e-125">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="6f68e-126">Sınıf ile Yapı Arasında Seçim Yapma</span><span class="sxs-lookup"><span data-stu-id="6f68e-126">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
