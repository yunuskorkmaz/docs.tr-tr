---
title: 'Nasıl yapılır: WSDL Sözleşmeleriyle Hizmet Bilinen Adı Kullanma'
ms.date: 03/30/2017
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
ms.openlocfilehash: 2968641538bf0b4d0e136d5784bf69e5e7fcb3a0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59298090"
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a>Nasıl yapılır: WSDL Sözleşmeleriyle Hizmet Bilinen Adı Kullanma
Tamamen bağımsız bir COM birlikte çalışma istemciniz isteyebileceğiniz durumlar vardır. Hizmeti çağırmak istediğinizde bir MEX uç noktası ve DLL COM birlikte çalışması için kayıtlı olmayabilir WCF istemcisini açığa çıkarmamak. Bu durumlarda, hizmeti tanımlayan bir WSDL dosyası oluşturun ve WCF hizmet bilinen adını geçirin. Bu konu, bir WSDL WCF bilinen adını kullanarak çalışmaya WCF başlama örneği çağrılacak açıklar.  
  
### <a name="using-the-wsdl-service-moniker"></a>WSDL hizmet bilinen adı kullanma  
  
1. Açın ve GettingStarted örnek Çözümü derleyin.  
  
2. Internet Explorer'ı açın ve `http://localhost/ServiceModelSamples/Service.svc` hizmetinin çalıştığından emin olmak için.  
  
3. Adını da dosyasında CalculatorService sınıfında aşağıdaki özniteliği ekleyin:  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4. Bir bağlama ad alanı, App.config hizmete ekleyin:  

5. Uygulamanın okuma WSDL dosyası oluşturun. Adım 3 ve 4 ad alanlarını eklenmiş olduğundan, hizmetin tüm WSDL açıklaması göz atarak sorgulamak için IE kullanabilirsiniz `http://localhost/ServiceModelSamples/Service.svc?wsdl`. Dosyayı serviceWSDL.xml Internet Explorer'dan kaydedin. Adım 3 ve 4 ad belirtmezseniz, yukarıdaki URL'yi sorgulamasını döndürülen WSDL belgesinde tam WSDL olmayacaktır. WSDL belgesi döndürülen diğer WSDL belgeleri içe birkaç içeri aktarma deyimlerini içerir. Her içeri aktarma deyimi aracılığıyla gidin ve tam bir WSDL belgesi oluşturmak WSDL içe WSDL ile hizmetten döndürülen birleştirme gerekir.  
  
6. Visual Basic 6.0 açın ve yeni bir standart .exe dosyası oluşturun. Forma bir düğme ekleyin ve aşağıdaki kodu için tıklama işleyicisi eklemek için Ekle düğmesine çift tıklayın:  
  
    ```  
    ' Open the WSDL contract file and read it all into the wsdlContract string.  
    Const ForReading = 1  
    Set objFSO = CreateObject("Scripting.FileSystemObject")  
    Set objFile = objFSO.OpenTextFile("c:\serviceWsdl.xml", ForReading)  
    wsdlContract = objFile.ReadAll  
    objFile.Close  
  
    ' Create a string for the service moniker including the content of the WSDL contract file.  
    wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
    wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
    wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
    wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
    ' Create the service moniker object.  
    Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
  
    ' Call the service operations using the moniker object.  
    MsgBox "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
    ```  
  
    > [!NOTE]
    >  Bilinen ad hatalı veya hizmet kullanılamıyorsa çağrısı `GetObject` "Geçersiz sözdizimi" belirten bir hata döndürür.  Bu hata iletisini alırsanız kullandığınız ad doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.  
  
7. Visual Basic uygulamasını çalıştırın. Bir ileti kutusu arama çıkarma (145, 76.54) sonuçlarını görüntülenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)
- [COM Uygulamaları ile Tümleştirme Genel Bakış](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
