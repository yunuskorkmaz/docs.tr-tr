---
title: "Temel seri hale getirme teknolojisi örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d824e16-08d1-4a36-bc7f-2388c1f75f34
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c3d269b7603c63db73fdcbab91b777e69b228cc9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="basic-serialization-technology-sample"></a><span data-ttu-id="69976-102">Temel seri hale getirme teknolojisi örneği</span><span class="sxs-lookup"><span data-stu-id="69976-102">Basic Serialization Technology Sample</span></span>
[<span data-ttu-id="69976-103">Örnek indirme</span><span class="sxs-lookup"><span data-stu-id="69976-103">Download sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)  
  
 <span data-ttu-id="69976-104">Bu örnek bir akışa bellekte bir nesne grafiğinin seri hale getirmek için ortak dil çalışma özelliği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="69976-104">This sample demonstrates the common language runtime's ability to serialize an object graph in memory to a stream.</span></span> <span data-ttu-id="69976-105">Bu örnek ya da kullanabilirsiniz <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> veya <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> seri hale getirme.</span><span class="sxs-lookup"><span data-stu-id="69976-105">This sample can use either the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> or the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> for serialization.</span></span> <span data-ttu-id="69976-106">Veri ile doldurulan bir bağlantılı liste serileştirilecek veya için veya bir dosya akışı serisi.</span><span class="sxs-lookup"><span data-stu-id="69976-106">A linked list, filled with data, is serialized or deserialized to or from a file stream.</span></span> <span data-ttu-id="69976-107">Her iki durumda da, sonuçları görebilmesi listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="69976-107">In either case the list is displayed so that you can see the results.</span></span> <span data-ttu-id="69976-108">Bağlantılı listesinin türünde `LinkedList`, bu örnek tarafından tanımlanan bir türü.</span><span class="sxs-lookup"><span data-stu-id="69976-108">The linked list is of type `LinkedList`, a type defined by this sample.</span></span>  
  
 <span data-ttu-id="69976-109">Serileştirme hakkında daha fazla bilgi için kaynak kodu ve build.proj dosyalarını yorumlarda inceleyin.</span><span class="sxs-lookup"><span data-stu-id="69976-109">Review comments in the source code and build.proj files for more information on serialization.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="69976-110">Komut istemi kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="69976-110">To build the sample using the Command Prompt</span></span>  
  
1.  <span data-ttu-id="69976-111">Komut istemi kullanarak Technologies\Serialization\Runtime Serialization\Basic dizin altında dile özgü alt birine gidin.</span><span class="sxs-lookup"><span data-stu-id="69976-111">Navigate to one of the language-specific subdirectories under the Technologies\Serialization\Runtime Serialization\Basic directory, using the command prompt.</span></span>  
  
2.  <span data-ttu-id="69976-112">Tür **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** veya **msbuild SerializationVB.sln**adresindeki programlama dili, tercih ettiğiniz bağlı olarak komut satırı.</span><span class="sxs-lookup"><span data-stu-id="69976-112">Type **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** or **msbuild SerializationVB.sln**, depending on your choice of programming language, at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="69976-113">Visual Studio kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="69976-113">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="69976-114">Açık [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] ve örnek için dile özgü alt birine gidin.</span><span class="sxs-lookup"><span data-stu-id="69976-114">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="69976-115">Visual Studio'da dosyayı açmak için dil, programlama dillerinden istediğinizi bağlı olarak SerializationCS.sln, SerializationJSL.sln veya SerializationVB.sln dosya simgesini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="69976-115">Double-click the icon for the SerializationCS.sln, SerializationJSL.sln or SerializationVB.sln file, depending on your choice of programming language, to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="69976-116">İçinde **yapı** menüsünde, select **yapı çözümü**.</span><span class="sxs-lookup"><span data-stu-id="69976-116">In the **Build** menu, select **Build Solution**.</span></span>  
  
 <span data-ttu-id="69976-117">Uygulama örneği varsayılan \bin veya \bin\debug'dır alt dizininde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="69976-117">The sample application will be built in the default \bin or \bin\Debug subdirectory.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="69976-118">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="69976-118">To run the sample</span></span>  
  
