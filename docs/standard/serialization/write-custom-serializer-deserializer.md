---
title: Özel serileştiricileri ve seri hale Getiricileri yazma System.Text.Json
description: Ad alanını kullanarak JSON için özel serileştiriciler ve seri hale getiriciler yazmayı öğrenin System.Text.Json .
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: a01d3c8dd18c114ea1c3aabc402bc841a6025ffe
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440024"
---
# <a name="how-to-write-custom-serializers-and-deserializers-with-no-locsystemtextjson"></a><span data-ttu-id="e8fce-103">Özel serileştiricileri ve seri hale Getiricileri yazma System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="e8fce-103">How to write custom serializers and deserializers with System.Text.Json</span></span>

<span data-ttu-id="e8fce-104"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> , bir veya ' dan okunan UTF-8 kodlu JSON metin için yüksek performanslı, düşük bir ayırma, Salt ilet okuyucu olur `ReadOnlySpan<byte>` `ReadOnlySequence<byte>` .</span><span class="sxs-lookup"><span data-stu-id="e8fce-104"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="e8fce-105">, `Utf8JsonReader` Özel Çözümleyicileri ve seri hale getiriciler oluşturmak için kullanılabilen alt düzey bir türdür.</span><span class="sxs-lookup"><span data-stu-id="e8fce-105">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="e8fce-106"><xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>Yöntemi `Utf8JsonReader` , kapakların altında kullanır.</span><span class="sxs-lookup"><span data-stu-id="e8fce-106">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="e8fce-107"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> , ve gibi ortak .NET türlerinden UTF-8 kodlu JSON metni yazmanın yüksek performanslı bir yoludur `String` `Int32` `DateTime` .</span><span class="sxs-lookup"><span data-stu-id="e8fce-107"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="e8fce-108">Yazıcı, özel serileştiriciler oluşturmak için kullanılabilen alt düzey bir türdür.</span><span class="sxs-lookup"><span data-stu-id="e8fce-108">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="e8fce-109"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>Yöntemi `Utf8JsonWriter` , kapakların altında kullanır.</span><span class="sxs-lookup"><span data-stu-id="e8fce-109">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="e8fce-110"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> kullanarak salt okunurdur Belge Nesne Modeli (DOM) oluşturma yeteneği sağlar `Utf8JsonReader` .</span><span class="sxs-lookup"><span data-stu-id="e8fce-110"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="e8fce-111">DOM, bir JSON yükünde verilere rastgele erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8fce-111">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="e8fce-112">Yükü oluşturan JSON öğelerine tür aracılığıyla erişilebilir <xref:System.Text.Json.JsonElement> .</span><span class="sxs-lookup"><span data-stu-id="e8fce-112">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="e8fce-113">`JsonElement`Türü, JSON metnini ortak .net türlerine dönüştürmek Için API 'lerle birlikte dizi ve nesne numaralandırıcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8fce-113">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="e8fce-114">`JsonDocument` bir <xref:System.Text.Json.JsonDocument.RootElement> özellik sunar.</span><span class="sxs-lookup"><span data-stu-id="e8fce-114">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="e8fce-115">Aşağıdaki bölümlerde, bu araçların JSON okuma ve yazma için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e8fce-115">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="e8fce-116">Veri erişimi için JsonDocument kullanın</span><span class="sxs-lookup"><span data-stu-id="e8fce-116">Use JsonDocument for access to data</span></span>

<span data-ttu-id="e8fce-117">Aşağıdaki örnek, <xref:System.Text.Json.JsonDocument> BIR JSON dizesindeki verilere rastgele erişim için sınıfının nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="e8fce-117">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs" id="AverageGrades1":::

<span data-ttu-id="e8fce-118">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="e8fce-118">The preceding code:</span></span>

* <span data-ttu-id="e8fce-119">Analiz edilecek JSON 'in adlı bir dizede olduğunu varsayar `jsonString` .</span><span class="sxs-lookup"><span data-stu-id="e8fce-119">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="e8fce-120">Özelliği olan bir dizideki nesneler için Ortalama bir sınıf hesaplar `Students` `Grade` .</span><span class="sxs-lookup"><span data-stu-id="e8fce-120">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span>
* <span data-ttu-id="e8fce-121">Bir sınıfa sahip olmayan öğrenciler için varsayılan bir 70 sınıfı atar.</span><span class="sxs-lookup"><span data-stu-id="e8fce-121">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="e8fce-122">Her yinelemeyle bir değişkeni arttırarak öğrencileri sayar `count` .</span><span class="sxs-lookup"><span data-stu-id="e8fce-122">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="e8fce-123"><xref:System.Text.Json.JsonElement.GetArrayLength%2A>Aşağıdaki örnekte gösterildiği gibi bir alternatif çağrdır:</span><span class="sxs-lookup"><span data-stu-id="e8fce-123">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  :::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs" id="AverageGrades2":::

