---
title: Temel Serileştirme Teknolojisi Örneği
ms.date: 03/30/2017
ms.assetid: 9d824e16-08d1-4a36-bc7f-2388c1f75f34
ms.openlocfilehash: e5dcc9ec7cf6f996c97262b14020552286c530da
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353144"
---
# <a name="basic-serialization-technology-sample"></a><span data-ttu-id="3919b-102">Temel Serileştirme Teknolojisi Örneği</span><span class="sxs-lookup"><span data-stu-id="3919b-102">Basic Serialization Technology Sample</span></span>

[<span data-ttu-id="3919b-103">Örnek indir</span><span class="sxs-lookup"><span data-stu-id="3919b-103">Download sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)

<span data-ttu-id="3919b-104">Bu örnek, ortak dil çalışma zamanının bir akışa bellekte bir nesne grafiğinin seri hale getirme yeteneğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3919b-104">This sample demonstrates the common language runtime's ability to serialize an object graph in memory to a stream.</span></span> <span data-ttu-id="3919b-105">Bu örnek ya da kullanabilirsiniz <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> veya <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> seri hale getirme.</span><span class="sxs-lookup"><span data-stu-id="3919b-105">This sample can use either the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> or the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> for serialization.</span></span> <span data-ttu-id="3919b-106">Verilerle doldurulan bağlantılı bir liste, bir dosya akışından serileştirilir veya seri hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3919b-106">A linked list, filled with data, is serialized or deserialized to or from a file stream.</span></span> <span data-ttu-id="3919b-107">Her iki durumda da, sonuçları görebilmesi listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3919b-107">In either case the list is displayed so that you can see the results.</span></span> <span data-ttu-id="3919b-108">Bağlantılı listesinin türünde `LinkedList`, bu örnek tarafından tanımlanan bir türü.</span><span class="sxs-lookup"><span data-stu-id="3919b-108">The linked list is of type `LinkedList`, a type defined by this sample.</span></span>

<span data-ttu-id="3919b-109">Serileştirme hakkında daha fazla bilgi için kaynak kodu ve build.proj dosyalarını yorumlarda inceleyin.</span><span class="sxs-lookup"><span data-stu-id="3919b-109">Review comments in the source code and build.proj files for more information on serialization.</span></span>

### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="3919b-110">Komut istemi kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3919b-110">To build the sample using the Command Prompt</span></span>

1. <span data-ttu-id="3919b-111">Komut istemi kullanarak Technologies\Serialization\Runtime Serialization\Basic dizin altında dile özgü alt birine gidin.</span><span class="sxs-lookup"><span data-stu-id="3919b-111">Navigate to one of the language-specific subdirectories under the Technologies\Serialization\Runtime Serialization\Basic directory, using the command prompt.</span></span>

2. <span data-ttu-id="3919b-112">Seçtiğiniz programlama diline bağlı olarak, komut satırında **MSBuild SerializationCS. sln**, **MSBuild serializationjsl. sln** veya **MSBuild serializationvb. sln**yazın.</span><span class="sxs-lookup"><span data-stu-id="3919b-112">Type **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** or **msbuild SerializationVB.sln**, depending on your choice of programming language, at the command line.</span></span>

### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="3919b-113">Visual Studio kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3919b-113">To build the sample using Visual Studio</span></span>

1. <span data-ttu-id="3919b-114">Dosya Gezgini 'ni açın ve örnek için dile özgü alt dizinlerden birine gidin.</span><span class="sxs-lookup"><span data-stu-id="3919b-114">Open File Explorer and navigate to one of the language-specific subdirectories for the sample.</span></span>

2. <span data-ttu-id="3919b-115">Visual Studio'da dosyayı açmak için dil, programlama dillerinden istediğinizi bağlı olarak SerializationCS.sln, SerializationJSL.sln veya SerializationVB.sln dosya simgesini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="3919b-115">Double-click the icon for the SerializationCS.sln, SerializationJSL.sln or SerializationVB.sln file, depending on your choice of programming language, to open the file in Visual Studio.</span></span>

