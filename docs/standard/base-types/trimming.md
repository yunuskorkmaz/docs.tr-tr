---
title: "Karakterleri kırpma ve .NET dizelerden kaldırma"
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
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: dac047c7efefcacb959401aedcb96080810f2278
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a><span data-ttu-id="61750-102">Karakterleri kırpma ve .NET dizelerden kaldırma</span><span class="sxs-lookup"><span data-stu-id="61750-102">Trimming and Removing Characters from Strings in .NET</span></span>
<span data-ttu-id="61750-103">Tek tek sözcüklere bir cümle ayrıştırma varsa, ya da sözcüğün sonuna boşluk (boşluk olarak da bilinir) sahip sözcükler şunun.</span><span class="sxs-lookup"><span data-stu-id="61750-103">If you are parsing a sentence into individual words, you might end up with words that have blank spaces (also called white spaces) on either end of the word.</span></span> <span data-ttu-id="61750-104">Bu durumda, kırpma yöntemlerden birini kullanabilirsiniz **System.String** dizedeki belirtilen alanları veya diğer karakterler herhangi bir sayıda kaldırmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="61750-104">In this situation, you can use one of the trim methods in the **System.String** class to remove any number of spaces or other characters from a specified position in the string.</span></span> <span data-ttu-id="61750-105">Aşağıdaki tabloda kullanılabilir kırpma yöntemleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="61750-105">The following table describes the available trim methods.</span></span>  
  
|<span data-ttu-id="61750-106">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="61750-106">Method name</span></span>|<span data-ttu-id="61750-107">Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında</span><span class="sxs-lookup"><span data-stu-id="61750-107">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|<span data-ttu-id="61750-108">Boşluk veya başlangıcını ve bitişini dizenin karakter dizisi belirtilen karakterleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="61750-108">Removes white spaces or characters specified in an array of characters from the beginning and end of a string.</span></span>|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|<span data-ttu-id="61750-109">Bir dize sonu karakter dizisi belirtilen karakterleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="61750-109">Removes characters specified in an array of characters from the end of a string.</span></span>|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|<span data-ttu-id="61750-110">Bir dizenin başından karakter belirtilen karakterleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="61750-110">Removes characters specified in an array of characters from the beginning of a string.</span></span>|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="61750-111">Belirtilen dizin konumu bir dizedeki belirtilen sayıda karakteri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="61750-111">Removes a specified number of characters from a specified index position in a string.</span></span>|  
  
