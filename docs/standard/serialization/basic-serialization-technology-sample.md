---
title: Temel seri hale getirme teknolojisi örneği
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9d824e16-08d1-4a36-bc7f-2388c1f75f34
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2aa2dd790a0f292175fae6c45d8bfc60859ac4ac
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="basic-serialization-technology-sample"></a>Temel seri hale getirme teknolojisi örneği
[Örnek indirme](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)  
  
 Bu örnek bir akışa bellekte bir nesne grafiğinin seri hale getirmek için ortak dil çalışma özelliği gösterilmektedir. Bu örnek ya da kullanabilirsiniz <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> veya <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> seri hale getirme. Veri ile doldurulan bir bağlantılı liste serileştirilecek veya için veya bir dosya akışı serisi. Her iki durumda da, sonuçları görebilmesi listesi görüntülenir. Bağlantılı listesinin türünde `LinkedList`, bu örnek tarafından tanımlanan bir türü.  
  
 Serileştirme hakkında daha fazla bilgi için kaynak kodu ve build.proj dosyalarını yorumlarda inceleyin.  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a>Komut istemi kullanarak örneği oluşturmak için  
  
1.  Komut istemi kullanarak Technologies\Serialization\Runtime Serialization\Basic dizin altında dile özgü alt birine gidin.  
  
2.  Tür **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** veya **msbuild SerializationVB.sln**adresindeki programlama dili, tercih ettiğiniz bağlı olarak komut satırı.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Visual Studio kullanarak örneği oluşturmak için  
  
1.  Açık [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] ve örnek için dile özgü alt birine gidin.  
  
2.  Visual Studio'da dosyayı açmak için dil, programlama dillerinden istediğinizi bağlı olarak SerializationCS.sln, SerializationJSL.sln veya SerializationVB.sln dosya simgesini çift tıklatın.  
  
3.  İçinde **yapı** menüsünde, select **yapı çözümü**.  
  
 Uygulama örneği varsayılan \bin veya \bin\debug'dır alt dizininde oluşturulur.  
  
### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  Yerleşik yürütülebilir dosya içeren dizine gidin.  
  
2.  Tür **Serialization.exe**, parametre değerleri ile birlikte, komut satırında istediğiniz.  
  
    > [!NOTE]
    >  Bu örnek, bir konsol uygulaması oluşturur. Çıktısını görüntülemek için komut istemi kullanarak başlatma gerekir.  
  
## <a name="remarks"></a>Açıklamalar  
 Örnek uygulama komut satırı parameTReleri, test belirten yürütmek istiyor musunuz kabul eder. 10-node listesini adlı bir dosyaya serileştirmek için **Test.xml** SOAP biçimlendirici kullanarak parametreleri **sx Test.xml 10**.  
  
 Örneğin:  
  
 **Serialize.exe - sx Test.xml 10**  
  
 Seri durumdan çıkarılacak **Test.xml** dosya önceki örnekten, parametrelerini kullanmak **dx Test.xml**.  
  
 Örneğin:  
  
 **Serialize.exe - dx Test.xml**  
  
 İki Yukarıdaki örneklerde, komut satırı anahtarı "x", XML SOAP serileştirme istediğinizi gösterir. İkili serileştirme kullanmak için "b" yerinde kullanabilirsiniz. Çok sayıda düğüm içeren serileştirme deneyin isterseniz, konsol çıktısı bir dosyaya yönlendirin isteyebilirsiniz.  
  
 Örneğin:  
  
 **Serialize.exe - sb Test.bin 10000 > somefile.txt**  
  
 Aşağıdaki madde işaretleri sınıflar Bu örnek tarafından kullanılan ve teknolojiler kısaca anlatın.  
  
-   Çalışma zamanı seri hale getirme  
  
    -   <xref:System.Runtime.Serialization.IFormatter>Ya da başvurmak için kullanılan bir <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> veya bir <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> nesne.  
  
    -   <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Bir ikili biçimi bir akışa bağlı bir listeye serileştirmek için kullanılır. İkili biçimlendirici, yalnızca bir biçimi kullanıp <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> anladığı türü. Ancak, veri kısa olabilir.  
  
    -   <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> SOAP biçiminde bir akışa bağlı bir listeyi serileştirmek için kullanılır. SOAP standart bir biçimidir.  
  
-   Akış G/Ç  
  
    -   <xref:System.IO.Stream>Serileştirme ve seri halinden dağıtmak için kullanılır. Bu örnekte kullanılan belirli akış türü <xref:System.IO.FileStream> türü. Ancak, serileştirme türetilen her türlü kullanılabilir <xref:System.IO.Stream>.  
  
    -   <xref:System.IO.File>Oluşturmak için kullanılan <xref:System.IO.FileStream> nesneleri için okuma ve disk üzerindeki dosyalar oluşturuluyor.  
  
    -   <xref:System.IO.FileStream>Seri hale getirmek ve bağlı listeler serisini kaldırmak için kullanılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
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
 [Temel Serileştirme](../../../docs/standard/serialization/basic-serialization.md)  
 [İkili Serileştirme](../../../docs/standard/serialization/binary-serialization.md)  
 [Öznitelikleri Kullanarak XML Serileştirmeyi Denetleme](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 [XML Serileştirmeye Giriş](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [Serileştirme](../../../docs/standard/serialization/index.md)  
 [XML ve SOAP Serileştirme](../../../docs/standard/serialization/xml-and-soap-serialization.md)
