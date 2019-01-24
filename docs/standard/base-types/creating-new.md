---
title: . NET'te yeni dizeler oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94ac21dfdf58e8aa1b629604792ad2f0f57c60d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659507"
---
# <a name="creating-new-strings-in-net"></a><span data-ttu-id="fd711-102">. NET'te yeni dizeler oluşturma</span><span class="sxs-lookup"><span data-stu-id="fd711-102">Creating New Strings in .NET</span></span>
<span data-ttu-id="fd711-103">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Basit atama kullanılarak oluşturulması dizeleri sağlar ve ayrıca çok sayıda farklı parametreler kullanarak dize oluşturma desteklemek için bir sınıf oluşturucu aşırı yüklemeleri.</span><span class="sxs-lookup"><span data-stu-id="fd711-103">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] allows strings to be created using simple assignment, and also overloads a class constructor to support string creation using a number of different parameters.</span></span> <span data-ttu-id="fd711-104">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Ayrıca, çeşitli yöntemler sunar <xref:System.String?displayProperty=nameWithType> yeni dize Oluştur sınıfı nesnelerini bir araya getirerek birkaç dizeleri, dize, veya nesneleri.</span><span class="sxs-lookup"><span data-stu-id="fd711-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] also provides several methods in the <xref:System.String?displayProperty=nameWithType> class that create new string objects by combining several strings, arrays of strings, or objects.</span></span>  
  
## <a name="creating-strings-using-assignment"></a><span data-ttu-id="fd711-105">Atama kullanarak dize oluşturma</span><span class="sxs-lookup"><span data-stu-id="fd711-105">Creating Strings Using Assignment</span></span>  
 <span data-ttu-id="fd711-106">Yeni bir oluşturmanın en kolay yolu <xref:System.String> nesnedir yalnızca bir dize sabit atamak için bir <xref:System.String> nesne.</span><span class="sxs-lookup"><span data-stu-id="fd711-106">The easiest way to create a new <xref:System.String> object is simply to assign a string literal to a <xref:System.String> object.</span></span>  
  
## <a name="creating-strings-using-a-class-constructor"></a><span data-ttu-id="fd711-107">Sınıf oluşturucusunu kullanarak dize oluşturma</span><span class="sxs-lookup"><span data-stu-id="fd711-107">Creating Strings Using a Class Constructor</span></span>  
 <span data-ttu-id="fd711-108">Aşırı yüklemesini kullanabilirsiniz <xref:System.String> karakter dizilerden dizeleri oluşturmak için sınıf oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="fd711-108">You can use overloads of the <xref:System.String> class constructor to create strings from character arrays.</span></span> <span data-ttu-id="fd711-109">Belirli bir karakterin belirtilen sayıda çoğaltarak, yeni bir dize da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd711-109">You can also create a new string by duplicating a particular character a specified number of times.</span></span>  
  
## <a name="methods-that-return-strings"></a><span data-ttu-id="fd711-110">Dizeleri döndüren yöntemler</span><span class="sxs-lookup"><span data-stu-id="fd711-110">Methods that Return Strings</span></span>  
 <span data-ttu-id="fd711-111">Yeni dize nesneleri döndürür çeşitli kullanışlı yöntemler aşağıdaki tabloda listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="fd711-111">The following table lists several useful methods that return new string objects.</span></span>  
  
|<span data-ttu-id="fd711-112">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="fd711-112">Method name</span></span>|<span data-ttu-id="fd711-113">Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında</span><span class="sxs-lookup"><span data-stu-id="fd711-113">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<span data-ttu-id="fd711-114">Biçimlendirilen dizeden Giriş bir nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fd711-114">Builds a formatted string from a set of input objects.</span></span>|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|<span data-ttu-id="fd711-115">İki veya daha fazla dizeleri dizelerden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fd711-115">Builds strings from two or more strings.</span></span>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|<span data-ttu-id="fd711-116">Dize dizisi birleştirerek yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fd711-116">Builds a new string by combining an array of strings.</span></span>|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|<span data-ttu-id="fd711-117">Varolan bir dizeyi belirtilen dizine bir dize ekleyerek yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fd711-117">Builds a new string by inserting a string into the specified index of an existing string.</span></span>|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|<span data-ttu-id="fd711-118">Bir dizedeki karakterleri karakter bir dizideki belirtilen bir konuma belirtilen kopyalar.</span><span class="sxs-lookup"><span data-stu-id="fd711-118">Copies specified characters in a string into a specified position in an array of characters.</span></span>|  
  