## <a name="trim"></a><span data-ttu-id="61750-112">Kırpma</span><span class="sxs-lookup"><span data-stu-id="61750-112">Trim</span></span>  
 <span data-ttu-id="61750-113">Kullanarak boşluk her iki ucunu bir dize kolayca kaldırabilirsiniz <xref:System.String.Trim%2A?displayProperty=nameWithType> aşağıdaki örnekte gösterildiği gibi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="61750-113">You can easily remove white spaces from both ends of a string by using the <xref:System.String.Trim%2A?displayProperty=nameWithType> method, as shown in the following example.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 <span data-ttu-id="61750-114">Başlangıç ve bitiş dizenin karakter dizisinden belirttiğiniz karakter da kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61750-114">You can also remove characters that you specify in a character array from the beginning and end of a string.</span></span> <span data-ttu-id="61750-115">Aşağıdaki örnek, boşluk karakterleri, nokta ve yıldız kaldırır.</span><span class="sxs-lookup"><span data-stu-id="61750-115">The following example removes white-space characters, periods, and asterisks.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a><span data-ttu-id="61750-116">TrimEnd</span><span class="sxs-lookup"><span data-stu-id="61750-116">TrimEnd</span></span>  
 <span data-ttu-id="61750-117">**String.TrimEnd** yöntemi, yeni bir dize nesnesi oluşturma bir dize sonundan karakterleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="61750-117">The **String.TrimEnd** method removes characters from the end of a string, creating a new string object.</span></span> <span data-ttu-id="61750-118">Karakter kaldırılacak karakter belirtmek için bu yöntem geçirilir.</span><span class="sxs-lookup"><span data-stu-id="61750-118">An array of characters is passed to this method to specify the characters to be removed.</span></span> <span data-ttu-id="61750-119">Karakter dizisindeki öğelerin sırasını kırpma işlemi etkilemez.</span><span class="sxs-lookup"><span data-stu-id="61750-119">The order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="61750-120">Dizideki belirtilmemiş bir karakter bulunduğunda kırpma durdurur.</span><span class="sxs-lookup"><span data-stu-id="61750-120">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="61750-121">Aşağıdaki örnek dizesini kullanarak, son harf kaldırır **TrimEnd** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="61750-121">The following example removes the last letters of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="61750-122">Bu örnekte, konumunu `'r'` karakter ve `'W'` karakter tersine dizi karakter sırası önemli değildir olduğunu göstermek için.</span><span class="sxs-lookup"><span data-stu-id="61750-122">In this example, the position of the `'r'` character and the `'W'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span> <span data-ttu-id="61750-123">Bu kodu son sözcüğün kaldırır fark `MyString` ilk parçası artı.</span><span class="sxs-lookup"><span data-stu-id="61750-123">Notice that this code removes the last word of `MyString` plus part of the first.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 <span data-ttu-id="61750-124">Bu kod görüntüler `He` Konsolu'na.</span><span class="sxs-lookup"><span data-stu-id="61750-124">This code displays `He` to the console.</span></span>  
  
 <span data-ttu-id="61750-125">Aşağıdaki örnek, bir dizesini kullanarak son word kaldırır **TrimEnd** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="61750-125">The following example removes the last word of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="61750-126">Bu kodda virgül word izleyen `Hello` ve virgül kırpma karakterleri dizisinde belirtilmediğinden kırpma virgülle biter.</span><span class="sxs-lookup"><span data-stu-id="61750-126">In this code, a comma follows the word `Hello` and, because the comma is not specified in the array of characters to trim, the trim ends at the comma.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 <span data-ttu-id="61750-127">Bu kod görüntüler `Hello,` Konsolu'na.</span><span class="sxs-lookup"><span data-stu-id="61750-127">This code displays `Hello,` to the console.</span></span>  
  
## <a name="trimstart"></a><span data-ttu-id="61750-128">TrimStart</span><span class="sxs-lookup"><span data-stu-id="61750-128">TrimStart</span></span>  
 <span data-ttu-id="61750-129">**String.TrimStart** yöntemi benzer **String.TrimEnd** yöntemi olan dışında var olan bir dize nesnesi baştan karakter kaldırarak yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="61750-129">The **String.TrimStart** method is similar to the **String.TrimEnd** method except that it creates a new string by removing characters from the beginning of an existing string object.</span></span> <span data-ttu-id="61750-130">Karakter geçirilir **TrimStart** yöntemi kaldırılacak karakter belirtin.</span><span class="sxs-lookup"><span data-stu-id="61750-130">An array of characters is passed to the **TrimStart** method to specify the characters to be removed.</span></span> <span data-ttu-id="61750-131">İle **TrimEnd** yöntemi, karakter dizisindeki öğelerin sırasını kırpma işlemi etkilemez.</span><span class="sxs-lookup"><span data-stu-id="61750-131">As with the **TrimEnd** method, the order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="61750-132">Dizideki belirtilmemiş bir karakter bulunduğunda kırpma durdurur.</span><span class="sxs-lookup"><span data-stu-id="61750-132">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="61750-133">Aşağıdaki örnek, bir dize ilk sözcüğün kaldırır.</span><span class="sxs-lookup"><span data-stu-id="61750-133">The following example removes the first word of a string.</span></span> <span data-ttu-id="61750-134">Bu örnekte, konumunu `'l'` karakter ve `'H'` karakter tersine dizi karakter sırası önemli değildir olduğunu göstermek için.</span><span class="sxs-lookup"><span data-stu-id="61750-134">In this example, the position of the `'l'` character and the `'H'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 <span data-ttu-id="61750-135">Bu kod görüntüler `World!` Konsolu'na.</span><span class="sxs-lookup"><span data-stu-id="61750-135">This code displays `World!` to the console.</span></span>  
  
## <a name="remove"></a><span data-ttu-id="61750-136">Kaldır</span><span class="sxs-lookup"><span data-stu-id="61750-136">Remove</span></span>  
 <span data-ttu-id="61750-137"><xref:System.String.Remove%2A?displayProperty=nameWithType> Yöntemi, belirtilen sayıda varolan bir dizeyi belirtilen konumda başlamak karakteri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="61750-137">The <xref:System.String.Remove%2A?displayProperty=nameWithType> method removes a specified number of characters that begin at a specified position in an existing string.</span></span> <span data-ttu-id="61750-138">Bu yöntem, sıfır tabanlı dizin varsayar.</span><span class="sxs-lookup"><span data-stu-id="61750-138">This method assumes a zero-based index.</span></span>  
  
 <span data-ttu-id="61750-139">Aşağıdaki örnek dizenin sıfır tabanlı dizini beş konumunu dize başında on karakterleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="61750-139">The following example removes ten characters from a string beginning at position five of a zero-based index of the string.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
 <span data-ttu-id="61750-140">Ayrıca belirtilen karakter veya alt dize bir dizeden çağırarak kaldırabilirsiniz <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> yöntemi ve boş bir dize belirtme (<xref:System.String.Empty?displayProperty=nameWithType>) olarak değiştirme.</span><span class="sxs-lookup"><span data-stu-id="61750-140">You can also remove a specified character or substring from a string by calling the <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> method and specifying an empty string (<xref:System.String.Empty?displayProperty=nameWithType>) as the replacement.</span></span> <span data-ttu-id="61750-141">Aşağıdaki örnek, bir dizeden tüm virgül kaldırır.</span><span class="sxs-lookup"><span data-stu-id="61750-141">The following example removes all commas from a string.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="61750-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="61750-142">See Also</span></span>  
 [<span data-ttu-id="61750-143">Temel Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="61750-143">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
