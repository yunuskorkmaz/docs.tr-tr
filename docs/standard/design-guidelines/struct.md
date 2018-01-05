---
title: "Yapı tasarım"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2f4a6debc25a51e3a0a83e70fc8c8f8fc55c62f5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="struct-design"></a><span data-ttu-id="b79bc-102">Yapı tasarım</span><span class="sxs-lookup"><span data-stu-id="b79bc-102">Struct Design</span></span>
<span data-ttu-id="b79bc-103">Genel amaçlı değer türü, genellikle kendi C# anahtar sözcüğü bir yapı da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b79bc-103">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="b79bc-104">Bu bölüm için genel yapısı tasarım yönergeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b79bc-104">This section provides guidelines for general struct design.</span></span>  
  
 <span data-ttu-id="b79bc-105">**X yok** yapısı için varsayılan bir oluşturucu sağlayın.</span><span class="sxs-lookup"><span data-stu-id="b79bc-105">**X DO NOT** provide a default constructor for a struct.</span></span>  
  
 <span data-ttu-id="b79bc-106">Bu kılavuz aşağıdaki Oluşturucusu dizinin her bir öğede çalıştırmak zorunda kalmadan oluşturulacak yapılar dizileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b79bc-106">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="b79bc-107">C# varsayılan oluşturucular olmasını yapılar izin vermediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b79bc-107">Notice that C# does not allow structs to have default constructors.</span></span>  
  
 <span data-ttu-id="b79bc-108">**X yok** değişmez değer türleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="b79bc-108">**X DO NOT** define mutable value types.</span></span>  
  
 <span data-ttu-id="b79bc-109">Değişmez değer türleri bazı sorunlar vardır.</span><span class="sxs-lookup"><span data-stu-id="b79bc-109">Mutable value types have several problems.</span></span> <span data-ttu-id="b79bc-110">Örneğin, bir özellik Get yordamı bir değer türü geri döndüğünde, çağıran bir kopyasını alır.</span><span class="sxs-lookup"><span data-stu-id="b79bc-110">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="b79bc-111">Kopya örtük olarak oluşturulduğundan, geliştiriciler, kopyalama ve özgün değeri diziyi, uyumlu olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="b79bc-111">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="b79bc-112">Ayrıca, bazı dillerde (özellikle dinamik dilleri) yerel değişkenler başvuru yapıldı olduğunda bile, yapılacak bir kopyasını neden olduğundan değişmez değer türleri kullanarak sorunları vardır.</span><span class="sxs-lookup"><span data-stu-id="b79bc-112">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>  
  
 <span data-ttu-id="b79bc-113">**✓ YAPMAK** veri tüm örnek olduğu bir duruma sıfıra ayarlanır ve yanlış veya boş (hangisi uygunsa) geçerli olduğundan emin.</span><span class="sxs-lookup"><span data-stu-id="b79bc-113">**✓ DO** ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>  
  
 <span data-ttu-id="b79bc-114">Yapılar dizisi oluşturulduğunda, bu geçersiz örnekleri yanlışlıkla oluşturulmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="b79bc-114">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>  
  
 <span data-ttu-id="b79bc-115">**✓ YAPMAK** uygulamak <xref:System.IEquatable%601> değer türleri üzerinde.</span><span class="sxs-lookup"><span data-stu-id="b79bc-115">**✓ DO** implement <xref:System.IEquatable%601> on value types.</span></span>  
  
 <span data-ttu-id="b79bc-116"><xref:System.Object.Equals%2A?displayProperty=nameWithType> Değer türleri üzerinde yöntemi kutulama neden olur ve yansıma kullandığından, varsayılan uygulama çok verimli değil.</span><span class="sxs-lookup"><span data-stu-id="b79bc-116">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="b79bc-117"><xref:System.IEquatable%601.Equals%2A>çok daha iyi performans sağlayabilirsiniz ve böylece kutulama açmayacağını uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b79bc-117"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>  
  
 <span data-ttu-id="b79bc-118">**X yok** açıkça genişletmek <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="b79bc-118">**X DO NOT** explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="b79bc-119">Aslında, çoğu dilleri bu engeller.</span><span class="sxs-lookup"><span data-stu-id="b79bc-119">In fact, most languages prevent this.</span></span>  
  
 <span data-ttu-id="b79bc-120">Genel olarak, yapılar çok kullanışlı olabilir ancak yalnızca sık Kutulu olmayan küçük, tek, değişmez değerler kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b79bc-120">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>  
  
 <span data-ttu-id="b79bc-121">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="b79bc-121">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b79bc-122">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="b79bc-122">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b79bc-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b79bc-123">See Also</span></span>  
 [<span data-ttu-id="b79bc-124">Tür Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="b79bc-124">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="b79bc-125">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="b79bc-125">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="b79bc-126">Sınıf ile Yapı Arasında Seçim Yapma</span><span class="sxs-lookup"><span data-stu-id="b79bc-126">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
