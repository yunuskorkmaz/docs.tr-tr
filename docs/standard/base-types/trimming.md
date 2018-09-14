---
title: Karakterleri kırpma ve. NET'te dizelerden kaldırma
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d13d4e115caa636e5d760b65bc98e195490f911
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45508102"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a><span data-ttu-id="04672-102">Karakterleri kırpma ve. NET'te dizelerden kaldırma</span><span class="sxs-lookup"><span data-stu-id="04672-102">Trimming and Removing Characters from Strings in .NET</span></span>
<span data-ttu-id="04672-103">Kelimeler bir cümle ayrıştırma ise, word'ün her iki ucunda boşluk (boşluk olarak da bilinir) sahip sözcük çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="04672-103">If you are parsing a sentence into individual words, you might end up with words that have blank spaces (also called white spaces) on either end of the word.</span></span> <span data-ttu-id="04672-104">Bu durumda, kırpma metotlarından birini kullanabilirsiniz **System.String** dizedeki belirtilen herhangi bir sayıda boşluk veya diğer karakterler kaldırmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="04672-104">In this situation, you can use one of the trim methods in the **System.String** class to remove any number of spaces or other characters from a specified position in the string.</span></span> <span data-ttu-id="04672-105">Aşağıdaki tabloda kullanılabilir kesim yöntemleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="04672-105">The following table describes the available trim methods.</span></span>  
  
|<span data-ttu-id="04672-106">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="04672-106">Method name</span></span>|<span data-ttu-id="04672-107">Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında</span><span class="sxs-lookup"><span data-stu-id="04672-107">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|<span data-ttu-id="04672-108">Boşluk veya bir dizenin sonunda ve başındaki karakter dizisi içinde belirtilen karakterleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="04672-108">Removes white spaces or characters specified in an array of characters from the beginning and end of a string.</span></span>|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|<span data-ttu-id="04672-109">Bir dizenin sonuna karakterler dizisi belirtilen karakterleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="04672-109">Removes characters specified in an array of characters from the end of a string.</span></span>|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|<span data-ttu-id="04672-110">Bir dize başından itibaren karakter belirtilen karakterleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="04672-110">Removes characters specified in an array of characters from the beginning of a string.</span></span>|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="04672-111">Bir dizedeki bir belirtilen dizine belirtilen sayıda karakteri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="04672-111">Removes a specified number of characters from a specified index position in a string.</span></span>|  
  
