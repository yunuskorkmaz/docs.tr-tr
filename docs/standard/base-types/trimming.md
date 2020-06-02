---
title: .NET 'teki Dizelerdeki karakterleri kırpma ve kaldırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET Framework], removing characters
- Remove method
- TrimEnd method
- Trim method
- trimming characters
- TrimStart method
- removing characters
ms.assetid: ab248dab-70d4-4413-81c6-542d153fd195
ms.openlocfilehash: 0777ba7348d13697fd53f556ac69cba3f98d1e4d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290882"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a><span data-ttu-id="ac896-102">.NET 'teki Dizelerdeki karakterleri kırpma ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="ac896-102">Trimming and Removing Characters from Strings in .NET</span></span>
<span data-ttu-id="ac896-103">Bir tümceyi tek tek sözcüklere ayrıştırdıysanız, sözcüğün her iki ucunda da boşluk olan (boşluk da denir) sözcüklerden oluşan sözcüklerle karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac896-103">If you are parsing a sentence into individual words, you might end up with words that have blank spaces (also called white spaces) on either end of the word.</span></span> <span data-ttu-id="ac896-104">Bu durumda, dizedeki belirli bir konumdan herhangi bir sayıda boşluğu veya diğer karakteri kaldırmak için **System. String** sınıfındaki trim yöntemlerinden birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac896-104">In this situation, you can use one of the trim methods in the **System.String** class to remove any number of spaces or other characters from a specified position in the string.</span></span> <span data-ttu-id="ac896-105">Aşağıdaki tabloda kullanılabilir kırpma yöntemleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ac896-105">The following table describes the available trim methods.</span></span>  
  
|<span data-ttu-id="ac896-106">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="ac896-106">Method name</span></span>|<span data-ttu-id="ac896-107">Kullanım</span><span class="sxs-lookup"><span data-stu-id="ac896-107">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|<span data-ttu-id="ac896-108">Bir dizenin başındaki ve sonundaki karakter dizisinde belirtilen boşluk veya karakterleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ac896-108">Removes white spaces or characters specified in an array of characters from the beginning and end of a string.</span></span>|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|<span data-ttu-id="ac896-109">Bir dizenin sonundaki karakter dizisinde belirtilen karakterleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ac896-109">Removes characters specified in an array of characters from the end of a string.</span></span>|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|<span data-ttu-id="ac896-110">Bir karakter dizisinde belirtilen karakterleri dizenin başından kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ac896-110">Removes characters specified in an array of characters from the beginning of a string.</span></span>|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="ac896-111">Bir dizedeki belirtilen dizin konumundan belirtilen sayıda karakteri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ac896-111">Removes a specified number of characters from a specified index position in a string.</span></span>|  
  
