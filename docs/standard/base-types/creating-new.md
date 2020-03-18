---
title: .NET'te Yeni Dizeleri Oluşturma
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
ms.openlocfilehash: ef65c50111d6ba91ab70d0b9c8cb90c606f9366c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73103825"
---
# <a name="creating-new-strings-in-net"></a><span data-ttu-id="46073-102">.NET'te Yeni Dizeleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="46073-102">Creating New Strings in .NET</span></span>
<span data-ttu-id="46073-103">.NET Framework dizeleri basit atama kullanılarak oluşturulacak sağlar ve aynı zamanda farklı parametreler bir dizi kullanarak dize oluşturma desteklemek için bir sınıf oluşturucu aşırı yükler.</span><span class="sxs-lookup"><span data-stu-id="46073-103">The .NET Framework allows strings to be created using simple assignment, and also overloads a class constructor to support string creation using a number of different parameters.</span></span> <span data-ttu-id="46073-104">.NET Framework ayrıca, çeşitli <xref:System.String?displayProperty=nameWithType> dizeleri, dize dizileri veya nesneleri birleştirerek yeni dize nesneleri oluşturmak sınıfta çeşitli yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="46073-104">The .NET Framework also provides several methods in the <xref:System.String?displayProperty=nameWithType> class that create new string objects by combining several strings, arrays of strings, or objects.</span></span>  
  
## <a name="creating-strings-using-assignment"></a><span data-ttu-id="46073-105">Atamayı Kullanarak Dizeleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="46073-105">Creating Strings Using Assignment</span></span>  
 <span data-ttu-id="46073-106">Yeni <xref:System.String> bir nesne oluşturmanın en kolay yolu, bir <xref:System.String> nesneye bir dize harfi atamaktır.</span><span class="sxs-lookup"><span data-stu-id="46073-106">The easiest way to create a new <xref:System.String> object is simply to assign a string literal to a <xref:System.String> object.</span></span>  
  
## <a name="creating-strings-using-a-class-constructor"></a><span data-ttu-id="46073-107">Sınıf Oluşturucu sularını kullanarak dizeler oluşturma</span><span class="sxs-lookup"><span data-stu-id="46073-107">Creating Strings Using a Class Constructor</span></span>  
 <span data-ttu-id="46073-108">Karakter dizilerinden dizeleri <xref:System.String> oluşturmak için sınıf oluşturucu aşırı yüklerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46073-108">You can use overloads of the <xref:System.String> class constructor to create strings from character arrays.</span></span> <span data-ttu-id="46073-109">Ayrıca, belirli bir karakteri belirli bir sayıda çoğaltarak yeni bir dize oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46073-109">You can also create a new string by duplicating a particular character a specified number of times.</span></span>  
  
## <a name="methods-that-return-strings"></a><span data-ttu-id="46073-110">Dizeleri Döndüren Yöntemler</span><span class="sxs-lookup"><span data-stu-id="46073-110">Methods that Return Strings</span></span>  
 <span data-ttu-id="46073-111">Aşağıdaki tabloda yeni dize nesneleri döndüren birkaç yararlı yöntem listelenilmiştir.</span><span class="sxs-lookup"><span data-stu-id="46073-111">The following table lists several useful methods that return new string objects.</span></span>  
  
|<span data-ttu-id="46073-112">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="46073-112">Method name</span></span>|<span data-ttu-id="46073-113">Kullanım</span><span class="sxs-lookup"><span data-stu-id="46073-113">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<span data-ttu-id="46073-114">Giriş nesneleri kümesinden biçimlendirilmiş bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46073-114">Builds a formatted string from a set of input objects.</span></span>|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|<span data-ttu-id="46073-115">İki veya daha fazla dizeden dizeleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46073-115">Builds strings from two or more strings.</span></span>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|<span data-ttu-id="46073-116">Bir dizi dizeyi birleştirerek yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46073-116">Builds a new string by combining an array of strings.</span></span>|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|<span data-ttu-id="46073-117">Varolan bir dizenin belirtilen dizinine bir dize ekleyerek yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46073-117">Builds a new string by inserting a string into the specified index of an existing string.</span></span>|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|<span data-ttu-id="46073-118">Bir dizedeki belirtilen karakterleri bir dizi karakterde belirtilen konuma kopyalar.</span><span class="sxs-lookup"><span data-stu-id="46073-118">Copies specified characters in a string into a specified position in an array of characters.</span></span>|  
  
