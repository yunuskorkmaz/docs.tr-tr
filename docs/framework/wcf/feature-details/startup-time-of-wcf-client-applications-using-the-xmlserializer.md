---
title: "Nasıl yapılır: XmlSerializer Kullanarak WCF İstemci Uygulamalarının Başlangıç Zamanlarını İyileştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 14f5cf25bbcde4732162f2c44c83661a0ac739ea
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a>Nasıl yapılır: XmlSerializer Kullanarak WCF İstemci Uygulamalarının Başlangıç Zamanlarını İyileştirme
Hizmetler ve seri hale getirilebilir kullanarak veri türlerini kullanan istemci uygulamaları <xref:System.Xml.Serialization.XmlSerializer> oluşturmak ve bu yavaş başlatma performansının düşmesine neden olabilir çalışma zamanında veri türleri için seri hale getirme kodu derleyin.  
  
> [!NOTE]
>  Önceden oluşturulmuş serileştirme kod yalnızca istemci uygulamaları ve Hizmetleri kullanılabilir.  
  
 [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) başlangıcından bu uygulamalar için uygulama için derlenmiş derlemelerden gerekli serileştirme kod oluşturarak performansı artırabilir. Svcutil.exe oluşturur kullanılarak serileştirilmiş derlenmiş uygulama derlemesindeki hizmet sözleşmelerinde kullanılan tüm veri türleri için seri hale getirme kodu <xref:System.Xml.Serialization.XmlSerializer>. Kullandığınız hizmet ve işlem sözleşmeler <xref:System.Xml.Serialization.XmlSerializer> işaretlenir <xref:System.ServiceModel.XmlSerializerFormatAttribute>.  
  
### <a name="to-generate-xmlserializer-serialization-code"></a>XmlSerializer seri hale getirme kodu oluşturmak için  
  
1.  Hizmet veya istemci kodunuzun bir veya daha fazla derlemeye derlemesi.  
  
2.  SDK komut istemi açın.  
  
3.  Komut isteminde, aşağıdaki biçimi kullanarak Svcutil.exe Aracı'nı başlatın.  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     `assemblyPath` Bağımsız değişkeni hizmet sözleşmesi türlerini içeren bir derleme yolu belirtir. Svcutil.exe oluşturur kullanılarak serileştirilmiş derlenmiş uygulama derlemesindeki hizmet sözleşmelerinde kullanılan tüm veri türleri için seri hale getirme kodu <xref:System.Xml.Serialization.XmlSerializer>.  
  
     Svcutil.exe yalnızca C# seri hale getirme kodu oluşturabilir. Bir kaynak kodu dosyasının her giriş derlemesi için oluşturulur. Kullanamazsınız **/language** oluşturulan kod dilini değiştirmek için anahtar.  
  
     Bağımlı derlemeleri yolunu belirtmek için kullanın **/reference** seçeneği.  
  
4.  Aşağıdaki seçeneklerden birini kullanarak oluşturulan seri hale getirme kodu uygulamanız için kullanılabilir hale getirmek:  
  
    1.  Adlı ayrı bir derleme halinde üretilen seri hale getirme kodu derleme [*özgün derleme*]. XmlSerializers.dll (örneğin, MyApp.XmlSerializers.dll). Uygulamanızı özgün derlemesi aynı anahtarla imzalanmalıdır derlemeyi yüklemek mümkün olması gerekir. Özgün derleme yeniden derleyin, seri hale getirme derlemesi oluşturmanız gerekir.  
  
    2.  Ayrı bir derleme üretilen seri hale getirme Kodu derlemek ve kullanmak <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> kullanan hizmet sözleşmesinde <xref:System.ServiceModel.XmlSerializerFormatAttribute>. Ayarlama <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> veya <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> derlenmiş serileştirme derlemeye işaret edecek şekilde özellikleri.  
  
    3.  Uygulama derlemeye üretilen seri hale getirme Kodu derlemek ve ekleme <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> kullanan hizmet sözleşmesi <xref:System.ServiceModel.XmlSerializerFormatAttribute>. Ayarlamayın <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> veya <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> özellikleri. Varsayılan seri hale getirme derlemesi geçerli derleme olduğu varsayılır.  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a>Visual Studio'da XmlSerializer seri hale getirme kodu oluşturmak için  
  
1.  WCF hizmeti ve istemci Visual Studio'da projeler oluşturun. Ardından, istemci projesine hizmet başvurusu ekleyin.  
  
2.  Ekleme bir <xref:System.ServiceModel.XmlSerializerFormatAttribute> hizmet sözleşmesi için *reference.cs* altında istemci uygulaması proje dosyasında **serviceReference** -> **reference.svcmap** . Tüm dosyaları göster gerektiğini unutmayın **Çözüm Gezgini** bu dosyaları görmek için.  
  
3.  İstemci uygulaması oluşturma.  
  
4.  Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) önceden oluşturulmuş bir seri hale getirici oluşturmak için *.cs* komutunu kullanarak dosya:  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     AssemblyPath bağımsız değişkeni WCF istemci derleme yolu belirtir.  
  
     Örneğin:  
  
    ```  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     *WCFClient.XmlSerializers.dll.cs* dosyası oluşturulur.  
  
5.  Önceden oluşturulmuş seri hale getirme derlemesi derleyin.  
  
     Örnek önceki adımda bağlı olarak, derleme komut aşağıdaki gibi olabilir:  
  
    ```  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     Oluşturulan emin olun *WCFClient.XmlSerializers.dll* olan istemci uygulaması ile aynı dizinde yer *WCFClient.exe* bu durumda.  
  
6.  İstemci uygulamayı her zamanki gibi çalıştırın. Önceden oluşturulmuş seri hale getirme derlemesi kullanılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut, seri hale getirme türlerinde oluşturur `XmlSerializer` derleme kullanımda herhangi bir hizmet sözleşmeleri türleri.  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
