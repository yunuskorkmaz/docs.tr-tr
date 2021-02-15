---
title: Metin dosyasına yazma-C# Programlama Kılavuzu
description: C# ile bir metin dosyası yazmayı öğrenin. Çeşitli kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 02/11/2021
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.topic: how-to
ms.custom: contperf-fy21q3
ms.openlocfilehash: ecc3ba73161d4f4571bbc6ae0c9aaa3337586ef7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475623"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="37469-104">Metin dosyasına yazma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="37469-104">How to write to a text file (C# Programming Guide)</span></span>

<span data-ttu-id="37469-105">Bu makalede, bir dosyaya metin yazmanın çeşitli yollarını gösteren birkaç örnek vardır.</span><span class="sxs-lookup"><span data-stu-id="37469-105">In this article, there are several examples showing various ways to write text to a file.</span></span> <span data-ttu-id="37469-106">İlk iki örnek, <xref:System.IO.File?displayProperty=nameWithType> herhangi bir öğesinin her `IEnumerable<string>` bir öğesini bir metin dosyasına yazmak için sınıfında statik kolay yöntemler kullanır `string` .</span><span class="sxs-lookup"><span data-stu-id="37469-106">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a `string` to a text file.</span></span> <span data-ttu-id="37469-107">Üçüncü örnek, dosyaya yazarken her satırı ayrı olarak işlemek gerektiğinde bir dosyaya nasıl metin ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="37469-107">The third example shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="37469-108">İlk üç örnekte, dosyadaki tüm varolan içeriğin üzerine yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="37469-108">In the first three examples, you overwrite all existing content in the file.</span></span> <span data-ttu-id="37469-109">Son örnek, varolan bir dosyaya nasıl metin ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="37469-109">The final example shows how to append text to an existing file.</span></span>

 <span data-ttu-id="37469-110">Bu örneklerin tümü dosyalara dize değişmez değerleri yazar.</span><span class="sxs-lookup"><span data-stu-id="37469-110">These examples all write string literals to files.</span></span> <span data-ttu-id="37469-111">Dosyaya yazılmış metni biçimlendirmek isterseniz, <xref:System.String.Format%2A> yöntemi veya C# [String enterpolasyon](../../language-reference/tokens/interpolated.md) özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="37469-111">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>

## <a name="write-a-collection-of-strings-to-a-file"></a><span data-ttu-id="37469-112">Bir dosyaya dizeler koleksiyonu yazma</span><span class="sxs-lookup"><span data-stu-id="37469-112">Write a collection of strings to a file</span></span>

:::code language="csharp" source="snippets/write-text/WriteAllLines.cs":::

<span data-ttu-id="37469-113">Yukarıdaki kaynak kodu örneği:</span><span class="sxs-lookup"><span data-stu-id="37469-113">The preceding source code example:</span></span>

- <span data-ttu-id="37469-114">Üç değerli bir dize dizisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37469-114">Instantiates a string array with three values.</span></span>
- <span data-ttu-id="37469-115">Abuna bir çağrıyı bekler <xref:System.IO.File.WriteAllLinesAsync%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="37469-115">Awaits a call to <xref:System.IO.File.WriteAllLinesAsync%2A?displayProperty=nameWithType> which:</span></span>

  - <span data-ttu-id="37469-116">Zaman uyumsuz bir dosya adı *WriteLines.txt* oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37469-116">Asynchronously creates a file name *WriteLines.txt*.</span></span> <span data-ttu-id="37469-117">Dosya zaten varsa, üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="37469-117">If the file already exists, it is overwritten.</span></span>
  - <span data-ttu-id="37469-118">Verilen satırları dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="37469-118">Writes the given lines to the file.</span></span>
  - <span data-ttu-id="37469-119">Dosyayı kapatır, gerektiğinde otomatik olarak reçeteye ve elden atılıyor.</span><span class="sxs-lookup"><span data-stu-id="37469-119">Closes the file, automatically flushing and disposing as needed.</span></span>

## <a name="write-one-string-to-a-file"></a><span data-ttu-id="37469-120">Bir dosyaya bir dize yaz</span><span class="sxs-lookup"><span data-stu-id="37469-120">Write one string to a file</span></span>

:::code language="csharp" source="snippets/write-text/WriteAllText.cs":::

<span data-ttu-id="37469-121">Yukarıdaki kaynak kodu örneği:</span><span class="sxs-lookup"><span data-stu-id="37469-121">The preceding source code example:</span></span>

- <span data-ttu-id="37469-122">Atanan dize sabit değeri verilen bir dizeyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="37469-122">Instantiates a string given the assigned string literal.</span></span>
- <span data-ttu-id="37469-123">Abuna bir çağrıyı bekler <xref:System.IO.File.WriteAllTextAsync%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="37469-123">Awaits a call to <xref:System.IO.File.WriteAllTextAsync%2A?displayProperty=nameWithType> which:</span></span>

  - <span data-ttu-id="37469-124">Zaman uyumsuz bir dosya adı *WriteText.txt* oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37469-124">Asynchronously creates a file name *WriteText.txt*.</span></span> <span data-ttu-id="37469-125">Dosya zaten varsa, üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="37469-125">If the file already exists, it is overwritten.</span></span>
  - <span data-ttu-id="37469-126">Verilen metni dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="37469-126">Writes the given text to the file.</span></span>
  - <span data-ttu-id="37469-127">Dosyayı kapatır, gerektiğinde otomatik olarak reçeteye ve elden atılıyor.</span><span class="sxs-lookup"><span data-stu-id="37469-127">Closes the file, automatically flushing and disposing as needed.</span></span>