### <a name="format"></a><span data-ttu-id="46073-119">Biçimlendir</span><span class="sxs-lookup"><span data-stu-id="46073-119">Format</span></span>  
 <span data-ttu-id="46073-120">Biçimlendirilmiş dizeleri oluşturmak ve birden çok nesneyi temsil eden dizeleri birleştirmek için **String.Format** yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46073-120">You can use the **String.Format** method to create formatted strings and concatenate strings representing multiple objects.</span></span> <span data-ttu-id="46073-121">Bu yöntem, geçirilen herhangi bir nesneyi otomatik olarak bir dize dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="46073-121">This method automatically converts any passed object into a string.</span></span> <span data-ttu-id="46073-122">Örneğin, uygulamanızın kullanıcıya bir **Int32** değeri ve **DateTime** değeri görüntülemesi gerekiyorsa, **Biçim** yöntemini kullanarak bu değerleri temsil edecek bir dize kolayca oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46073-122">For example, if your application must display an **Int32** value and a **DateTime** value to the user, you can easily construct a string to represent these values using the **Format** method.</span></span> <span data-ttu-id="46073-123">Bu yöntemle kullanılan biçimlendirme kuralları hakkında bilgi için [bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="46073-123">For information about formatting conventions used with this method, see the section on [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>  
  
 <span data-ttu-id="46073-124">Aşağıdaki örnekte, tamsayı değişkeni kullanan bir dize oluşturmak için **Biçim** yöntemi ni kullanır.</span><span class="sxs-lookup"><span data-stu-id="46073-124">The following example uses the **Format** method to create a string that uses an integer variable.</span></span>  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 <span data-ttu-id="46073-125">Bu örnekte,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> geçerli tarih ve saati geçerli iş parçacığıyla ilişkili kültür tarafından belirtilen şekilde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="46073-125">In this example,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> displays the current date and time in a manner specified by the culture associated with the current thread.</span></span>  
  
### <a name="concat"></a><span data-ttu-id="46073-126">Concat</span><span class="sxs-lookup"><span data-stu-id="46073-126">Concat</span></span>  
 <span data-ttu-id="46073-127">**String.Concat** yöntemi, varolan iki veya daha fazla nesneden kolayca yeni bir dize nesnesi oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="46073-127">The **String.Concat** method can be used to easily create a new string object from two or more existing objects.</span></span> <span data-ttu-id="46073-128">Dizeleri biraraya getirmek için dilden bağımsız bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="46073-128">It provides a language-independent way to concatenate strings.</span></span> <span data-ttu-id="46073-129">Bu yöntem **System.Object**türetilen herhangi bir sınıf kabul eder.</span><span class="sxs-lookup"><span data-stu-id="46073-129">This method accepts any class that derives from **System.Object**.</span></span> <span data-ttu-id="46073-130">Aşağıdaki örnek, varolan iki dize nesnesinden bir dize ve ayıran bir karakter oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46073-130">The following example creates a string from two existing string objects and a separating character.</span></span>  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a><span data-ttu-id="46073-131">Birleştir</span><span class="sxs-lookup"><span data-stu-id="46073-131">Join</span></span>  
 <span data-ttu-id="46073-132">**String.Join** yöntemi, bir dizi dize ve ayırıcı dizeden yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46073-132">The **String.Join** method creates a new string from an array of strings and a separator string.</span></span> <span data-ttu-id="46073-133">Bu yöntem, birden çok dizeleri bir araya getirmek istiyorsanız, belki virgülle ayrılmış bir liste yapmak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="46073-133">This method is useful if you want to concatenate multiple strings together, making a list perhaps separated by a comma.</span></span>  
  
 <span data-ttu-id="46073-134">Aşağıdaki örnek, bir dize dizisini bağlamak için bir boşluk kullanır.</span><span class="sxs-lookup"><span data-stu-id="46073-134">The following example uses a space to bind a string array.</span></span>  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a><span data-ttu-id="46073-135">Ekle</span><span class="sxs-lookup"><span data-stu-id="46073-135">Insert</span></span>  
 <span data-ttu-id="46073-136">**String.Insert** yöntemi, başka bir dizede belirli bir konuma bir dize ekleyerek yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46073-136">The **String.Insert** method creates a new string by inserting a string into a specified position in another string.</span></span> <span data-ttu-id="46073-137">Bu yöntem, sıfır tabanlı dizin kullanır.</span><span class="sxs-lookup"><span data-stu-id="46073-137">This method uses a zero-based index.</span></span> <span data-ttu-id="46073-138">Aşağıdaki örnek, beşinci dizin konumuna bir `MyString` dize ekler ve bu değere sahip yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46073-138">The following example inserts a string into the fifth index position of `MyString` and creates a new string with this value.</span></span>  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a><span data-ttu-id="46073-139">CopyTo</span><span class="sxs-lookup"><span data-stu-id="46073-139">CopyTo</span></span>  
 <span data-ttu-id="46073-140">**String.CopyTo** yöntemi, bir dizebölümlerini bir karakter dizisine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="46073-140">The **String.CopyTo** method copies portions of a string into an array of characters.</span></span> <span data-ttu-id="46073-141">Hem dizenin başlangıç dizinini hem de kopyalanacak karakter sayısını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46073-141">You can specify both the beginning index of the string and the number of characters to be copied.</span></span> <span data-ttu-id="46073-142">Bu yöntem kaynak dizini, bir karakter dizisini, hedef dizini ve kopyalanması gereken karakter sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="46073-142">This method takes the source index, an array of characters, the destination index, and the number of characters to copy.</span></span> <span data-ttu-id="46073-143">Tüm dizinler sıfır tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="46073-143">All indexes are zero-based.</span></span>  
  
 <span data-ttu-id="46073-144">Aşağıdaki örnek, "Merhaba" sözcüğünün karakterlerini bir dize nesnesinden bir dizi karakterin ilk dizin konumuna kopyalamak için **CopyTo** yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="46073-144">The following example uses the **CopyTo** method to copy the characters of the word "Hello" from a string object to the first index position of an array of characters.</span></span>  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="46073-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46073-145">See also</span></span>

- [<span data-ttu-id="46073-146">Temel Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="46073-146">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
- [<span data-ttu-id="46073-147">Bileşik Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="46073-147">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