3. <span data-ttu-id="3919b-116">**Build** menüsünde **Build Solution**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="3919b-116">In the **Build** menu, select **Build Solution**.</span></span>

 <span data-ttu-id="3919b-117">Uygulama örneği varsayılan \bin veya \bin\debug'dır alt dizininde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3919b-117">The sample application will be built in the default \bin or \bin\Debug subdirectory.</span></span>

### <a name="to-run-the-sample"></a><span data-ttu-id="3919b-118">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3919b-118">To run the sample</span></span>

1. <span data-ttu-id="3919b-119">Yerleşik yürütülebilir dosya içeren dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="3919b-119">Navigate to the directory containing the built executable.</span></span>

2. <span data-ttu-id="3919b-120">Komut satırında, istediğiniz parametre değerleriyle birlikte **serileştirme. exe**yazın.</span><span class="sxs-lookup"><span data-stu-id="3919b-120">Type **Serialization.exe**, along with the parameter values you desire, at the command line.</span></span>

  > [!NOTE]
  > <span data-ttu-id="3919b-121">Bu örnek, bir konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3919b-121">This sample builds a console application.</span></span> <span data-ttu-id="3919b-122">Çıktısını görüntülemek için komut istemi kullanarak başlatma gerekir.</span><span class="sxs-lookup"><span data-stu-id="3919b-122">You must launch it using the command prompt in order to view its output.</span></span>

## <a name="remarks"></a><span data-ttu-id="3919b-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3919b-123">Remarks</span></span>

<span data-ttu-id="3919b-124">Örnek uygulama komut satırı parameTReleri, test belirten yürütmek istiyor musunuz kabul eder.</span><span class="sxs-lookup"><span data-stu-id="3919b-124">The sample application accepts command line parameters indicating which test you would like to execute.</span></span> <span data-ttu-id="3919b-125">10 düğümlü bir listeyi SOAP biçimlendirici kullanarak **test. xml** adlı bir dosyaya seri hale getirmek için, **SX test. xml 10**parametresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3919b-125">To serialize a 10-node list to a file named **Test.xml** using the SOAP formatter, use the parameters **sx Test.xml 10**.</span></span>

<span data-ttu-id="3919b-126">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3919b-126">For Example:</span></span>

```console
Serialize.exe -sx Test.xml 10
```

<span data-ttu-id="3919b-127">Önceki örnekteki **test. xml** dosyasının serisini kaldırmak Için **DX test. xml**parametrelerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3919b-127">To deserialize the **Test.xml** file from the previous example, use the parameters **dx Test.xml**.</span></span>

<span data-ttu-id="3919b-128">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3919b-128">For Example:</span></span>

```console
Serialize.exe -dx Test.xml
```

<span data-ttu-id="3919b-129">İki Yukarıdaki örneklerde, komut satırı anahtarı "x", XML SOAP serileştirme istediğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="3919b-129">In the two examples above, the "x" in the command line switch indicates that you want XML SOAP serialization.</span></span> <span data-ttu-id="3919b-130">İkili serileştirme kullanmak için "b" yerinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3919b-130">You can use "b" in its place to use binary serialization.</span></span> <span data-ttu-id="3919b-131">Serileştirmeyi çok fazla sayıda düğümle denemek istiyorsanız, konsol çıkışını bir dosyaya yeniden yönlendirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3919b-131">If you wish to try serialization with a very large number of nodes, you might want to redirect the console output to a file.</span></span>

<span data-ttu-id="3919b-132">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3919b-132">For Example:</span></span>

```console
Serialize.exe -sb Test.bin 10000 >somefile.txt
```

<span data-ttu-id="3919b-133">Aşağıdaki madde işaretleri sınıflar Bu örnek tarafından kullanılan ve teknolojiler kısaca anlatın.</span><span class="sxs-lookup"><span data-stu-id="3919b-133">The following bullets briefly describe the classes and technologies used by this sample.</span></span>