1.  <span data-ttu-id="69976-119">Yerleşik yürütülebilir dosya içeren dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="69976-119">Navigate to the directory containing the built executable.</span></span>  
  
2.  <span data-ttu-id="69976-120">Tür **Serialization.exe**, parametre değerleri ile birlikte, komut satırında istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="69976-120">Type **Serialization.exe**, along with the parameter values you desire, at the command line.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="69976-121">Bu örnek, bir konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="69976-121">This sample builds a console application.</span></span> <span data-ttu-id="69976-122">Çıktısını görüntülemek için komut istemi kullanarak başlatma gerekir.</span><span class="sxs-lookup"><span data-stu-id="69976-122">You must launch it using the command prompt in order to view its output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69976-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="69976-123">Remarks</span></span>  
 <span data-ttu-id="69976-124">Örnek uygulama komut satırı parameTReleri, test belirten yürütmek istiyor musunuz kabul eder.</span><span class="sxs-lookup"><span data-stu-id="69976-124">The sample application accepts command line parameters indicating which test you would like to execute.</span></span> <span data-ttu-id="69976-125">10-node listesini adlı bir dosyaya serileştirmek için **Test.xml** SOAP biçimlendirici kullanarak parametreleri **sx Test.xml 10**.</span><span class="sxs-lookup"><span data-stu-id="69976-125">To serialize a 10-node list to a file named **Test.xml** using the SOAP formatter, use the parameters **sx Test.xml 10**.</span></span>  
  
 <span data-ttu-id="69976-126">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="69976-126">For Example:</span></span>  
  
 <span data-ttu-id="69976-127">**Serialize.exe - sx Test.xml 10**</span><span class="sxs-lookup"><span data-stu-id="69976-127">**Serialize.exe -sx Test.xml 10**</span></span>  
  
 <span data-ttu-id="69976-128">Seri durumdan çıkarılacak **Test.xml** dosya önceki örnekten, parametrelerini kullanmak **dx Test.xml**.</span><span class="sxs-lookup"><span data-stu-id="69976-128">To deserialize the **Test.xml** file from the previous example, use the parameters **dx Test.xml**.</span></span>  
  
 <span data-ttu-id="69976-129">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="69976-129">For Example:</span></span>  
  
 <span data-ttu-id="69976-130">**Serialize.exe - dx Test.xml**</span><span class="sxs-lookup"><span data-stu-id="69976-130">**Serialize.exe -dx Test.xml**</span></span>  
  
 <span data-ttu-id="69976-131">İki Yukarıdaki örneklerde, komut satırı anahtarı "x", XML SOAP serileştirme istediğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="69976-131">In the two examples above, the "x" in the command line switch indicates that you want XML SOAP serialization.</span></span> <span data-ttu-id="69976-132">İkili serileştirme kullanmak için "b" yerinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69976-132">You can use "b" in its place to use binary serialization.</span></span> <span data-ttu-id="69976-133">Çok sayıda düğüm içeren serileştirme deneyin isterseniz, konsol çıktısı bir dosyaya yönlendirin isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69976-133">If you wish to try serialization with a very large number of nodes, you might want to redirect the console output to a file.</span></span>  
  
 <span data-ttu-id="69976-134">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="69976-134">For Example:</span></span>  
  
 <span data-ttu-id="69976-135">**Serialize.exe - sb Test.bin 10000 > somefile.txt**</span><span class="sxs-lookup"><span data-stu-id="69976-135">**Serialize.exe -sb Test.bin 10000 >somefile.txt**</span></span>  
  
 <span data-ttu-id="69976-136">Aşağıdaki madde işaretleri sınıflar Bu örnek tarafından kullanılan ve teknolojiler kısaca anlatın.</span><span class="sxs-lookup"><span data-stu-id="69976-136">The following bullets briefly describe the classes and technologies used by this sample.</span></span>  
  