## <a name="write-selected-strings-from-an-array-to-a-file"></a><span data-ttu-id="37469-128">Seçili dizeleri bir diziden bir dosyaya yaz</span><span class="sxs-lookup"><span data-stu-id="37469-128">Write selected strings from an array to a file</span></span>

:::code language="csharp" source="snippets/write-text/StreamWriterOne.cs":::

<span data-ttu-id="37469-129">Yukarıdaki kaynak kodu örneği:</span><span class="sxs-lookup"><span data-stu-id="37469-129">The preceding source code example:</span></span>

- <span data-ttu-id="37469-130">Üç değerli bir dize dizisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37469-130">Instantiates a string array with three values.</span></span>
- <span data-ttu-id="37469-131">Bir <xref:System.IO.StreamWriter> *WriteLines2.txt* dosya yolu ile bir [using bildirimi](../../whats-new/csharp-8.md#using-declarations)olarak başlatır.</span><span class="sxs-lookup"><span data-stu-id="37469-131">Instantiates a <xref:System.IO.StreamWriter> with a file path of *WriteLines2.txt* as a [using declaration](../../whats-new/csharp-8.md#using-declarations).</span></span>
- <span data-ttu-id="37469-132">Tüm satırlarda yinelenir.</span><span class="sxs-lookup"><span data-stu-id="37469-132">Iterates through all the lines.</span></span>
- <span data-ttu-id="37469-133">Koşullu olarak öğesine bir çağrı bekler <xref:System.IO.StreamWriter.WriteLineAsync(System.String)?displayProperty=nameWithType> , bu, satır içermiyorsa dosyayı dosyaya yazar `"Second"` .</span><span class="sxs-lookup"><span data-stu-id="37469-133">Conditionally awaits a call to <xref:System.IO.StreamWriter.WriteLineAsync(System.String)?displayProperty=nameWithType>, which writes the line to the file when the line doesn't contain `"Second"`.</span></span>

## <a name="append-text-to-an-existing-file"></a><span data-ttu-id="37469-134">Varolan bir dosyaya metin ekle</span><span class="sxs-lookup"><span data-stu-id="37469-134">Append text to an existing file</span></span>

:::code language="csharp" source="snippets/write-text/StreamWriterTwo.cs":::

<span data-ttu-id="37469-135">Yukarıdaki kaynak kodu örneği:</span><span class="sxs-lookup"><span data-stu-id="37469-135">The preceding source code example:</span></span>

- <span data-ttu-id="37469-136">Üç değerli bir dize dizisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37469-136">Instantiates a string array with three values.</span></span>
- <span data-ttu-id="37469-137">Bir <xref:System.IO.StreamWriter> *WriteLines2.txt* dosya yolu ile, bir [using bildirimi](../../whats-new/csharp-8.md#using-declarations)olarak bir örneğini başlatır ve `true` sonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="37469-137">Instantiates a <xref:System.IO.StreamWriter> with a file path of *WriteLines2.txt* as a [using declaration](../../whats-new/csharp-8.md#using-declarations), passing in `true` to append.</span></span>
- <span data-ttu-id="37469-138">' A bir çağrısını bekler <xref:System.IO.StreamWriter.WriteLineAsync(System.String)?displayProperty=nameWithType> , bu, dizeyi dosyaya eklenen bir satır olarak yazar.</span><span class="sxs-lookup"><span data-stu-id="37469-138">Awaits a call to <xref:System.IO.StreamWriter.WriteLineAsync(System.String)?displayProperty=nameWithType>, which writes the string to the file as an appended line.</span></span>

## <a name="exceptions"></a><span data-ttu-id="37469-139">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="37469-139">Exceptions</span></span>

<span data-ttu-id="37469-140">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="37469-140">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="37469-141"><xref:System.InvalidOperationException>: Dosya var ve salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="37469-141"><xref:System.InvalidOperationException>: The file exists and is read-only.</span></span>
- <span data-ttu-id="37469-142"><xref:System.IO.PathTooLongException>: Yol adı çok uzun olabilir.</span><span class="sxs-lookup"><span data-stu-id="37469-142"><xref:System.IO.PathTooLongException>: The path name may be too long.</span></span>
- <span data-ttu-id="37469-143"><xref:System.IO.IOException>: Disk dolu olabilir.</span><span class="sxs-lookup"><span data-stu-id="37469-143"><xref:System.IO.IOException>: The disk may be full.</span></span>

<span data-ttu-id="37469-144">Dosya sistemi ile çalışırken özel durumlara neden olabilecek ek koşullar vardır. Bu, en iyi şekilde programlama savunmalarıdır.</span><span class="sxs-lookup"><span data-stu-id="37469-144">There are additional conditions that may cause exceptions when working with the file system, it is best to program defensively.</span></span>

## <a name="see-also"></a><span data-ttu-id="37469-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37469-145">See also</span></span>

- [<span data-ttu-id="37469-146">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="37469-146">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="37469-147">Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="37469-147">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="37469-148">Örnek: bir koleksiyonu uygulama depolamasına kaydetme</span><span class="sxs-lookup"><span data-stu-id="37469-148">Sample: Save a collection to Application Storage</span></span>](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