- <span data-ttu-id="3919b-134">Çalışma zamanı seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="3919b-134">Runtime Serialization</span></span>

  - <span data-ttu-id="3919b-135"><xref:System.Runtime.Serialization.IFormatter>Ya da başvurmak için kullanılan bir <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> veya bir <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> nesne.</span><span class="sxs-lookup"><span data-stu-id="3919b-135"><xref:System.Runtime.Serialization.IFormatter> Used to refer to either a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> or a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> object.</span></span>

  - <span data-ttu-id="3919b-136"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ' ın bir ikili biçimdeki bir akışa bağlı bir liste serileştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3919b-136"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Used to serialize a linked list to a stream in a binary format.</span></span> <span data-ttu-id="3919b-137">İkili biçimlendirici, yalnızca bir biçimi kullanıp <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> anladığı türü.</span><span class="sxs-lookup"><span data-stu-id="3919b-137">The binary formatter uses a format that only the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> type understands.</span></span> <span data-ttu-id="3919b-138">Ancak, veri kısa olabilir.</span><span class="sxs-lookup"><span data-stu-id="3919b-138">However, the data is concise.</span></span>

  - <span data-ttu-id="3919b-139"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>, bağlantılı bir listeyi SOAP biçimindeki bir akışa seri hale getirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3919b-139"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> Used to serialize a linked list to a stream in the SOAP format.</span></span> <span data-ttu-id="3919b-140">SOAP standart bir biçimidir.</span><span class="sxs-lookup"><span data-stu-id="3919b-140">SOAP is a standard format.</span></span>

- <span data-ttu-id="3919b-141">Akış G/Ç</span><span class="sxs-lookup"><span data-stu-id="3919b-141">Stream I/O</span></span>

  - <span data-ttu-id="3919b-142"><xref:System.IO.Stream>Serileştirme ve seri halinden dağıtmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3919b-142"><xref:System.IO.Stream> Used to serialize and deserialize.</span></span> <span data-ttu-id="3919b-143">Bu örnekte kullanılan belirli akış türü <xref:System.IO.FileStream> türüdür.</span><span class="sxs-lookup"><span data-stu-id="3919b-143">The specific stream type used in this sample is the <xref:System.IO.FileStream> type.</span></span> <span data-ttu-id="3919b-144">Ancak, serileştirme türetilen her türlü kullanılabilir <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="3919b-144">However, serialization can be used with any type derived from <xref:System.IO.Stream>.</span></span>

  - <span data-ttu-id="3919b-145"><xref:System.IO.File> disk üzerinde dosya okumak ve oluşturmak için <xref:System.IO.FileStream> nesneleri oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3919b-145"><xref:System.IO.File> Used to create <xref:System.IO.FileStream> objects for reading and creating files on disk.</span></span>

  - <span data-ttu-id="3919b-146"><xref:System.IO.FileStream> bağlantılı listeleri seri hale getirmek ve seri durumdan çıkarmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3919b-146"><xref:System.IO.FileStream> Used to serialize and deserialize linked lists.</span></span>

## <a name="see-also"></a><span data-ttu-id="3919b-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3919b-147">See also</span></span>

- <xref:System.IO>
- <xref:System.IO.File>
- <xref:System.IO.FileStream>
- <xref:System.IO.Stream>
- <xref:System.Random>
- <xref:System.Runtime.Serialization>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
- <xref:System.Runtime.Serialization.IFormatter>
- <xref:System.SerializableAttribute>
- <xref:System.Xml.Serialization>
- [<span data-ttu-id="3919b-148">Temel Serileştirme</span><span class="sxs-lookup"><span data-stu-id="3919b-148">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)
- [<span data-ttu-id="3919b-149">İkili Serileştirme</span><span class="sxs-lookup"><span data-stu-id="3919b-149">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)
- [<span data-ttu-id="3919b-150">Öznitelikleri Kullanarak XML Serileştirmeyi Denetleme</span><span class="sxs-lookup"><span data-stu-id="3919b-150">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)
- [<span data-ttu-id="3919b-151">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="3919b-151">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="3919b-152">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="3919b-152">Serialization</span></span>](../../../docs/standard/serialization/index.md)
- [<span data-ttu-id="3919b-153">XML ve SOAP Serileştirme</span><span class="sxs-lookup"><span data-stu-id="3919b-153">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