-   <span data-ttu-id="69976-137">Çalışma zamanı seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="69976-137">Runtime Serialization</span></span>  
  
    -   <span data-ttu-id="69976-138"><xref:System.Runtime.Serialization.IFormatter>Ya da başvurmak için kullanılan bir <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> veya bir <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> nesne.</span><span class="sxs-lookup"><span data-stu-id="69976-138"><xref:System.Runtime.Serialization.IFormatter> Used to refer to either a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> or a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> object.</span></span>  
  
    -   <span data-ttu-id="69976-139"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>Bir ikili biçimi bir akışa bağlı bir listeye serileştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="69976-139"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Used to serialize a linked list to a stream in a binary format.</span></span> <span data-ttu-id="69976-140">İkili biçimlendirici, yalnızca bir biçimi kullanıp <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> anladığı türü.</span><span class="sxs-lookup"><span data-stu-id="69976-140">The binary formatter uses a format that only the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> type understands.</span></span> <span data-ttu-id="69976-141">Ancak, veri kısa olabilir.</span><span class="sxs-lookup"><span data-stu-id="69976-141">However, the data is concise.</span></span>  
  
    -   <span data-ttu-id="69976-142"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>SOAP biçiminde bir akışa bağlı bir listeyi serileştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="69976-142"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> Used to serialize a linked list to a stream in the SOAP format.</span></span> <span data-ttu-id="69976-143">SOAP standart bir biçimidir.</span><span class="sxs-lookup"><span data-stu-id="69976-143">SOAP is a standard format.</span></span>  
  
-   <span data-ttu-id="69976-144">Akış G/Ç</span><span class="sxs-lookup"><span data-stu-id="69976-144">Stream I/O</span></span>  
  
    -   <span data-ttu-id="69976-145"><xref:System.IO.Stream>Serileştirme ve seri halinden dağıtmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="69976-145"><xref:System.IO.Stream> Used to serialize and deserialize.</span></span> <span data-ttu-id="69976-146">Bu örnekte kullanılan belirli akış türü <xref:System.IO.FileStream> türü.</span><span class="sxs-lookup"><span data-stu-id="69976-146">The specific stream type used in this sample is the <xref:System.IO.FileStream> type.</span></span> <span data-ttu-id="69976-147">Ancak, serileştirme türetilen her türlü kullanılabilir <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="69976-147">However, serialization can be used with any type derived from <xref:System.IO.Stream>.</span></span>  
  
    -   <span data-ttu-id="69976-148"><xref:System.IO.File>Oluşturmak için kullanılan <xref:System.IO.FileStream> nesneleri için okuma ve disk üzerindeki dosyalar oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="69976-148"><xref:System.IO.File> Used to create <xref:System.IO.FileStream> objects for reading and creating files on disk.</span></span>  
  
    -   <span data-ttu-id="69976-149"><xref:System.IO.FileStream>Seri hale getirmek ve bağlı listeler serisini kaldırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="69976-149"><xref:System.IO.FileStream> Used to serialize and deserialize linked lists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69976-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="69976-150">See Also</span></span>  
 <xref:System.IO>  
 <xref:System.IO.File>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.Stream>  
 <xref:System.Random>  
 <xref:System.Runtime.Serialization>  
 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>  
 <xref:System.Runtime.Serialization.IFormatter>  
 <xref:System.SerializableAttribute>  
 <xref:System.Xml.Serialization>  
 [<span data-ttu-id="69976-151">Temel Serileştirme</span><span class="sxs-lookup"><span data-stu-id="69976-151">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)  
 [<span data-ttu-id="69976-152">İkili Serileştirme</span><span class="sxs-lookup"><span data-stu-id="69976-152">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
 [<span data-ttu-id="69976-153">Öznitelikleri Kullanarak XML Serileştirmeyi Denetleme</span><span class="sxs-lookup"><span data-stu-id="69976-153">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 [<span data-ttu-id="69976-154">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="69976-154">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="69976-155">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="69976-155">Serialization</span></span>](../../../docs/standard/serialization/index.md)  
 [<span data-ttu-id="69976-156">XML ve SOAP Serileştirme</span><span class="sxs-lookup"><span data-stu-id="69976-156">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
