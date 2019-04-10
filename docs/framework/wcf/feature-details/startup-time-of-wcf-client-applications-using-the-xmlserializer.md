---
title: 'Nasıl yapılır: XmlSerializer Kullanarak WCF İstemci Uygulamalarının Başlangıç Zamanlarını İyileştirme'
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: b6f010cb5edc3111f05c78f5d27cf178bd501ef9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326430"
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a>Nasıl yapılır: XmlSerializer Kullanarak WCF İstemci Uygulamalarının Başlangıç Zamanlarını İyileştirme
Hizmetler ve seri hale getirilebilir kullanarak veri türlerini kullanan istemci uygulamalar <xref:System.Xml.Serialization.XmlSerializer> oluşturmak ve yavaş başlatma performansı düşürebilir çalışma zamanında bu veri türleri için serileştirme kodu derleyin.  
  
> [!NOTE]
>  Önceden oluşturulan serileştirme kod, yalnızca istemci uygulamaları ve Hizmetleri kullanılabilir.  
  
 [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) derlenmiş bütünleştirilmiş uygulama için gerekli serileştirme kod oluşturarak bu uygulamaları için başlatma performansını geliştirebilir. Svcutil.exe kullanarak seri hale getirilebilir derlenmiş uygulama derlemesindeki hizmet sözleşmelerinde kullanılan tüm veri türleri için serileştirme kod oluşturur <xref:System.Xml.Serialization.XmlSerializer>. Kullandığınız hizmet ve işlem sözleşmeler <xref:System.Xml.Serialization.XmlSerializer> ile işaretlenmiş <xref:System.ServiceModel.XmlSerializerFormatAttribute>.  
  
### <a name="to-generate-xmlserializer-serialization-code"></a>XmlSerializer serileştirme kod oluşturmak için  
  
1. Hizmet veya istemci kodunuz, bir veya daha fazla derlemeye derlemesi.  
  
2. Bir SDK komut istemi açın.  
  
3. Komut isteminde, aşağıdaki biçimi kullanarak Svcutil.exe aracını başlatın.  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     `assemblyPath` Bağımsız değişkeni, hizmet sözleşmesi türleri içeren bir bütünleştirilmiş kod yolu belirtir. Svcutil.exe kullanarak seri hale getirilebilir derlenmiş uygulama derlemesindeki hizmet sözleşmelerinde kullanılan tüm veri türleri için serileştirme kod oluşturur <xref:System.Xml.Serialization.XmlSerializer>.  
  
     Svcutil.exe yalnızca oluşturabileceği C# serileştirme kodu. Giriş her derleme için bir kaynak kodu dosyası oluşturulur. Kullanamazsınız **/language** oluşturulan kod dilini değiştirmek için anahtar.  
  
     Bağımlı derlemelerin yolu belirtmek için kullanın **/reference** seçeneği.  
  
4. Aşağıdaki seçeneklerden birini kullanarak oluşturulan serileştirme kodu, uygulamanızın kullanılabilir hale getirmek:  
  
    1.  Ada sahip ayrı bir derleme halinde oluşturulan serileştirme kodu derleme [*orijinal derleme*]. XmlSerializers.dll (örneğin, MyApp.XmlSerializers.dll). Uygulamanızı orijinal derleme olarak aynı anahtarla imzalanmalıdır derlemeyi yüklemek mümkün olması gerekir. Orijinal derlemeyi yeniden derlerseniz, serileştirme bütünleştirilmiş kodu oluşturmanız gerekir.  
  
    2.  Oluşturulan serileştirme kodu ayrı bir derlemeye derlemek ve kullanmak <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> kullanır hizmet sözleşmesindeki <xref:System.ServiceModel.XmlSerializerFormatAttribute>. Ayarlama <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> veya <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> derlenmiş serileştirme derlemeye işaret edecek şekilde özellikleri.  
  
    3.  Oluşturulan serileştirme kodu, uygulama derlemeye derlemek ve ekleme <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> kullanan hizmet sözleşmesi <xref:System.ServiceModel.XmlSerializerFormatAttribute>. Ayarlı değil <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> veya <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> özellikleri. Varsayılan serileştirme bütünleştirilmiş kodu geçerli derleme varsayılır.  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a>Visual Studio'da XmlSerializer serileştirme kod oluşturmak için  
  
1. WCF hizmeti ve istemcisine Visual Studio'da projeler oluşturun. Ardından, istemci projesinin bir hizmet başvurusu ekleyin.  
  
2. Ekleme bir <xref:System.ServiceModel.XmlSerializerFormatAttribute> için hizmet sözleşmesi içerisinde *reference.cs* altında istemci uygulaması projenizi dosyasında **serviceReference** -> **reference.svcmap** . Tüm dosyaları göster gerektiğini unutmayın **Çözüm Gezgini** bu dosyaları görmek için.  
  
3. İstemci uygulaması oluşturun.  
  
4. Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) önceden oluşturulmuş bir seri hale getirici oluşturulacak *.cs* komutu kullanarak dosya:  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     WCF istemci derleme yolu assemblyPath bağımsız değişken belirtir.  
  
     Örneğin:  
  
    ```  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     *WCFClient.XmlSerializers.dll.cs* dosyası oluşturulur.  
  
5. Önceden oluşturulan serileştirme bütünleştirilmiş kodu derleyin.  
  
     Örnek önceki adımda bağlı olarak, derleme komut şöyle olur:  
  
    ```  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     Oluşturulan emin *WCFClient.XmlSerializers.dll* olan istemci uygulaması ile aynı dizinde olduğu *WCFClient.exe* böyle bir durumda.  
  
6. İstemci uygulaması her zaman olduğu gibi çalıştırın. Önceden oluşturulan serileştirme bütünleştirilmiş kodu kullanılacak.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komutu için seri hale getirme türlerinde oluşturur `XmlSerializer` derleme kullanımda herhangi bir hizmet sözleşmeleri türleri.  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
