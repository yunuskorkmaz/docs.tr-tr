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
# <a name="basic-serialization-technology-sample"></a>Temel Serileştirme Teknolojisi Örneği

[Örnek indir](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)

Bu örnek, ortak dil çalışma zamanının bir akışa bellekte bir nesne grafiğinin seri hale getirme yeteneğini gösterir. Bu örnek ya da kullanabilirsiniz <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> veya <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> seri hale getirme. Verilerle doldurulan bağlantılı bir liste, bir dosya akışından serileştirilir veya seri hale getirilebilir. Her iki durumda da, sonuçları görebilmesi listesi görüntülenir. Bağlantılı listesinin türünde `LinkedList`, bu örnek tarafından tanımlanan bir türü.

Serileştirme hakkında daha fazla bilgi için kaynak kodu ve build.proj dosyalarını yorumlarda inceleyin.

### <a name="to-build-the-sample-using-the-command-prompt"></a>Komut istemi kullanarak örneği oluşturmak için

1. Komut istemi kullanarak Technologies\Serialization\Runtime Serialization\Basic dizin altında dile özgü alt birine gidin.

2. Seçtiğiniz programlama diline bağlı olarak, komut satırında **MSBuild SerializationCS. sln**, **MSBuild serializationjsl. sln** veya **MSBuild serializationvb. sln**yazın.

### <a name="to-build-the-sample-using-visual-studio"></a>Visual Studio kullanarak örneği oluşturmak için

1. Dosya Gezgini 'ni açın ve örnek için dile özgü alt dizinlerden birine gidin.

2. Visual Studio'da dosyayı açmak için dil, programlama dillerinden istediğinizi bağlı olarak SerializationCS.sln, SerializationJSL.sln veya SerializationVB.sln dosya simgesini çift tıklatın.

3. **Build** menüsünde **Build Solution**' ı seçin.

 Uygulama örneği varsayılan \bin veya \bin\debug'dır alt dizininde oluşturulur.

### <a name="to-run-the-sample"></a>Örnek çalıştırmak için

1. Yerleşik yürütülebilir dosya içeren dizine gidin.

2. Komut satırında, istediğiniz parametre değerleriyle birlikte **serileştirme. exe**yazın.

  > [!NOTE]
  > Bu örnek, bir konsol uygulaması oluşturur. Çıktısını görüntülemek için komut istemi kullanarak başlatma gerekir.

## <a name="remarks"></a>Açıklamalar

Örnek uygulama komut satırı parameTReleri, test belirten yürütmek istiyor musunuz kabul eder. 10 düğümlü bir listeyi SOAP biçimlendirici kullanarak **test. xml** adlı bir dosyaya seri hale getirmek için, **SX test. xml 10**parametresini kullanın.

Örneğin:

```console
Serialize.exe -sx Test.xml 10
```

Önceki örnekteki **test. xml** dosyasının serisini kaldırmak Için **DX test. xml**parametrelerini kullanın.

Örneğin:

```console
Serialize.exe -dx Test.xml
```

İki Yukarıdaki örneklerde, komut satırı anahtarı "x", XML SOAP serileştirme istediğinizi gösterir. İkili serileştirme kullanmak için "b" yerinde kullanabilirsiniz. Serileştirmeyi çok fazla sayıda düğümle denemek istiyorsanız, konsol çıkışını bir dosyaya yeniden yönlendirmek isteyebilirsiniz.

Örneğin:

```console
Serialize.exe -sb Test.bin 10000 >somefile.txt
```

Aşağıdaki madde işaretleri sınıflar Bu örnek tarafından kullanılan ve teknolojiler kısaca anlatın.

- Çalışma zamanı seri hale getirme

  - <xref:System.Runtime.Serialization.IFormatter>Ya da başvurmak için kullanılan bir <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> veya bir <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> nesne.

  - <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ' ın bir ikili biçimdeki bir akışa bağlı bir liste serileştirmek için kullanılır. İkili biçimlendirici, yalnızca bir biçimi kullanıp <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> anladığı türü. Ancak, veri kısa olabilir.

  - <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>, bağlantılı bir listeyi SOAP biçimindeki bir akışa seri hale getirmek için kullanılır. SOAP standart bir biçimidir.

- Akış G/Ç

  - <xref:System.IO.Stream>Serileştirme ve seri halinden dağıtmak için kullanılır. Bu örnekte kullanılan belirli akış türü <xref:System.IO.FileStream> türüdür. Ancak, serileştirme türetilen her türlü kullanılabilir <xref:System.IO.Stream>.

  - <xref:System.IO.File> disk üzerinde dosya okumak ve oluşturmak için <xref:System.IO.FileStream> nesneleri oluşturmak için kullanılır.

  - <xref:System.IO.FileStream> bağlantılı listeleri seri hale getirmek ve seri durumdan çıkarmak için kullanılır.

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
