---
title: Temel serileştirme teknolojisi örneği
ms.date: 03/30/2017
ms.assetid: 9d824e16-08d1-4a36-bc7f-2388c1f75f34
ms.openlocfilehash: 474eb8ded01a72182533a6d49397d7567447d64e
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44361488"
---
# <a name="basic-serialization-technology-sample"></a>Temel serileştirme teknolojisi örneği
[Örneği indirin](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)  
  
 Bu örnek, bir akışa bellekte bir nesne grafiğinin seri hale getirmek için ortak dil çalışma zamanının yeteneğini gösterir. Bu örnek ya da kullanabilirsiniz <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> veya <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> seri hale getirme. Veri ile doldurulan bir bağlantılı listesinin serileştirilecek veya için veya bir dosya akışı seri durumdan. Her iki durumda da, sonuçları görebilmesi listesi görüntülenir. Bağlantılı listesinin türünde `LinkedList`, bu örnek tarafından tanımlanan bir türü.  
  
 Serileştirme hakkında daha fazla bilgi için kaynak kodu ve build.proj dosyalarını yorumlarda inceleyin.  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a>Komut istemi kullanarak örneği oluşturmak için  
  
1.  Komut istemi kullanarak Technologies\Serialization\Runtime Serialization\Basic dizin altında dile özgü alt birine gidin.  
  
2.  Tür **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** veya **msbuild SerializationVB.sln**, dil, programlama dillerinden bağlı olarak komut satırı.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Visual Studio kullanarak örneği oluşturmak için  
  
1.  Açık [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] ve örnek için dile özgü alt birine gidin.  
  
2.  Visual Studio'da dosyayı açmak için dil, programlama dillerinden istediğinizi bağlı olarak SerializationCS.sln, SerializationJSL.sln veya SerializationVB.sln dosya simgesini çift tıklatın.  
  
3.  İçinde **derleme** menüsünde **Çözümü Derle**.  
  
 Uygulama örneği varsayılan \bin veya \bin\debug'dır alt dizininde oluşturulur.  
  
### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  Yerleşik yürütülebilir dosya içeren dizine gidin.  
  
2.  Tür **Serialization.exe**, parametre değerleri ile birlikte, komut satırında istediğiniz.  
  
    > [!NOTE]
    >  Bu örnek, bir konsol uygulaması oluşturur. Çıktısını görüntülemek için komut istemi kullanarak başlatma gerekir.  
  
## <a name="remarks"></a>Açıklamalar  
 Örnek uygulama komut satırı parameTReleri, test belirten yürütmek istiyor musunuz kabul eder. 10-düğüm listesini adlı bir dosyaya serileştirmek için **Test.xml** SOAP biçimlendirici kullanılarak kullanın parametreleri **sx Test.xml 10**.  
  
 Örneğin:  
  
 **Serialize.exe - sx Test.xml 10**  
  
 Seri durumdan çıkarılacak **Test.xml** dosya önceki örnekteki, parametrelerini **dx Test.xml**.  
  
 Örneğin:  
  
 **Serialize.exe - dx Test.xml**  
  
 İki Yukarıdaki örneklerde, komut satırı anahtarı "x", XML SOAP serileştirme istediğinizi gösterir. İkili serileştirme kullanmak için "b" yerinde kullanabilirsiniz. Serileştirme çok büyük bir düğüm sayısı ile deneyin istiyorsanız, bir dosyaya konsol çıkışı yönlendirmek isteyebilirsiniz.  
  
 Örneğin:  
  
 **Serialize.exe - sb Test.bin 10000 > somefile.txt**  
  
 Aşağıdaki madde işaretleri sınıflar Bu örnek tarafından kullanılan ve teknolojiler kısaca anlatın.  
  
-   Çalışma zamanı seri hale getirme  
  
    -   <xref:System.Runtime.Serialization.IFormatter>Ya da başvurmak için kullanılan bir <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> veya bir <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> nesne.  
  
    -   <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> İkili biçimde bir akışa bağlı bir liste serileştirmek için kullanılır. İkili biçimlendirici, yalnızca bir biçimi kullanıp <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> anladığı türü. Ancak, veri kısa olabilir.  
  
    -   <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> SOAP biçiminde bir akışa bağlı bir liste serileştirmek için kullanılır. SOAP standart bir biçimidir.  
  
-   Akış G/Ç  
  
    -   <xref:System.IO.Stream>Serileştirme ve seri halinden dağıtmak için kullanılır. Bu örnekte kullanılan belirli akış türü <xref:System.IO.FileStream> türü. Ancak, serileştirme türetilen her türlü kullanılabilir <xref:System.IO.Stream>.  
  
    -   <xref:System.IO.File>Oluşturmak için kullanılan <xref:System.IO.FileStream> nesneleri için okuma ve disk üzerindeki dosyalar oluşturuluyor.  
  
    -   <xref:System.IO.FileStream>Seri hale getirmek ve bağlı listeler serisini kaldırmak için kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

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
- [Temel Serileştirme](../../../docs/standard/serialization/basic-serialization.md)  
- [İkili Serileştirme](../../../docs/standard/serialization/binary-serialization.md)  
- [Öznitelikleri Kullanarak XML Serileştirmeyi Denetleme](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
- [XML Serileştirmeye Giriş](../../../docs/standard/serialization/introducing-xml-serialization.md)  
- [Serileştirme](../../../docs/standard/serialization/index.md)  
- [XML ve SOAP Serileştirme](../../../docs/standard/serialization/xml-and-soap-serialization.md)
