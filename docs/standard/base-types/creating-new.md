---
title: ".NET ile yeni dizeler oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CopyTo method
- Join method
- Format method
- Concat method
- strings [.NET Framework], creating
- Insert method
ms.assetid: 06fdf123-2fac-4459-8904-eb48ab908a30
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3ba91b42bc9815b1b12fdc761882741b11790060
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="creating-new-strings-in-net"></a><span data-ttu-id="51e63-102">.NET ile yeni dizeler oluşturma</span><span class="sxs-lookup"><span data-stu-id="51e63-102">Creating New Strings in .NET</span></span>
<span data-ttu-id="51e63-103">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Basit atama kullanılarak oluşturulması dizeleri sağlar ve aynı zamanda çok sayıda farklı parametreler kullanarak dize oluşturma desteklemek için bir sınıf oluşturucu overloads.</span><span class="sxs-lookup"><span data-stu-id="51e63-103">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] allows strings to be created using simple assignment, and also overloads a class constructor to support string creation using a number of different parameters.</span></span> <span data-ttu-id="51e63-104">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Ayrıca çeşitli yöntemlerin sağlar <xref:System.String?displayProperty=nameWithType> yeni bir dize oluşturma sınıf nesneleri birkaç dizeleri, dizeleri, dizilerin birleştirerek veya nesneleri.</span><span class="sxs-lookup"><span data-stu-id="51e63-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] also provides several methods in the <xref:System.String?displayProperty=nameWithType> class that create new string objects by combining several strings, arrays of strings, or objects.</span></span>  
  
## <a name="creating-strings-using-assignment"></a><span data-ttu-id="51e63-105">Atama kullanarak dizeler oluşturma</span><span class="sxs-lookup"><span data-stu-id="51e63-105">Creating Strings Using Assignment</span></span>  
 <span data-ttu-id="51e63-106">Yeni bir oluşturmanın en kolay yolu <xref:System.String> nesnesidir yalnızca bir dize sabit değeri için atamak için bir <xref:System.String> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="51e63-106">The easiest way to create a new <xref:System.String> object is simply to assign a string literal to a <xref:System.String> object.</span></span>  
  
## <a name="creating-strings-using-a-class-constructor"></a><span data-ttu-id="51e63-107">Bir sınıf oluşturucu kullanılarak dizeler oluşturma</span><span class="sxs-lookup"><span data-stu-id="51e63-107">Creating Strings Using a Class Constructor</span></span>  
 <span data-ttu-id="51e63-108">Aşırı kullanabilirsiniz <xref:System.String> karakter dizileri dizesi oluşturmak için sınıfı oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="51e63-108">You can use overloads of the <xref:System.String> class constructor to create strings from character arrays.</span></span> <span data-ttu-id="51e63-109">Belirli bir karakterin belirtilen sayıda çoğaltarak, yeni bir dize de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51e63-109">You can also create a new string by duplicating a particular character a specified number of times.</span></span>  
  
## <a name="methods-that-return-strings"></a><span data-ttu-id="51e63-110">Dizeleri döndüren yöntemler</span><span class="sxs-lookup"><span data-stu-id="51e63-110">Methods that Return Strings</span></span>  
 <span data-ttu-id="51e63-111">Aşağıdaki tabloda yeni dize nesneler döndürmeye birkaç yararlı yöntemleri listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="51e63-111">The following table lists several useful methods that return new string objects.</span></span>  
  
|<span data-ttu-id="51e63-112">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="51e63-112">Method name</span></span>|<span data-ttu-id="51e63-113">Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında</span><span class="sxs-lookup"><span data-stu-id="51e63-113">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<span data-ttu-id="51e63-114">Giriş nesneler kümesinden biçimlendirilmiş bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="51e63-114">Builds a formatted string from a set of input objects.</span></span>|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|<span data-ttu-id="51e63-115">İki veya daha fazla dizelerden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="51e63-115">Builds strings from two or more strings.</span></span>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|<span data-ttu-id="51e63-116">Dize dizisi birleştiren yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="51e63-116">Builds a new string by combining an array of strings.</span></span>|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|<span data-ttu-id="51e63-117">Varolan bir dizeyi belirtilen dizine bir dize ekleyerek yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="51e63-117">Builds a new string by inserting a string into the specified index of an existing string.</span></span>|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|<span data-ttu-id="51e63-118">Bir dizedeki karakterleri karakter dizideki belirlenen bir konuma belirtilen kopyalar.</span><span class="sxs-lookup"><span data-stu-id="51e63-118">Copies specified characters in a string into a specified position in an array of characters.</span></span>|  
  