## <a name="trim"></a><span data-ttu-id="04672-112">Kırpma</span><span class="sxs-lookup"><span data-stu-id="04672-112">Trim</span></span>  
 <span data-ttu-id="04672-113">Kullanarak boşluk her iki ucunda da bir dize kolayca kaldırabilirsiniz <xref:System.String.Trim%2A?displayProperty=nameWithType> yöntemi, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="04672-113">You can easily remove white spaces from both ends of a string by using the <xref:System.String.Trim%2A?displayProperty=nameWithType> method, as shown in the following example.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 <span data-ttu-id="04672-114">Ayrıca, bir karakter dizisinden bir dizenin sonunda ve başındaki belirttiğiniz karakter kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04672-114">You can also remove characters that you specify in a character array from the beginning and end of a string.</span></span> <span data-ttu-id="04672-115">Aşağıdaki örnek, boşluk karakteri, nokta ve yıldız kaldırır.</span><span class="sxs-lookup"><span data-stu-id="04672-115">The following example removes white-space characters, periods, and asterisks.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a><span data-ttu-id="04672-116">TrimEnd</span><span class="sxs-lookup"><span data-stu-id="04672-116">TrimEnd</span></span>  
 <span data-ttu-id="04672-117">**String.TrimEnd** yöntemi yeni bir dize nesnesi oluşturma, bir dizenin sonundan karakterleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="04672-117">The **String.TrimEnd** method removes characters from the end of a string, creating a new string object.</span></span> <span data-ttu-id="04672-118">Bir karakter dizisini kaldırılacak karakter belirtmek için bu yönteme geçirilir.</span><span class="sxs-lookup"><span data-stu-id="04672-118">An array of characters is passed to this method to specify the characters to be removed.</span></span> <span data-ttu-id="04672-119">Karakter dizisinde öğelerin sırasını kesme işlemi etkilemez.</span><span class="sxs-lookup"><span data-stu-id="04672-119">The order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="04672-120">Trim dizide belirtilmemiş bir karakter bulunduğunda durur.</span><span class="sxs-lookup"><span data-stu-id="04672-120">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="04672-121">Aşağıdaki örnek, bir dize kullanarak, son harf kaldırır **TrimEnd** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="04672-121">The following example removes the last letters of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="04672-122">Bu örnekte, konumunu `'r'` karakter ve `'W'` karakteri ters dizideki karakterlerin sırası önemli değildir göstermek için.</span><span class="sxs-lookup"><span data-stu-id="04672-122">In this example, the position of the `'r'` character and the `'W'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span> <span data-ttu-id="04672-123">Bu kod, son sözcüğü kaldırır fark `MyString` artı ilk parçası.</span><span class="sxs-lookup"><span data-stu-id="04672-123">Notice that this code removes the last word of `MyString` plus part of the first.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 <span data-ttu-id="04672-124">Bu kod görüntüler `He` konsola.</span><span class="sxs-lookup"><span data-stu-id="04672-124">This code displays `He` to the console.</span></span>  
  
 <span data-ttu-id="04672-125">Aşağıdaki örneği kullanarak bir dize olan son sözcüğü kaldırır **TrimEnd** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="04672-125">The following example removes the last word of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="04672-126">Bu kodda virgül sözcüğünü izleyen `Hello` ve virgül içerecek şekilde kırpmanıza karakter dizisinde belirtilmediğinden, kırpma virgülle biter.</span><span class="sxs-lookup"><span data-stu-id="04672-126">In this code, a comma follows the word `Hello` and, because the comma is not specified in the array of characters to trim, the trim ends at the comma.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 <span data-ttu-id="04672-127">Bu kod görüntüler `Hello,` konsola.</span><span class="sxs-lookup"><span data-stu-id="04672-127">This code displays `Hello,` to the console.</span></span>  
  
## <a name="trimstart"></a><span data-ttu-id="04672-128">TrimStart</span><span class="sxs-lookup"><span data-stu-id="04672-128">TrimStart</span></span>  
 <span data-ttu-id="04672-129">**String.TrimStart** yöntemi benzer **String.TrimEnd** yöntemi dışında olan mevcut bir dize nesnesi başından itibaren karakter kaldırarak yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="04672-129">The **String.TrimStart** method is similar to the **String.TrimEnd** method except that it creates a new string by removing characters from the beginning of an existing string object.</span></span> <span data-ttu-id="04672-130">Karakter dizisi geçirilir **TrimStart** kaldırılacak karakter belirtmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="04672-130">An array of characters is passed to the **TrimStart** method to specify the characters to be removed.</span></span> <span data-ttu-id="04672-131">Olduğu gibi **TrimEnd** yöntemi, karakter dizideki öğelerin sırasını kesme işlemi etkilemez.</span><span class="sxs-lookup"><span data-stu-id="04672-131">As with the **TrimEnd** method, the order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="04672-132">Trim dizide belirtilmemiş bir karakter bulunduğunda durur.</span><span class="sxs-lookup"><span data-stu-id="04672-132">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="04672-133">Aşağıdaki örnek bir dizenin ilk sözcük kaldırır.</span><span class="sxs-lookup"><span data-stu-id="04672-133">The following example removes the first word of a string.</span></span> <span data-ttu-id="04672-134">Bu örnekte, konumunu `'l'` karakter ve `'H'` karakteri ters dizideki karakterlerin sırası önemli değildir göstermek için.</span><span class="sxs-lookup"><span data-stu-id="04672-134">In this example, the position of the `'l'` character and the `'H'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 <span data-ttu-id="04672-135">Bu kod görüntüler `World!` konsola.</span><span class="sxs-lookup"><span data-stu-id="04672-135">This code displays `World!` to the console.</span></span>  
  
## <a name="remove"></a><span data-ttu-id="04672-136">Kaldır</span><span class="sxs-lookup"><span data-stu-id="04672-136">Remove</span></span>  
 <span data-ttu-id="04672-137"><xref:System.String.Remove%2A?displayProperty=nameWithType> Yöntemi, belirtilen sayıda varolan bir dizeyi, belirtilen konumda başlayan karakteri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="04672-137">The <xref:System.String.Remove%2A?displayProperty=nameWithType> method removes a specified number of characters that begin at a specified position in an existing string.</span></span> <span data-ttu-id="04672-138">Bu yöntem, sıfır tabanlı dizin varsayar.</span><span class="sxs-lookup"><span data-stu-id="04672-138">This method assumes a zero-based index.</span></span>  
  
 <span data-ttu-id="04672-139">Aşağıdaki örnek, dizenin bir sıfır tabanlı dizini beş konumunda başlayan bir dizedeki on karakterlerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="04672-139">The following example removes ten characters from a string beginning at position five of a zero-based index of the string.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
 <span data-ttu-id="04672-140">Ayrıca belirtilen karakter veya alt dizenin bir dizeden çağırarak kaldırabilirsiniz <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> yöntemi ve boş bir dize belirtme (<xref:System.String.Empty?displayProperty=nameWithType>) yerine.</span><span class="sxs-lookup"><span data-stu-id="04672-140">You can also remove a specified character or substring from a string by calling the <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> method and specifying an empty string (<xref:System.String.Empty?displayProperty=nameWithType>) as the replacement.</span></span> <span data-ttu-id="04672-141">Aşağıdaki örnek, bir dizedeki tüm virgül kaldırır.</span><span class="sxs-lookup"><span data-stu-id="04672-141">The following example removes all commas from a string.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="04672-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04672-142">See also</span></span>

- [<span data-ttu-id="04672-143">Temel Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="04672-143">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