### <a name="format"></a><span data-ttu-id="fd711-119">Biçimi</span><span class="sxs-lookup"><span data-stu-id="fd711-119">Format</span></span>  
 <span data-ttu-id="fd711-120">Kullanabileceğiniz **String.Format** biçimlendirilmiş dizeler oluşturmak ve bağlamak için yöntemi, birden çok nesneyi temsil eden dizeleri.</span><span class="sxs-lookup"><span data-stu-id="fd711-120">You can use the **String.Format** method to create formatted strings and concatenate strings representing multiple objects.</span></span> <span data-ttu-id="fd711-121">Bu yöntem, otomatik olarak geçirilen herhangi bir nesne bir dizeye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="fd711-121">This method automatically converts any passed object into a string.</span></span> <span data-ttu-id="fd711-122">Örneğin, uygulamanızın görüntülemelidir bir **Int32** değeri ve bir **DateTime** değeri kullanıcıya bir dize kullanarak bu değerleri göstermek için kolayca oluşturabilirsiniz **biçimi**yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fd711-122">For example, if your application must display an **Int32** value and a **DateTime** value to the user, you can easily construct a string to represent these values using the **Format** method.</span></span> <span data-ttu-id="fd711-123">Bu yöntemle kullanılan kuralları biçimlendirme hakkında daha fazla bilgi için üzerinde bölümüne bakın. [bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="fd711-123">For information about formatting conventions used with this method, see the section on [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>  
  
 <span data-ttu-id="fd711-124">Aşağıdaki örnekte **biçimi** yöntemini kullanan bir tam sayı değişkeni bir dize.</span><span class="sxs-lookup"><span data-stu-id="fd711-124">The following example uses the **Format** method to create a string that uses an integer variable.</span></span>  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 <span data-ttu-id="fd711-125">Bu örnekte,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> geçerli iş parçacığıyla ilişkilendirilmiş kültürü tarafından belirtilen şekilde geçerli tarih ve saati görüntüler.</span><span class="sxs-lookup"><span data-stu-id="fd711-125">In this example,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> displays the current date and time in a manner specified by the culture associated with the current thread.</span></span>  
  
### <a name="concat"></a><span data-ttu-id="fd711-126">concat</span><span class="sxs-lookup"><span data-stu-id="fd711-126">Concat</span></span>  
 <span data-ttu-id="fd711-127">**String.Concat** yöntemi, kolayca yeni bir dize nesnesi iki veya daha fazla varolan nesnelerden oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fd711-127">The **String.Concat** method can be used to easily create a new string object from two or more existing objects.</span></span> <span data-ttu-id="fd711-128">Dizeleri birleştirmek için bir dilden bağımsız yol sunar.</span><span class="sxs-lookup"><span data-stu-id="fd711-128">It provides a language-independent way to concatenate strings.</span></span> <span data-ttu-id="fd711-129">Bu yöntem, türetilen herhangi bir sınıf kabul eden **System.Object**.</span><span class="sxs-lookup"><span data-stu-id="fd711-129">This method accepts any class that derives from **System.Object**.</span></span> <span data-ttu-id="fd711-130">Aşağıdaki örnek, iki var olan dize nesneleri ve ayırıcı karakteri bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fd711-130">The following example creates a string from two existing string objects and a separating character.</span></span>  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a><span data-ttu-id="fd711-131">Birleştirme</span><span class="sxs-lookup"><span data-stu-id="fd711-131">Join</span></span>  
 <span data-ttu-id="fd711-132">**String.Join** yöntemi, bir dizi dizeleri ve bir ayırıcı dizesinde yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fd711-132">The **String.Join** method creates a new string from an array of strings and a separator string.</span></span> <span data-ttu-id="fd711-133">Bu yöntem, belki de bir virgülle ayrılmış bir listede yapmadan birlikte, birden çok dizeyi birleştirme istiyorsanız yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="fd711-133">This method is useful if you want to concatenate multiple strings together, making a list perhaps separated by a comma.</span></span>  
  
 <span data-ttu-id="fd711-134">Aşağıdaki örnek, bir dize dizisi bağlamak için bir alanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="fd711-134">The following example uses a space to bind a string array.</span></span>  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a><span data-ttu-id="fd711-135">Ekleme</span><span class="sxs-lookup"><span data-stu-id="fd711-135">Insert</span></span>  
 <span data-ttu-id="fd711-136">**String.Insert** yöntemi, bir dizeyi başka bir dizede belirtilen konuma içine ekleyerek yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fd711-136">The **String.Insert** method creates a new string by inserting a string into a specified position in another string.</span></span> <span data-ttu-id="fd711-137">Bu yöntem, sıfır tabanlı dizini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fd711-137">This method uses a zero-based index.</span></span> <span data-ttu-id="fd711-138">Aşağıdaki örnek bir dize beşinci dizin konumu ekler `MyString` ve bu değeri ile yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fd711-138">The following example inserts a string into the fifth index position of `MyString` and creates a new string with this value.</span></span>  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a><span data-ttu-id="fd711-139">CopyTo</span><span class="sxs-lookup"><span data-stu-id="fd711-139">CopyTo</span></span>  
 <span data-ttu-id="fd711-140">**String.CopyTo** yöntemi, bir dizenin bölümlerini bir karakter dizisine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="fd711-140">The **String.CopyTo** method copies portions of a string into an array of characters.</span></span> <span data-ttu-id="fd711-141">Dize ve karakter kopyalanması sayısını hem başlangıç dizini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd711-141">You can specify both the beginning index of the string and the number of characters to be copied.</span></span> <span data-ttu-id="fd711-142">Bu yöntem, kaynak dizin, bir karakter dizisini, hedef dizin ve kopyalamak için karakter sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="fd711-142">This method takes the source index, an array of characters, the destination index, and the number of characters to copy.</span></span> <span data-ttu-id="fd711-143">Tüm dizinler sıfır tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="fd711-143">All indexes are zero-based.</span></span>  
  
 <span data-ttu-id="fd711-144">Aşağıdaki örnekte **CopyTo** nesnesi "bir dizeden Hello" sözcüğünü karakterleri karakter dizisi ilk dizin konumuna kopyalamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fd711-144">The following example uses the **CopyTo** method to copy the characters of the word "Hello" from a string object to the first index position of an array of characters.</span></span>  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="fd711-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd711-145">See also</span></span>

- [<span data-ttu-id="fd711-146">Temel Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="fd711-146">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
- [<span data-ttu-id="fd711-147">Bileşik Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="fd711-147">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
