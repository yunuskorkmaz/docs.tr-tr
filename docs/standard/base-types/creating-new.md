---
title: .NET ' te yeni dizeler oluşturma
description: Birkaç dizeyi, dize dizilerini veya .NET içindeki nesneleri birleştiren atama, sınıf oluşturucuları veya System. String yöntemlerini kullanarak dizeler oluşturmayı öğrenin.
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
ms.openlocfilehash: b44d0f8e1717ead72e28f0be644644961d1482b6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596454"
---
# <a name="creating-new-strings-in-net"></a><span data-ttu-id="db1bd-103">.NET ' te yeni dizeler oluşturma</span><span class="sxs-lookup"><span data-stu-id="db1bd-103">Creating New Strings in .NET</span></span>
<span data-ttu-id="db1bd-104">.NET Framework, dizelerin basit atama kullanılarak oluşturulmasına izin verir ve ayrıca bir dizi farklı parametre kullanarak dize oluşturmayı desteklemek için bir sınıf oluşturucusunu aşırı yükler.</span><span class="sxs-lookup"><span data-stu-id="db1bd-104">The .NET Framework allows strings to be created using simple assignment, and also overloads a class constructor to support string creation using a number of different parameters.</span></span> <span data-ttu-id="db1bd-105">.NET Framework Ayrıca <xref:System.String?displayProperty=nameWithType> birkaç dizeyi, dize dizilerini veya nesneleri birleştirerek yeni dize nesneleri oluşturan sınıfta çeşitli yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="db1bd-105">The .NET Framework also provides several methods in the <xref:System.String?displayProperty=nameWithType> class that create new string objects by combining several strings, arrays of strings, or objects.</span></span>  
  
## <a name="creating-strings-using-assignment"></a><span data-ttu-id="db1bd-106">Atama kullanarak dizeler oluşturma</span><span class="sxs-lookup"><span data-stu-id="db1bd-106">Creating Strings Using Assignment</span></span>  
 <span data-ttu-id="db1bd-107">Yeni bir nesne oluşturmanın en kolay yolu, <xref:System.String> bir nesneye dize sabit değeri atamanız yeterlidir <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="db1bd-107">The easiest way to create a new <xref:System.String> object is simply to assign a string literal to a <xref:System.String> object.</span></span>  
  
## <a name="creating-strings-using-a-class-constructor"></a><span data-ttu-id="db1bd-108">Sınıf Oluşturucusu kullanarak dizeler oluşturma</span><span class="sxs-lookup"><span data-stu-id="db1bd-108">Creating Strings Using a Class Constructor</span></span>  
 <span data-ttu-id="db1bd-109"><xref:System.String>Karakter dizelerinden dizeler oluşturmak için sınıf oluşturucusunun aşırı yüklerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db1bd-109">You can use overloads of the <xref:System.String> class constructor to create strings from character arrays.</span></span> <span data-ttu-id="db1bd-110">Belirli bir karakteri belirtilen sayıda çoğaltarak yeni bir dize de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db1bd-110">You can also create a new string by duplicating a particular character a specified number of times.</span></span>  
  
## <a name="methods-that-return-strings"></a><span data-ttu-id="db1bd-111">Dizeleri döndüren yöntemler</span><span class="sxs-lookup"><span data-stu-id="db1bd-111">Methods that Return Strings</span></span>  
 <span data-ttu-id="db1bd-112">Aşağıdaki tabloda yeni dize nesneleri döndüren çeşitli yararlı yöntemler listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="db1bd-112">The following table lists several useful methods that return new string objects.</span></span>  
  