## <a name="trim"></a><span data-ttu-id="ac896-112">Trim</span><span class="sxs-lookup"><span data-stu-id="ac896-112">Trim</span></span>

 <span data-ttu-id="ac896-113"><xref:System.String.Trim%2A?displayProperty=nameWithType>Aşağıdaki örnekte gösterildiği gibi, yöntemini kullanarak, bir dizenin her iki ucunda da kolayca beyaz boşluk çıkarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac896-113">You can easily remove white spaces from both ends of a string by using the <xref:System.String.Trim%2A?displayProperty=nameWithType> method, as shown in the following example.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 <span data-ttu-id="ac896-114">Bir dizenin başındaki ve sonundaki bir karakter dizisinde belirttiğiniz karakterleri de kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac896-114">You can also remove characters that you specify in a character array from the beginning and end of a string.</span></span> <span data-ttu-id="ac896-115">Aşağıdaki örnek boşluk karakterlerini, dönemleri ve yıldız işaretlerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ac896-115">The following example removes white-space characters, periods, and asterisks.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a><span data-ttu-id="ac896-116">TrimEnd</span><span class="sxs-lookup"><span data-stu-id="ac896-116">TrimEnd</span></span>

 <span data-ttu-id="ac896-117">**String. TrimEnd** yöntemi bir dizenin sonundaki karakterleri kaldırır ve yeni bir dize nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ac896-117">The **String.TrimEnd** method removes characters from the end of a string, creating a new string object.</span></span> <span data-ttu-id="ac896-118">Kaldırılacak karakterleri belirtmek için bu yönteme bir karakter dizisi geçirilir.</span><span class="sxs-lookup"><span data-stu-id="ac896-118">An array of characters is passed to this method to specify the characters to be removed.</span></span> <span data-ttu-id="ac896-119">Karakter dizisindeki öğelerin sırası, kırpma işlemini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="ac896-119">The order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="ac896-120">Dizide belirtilen bir karakter bulunduğunda kırpma durdu.</span><span class="sxs-lookup"><span data-stu-id="ac896-120">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="ac896-121">Aşağıdaki örnek, **TrimEnd** yöntemini kullanarak bir dizenin son harflerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ac896-121">The following example removes the last letters of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="ac896-122">Bu örnekte, `'r'` `'W'` dizideki karakterlerin sırasının ne olduğunu göstermek için karakterin ve karakterin konumu tersine çevrilir.</span><span class="sxs-lookup"><span data-stu-id="ac896-122">In this example, the position of the `'r'` character and the `'W'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span> <span data-ttu-id="ac896-123">Bu kodun en son sözcüğünü ve ilk bir kısmını kaldırdığına dikkat edin `MyString` .</span><span class="sxs-lookup"><span data-stu-id="ac896-123">Notice that this code removes the last word of `MyString` plus part of the first.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 <span data-ttu-id="ac896-124">Bu kod `He` konsola görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ac896-124">This code displays `He` to the console.</span></span>  
  
 <span data-ttu-id="ac896-125">Aşağıdaki örnek, **TrimEnd** yöntemini kullanarak bir dizenin son sözcüğünü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ac896-125">The following example removes the last word of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="ac896-126">Bu kodda, virgülden sonra bir virgül `Hello` ve kırpılacak karakter dizisinde kırpılacak şekilde, kırpma, virgülden sona erer.</span><span class="sxs-lookup"><span data-stu-id="ac896-126">In this code, a comma follows the word `Hello` and, because the comma is not specified in the array of characters to trim, the trim ends at the comma.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 <span data-ttu-id="ac896-127">Bu kod `Hello,` konsola görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ac896-127">This code displays `Hello,` to the console.</span></span>  
  
## <a name="trimstart"></a><span data-ttu-id="ac896-128">TrimStart</span><span class="sxs-lookup"><span data-stu-id="ac896-128">TrimStart</span></span>

 <span data-ttu-id="ac896-129">**String. Kırosstart** yöntemi **String. TrimEnd** yöntemine benzer, ancak karakterleri varolan bir dize nesnesinin başından kaldırarak yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ac896-129">The **String.TrimStart** method is similar to the **String.TrimEnd** method except that it creates a new string by removing characters from the beginning of an existing string object.</span></span> <span data-ttu-id="ac896-130">Kaldırılacak karakterleri belirtmek için, bir karakter dizisi **kırılımı başlangıç** yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="ac896-130">An array of characters is passed to the **TrimStart** method to specify the characters to be removed.</span></span> <span data-ttu-id="ac896-131">**TrimEnd** yönteminde olduğu gibi, karakter dizisindeki öğelerin sırası trim işlemini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="ac896-131">As with the **TrimEnd** method, the order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="ac896-132">Dizide belirtilen bir karakter bulunduğunda kırpma durdu.</span><span class="sxs-lookup"><span data-stu-id="ac896-132">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="ac896-133">Aşağıdaki örnek bir dizenin ilk sözcüğünü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ac896-133">The following example removes the first word of a string.</span></span> <span data-ttu-id="ac896-134">Bu örnekte, `'l'` `'H'` dizideki karakterlerin sırasının ne olduğunu göstermek için karakterin ve karakterin konumu tersine çevrilir.</span><span class="sxs-lookup"><span data-stu-id="ac896-134">In this example, the position of the `'l'` character and the `'H'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 <span data-ttu-id="ac896-135">Bu kod `World!` konsola görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ac896-135">This code displays `World!` to the console.</span></span>  
  
## <a name="remove"></a><span data-ttu-id="ac896-136">Kaldır</span><span class="sxs-lookup"><span data-stu-id="ac896-136">Remove</span></span>

 <span data-ttu-id="ac896-137"><xref:System.String.Remove%2A?displayProperty=nameWithType>Yöntemi, varolan bir dizedeki belirli bir konumda başlayan belirtilen sayıda karakteri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ac896-137">The <xref:System.String.Remove%2A?displayProperty=nameWithType> method removes a specified number of characters that begin at a specified position in an existing string.</span></span> <span data-ttu-id="ac896-138">Bu yöntem sıfır tabanlı bir dizini varsayar.</span><span class="sxs-lookup"><span data-stu-id="ac896-138">This method assumes a zero-based index.</span></span>  
  
 <span data-ttu-id="ac896-139">Aşağıdaki örnek, dizenin sıfır tabanlı dizininin beş konumunda başlayan bir dizeden on karakteri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ac896-139">The following example removes ten characters from a string beginning at position five of a zero-based index of the string.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
## <a name="replace"></a><span data-ttu-id="ac896-140">Değiştir</span><span class="sxs-lookup"><span data-stu-id="ac896-140">Replace</span></span>

 <span data-ttu-id="ac896-141">Ayrıca, <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> yöntemi çağırarak ve değiştirme olarak boş bir dize () belirterek, bir dizeden belirtilen bir karakteri veya alt dizeyi kaldırabilirsiniz <xref:System.String.Empty?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ac896-141">You can also remove a specified character or substring from a string by calling the <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> method and specifying an empty string (<xref:System.String.Empty?displayProperty=nameWithType>) as the replacement.</span></span> <span data-ttu-id="ac896-142">Aşağıdaki örnek bir dizeden tüm virgülleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ac896-142">The following example removes all commas from a string.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="ac896-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac896-143">See also</span></span>

- [<span data-ttu-id="ac896-144">Temel dize Işlemleri</span><span class="sxs-lookup"><span data-stu-id="ac896-144">Basic String Operations</span></span>](basic-string-operations.md)