<span data-ttu-id="e8fce-124">Bu kodun işlediği JSON örneğine bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e8fce-124">Here's an example of the JSON that this code processes:</span></span>

:::code language="json" source="snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json":::

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="e8fce-125">JSON yazmak için JsonDocument kullanın</span><span class="sxs-lookup"><span data-stu-id="e8fce-125">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="e8fce-126">Aşağıdaki örnek, öğesinden nasıl JSON yazılacağını göstermektedir <xref:System.Text.Json.JsonDocument> :</span><span class="sxs-lookup"><span data-stu-id="e8fce-126">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs" id="Serialize":::

<span data-ttu-id="e8fce-127">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="e8fce-127">The preceding code:</span></span>

* <span data-ttu-id="e8fce-128">Bir JSON dosyasını okur, verileri bir `JsonDocument` dosyasına yükler ve bir dosyaya biçimli (düzgün yazdırılmış) JSON yazar.</span><span class="sxs-lookup"><span data-stu-id="e8fce-128">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="e8fce-129"><xref:System.Text.Json.JsonDocumentOptions>JSON girişi içindeki açıklamalara izin verildiğini ancak yok sayılacağını belirtmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="e8fce-129">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="e8fce-130">İşiniz bittiğinde, <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> Yazıcı üzerindeki çağrılar.</span><span class="sxs-lookup"><span data-stu-id="e8fce-130">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="e8fce-131">Alternatif olarak, yazıcı bırakıldığında otomatik olarak temizlemeye izin verilir.</span><span class="sxs-lookup"><span data-stu-id="e8fce-131">An alternative is to let the writer auto-flush when it's disposed.</span></span>

<span data-ttu-id="e8fce-132">Örnek kod tarafından işlenecek JSON girişi örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e8fce-132">Here's an example of JSON input to be processed by the example code:</span></span>

:::code language="json" source="snippets/system-text-json-how-to/csharp/Grades.json":::

<span data-ttu-id="e8fce-133">Sonuç, aşağıdaki düzgün yazdırılmış JSON çıktıdır:</span><span class="sxs-lookup"><span data-stu-id="e8fce-133">The result is the following pretty-printed JSON output:</span></span>

:::code language="json" source="snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json":::

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="e8fce-134">Utf8JsonWriter kullanma</span><span class="sxs-lookup"><span data-stu-id="e8fce-134">Use Utf8JsonWriter</span></span>

<span data-ttu-id="e8fce-135">Aşağıdaki örnek sınıfının nasıl kullanılacağını gösterir <xref:System.Text.Json.Utf8JsonWriter> :</span><span class="sxs-lookup"><span data-stu-id="e8fce-135">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs" id="Serialize":::

## <a name="use-utf8jsonreader"></a><span data-ttu-id="e8fce-136">Utf8JsonReader kullanma</span><span class="sxs-lookup"><span data-stu-id="e8fce-136">Use Utf8JsonReader</span></span>

<span data-ttu-id="e8fce-137">Aşağıdaki örnek sınıfının nasıl kullanılacağını gösterir <xref:System.Text.Json.Utf8JsonReader> :</span><span class="sxs-lookup"><span data-stu-id="e8fce-137">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs" id="Deserialize":::

<span data-ttu-id="e8fce-138">Yukarıdaki kod, `jsonUtf8` DEĞIŞKENIN UTF-8 olarak kodlanmış GEÇERLI JSON içeren bir bayt dizisi olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="e8fce-138">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="e8fce-139">Utf8JsonReader kullanarak verileri filtreleme</span><span class="sxs-lookup"><span data-stu-id="e8fce-139">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="e8fce-140">Aşağıdaki örnek, bir dosyanın zaman uyumlu olarak nasıl okunacağını gösterir ve bir değer arar.</span><span class="sxs-lookup"><span data-stu-id="e8fce-140">The following example shows how to synchronously read a file, and search for a value.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs":::

