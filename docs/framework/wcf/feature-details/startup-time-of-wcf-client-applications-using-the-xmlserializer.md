---
title: 'Nasıl yapılır: XmlSerializer Kullanarak WCF İstemci Uygulamalarının Başlangıç Zamanlarını İyileştirme'
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: 91712963908ecc56ff17fbac028389207544b82f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600263"
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a>Nasıl yapılır: XmlSerializer Kullanarak WCF İstemci Uygulamalarının Başlangıç Zamanlarını İyileştirme
<xref:System.Xml.Serialization.XmlSerializer>Çalışma zamanında bu veri türleri için Oluştur ve derle serileştirme kodu kullanılarak seri hale getirilebilir veri türlerini kullanan hizmet ve istemci uygulamaları, yavaş başlangıç performansına yol açabilir.  
  
> [!NOTE]
> Önceden oluşturulmuş serileştirme kodu, hizmetlerde değil yalnızca istemci uygulamalarında kullanılabilir.  
  
 [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , uygulama için derlenmiş derlemelerden gerekli serileştirme kodunu oluşturarak bu uygulamalar için başlangıç performansını iyileştirebilir. Svcutil. exe, kullanılarak seri hale getirilenebilecek derlenmiş uygulama derlemesindeki hizmet sözleşmelerinde kullanılan tüm veri türleri için serileştirme kodu oluşturur <xref:System.Xml.Serialization.XmlSerializer> . Kullanan hizmet ve işlem sözleşmeleri <xref:System.Xml.Serialization.XmlSerializer> ile işaretlenir <xref:System.ServiceModel.XmlSerializerFormatAttribute> .  
  
### <a name="to-generate-xmlserializer-serialization-code"></a>XmlSerializer Serileştirme kodu oluşturmak için  
  
1. Hizmetinizi veya istemci kodunuzu bir veya daha fazla derlemede derleyin.  
  
2. SDK komut istemi açın.  
  
3. Komut isteminde, aşağıdaki biçimi kullanarak Svcutil. exe aracını başlatın.  
  
    ```console  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     `assemblyPath`Bağımsız değişkeni, hizmet sözleşmesi türlerini içeren bir derlemenin yolunu belirtir. Svcutil. exe, kullanılarak seri hale getirilenebilecek derlenmiş uygulama derlemesindeki hizmet sözleşmelerinde kullanılan tüm veri türleri için serileştirme kodu oluşturur <xref:System.Xml.Serialization.XmlSerializer> .  
  
     Svcutil. exe yalnızca C# serileştirme kodu oluşturabilir. Her giriş derlemesi için bir kaynak kodu dosyası oluşturulur. Oluşturulan kodun dilini değiştirmek için **/Language** anahtarını kullanamazsınız.  
  
     Bağımlı derlemelerin yolunu belirtmek için **/Reference** seçeneğini kullanın.  
  
4. Aşağıdaki seçeneklerden birini kullanarak, üretilen serileştirme kodunu uygulamanız için kullanılabilir hale getirin:  
  
    1. Oluşturulan serileştirme kodunu, adı [*özgün derleme*] olan ayrı bir derlemede derleyin. Xmlserileştiriciler. dll (örneğin, MyApp. Xmlserileştiriciler. dll). Uygulamanız, özgün derlemeyle aynı anahtarla imzalanması gereken derlemeyi yükleyebilmelidir. Özgün derlemeyi yeniden derlemenizin serileştirme derlemesini yeniden oluşturmanız gerekir.  
  
    2. Oluşturulan serileştirme kodunu ayrı bir derlemede derleyin ve öğesini <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> kullanan hizmet sözleşmesinde kullanın <xref:System.ServiceModel.XmlSerializerFormatAttribute> . <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A>Veya <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> özelliklerini derlenen serileştirme derlemesini işaret etmek için ayarlayın.  
  
    3. Oluşturulan serileştirme kodunu uygulama derlemenizde derleyin ve öğesini <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> kullanan hizmet sözleşmesine ekleyin <xref:System.ServiceModel.XmlSerializerFormatAttribute> . <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A>Veya <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> özelliklerini ayarlamayın. Varsayılan serileştirme derlemesinin geçerli derleme olduğu varsayılır.  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a>Visual Studio 'da XmlSerializer Serileştirme kodu oluşturmak için  
  
1. Visual Studio 'da WCF hizmetini ve istemci projelerini oluşturun. Ardından, istemci projesine bir hizmet başvurusu ekleyin.  
  
2. <xref:System.ServiceModel.XmlSerializerFormatAttribute> *reference.cs* **ServiceReference**  ->  **Reference. svcmap**altındaki istemci uygulaması projesindeki Reference.cs dosyasına hizmet sözleşmesine ekleyin. Bu dosyaları görmek için **Çözüm Gezgini** tüm dosyaları göstermesinin gerekli olduğunu unutmayın.  
  
3. İstemci uygulamasını oluşturun.  
  
4. Şu komutu kullanarak önceden oluşturulmuş bir seri hale getirici *. cs* dosyası oluşturmak Için [ServiceModel meta veri yardımcı programı aracı 'Nı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın:  
  
    ```console  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     AssemblyPath bağımsız değişkeni, WCF istemci derlemesinin yolunu belirtir.  
  
     Örneğin:  
  
    ```console  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     *WCFClient.XmlSerializers.dll.cs* dosyası oluşturulacaktır.  
  
5. Önceden oluşturulmuş serileştirme derlemesini derleyin.  
  
     Önceki adımdaki örneğe bağlı olarak, derleme komutu aşağıdaki gibi olacaktır:  
  
    ```console  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     Oluşturulan *Wcfclient. Xmlserileştiriciler. dll dosyasının* bu durumda *wcfclient. exe* olan istemci uygulamasıyla aynı dizinde olduğundan emin olun.  
  
6. İstemci uygulamasını her zamanki gibi çalıştırın. Önceden oluşturulmuş serileştirme derlemesi kullanılacaktır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut, `XmlSerializer` derlemedeki herhangi bir hizmet sözleşmesi tarafından kullanılan türler için serileştirme türleri oluşturur.  
  
```console  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
