---
title: LINQ ve dizeler (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75ddb201-d97a-4f98-8cdf-4ad51714529a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b615f3dc76d72e7f73146498e0143f88c52278a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="linq-and-strings-visual-basic"></a><span data-ttu-id="1d58b-102">LINQ ve dizeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d58b-102">LINQ and Strings (Visual Basic)</span></span>
<span data-ttu-id="1d58b-103">LINQ Sorgu ve dizeler ve koleksiyonları dizeleri dönüştürmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1d58b-103">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="1d58b-104">Metin dosyaları yarı yapılandırılmış veriyle özellikle yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1d58b-104">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="1d58b-105">LINQ sorgularını geleneksel dize işlevleri ve normal ifadeler ile birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1d58b-105">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="1d58b-106">Örneğin, kullanabileceğiniz <xref:System.String.Split%2A> veya <xref:System.Text.RegularExpressions.Regex.Split%2A> sonra sorgu veya LINQ kullanarak değiştirmek için bir dizeler dizisi oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1d58b-106">For example, you can use the <xref:System.String.Split%2A> or <xref:System.Text.RegularExpressions.Regex.Split%2A> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="1d58b-107">Kullanabileceğiniz <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> yönteminde `where` bir LINQ sorgu yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="1d58b-107">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="1d58b-108">LINQ Sorgu veya değiştirmek için kullanabileceğiniz <xref:System.Text.RegularExpressions.MatchCollection> normal bir ifade tarafından döndürülen sonuç.</span><span class="sxs-lookup"><span data-stu-id="1d58b-108">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>  
  
 <span data-ttu-id="1d58b-109">Bu bölümde açıklanan teknikleri, yarı yapılandırılmış metin verilerini XML'e dönüştürmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d58b-109">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="1d58b-110">Daha fazla bilgi için bkz: [nasıl yapılır: XML oluşturmak CSV dosyalarından](how-to-generate-xml-from-csv-files.md).</span><span class="sxs-lookup"><span data-stu-id="1d58b-110">For more information, see [How to: Generate XML from CSV Files](how-to-generate-xml-from-csv-files.md).</span></span>  
  
 <span data-ttu-id="1d58b-111">Bu bölümdeki örnekleri iki kategoriye ayrılır:</span><span class="sxs-lookup"><span data-stu-id="1d58b-111">The examples in this section fall into two categories:</span></span>  
  
## <a name="querying-a-block-of-text"></a><span data-ttu-id="1d58b-112">Bir metin bloğunu sorgulama</span><span class="sxs-lookup"><span data-stu-id="1d58b-112">Querying a Block of Text</span></span>  
 <span data-ttu-id="1d58b-113">Sorgu, çözümlemek ve daha küçük dizeleri sorgulanabilir bir diziye bölerek kullanarak metin blokları değiştirme <xref:System.String.Split%2A> yöntemi veya <xref:System.Text.RegularExpressions.Regex.Split%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1d58b-113">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A> method.</span></span> <span data-ttu-id="1d58b-114">Kaynak metni sözcükler, cümle, paragraf, sayfalar veya başka bir ölçüt bölme ve sorgunuzda gerekirse ek bölmelerini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="1d58b-114">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>  
  
 [<span data-ttu-id="1d58b-115">Nasıl yapılır: bir sözcüğün bir dizede (LINQ) (Visual Basic) yinelemeleri Say</span><span class="sxs-lookup"><span data-stu-id="1d58b-115">How to: Count Occurrences of a Word in a String (LINQ) (Visual Basic)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 <span data-ttu-id="1d58b-116">Basit metin sorgulamaya LINQ kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d58b-116">Shows how to use LINQ for simple querying over text.</span></span>  
  
 [<span data-ttu-id="1d58b-117">Nasıl yapılır: sözcükleri (LINQ) (Visual Basic) belirtilen bir kümesini içeren cümleleri sorgulama</span><span class="sxs-lookup"><span data-stu-id="1d58b-117">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 <span data-ttu-id="1d58b-118">Metin dosyaları rasgele sınırlarındaki ayırma ve her bölümü sorguları gerçekleştirmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d58b-118">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>  
  
 [<span data-ttu-id="1d58b-119">Nasıl yapılır: sorgu (LINQ) (Visual Basic) bir dizedeki karakter için</span><span class="sxs-lookup"><span data-stu-id="1d58b-119">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>](how-to-query-for-characters-in-a-string-linq.md)  
 <span data-ttu-id="1d58b-120">Bir dize sorgulanabilir türü olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d58b-120">Demonstrates that a string is a queryable type.</span></span>  
  
 [<span data-ttu-id="1d58b-121">Nasıl yapılır: (Visual Basic) Normal ifadelerle LINQ sorgularını birleştirme</span><span class="sxs-lookup"><span data-stu-id="1d58b-121">How to: Combine LINQ Queries with Regular Expressions (Visual Basic)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)  
 <span data-ttu-id="1d58b-122">Normal ifadeler LINQ sorgularında karmaşık desen filtrelenmiş sorgu sonuçlarına eşleştirme için kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d58b-122">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>  
  
## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="1d58b-123">Metin biçimindeki yarı yapılandırılmış veri sorgulama</span><span class="sxs-lookup"><span data-stu-id="1d58b-123">Querying Semi-Structured Data in Text Format</span></span>  
 <span data-ttu-id="1d58b-124">Sekme veya virgülle ayrılmış dosyalar veya sabit uzunluklu satırları gibi benzer biçimlendirmeye sahip genellikle satırları, bir dizi farklı türlerde metin dosyaları oluşur.</span><span class="sxs-lookup"><span data-stu-id="1d58b-124">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="1d58b-125">Belleğe gibi bir metin dosyası okuma sonra LINQ Sorgu ve/veya satırları değiştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d58b-125">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="1d58b-126">LINQ sorguları da birden fazla kaynaktan veri birleştirme görevini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="1d58b-126">LINQ queries also simplify the task of combining data from multiple sources.</span></span>  
  
 [<span data-ttu-id="1d58b-127">Nasıl yapılır: iki liste (LINQ) (Visual Basic) arasında ayarlanmış farkı bulma</span><span class="sxs-lookup"><span data-stu-id="1d58b-127">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)  
 <span data-ttu-id="1d58b-128">Bir liste ancak diğer var olan tüm dizeleri bulmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1d58b-128">Shows how to find all the strings that are present in one list but not the other.</span></span>  
  
 [<span data-ttu-id="1d58b-129">Nasıl yapılır: sıralama veya filtre metni verilerle herhangi bir sözcük veya alana (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d58b-129">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 <span data-ttu-id="1d58b-130">Metin satırlarını herhangi bir sözcük veya alana göre sıralamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1d58b-130">Shows how to sort text lines based on any word or field.</span></span>  
  
 [<span data-ttu-id="1d58b-131">Nasıl yapılır: sınırlandırılmış bir dosyanın (LINQ) (Visual Basic) alanlarını yeniden sıralama</span><span class="sxs-lookup"><span data-stu-id="1d58b-131">How to: Reorder the Fields of a Delimited File (LINQ) (Visual Basic)</span></span>](how-to-reorder-the-fields-of-a-delimited-file.md)  
 <span data-ttu-id="1d58b-132">Bir .csv dosyası bir satırda alanları yeniden sıralamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1d58b-132">Shows how to reorder fields in a line in a .csv file.</span></span>  
  
 [<span data-ttu-id="1d58b-133">Nasıl yapılır: dize koleksiyonlarını (LINQ) (Visual Basic) birleştirme ve karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="1d58b-133">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](how-to-combine-and-compare-string-collections-linq.md)  
 <span data-ttu-id="1d58b-134">Dize listesi çeşitli şekillerde birleştirmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1d58b-134">Shows how to combine string lists in various ways.</span></span>  
  
 [<span data-ttu-id="1d58b-135">Nasıl yapılır: (LINQ) (Visual Basic) birden fazla kaynaktan nesne koleksiyonları doldurma</span><span class="sxs-lookup"><span data-stu-id="1d58b-135">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 <span data-ttu-id="1d58b-136">Veri kaynakları olarak birden çok metin dosyalarını kullanarak nesne koleksiyonları oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d58b-136">Shows how to create object collections by using multiple text files as data sources.</span></span>  
  
 [<span data-ttu-id="1d58b-137">Nasıl yapılır: (LINQ) (Visual Basic) farklı dosyalardan içerik birleştirme</span><span class="sxs-lookup"><span data-stu-id="1d58b-137">How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)  
 <span data-ttu-id="1d58b-138">İki liste dizelerde eşleşen bir anahtarı'nı kullanarak tek bir dize halinde birleştirmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1d58b-138">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>  
  
 [<span data-ttu-id="1d58b-139">Nasıl yapılır: bir dosya grupları (LINQ) (Visual Basic) kullanarak birden çok dosyaya bölme</span><span class="sxs-lookup"><span data-stu-id="1d58b-139">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 <span data-ttu-id="1d58b-140">Bir veri kaynağı olarak tek bir dosya kullanarak yeni dosyalar oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d58b-140">Shows how to create new files by using a single file as a data source.</span></span>  
  
 [<span data-ttu-id="1d58b-141">Nasıl yapılır: bir CSV metinde dosyasında (LINQ) (Visual Basic) sütun değerlerini hesaplama</span><span class="sxs-lookup"><span data-stu-id="1d58b-141">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 <span data-ttu-id="1d58b-142">.Csv dosyaları metin veriler üzerinde matematiksel hesaplamalar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1d58b-142">Shows how to perform mathematical computations on text data in .csv files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d58b-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1d58b-143">See Also</span></span>  
 [<span data-ttu-id="1d58b-144">Dil ile tümleşik sorgu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d58b-144">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)  
 [<span data-ttu-id="1d58b-145">Nasıl yapılır: XML CSV dosyalarından oluştur</span><span class="sxs-lookup"><span data-stu-id="1d58b-145">How to: Generate XML from CSV Files</span></span>](how-to-generate-xml-from-csv-files.md)