<span data-ttu-id="e8fce-141">Bu örneğin zaman uyumsuz bir sürümü için bkz. [.net ÖRNEKLERI JSON projesi](https://github.com/dotnet/samples/blob/18e31a5f1abd4f347bf96bfdc3e40e2cfb36e319/core/json/Program.cs).</span><span class="sxs-lookup"><span data-stu-id="e8fce-141">For an asynchronous version of this example, see [.NET samples JSON project](https://github.com/dotnet/samples/blob/18e31a5f1abd4f347bf96bfdc3e40e2cfb36e319/core/json/Program.cs).</span></span>

<span data-ttu-id="e8fce-142">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="e8fce-142">The preceding code:</span></span>

* <span data-ttu-id="e8fce-143">JSON 'un bir nesne dizisi içerdiğini ve her nesne dize türünde bir "ad" özelliği içerebildiği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="e8fce-143">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="e8fce-144">"University" ile biten nesneleri ve "ad" özellik değerlerini sayar.</span><span class="sxs-lookup"><span data-stu-id="e8fce-144">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="e8fce-145">Dosyanın UTF-16 olarak kodlandığını varsayar ve bunu UTF-8 ' e dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="e8fce-145">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="e8fce-146">Aşağıdaki kod kullanılarak UTF-8 olarak kodlanmış bir dosya doğrudan bir ile okunabilir `ReadOnlySpan<byte>` :</span><span class="sxs-lookup"><span data-stu-id="e8fce-146">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  <span data-ttu-id="e8fce-147">Dosya bir UTF-8 bayt sırası işareti (BOM) içeriyorsa, okuyucu metin gerektirdiğinden, baytları öğesine geçirmeden önce kaldırın `Utf8JsonReader` .</span><span class="sxs-lookup"><span data-stu-id="e8fce-147">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="e8fce-148">Aksi takdirde, BOM geçersiz JSON olarak değerlendirilir ve okuyucu bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e8fce-148">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="e8fce-149">Yukarıdaki kodun okuya, bir JSON örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e8fce-149">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="e8fce-150">Sonuçtaki Özet ileti "2 ' den 4 ' ün" University "ile biten adlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e8fce-150">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

:::code language="json" source="snippets/system-text-json-how-to/csharp/Universities.json":::

### <a name="read-from-a-stream-using-utf8jsonreader"></a><span data-ttu-id="e8fce-151">Utf8JsonReader kullanarak akıştan okuma</span><span class="sxs-lookup"><span data-stu-id="e8fce-151">Read from a stream using Utf8JsonReader</span></span>

<span data-ttu-id="e8fce-152">Büyük bir dosyayı (örneğin, boyutu bir gigabayt veya daha fazla) okurken, dosyanın tamamını aynı anda belleğe yükleme zorunluluğunu ortadan kaldırmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8fce-152">When reading a large file (a gigabyte or more in size, for example), you might want to avoid having to load the entire file into memory at once.</span></span> <span data-ttu-id="e8fce-153">Bu senaryo için bir kullanabilirsiniz <xref:System.IO.FileStream> .</span><span class="sxs-lookup"><span data-stu-id="e8fce-153">For this scenario, you can use a <xref:System.IO.FileStream>.</span></span>

<span data-ttu-id="e8fce-154">`Utf8JsonReader`Bir akıştan okumak için kullanırken, aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="e8fce-154">When using the `Utf8JsonReader` to read from a stream, the following rules apply:</span></span>

* <span data-ttu-id="e8fce-155">Kısmi JSON yükünün bulunduğu arabellek en az, onun içindeki en büyük JSON belirteci kadar büyük olmalıdır, böylece okuyucu ilerlemeye devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="e8fce-155">The buffer containing the partial JSON payload must be at least as large as the largest JSON token within it so that the reader can make forward progress.</span></span>
* <span data-ttu-id="e8fce-156">Arabellek en az JSON içindeki boşluk olan en büyük dizi kadar büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e8fce-156">The buffer must be at least as large as the largest sequence of white space within the JSON.</span></span>
* <span data-ttu-id="e8fce-157">Okuyucu, JSON yükünde bir sonrakini tamamen okuuncaya kadar okuduğu verileri takip etmez <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> .</span><span class="sxs-lookup"><span data-stu-id="e8fce-157">The reader doesn't keep track of the data it has read until it completely reads the next <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> in the JSON payload.</span></span> <span data-ttu-id="e8fce-158">Bu nedenle, arabellekte kalan baytlar varsa, bunları okuyucuya yeniden geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8fce-158">So when there are bytes left over in the buffer, you have to pass them to the reader again.</span></span> <span data-ttu-id="e8fce-159"><xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A>Kaç baytın kaldığını anlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8fce-159">You can use <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> to determine how many bytes are left over.</span></span>

<span data-ttu-id="e8fce-160">Aşağıdaki kod bir akıştan nasıl okunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8fce-160">The following code illustrates how to read from a stream.</span></span> <span data-ttu-id="e8fce-161">Örnek bir gösterir <xref:System.IO.MemoryStream> .</span><span class="sxs-lookup"><span data-stu-id="e8fce-161">The example shows a <xref:System.IO.MemoryStream>.</span></span> <span data-ttu-id="e8fce-162">Benzer kod, <xref:System.IO.FileStream> `FileStream` Başlangıç AŞAMASıNDA bir UTF-8 bom içerdiğinde, ile birlikte çalışır.</span><span class="sxs-lookup"><span data-stu-id="e8fce-162">Similar code will work with a <xref:System.IO.FileStream>, except when the `FileStream` contains a UTF-8 BOM at the start.</span></span> <span data-ttu-id="e8fce-163">Bu durumda, kalan baytları öğesine geçirmeden önce bu üç baytı arabellekten çıkarmanız gerekir `Utf8JsonReader` .</span><span class="sxs-lookup"><span data-stu-id="e8fce-163">In that case, you need to strip those three bytes from the buffer before passing the remaining bytes to the `Utf8JsonReader`.</span></span> <span data-ttu-id="e8fce-164">Aksi halde, BOM JSON 'ın geçerli bir parçası olarak kabul edilmediğinden okuyucu bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e8fce-164">Otherwise the reader would throw an exception, since the BOM is not considered a valid part of the JSON.</span></span>

<span data-ttu-id="e8fce-165">Örnek kod, bir 4KB arabelleği ile başlar ve boyutun, bir bütün JSON belirtecine sığamayacak kadar büyük olmadığını bulduğu her bulduğunda, bu, okuyucunun JSON yükünde ilerlemesinin ilerlemesini sağlamak için gerekli olan her seferinde arabellek boyutunu iki katına çıkarır.</span><span class="sxs-lookup"><span data-stu-id="e8fce-165">The sample code starts with a 4KB buffer and doubles the buffer size each time it finds that the size is not large enough to fit a complete JSON token, which is required for the reader to make forward progress on the JSON payload.</span></span> <span data-ttu-id="e8fce-166">Kod parçacığında belirtilen JSON örneği, yalnızca çok küçük bir başlangıç arabelleği boyutu ayarlarsanız (örneğin, 10 bayt) bir arabellek boyutunu tetikler.</span><span class="sxs-lookup"><span data-stu-id="e8fce-166">The JSON sample provided in the snippet triggers a buffer size increase only if you set a very small initial buffer size, for example, 10 bytes.</span></span> <span data-ttu-id="e8fce-167">Başlangıçtaki arabellek boyutunu 10 olarak ayarlarsanız, `Console.WriteLine` deyimler arabellek boyutunun arttığı nedeni ve etkisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8fce-167">If you set the initial buffer size to 10, the `Console.WriteLine` statements illustrate the cause and effect of buffer size increases.</span></span> <span data-ttu-id="e8fce-168">4 KB ilk arabellek boyutunda, tüm örnek JSON her biri tarafından gösterilir `Console.WriteLine` ve arabellek boyutunun hiçbir zaman artırılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e8fce-168">At the 4KB initial buffer size, the entire sample JSON is shown by each `Console.WriteLine`, and the buffer size never has to be increased.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs":::

<span data-ttu-id="e8fce-169">Yukarıdaki örnek, arabelleğin ne kadar büyüeceği hakkında sınır yoktur.</span><span class="sxs-lookup"><span data-stu-id="e8fce-169">The preceding example sets no limit to how large the buffer can grow.</span></span> <span data-ttu-id="e8fce-170">Belirteç boyutu çok büyükse, kod bir <xref:System.OutOfMemoryException> özel durumla başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="e8fce-170">If the token size is too large, the code could fail with an <xref:System.OutOfMemoryException> exception.</span></span> <span data-ttu-id="e8fce-171">Bu, JSON 1 GB veya daha fazla boyuttaki bir belirteç içeriyorsa, 1 GB boyutunun, arabelleğe sığamayacak kadar büyük bir boyuta neden olduğundan bu durum oluşabilir `int32` .</span><span class="sxs-lookup"><span data-stu-id="e8fce-171">This can happen if the JSON contains a token that is around 1 GB or more in size, because doubling the 1 GB size results in a size that is too large to fit into an `int32` buffer.</span></span>

## <a name="see-also"></a><span data-ttu-id="e8fce-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8fce-172">See also</span></span>

* [<span data-ttu-id="e8fce-173">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="e8fce-173">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="e8fce-174">Karakter kodlamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="e8fce-174">How to customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="e8fce-175">JSON serileştirme için özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="e8fce-175">How to write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="e8fce-176">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="e8fce-176">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
