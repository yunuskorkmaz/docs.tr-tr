---
title: LINQ ve dizeler (C#)
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: fb1714c54331ead80cd28435cf3ed1c4c54a704e
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140901"
---
# <a name="linq-and-strings-c"></a><span data-ttu-id="630d9-102">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="630d9-102">LINQ and strings (C#)</span></span>

<span data-ttu-id="630d9-103">LINQ, dizeleri ve dize koleksiyonlarını sorgulamak ve dönüştürmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="630d9-103">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="630d9-104">Bu, özellikle metin dosyalarındaki yarı yapılandırılmış verilerle yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="630d9-104">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="630d9-105">LINQ sorguları, geleneksel dize işlevleri ve normal ifadelerle birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="630d9-105">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="630d9-106">Örneğin, LINQ kullanarak sorgulayabilmeniz veya değiştiremeyeceğiniz bir dize dizisi oluşturmak için <xref:System.String.Split%2A?displayProperty=nameWithType> veya <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="630d9-106">For example, you can use the <xref:System.String.Split%2A?displayProperty=nameWithType> or <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="630d9-107">Bir LINQ sorgusunun `where` yan tümcesinde <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="630d9-107">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="630d9-108">Aynı şekilde, bir normal ifade tarafından döndürülen <xref:System.Text.RegularExpressions.MatchCollection> sonuçlarını sorgulamak veya değiştirmek için LINQ kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="630d9-108">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>

<span data-ttu-id="630d9-109">Yarı yapılandırılmış metin verilerini XML 'e dönüştürmek için bu bölümde açıklanan teknikleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="630d9-109">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="630d9-110">Daha fazla bilgi için bkz. [nasıl yapılır: CSV DOSYALARıNDAN XML oluşturma](how-to-generate-xml-from-csv-files.md).</span><span class="sxs-lookup"><span data-stu-id="630d9-110">For more information, see [How to: Generate XML from CSV Files](how-to-generate-xml-from-csv-files.md).</span></span>

<span data-ttu-id="630d9-111">Bu bölümdeki örnekler iki kategoriye ayrılır:</span><span class="sxs-lookup"><span data-stu-id="630d9-111">The examples in this section fall into two categories:</span></span>

## <a name="querying-a-block-of-text"></a><span data-ttu-id="630d9-112">Metin bloğunu sorgulama</span><span class="sxs-lookup"><span data-stu-id="630d9-112">Querying a block of text</span></span>

<span data-ttu-id="630d9-113"><xref:System.String.Split%2A?displayProperty=nameWithType> yöntemini veya <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> yöntemini kullanarak bunları bir daha küçük dizeler dizisine bölerek metin bloklarını sorgulayabilir, çözümleyebilir ve değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="630d9-113">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A?displayProperty=nameWithType> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="630d9-114">Kaynak metni sözcükler, cümleler, paragraflar, sayfalar veya diğer ölçütlere bölebilir ve ardından sorgunuzda gerekliyse ek bölmeler gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="630d9-114">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>

- [<span data-ttu-id="630d9-115">Dizedeki bir sözcüğün tekrarlamalarını sayma (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="630d9-115">How to count occurrences of a word in a string (LINQ) (C#)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  <span data-ttu-id="630d9-116">Metin üzerinde basit sorgulama için LINQ 'ın nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="630d9-116">Shows how to use LINQ for simple querying over text.</span></span>

- [<span data-ttu-id="630d9-117">Nasıl yapılır: belirli bir sözcükler kümesini içeren cümleleri sorgulama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="630d9-117">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  <span data-ttu-id="630d9-118">Metin dosyalarının rastgele sınırlarda nasıl bölüneceği ve her parçaya yönelik sorguların nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="630d9-118">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>

- [<span data-ttu-id="630d9-119">Nasıl yapılır: bir dizedeki karakterleri sorgulama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="630d9-119">How to: Query for Characters in a String (LINQ) (C#)</span></span>](how-to-query-for-characters-in-a-string-linq.md)

  <span data-ttu-id="630d9-120">Bir dizenin sorgulanabilir bir tür olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="630d9-120">Demonstrates that a string is a queryable type.</span></span>

- [<span data-ttu-id="630d9-121">LINQ sorgularını normal ifadelerle birleştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="630d9-121">How to combine LINQ queries with regular expressions (C#)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)

  <span data-ttu-id="630d9-122">Filtrelenmiş sorgu sonuçlarında karmaşık model eşleştirmesi için LINQ sorgularında normal ifadelerin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="630d9-122">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>

## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="630d9-123">Yarı yapılandırılmış verileri metin biçiminde sorgulama</span><span class="sxs-lookup"><span data-stu-id="630d9-123">Querying semi-structured data in text format</span></span>

<span data-ttu-id="630d9-124">Birçok farklı metin dosyası türü, genellikle sekme veya virgülle ayrılmış dosyalar ya da sabit uzunluklu çizgiler gibi benzer biçimlendirmeler içeren bir dizi satırdan oluşur.</span><span class="sxs-lookup"><span data-stu-id="630d9-124">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="630d9-125">Bu tür bir metin dosyasını belleğe okuduktan sonra, satırları sorgulamak ve/veya değiştirmek için LINQ kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="630d9-125">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="630d9-126">LINQ sorguları Ayrıca birden çok kaynaktan veri birleştirme görevini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="630d9-126">LINQ queries also simplify the task of combining data from multiple sources.</span></span>

- [<span data-ttu-id="630d9-127">Nasıl yapılır: Iki liste arasında küme farkını bulma (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="630d9-127">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)

  <span data-ttu-id="630d9-128">Bir listede bulunan ancak diğeri olmayan tüm dizelerin nasıl bulunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="630d9-128">Shows how to find all the strings that are present in one list but not the other.</span></span>

- [<span data-ttu-id="630d9-129">Nasıl yapılır: herhangi bir sözcük veya alana göre metin verilerini sıralama veya filtreleme (LINQ)C#()</span><span class="sxs-lookup"><span data-stu-id="630d9-129">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  <span data-ttu-id="630d9-130">Metin çizgilerinin herhangi bir sözcük veya alana göre nasıl sıralanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="630d9-130">Shows how to sort text lines based on any word or field.</span></span>

- [<span data-ttu-id="630d9-131">Nasıl yapılır: ayrılmış bir dosyanın alanlarını yeniden sıralama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="630d9-131">How to: Reorder the Fields of a Delimited File (LINQ) (C#)</span></span>](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  <span data-ttu-id="630d9-132">Bir. csv dosyasındaki bir satırdaki alanların nasıl yeniden oluşturulduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="630d9-132">Shows how to reorder fields in a line in a .csv file.</span></span>

- [<span data-ttu-id="630d9-133">Nasıl yapılır: dize koleksiyonlarını birleştirme ve karşılaştırma (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="630d9-133">How to: combine and compare string collections (LINQ) (C#)</span></span>](how-to-combine-and-compare-string-collections-linq.md)

  <span data-ttu-id="630d9-134">Dize listelerinin çeşitli yollarla nasıl birleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="630d9-134">Shows how to combine string lists in various ways.</span></span>

- [<span data-ttu-id="630d9-135">Nasıl yapılır: birden çok kaynaktan nesne koleksiyonları doldurma (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="630d9-135">How to: Populate Object Collections from Multiple Sources (LINQ) (C#)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)

  <span data-ttu-id="630d9-136">Birden çok metin dosyasını veri kaynağı olarak kullanarak nasıl nesne koleksiyonları oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="630d9-136">Shows how to create object collections by using multiple text files as data sources.</span></span>

- [<span data-ttu-id="630d9-137">Nasıl yapılır: farklı dosyalardan Içerik ekleme (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="630d9-137">How to: Join Content from Dissimilar Files (LINQ) (C#)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)
  
  <span data-ttu-id="630d9-138">İki listedeki dizelerin, eşleşen bir anahtar kullanılarak tek bir dize içinde nasıl birleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="630d9-138">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>

- [<span data-ttu-id="630d9-139">Nasıl yapılır: grupları (LINQ) kullanarak bir dosyayı birçok dosyaya bölme (LINQ)C#()</span><span class="sxs-lookup"><span data-stu-id="630d9-139">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  <span data-ttu-id="630d9-140">Veri kaynağı olarak tek bir dosya kullanarak yeni dosyaların nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="630d9-140">Shows how to create new files by using a single file as a data source.</span></span>

- [<span data-ttu-id="630d9-141">CSV metin dosyasında (LINQ) sütun değerlerini hesaplama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="630d9-141">How to compute column values in a CSV text file (LINQ) (C#)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  <span data-ttu-id="630d9-142">. Csv dosyalarındaki metin verilerinde matematiksel hesaplamaların nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="630d9-142">Shows how to perform mathematical computations on text data in .csv files.</span></span>

## <a name="see-also"></a><span data-ttu-id="630d9-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="630d9-143">See also</span></span>

- [<span data-ttu-id="630d9-144">Dil ile tümleşik sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="630d9-144">Language-Integrated Query (LINQ) (C#)</span></span>](index.md)
- [<span data-ttu-id="630d9-145">Nasıl yapılır: CSV Dosyalarından XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="630d9-145">How to: Generate XML from CSV Files</span></span>](how-to-generate-xml-from-csv-files.md)
