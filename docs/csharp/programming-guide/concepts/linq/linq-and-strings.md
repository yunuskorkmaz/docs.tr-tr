---
title: LINQ ve dizeler (C#)
description: LINQ, dizeleri ve dize koleksiyonlarını sorgulayabilir ve dönüştürebilir. LINQ sorgularını C# dize işlevleri ve normal ifadeler ile birleştirebilirsiniz.
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: 0500d821335659fa29dd4809513f38dac0a8b193
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556726"
---
# <a name="linq-and-strings-c"></a><span data-ttu-id="d953d-104">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="d953d-104">LINQ and strings (C#)</span></span>

<span data-ttu-id="d953d-105">LINQ, dizeleri ve dize koleksiyonlarını sorgulamak ve dönüştürmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d953d-105">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="d953d-106">Bu, özellikle metin dosyalarındaki yarı yapılandırılmış verilerle yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d953d-106">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="d953d-107">LINQ sorguları, geleneksel dize işlevleri ve normal ifadelerle birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d953d-107">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="d953d-108">Örneğin, <xref:System.String.Split%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> daha sonra LINQ kullanarak sorgulayabilmeniz veya değiştiremeyeceğiniz bir dize dizisi oluşturmak için veya yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d953d-108">For example, you can use the <xref:System.String.Split%2A?displayProperty=nameWithType> or <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="d953d-109"><xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> `where` Bir LINQ sorgusunun yan tümcesindeki yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d953d-109">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="d953d-110">Aynı şekilde, <xref:System.Text.RegularExpressions.MatchCollection> bir normal ifade tarafından döndürülen sonuçları sorgulamak veya değiştirmek IÇIN LINQ kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d953d-110">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>

<span data-ttu-id="d953d-111">Yarı yapılandırılmış metin verilerini XML 'e dönüştürmek için bu bölümde açıklanan teknikleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d953d-111">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="d953d-112">Daha fazla bilgi için bkz. [CSV DOSYALARıNDAN XML oluşturma](../../../../standard/linq/generate-xml-csv-files.md).</span><span class="sxs-lookup"><span data-stu-id="d953d-112">For more information, see [How to generate XML from CSV files](../../../../standard/linq/generate-xml-csv-files.md).</span></span>

<span data-ttu-id="d953d-113">Bu bölümdeki örnekler iki kategoriye ayrılır:</span><span class="sxs-lookup"><span data-stu-id="d953d-113">The examples in this section fall into two categories:</span></span>

## <a name="querying-a-block-of-text"></a><span data-ttu-id="d953d-114">Metin bloğunu sorgulama</span><span class="sxs-lookup"><span data-stu-id="d953d-114">Querying a block of text</span></span>

<span data-ttu-id="d953d-115">Yöntemini veya yöntemini kullanarak bunları bir daha küçük dizeler dizisine bölerek metin bloklarını sorgulayabilir, çözümleyebilir ve değiştirebilirsiniz <xref:System.String.Split%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d953d-115">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A?displayProperty=nameWithType> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d953d-116">Kaynak metni sözcükler, cümleler, paragraflar, sayfalar veya diğer ölçütlere bölebilir ve ardından sorgunuzda gerekliyse ek bölmeler gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d953d-116">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>

- [<span data-ttu-id="d953d-117">Dizedeki bir sözcüğün tekrarlamalarını sayma (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d953d-117">How to count occurrences of a word in a string (LINQ) (C#)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  <span data-ttu-id="d953d-118">Metin üzerinde basit sorgulama için LINQ 'ın nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d953d-118">Shows how to use LINQ for simple querying over text.</span></span>

- [<span data-ttu-id="d953d-119">Belirli bir sözcük kümesini (LINQ) içeren cümleleri sorgulama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d953d-119">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  <span data-ttu-id="d953d-120">Metin dosyalarının rastgele sınırlarda nasıl bölüneceği ve her parçaya yönelik sorguların nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d953d-120">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>

- [<span data-ttu-id="d953d-121">Dizedeki karakterleri sorgulama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d953d-121">How to query for characters in a string (LINQ) (C#)</span></span>](how-to-query-for-characters-in-a-string-linq.md)

  <span data-ttu-id="d953d-122">Bir dizenin sorgulanabilir bir tür olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d953d-122">Demonstrates that a string is a queryable type.</span></span>

- [<span data-ttu-id="d953d-123">LINQ sorgularını normal ifadelerle birleştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="d953d-123">How to combine LINQ queries with regular expressions (C#)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)

  <span data-ttu-id="d953d-124">Filtrelenmiş sorgu sonuçlarında karmaşık model eşleştirmesi için LINQ sorgularında normal ifadelerin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d953d-124">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>

## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="d953d-125">Yarı yapılandırılmış verileri metin biçiminde sorgulama</span><span class="sxs-lookup"><span data-stu-id="d953d-125">Querying semi-structured data in text format</span></span>

<span data-ttu-id="d953d-126">Birçok farklı metin dosyası türü, genellikle sekme veya virgülle ayrılmış dosyalar ya da sabit uzunluklu çizgiler gibi benzer biçimlendirmeler içeren bir dizi satırdan oluşur.</span><span class="sxs-lookup"><span data-stu-id="d953d-126">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="d953d-127">Bu tür bir metin dosyasını belleğe okuduktan sonra, satırları sorgulamak ve/veya değiştirmek için LINQ kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d953d-127">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="d953d-128">LINQ sorguları Ayrıca birden çok kaynaktan veri birleştirme görevini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="d953d-128">LINQ queries also simplify the task of combining data from multiple sources.</span></span>

- [<span data-ttu-id="d953d-129">İki liste arasındaki küme farkını bulma (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d953d-129">How to find the set difference between two lists (LINQ) (C#)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)

  <span data-ttu-id="d953d-130">Bir listede bulunan ancak diğeri olmayan tüm dizelerin nasıl bulunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d953d-130">Shows how to find all the strings that are present in one list but not the other.</span></span>

- [<span data-ttu-id="d953d-131">Her kelime veya alana göre metin verilerini sıralama veya filtreleme (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d953d-131">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  <span data-ttu-id="d953d-132">Metin çizgilerinin herhangi bir sözcük veya alana göre nasıl sıralanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d953d-132">Shows how to sort text lines based on any word or field.</span></span>

- [<span data-ttu-id="d953d-133">Ayrılmış bir dosyanın alanlarını yeniden sıralama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d953d-133">How to reorder the fields of a delimited file (LINQ) (C#)</span></span>](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  <span data-ttu-id="d953d-134">Bir. csv dosyasındaki bir satırdaki alanların nasıl yeniden oluşturulduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d953d-134">Shows how to reorder fields in a line in a .csv file.</span></span>

- [<span data-ttu-id="d953d-135">Dize koleksiyonlarını birleştirme ve karşılaştırma (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d953d-135">How to combine and compare string collections (LINQ) (C#)</span></span>](how-to-combine-and-compare-string-collections-linq.md)

  <span data-ttu-id="d953d-136">Dize listelerinin çeşitli yollarla nasıl birleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d953d-136">Shows how to combine string lists in various ways.</span></span>

- [<span data-ttu-id="d953d-137">Birden çok kaynaktan nesne koleksiyonlarını doldurma (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d953d-137">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)

  <span data-ttu-id="d953d-138">Birden çok metin dosyasını veri kaynağı olarak kullanarak nasıl nesne koleksiyonları oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d953d-138">Shows how to create object collections by using multiple text files as data sources.</span></span>

- [<span data-ttu-id="d953d-139">Benzer olmayan dosyalardaki (LINQ) içerik ekleme (C#)</span><span class="sxs-lookup"><span data-stu-id="d953d-139">How to join content from dissimilar files (LINQ) (C#)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)
  
  <span data-ttu-id="d953d-140">İki listedeki dizelerin, eşleşen bir anahtar kullanılarak tek bir dize içinde nasıl birleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d953d-140">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>

- [<span data-ttu-id="d953d-141">Grupları (LINQ) kullanarak bir dosyayı birden çok dosyaya bölme (C#)</span><span class="sxs-lookup"><span data-stu-id="d953d-141">How to split a file into many files by using groups (LINQ) (C#)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  <span data-ttu-id="d953d-142">Veri kaynağı olarak tek bir dosya kullanarak yeni dosyaların nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d953d-142">Shows how to create new files by using a single file as a data source.</span></span>

- [<span data-ttu-id="d953d-143">Bir CSV metin dosyasında (LINQ) sütun değerlerini hesaplama (C#)</span><span class="sxs-lookup"><span data-stu-id="d953d-143">How to compute column values in a CSV text file (LINQ) (C#)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  <span data-ttu-id="d953d-144">. Csv dosyalarındaki metin verilerinde matematiksel hesaplamaların nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d953d-144">Shows how to perform mathematical computations on text data in .csv files.</span></span>

## <a name="see-also"></a><span data-ttu-id="d953d-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d953d-145">See also</span></span>

- [<span data-ttu-id="d953d-146">Dil ile tümleşik sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d953d-146">Language-Integrated Query (LINQ) (C#)</span></span>](index.md)
- [<span data-ttu-id="d953d-147">CSV dosyalarından XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="d953d-147">How to generate XML from CSV files</span></span>](../../../../standard/linq/generate-xml-csv-files.md)