|<span data-ttu-id="db1bd-113">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="db1bd-113">Method name</span></span>|<span data-ttu-id="db1bd-114">Kullanım</span><span class="sxs-lookup"><span data-stu-id="db1bd-114">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<span data-ttu-id="db1bd-115">Bir giriş nesneleri kümesinden biçimli bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="db1bd-115">Builds a formatted string from a set of input objects.</span></span>|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|<span data-ttu-id="db1bd-116">İki veya daha fazla dizeden dizeler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="db1bd-116">Builds strings from two or more strings.</span></span>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|<span data-ttu-id="db1bd-117">Dizelerin dizisini birleştirerek yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="db1bd-117">Builds a new string by combining an array of strings.</span></span>|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|<span data-ttu-id="db1bd-118">Varolan bir dizenin belirtilen dizinine bir dize ekleyerek yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="db1bd-118">Builds a new string by inserting a string into the specified index of an existing string.</span></span>|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|<span data-ttu-id="db1bd-119">Bir dizedeki belirtilen karakterleri, bir karakter dizisinde belirtilen konuma kopyalar.</span><span class="sxs-lookup"><span data-stu-id="db1bd-119">Copies specified characters in a string into a specified position in an array of characters.</span></span>|  
  
### <a name="format"></a><span data-ttu-id="db1bd-120">Biçimlendir</span><span class="sxs-lookup"><span data-stu-id="db1bd-120">Format</span></span>  
 <span data-ttu-id="db1bd-121">Biçimlendirilen dizeler oluşturmak ve birden çok nesneyi temsil eden dizeleri birleştirmek için **String. Format** yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db1bd-121">You can use the **String.Format** method to create formatted strings and concatenate strings representing multiple objects.</span></span> <span data-ttu-id="db1bd-122">Bu yöntem, geçirilen nesneleri otomatik olarak bir dizeye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="db1bd-122">This method automatically converts any passed object into a string.</span></span> <span data-ttu-id="db1bd-123">Örneğin, uygulamanızın kullanıcıya bir **Int32** değeri ve bir **Tarih saat** değeri görüntülemesi gerekiyorsa, **Biçim** yöntemini kullanarak bu değerleri temsil eden bir dizeyi kolayca oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db1bd-123">For example, if your application must display an **Int32** value and a **DateTime** value to the user, you can easily construct a string to represent these values using the **Format** method.</span></span> <span data-ttu-id="db1bd-124">Bu yöntemle kullanılan biçimlendirme kuralları hakkında daha fazla bilgi için, [Bileşik biçimlendirme](composite-formatting.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="db1bd-124">For information about formatting conventions used with this method, see the section on [composite formatting](composite-formatting.md).</span></span>  
  
 <span data-ttu-id="db1bd-125">Aşağıdaki örnek, bir tamsayı değişkeni kullanan bir dize oluşturmak için **Format** yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="db1bd-125">The following example uses the **Format** method to create a string that uses an integer variable.</span></span>  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 <span data-ttu-id="db1bd-126">Bu örnekte, geçerli <xref:System.DateTime.Now%2A?displayProperty=nameWithType> Tarih ve saati geçerli iş parçacığıyla ilişkili kültür tarafından belirtilen şekilde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="db1bd-126">In this example,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> displays the current date and time in a manner specified by the culture associated with the current thread.</span></span>  
  
### <a name="concat"></a><span data-ttu-id="db1bd-127">Concat</span><span class="sxs-lookup"><span data-stu-id="db1bd-127">Concat</span></span>  
 <span data-ttu-id="db1bd-128">**String. Concat** yöntemi, iki veya daha fazla var olan nesneden kolayca yeni bir dize nesnesi oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="db1bd-128">The **String.Concat** method can be used to easily create a new string object from two or more existing objects.</span></span> <span data-ttu-id="db1bd-129">Dizeleri birleştirmek için dile bağımsız bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="db1bd-129">It provides a language-independent way to concatenate strings.</span></span> <span data-ttu-id="db1bd-130">Bu yöntem, **System. Object**sınıfından türetilen tüm sınıfları kabul eder.</span><span class="sxs-lookup"><span data-stu-id="db1bd-130">This method accepts any class that derives from **System.Object**.</span></span> <span data-ttu-id="db1bd-131">Aşağıdaki örnek, iki var olan dize nesnesinden ve ayırma karakterinden oluşan bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="db1bd-131">The following example creates a string from two existing string objects and a separating character.</span></span>  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a><span data-ttu-id="db1bd-132">Birleştir</span><span class="sxs-lookup"><span data-stu-id="db1bd-132">Join</span></span>  
 <span data-ttu-id="db1bd-133">**String. JOIN** yöntemi bir dize dizisinden ve bir ayırıcı dizeden yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="db1bd-133">The **String.Join** method creates a new string from an array of strings and a separator string.</span></span> <span data-ttu-id="db1bd-134">Bu yöntem, birden fazla dizeyi birlikte birleştirmek istiyorsanız yararlı olur ve bir listeyi virgülle ayırarak bir liste yapar.</span><span class="sxs-lookup"><span data-stu-id="db1bd-134">This method is useful if you want to concatenate multiple strings together, making a list perhaps separated by a comma.</span></span>  
  
 <span data-ttu-id="db1bd-135">Aşağıdaki örnek bir dize dizisini bağlamak için bir boşluk kullanır.</span><span class="sxs-lookup"><span data-stu-id="db1bd-135">The following example uses a space to bind a string array.</span></span>  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a><span data-ttu-id="db1bd-136">Ekle</span><span class="sxs-lookup"><span data-stu-id="db1bd-136">Insert</span></span>  
 <span data-ttu-id="db1bd-137">**String. Insert** yöntemi, başka bir dizedeki belirtilen konuma bir dize ekleyerek yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="db1bd-137">The **String.Insert** method creates a new string by inserting a string into a specified position in another string.</span></span> <span data-ttu-id="db1bd-138">Bu yöntem sıfır tabanlı bir dizin kullanır.</span><span class="sxs-lookup"><span data-stu-id="db1bd-138">This method uses a zero-based index.</span></span> <span data-ttu-id="db1bd-139">Aşağıdaki örnek öğesinin beşinci dizin konumuna bir dize ekler `MyString` ve bu değere sahip yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="db1bd-139">The following example inserts a string into the fifth index position of `MyString` and creates a new string with this value.</span></span>  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a><span data-ttu-id="db1bd-140">CopyTo</span><span class="sxs-lookup"><span data-stu-id="db1bd-140">CopyTo</span></span>  
 <span data-ttu-id="db1bd-141">**String. CopyTo** yöntemi bir dizenin bölümlerini bir karakter dizisine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="db1bd-141">The **String.CopyTo** method copies portions of a string into an array of characters.</span></span> <span data-ttu-id="db1bd-142">Hem dizenin başlangıç dizinini hem de kopyalanacak karakter sayısını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db1bd-142">You can specify both the beginning index of the string and the number of characters to be copied.</span></span> <span data-ttu-id="db1bd-143">Bu yöntem, kaynak dizinini, bir karakter dizisini, hedef dizini ve kopyalanacak karakter sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="db1bd-143">This method takes the source index, an array of characters, the destination index, and the number of characters to copy.</span></span> <span data-ttu-id="db1bd-144">Tüm dizinler sıfır tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="db1bd-144">All indexes are zero-based.</span></span>  
  
 <span data-ttu-id="db1bd-145">Aşağıdaki örnek, "Hello" sözcüğünün karakterlerini dize nesnesinden bir karakter dizisinin ilk dizin konumuna kopyalamak için **CopyTo** yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="db1bd-145">The following example uses the **CopyTo** method to copy the characters of the word "Hello" from a string object to the first index position of an array of characters.</span></span>  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="db1bd-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db1bd-146">See also</span></span>

- [<span data-ttu-id="db1bd-147">Temel dize Işlemleri</span><span class="sxs-lookup"><span data-stu-id="db1bd-147">Basic String Operations</span></span>](basic-string-operations.md)
- [<span data-ttu-id="db1bd-148">Bileşik biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="db1bd-148">Composite Formatting</span></span>](composite-formatting.md)
