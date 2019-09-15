---
title: 'Nasıl yapılır: WSDL Sözleşmeleriyle Hizmet Bilinen Adı Kullanma'
ms.date: 03/30/2017
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
ms.openlocfilehash: 7bc628952d4a7198f0b5545014ae931bbf73dab3
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70968997"
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a>Nasıl yapılır: WSDL Sözleşmeleriyle Hizmet Bilinen Adı Kullanma
Tamamen kendi kendine bağımsız bir COM birlikte çalışma istemcisine sahip olmak isteyebileceğiniz durumlar vardır. Çağırmak istediğiniz hizmet bir MEX uç noktası açığa sunmayabilir ve WCF istemci DLL 'SI COM birlikte çalışması için kaydedilmemiş olabilir. Bu durumlarda, hizmeti açıklayan bir WSDL dosyası oluşturabilir ve bunu WCF hizmeti bilinen adına geçirebilirsiniz. Bu konu, bir WCF WSDL bilinen adı kullanılarak Başlarken WCF örneğinin nasıl çağrılacağını açıklar.  
  
### <a name="using-the-wsdl-service-moniker"></a>WSDL hizmeti bilinen adını kullanma  
  
1. GettingStarted örnek çözümünü açın ve oluşturun.  
  
2. Internet Explorer 'ı açın ve hizmetin `http://localhost/ServiceModelSamples/Service.svc` çalıştığından emin olmak için öğesine gidin.  
  
3. Service.cs dosyasında, Hesaplatorservice sınıfına aşağıdaki özniteliği ekleyin:  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4. Service App. config dosyasına bir bağlama ad alanı ekleyin:  

5. Uygulamanın okuması için bir WSDL dosyası oluşturun. Ad alanları 3 ve 4. adımlarda eklendiğinden, ' a giderek hizmetin `http://localhost/ServiceModelSamples/Service.svc?wsdl`WSDL açıklamasının TAMAMıNı sorgulamak için IE kullanabilirsiniz. Dosyayı daha sonra serviceWSDL. xml olarak Internet Explorer 'dan kaydedebilirsiniz. Adım 3 ve 4 ' te ad alanlarını belirtmezseniz, yukarıdaki URL 'yi sorgulamadan döndürülen WSDL belgesi, WSDL 'nin tamamını belirtmeyecektir. Döndürülen WSDL belgesi, diğer WSDL belgelerini içeri aktaracak birkaç içeri aktarma deyimi içerir. Her bir içeri aktarma ekstresini ilerlemenize ve WSDL 'yi içeri aktarılan wsdl ile birleştiren WSDL belgesinin tamamını derlemeniz gerekir.  
  
6. Visual Basic 6,0 ' i açın ve yeni bir standart. exe dosyası oluşturun. Forma bir düğme ekleyin ve tıklama işleyicisine aşağıdaki kodu eklemek için düğmeye çift tıklayın:  
  
    ```vb
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
    > Bilinen ad hatalı biçimlendirilmiş veya hizmet kullanılamıyorsa `GetObject` , "geçersiz söz dizimi" belirten bir hata döndürür.  Bu hatayı alırsanız, kullanmakta olduğunuz bilinen adın doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.  
  
7. Visual Basic uygulamasını çalıştırın. Çıkarma çağrısı sonuçlarıyla birlikte bir ileti kutusu görüntülenir (145, 76,54).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)
- [COM Uygulamaları ile Tümleştirme Genel Bakış](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