### <a name="format"></a><span data-ttu-id="51e63-119">Biçimi</span><span class="sxs-lookup"><span data-stu-id="51e63-119">Format</span></span>  
 <span data-ttu-id="51e63-120">Kullanabileceğiniz **String.Format** biçimlendirilmiş dizeler oluşturmak ve bağlamak için yöntem dizeleri birden çok nesneyi temsil eden.</span><span class="sxs-lookup"><span data-stu-id="51e63-120">You can use the **String.Format** method to create formatted strings and concatenate strings representing multiple objects.</span></span> <span data-ttu-id="51e63-121">Bu yöntem, otomatik olarak geçirilen nesnelere bir dizeye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="51e63-121">This method automatically converts any passed object into a string.</span></span> <span data-ttu-id="51e63-122">Örneğin, uygulamanızın görüntülemeniz gerekir, bir **Int32** değeri ve **DateTime** değeri kullanıcıya kullanarak bu değerleri temsil eden bir dize kolayca oluşturabileceğiniz **biçimi**yöntemi.</span><span class="sxs-lookup"><span data-stu-id="51e63-122">For example, if your application must display an **Int32** value and a **DateTime** value to the user, you can easily construct a string to represent these values using the **Format** method.</span></span> <span data-ttu-id="51e63-123">Bu yöntemle kullanılan kuralları biçimlendirme hakkında daha fazla bilgi için bölümüne bakarak [bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="51e63-123">For information about formatting conventions used with this method, see the section on [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>  
  
 <span data-ttu-id="51e63-124">Aşağıdaki örnek kullanır **biçimi** yöntemi kullanan bir tamsayı değişken bir dize oluşturma.</span><span class="sxs-lookup"><span data-stu-id="51e63-124">The following example uses the **Format** method to create a string that uses an integer variable.</span></span>  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 <span data-ttu-id="51e63-125">Bu örnekte,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> geçerli iş parçacığı ile ilişkili kültür tarafından belirtilen şekilde geçerli tarih ve saati görüntüler.</span><span class="sxs-lookup"><span data-stu-id="51e63-125">In this example,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> displays the current date and time in a manner specified by the culture associated with the current thread.</span></span>  
  
### <a name="concat"></a><span data-ttu-id="51e63-126">concat</span><span class="sxs-lookup"><span data-stu-id="51e63-126">Concat</span></span>  
 <span data-ttu-id="51e63-127">**String.Concat** yöntemi, kolayca yeni bir dize nesnesi iki veya daha fazla var olan nesneleri oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="51e63-127">The **String.Concat** method can be used to easily create a new string object from two or more existing objects.</span></span> <span data-ttu-id="51e63-128">Dizeyi birleştirmek için dil bağımsız bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="51e63-128">It provides a language-independent way to concatenate strings.</span></span> <span data-ttu-id="51e63-129">Bu yöntem, türetilen herhangi bir sınıf kabul eder **System.Object**.</span><span class="sxs-lookup"><span data-stu-id="51e63-129">This method accepts any class that derives from **System.Object**.</span></span> <span data-ttu-id="51e63-130">Aşağıdaki örnekte, iki mevcut string nesneleri ve ayıran karakter bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="51e63-130">The following example creates a string from two existing string objects and a separating character.</span></span>  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a><span data-ttu-id="51e63-131">Birleştirme</span><span class="sxs-lookup"><span data-stu-id="51e63-131">Join</span></span>  
 <span data-ttu-id="51e63-132">**String.Join** yöntemi, bir dizi dizeler ve ayırıcı dize yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="51e63-132">The **String.Join** method creates a new string from an array of strings and a separator string.</span></span> <span data-ttu-id="51e63-133">Bu yöntem belki de virgülle ayrılmış bir listede yapmadan birlikte, birden çok dizeyi birleştirme istiyorsanız kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="51e63-133">This method is useful if you want to concatenate multiple strings together, making a list perhaps separated by a comma.</span></span>  
  
 <span data-ttu-id="51e63-134">Aşağıdaki örnekte bir alan bir dize dizisi bağlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="51e63-134">The following example uses a space to bind a string array.</span></span>  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a><span data-ttu-id="51e63-135">Ekleme</span><span class="sxs-lookup"><span data-stu-id="51e63-135">Insert</span></span>  
 <span data-ttu-id="51e63-136">**String.Insert** yöntemi, başka bir dize olarak belirtilen bir konuma bir dize ekleyerek yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="51e63-136">The **String.Insert** method creates a new string by inserting a string into a specified position in another string.</span></span> <span data-ttu-id="51e63-137">Bu yöntem, sıfır tabanlı bir dizin kullanır.</span><span class="sxs-lookup"><span data-stu-id="51e63-137">This method uses a zero-based index.</span></span> <span data-ttu-id="51e63-138">Aşağıdaki örnek bir dize beşinci dizin konumunu ekler `MyString` ve bu değeri ile yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="51e63-138">The following example inserts a string into the fifth index position of `MyString` and creates a new string with this value.</span></span>  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a><span data-ttu-id="51e63-139">CopyTo</span><span class="sxs-lookup"><span data-stu-id="51e63-139">CopyTo</span></span>  
 <span data-ttu-id="51e63-140">**String.CopyTo** yöntemi dize bölümlerini karakterden oluşan bir diziye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="51e63-140">The **String.CopyTo** method copies portions of a string into an array of characters.</span></span> <span data-ttu-id="51e63-141">Dize kopyalanacak karakter sayısını ve her iki başlangıç dizini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51e63-141">You can specify both the beginning index of the string and the number of characters to be copied.</span></span> <span data-ttu-id="51e63-142">Bu yöntem, kaynak dizin, bir karakter dizisi, hedef dizin ve kopyalamak için karakter sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="51e63-142">This method takes the source index, an array of characters, the destination index, and the number of characters to copy.</span></span> <span data-ttu-id="51e63-143">Tüm dizinler sıfır tabanlı.</span><span class="sxs-lookup"><span data-stu-id="51e63-143">All indexes are zero-based.</span></span>  
  
 <span data-ttu-id="51e63-144">Aşağıdaki örnek kullanır **CopyTo** "bir dizeden Hello" ifadesini nesne word'ün karakterleri karakter ilk dizin konumuna kopyalamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="51e63-144">The following example uses the **CopyTo** method to copy the characters of the word "Hello" from a string object to the first index position of an array of characters.</span></span>  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="51e63-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="51e63-145">See Also</span></span>  
 [<span data-ttu-id="51e63-146">Temel Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="51e63-146">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)  
 [<span data-ttu-id="51e63-147">Bileşik Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="51e63-147">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
