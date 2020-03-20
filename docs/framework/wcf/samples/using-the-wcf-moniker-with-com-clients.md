---
title: WCF Bilinen Adını COM İstemcileri ile Kullanma
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: d4d812c59a504f365eb3ad63ddd45ba5a66296e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183229"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a>WCF Bilinen Adını COM İstemcileri ile Kullanma
Bu örnek, Windows Communication Foundation (WCF) hizmet lakabının, Web hizmetlerini Microsoft Office Visual Basic for Applications (Office VBA) veya Visual Basic 6.0 gibi COM tabanlı geliştirme ortamlarına entegre etmek için nasıl kullanılacağını göstermektedir. Bu örnek, Bir Windows Script Host istemcisi (.vbs), destekleyen istemci kitaplığı (.dll) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığından (.dll) oluşur. Hizmet bir hesap makinesi hizmetidir ve COM istemcisi hizmette matematik işlemlerini çağırır-Ekle, Çıkar, Çarpve Böl- çağırır. İstemci etkinliği ileti kutusu pencerelerinde görünür.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 Hizmet, aşağıdaki `ICalculator` kod örneğinde gösterildiği gibi tanımlanan bir sözleşme uygular.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 Örnek, lakabı kullanmak için üç alternatif yaklaşımı göstermektedir:  
  
- Dakti-iş sözleşmesi – Sözleşme istemci bilgisayarda COM görünür türü olarak kaydedilir.  
  
- WSDL sözleşmesi – Sözleşme bir WSDL belgesi şeklinde sağlanır.  
  
- Meta veri değişimi sözleşmesi – Sözleşme çalışma zamanında Meta veri değişimi (MEX) bitiş noktasından alınır.  
  
## <a name="typed-contract"></a>Yazılı Sözleşme  
 Lakabı yazılı sözleşme kullanımıyla kullanmak için, hizmet sözleşmesi için uygun şekilde atfedilen türlerin COM'a kaydedilmesi gerekir. İlk olarak, bir istemci [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)kullanılarak oluşturulmalıdır. Yazılan proxy'yi oluşturmak için istemci dizinindeki bir komut isteminden aşağıdaki komutu çalıştırın.  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 Bu sınıf bir projeye dahil edilmeli ve proje derlendiğinde COM görünür, imzalı bir derleme oluşturacak şekilde yapılandırılmalıdır. Aşağıdaki öznitelik AssemblyInfo.cs dosyasına eklenmelidir.  
  
```csharp
[assembly: ComVisible(true)]  
```  
  
 Projeyi yaptıktan sonra, aşağıdaki örnekte `regasm` gösterildiği gibi kullanarak COM-görünür türlerini kaydedin.  
  
```console  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 Oluşturulan derleme, Genel Montaj Önbelleğine eklenmelidir. Kesinlikle gerekli olmasa da, bu, derlemeyi bulma çalışma zamanı işlemini kolaylaştırır. Aşağıdaki komut, derlemeyi Genel Montaj Önbelleğine ekler.  
  
```console  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
> Hizmet lakabı yalnızca tür kaydı gerektirir ve hizmetle iletişim kurmak için proxy'yi kullanmaz.  
  
 ComCalcClient.vbs istemci uygulaması, hizmetin adresini, bağlamasını ve sözleşmesini belirtmek için hizmet ad sözdizimini kullanarak hizmet için bir proxy oluşturmak için `GetObject` işlevi kullanır.  
  
```vbscript
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 Takma alakadar kullanılan parametreler şunları belirtir:  
  
- Hizmet bitiş noktasının adresi.  
  
- İstemcinin bu uç noktaya bağlanmak için kullanması gereken bağlama. Bu durumda, sistem tanımlı wsHttpBinding istemci yapılandırma dosyalarında özel bağlamalar tanımlanabilir rağmen kullanılır. Windows Script Ana Bilgisayarı'nda kullanım için özel bağlama, Cscript.exe ile aynı dizinde bir Cscript.exe.config dosyasında tanımlanır.  
  
- Bitiş noktasında desteklenen sözleşmenin türü. Bu, yukarıda oluşturulan ve kaydedilmiş türdür. Visual Basic komut dosyası güçlü bir şekilde yazılmış bir COM ortamı sağlamadığından, sözleşme için bir tanımlayıcı belirtilmelidir. Bu GUID `interfaceID` CalcProxy.tlb, OLE / COM Nesne Görüntüleyici (OleView.exe) gibi COM araçları kullanılarak görüntülenebilir. Office VBA veya Visual Basic 6.0 gibi güçlü bir şekilde yazılan ortamlar için, tür kitaplığına açık bir başvuru eklemek ve ardından proxy nesnesinin türünü bildiren sözleşme parametresi yerine kullanılabilir. Bu da istemci uygulama geliştirme sırasında IntelliSense desteği sağlar.  
  
 Hizmet lakabını içeren proxy örneğini oluşturan istemci uygulaması, proxy'deki yöntemleri arayabilir ve bu da servis takma altyapısının ilgili hizmet işlemlerini çağırmasıyla sonuçlanır.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Örneği çalıştırdığınızda, işlem yanıtı bir Windows Script Ana Bilgisayar ileti kutusu penceresinde görüntülenir. Bu, bir WCF hizmetiyle iletişim kurmak için yazılan takma ad kullanarak COM çağrıları yapan bir COM istemcisini gösterir. Müşteri uygulamasında COM kullanımına rağmen, hizmetle iletişim yalnızca Web servis çağrılarından oluşur.  
  
## <a name="wsdl-contract"></a>WSDL Sözleşmesi  
 WsDL sözleşmesi yle takma adı kullanmak için istemci kitaplığı kaydı gerekmez, ancak hizmet için WSDL sözleşmesi, hizmet için WSDL bitiş noktasına erişmek için bir tarayıcı kullanmak gibi bant dışı bir mekanizma aracılığıyla alınmalıdır. Takma adı daha sonra yürütme sırasında bu sözleşmeerişebilirsiniz.  
  
 ComCalcClient.vbs istemci uygulaması `FileSystemObject` yerel olarak kaydedilen WSDL dosyasına erişmek `GetObject` için kullanır ve sonra tekrar hizmet için bir proxy oluşturmak için işlevi kullanır.  
  
```vbscript  
' Open the WSDL contract file and read it all into the wsdlContract string  
Const ForReading = 1  
Set objFSO = CreateObject("Scripting.FileSystemObject")  
Set objFile = objFSO.OpenTextFile("serviceWsdl.xml", ForReading)  
wsdlContract = objFile.ReadAll  
objFile.Close  
  
' Create a string for the service moniker including the content of the WSDL contract file  
wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
```  
  
 Takma alakadar kullanılan parametreler şunları belirtir:  
  
- Hizmet bitiş noktasının adresi.  
  
- İstemcinin bu uç noktayla bağlantı kurmak için kullanması gereken bağlama ve bu bağlamanın tanımlandığı ad alanı. Bu durumda, `wsHttpBinding_ICalculator` kullanılır.  
  
- Sözleşmeyi tanımlayan WSDL. Bu durumda serviceWsdl.xml dosyasından okunan dizedir.  
  
- Sözleşmenin adı ve ad alanı. WSDL birden fazla sözleşme içerebileceğinden bu tanımlama gereklidir.  
  
    > [!NOTE]
    > Varsayılan olarak, WCF hizmetleri, kullanıldığı her ad alanı için ayrı WSDL dosyaları oluşturur. Bunlar WSDL alma yapısının kullanımıyla bağlantılıdır. Takma ad tek bir WSDL tanımı beklediğinden, hizmetin bu örnekte gösterildiği gibi tek bir ad alanı kullanması veya ayrı dosyaların el ile birleştirilmesi gerekir.  
  
 Hizmet lakabını içeren proxy örneğini oluşturan istemci uygulaması, proxy'deki yöntemleri arayabilir ve bu da servis takma altyapısının ilgili hizmet işlemlerini çağırmasıyla sonuçlanır.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Örneği çalıştırdığınızda, işlem yanıtı bir Windows Script Ana Bilgisayar ileti kutusu penceresinde görüntülenir. Bu, bir WCF hizmetiyle iletişim kurmak için WSDL sözleşmesi olan takma ad kullanan com istemcisinin COM aramaları yaptığını gösterir.  
  
## <a name="metadata-exchange-contract"></a>Meta veri değişim sözleşmesi  
 WSDL sözleşmesinde olduğu gibi, bir MEX sözleşmesi ile takma takma kullanmak için, hiçbir istemci kaydı gereklidir. Hizmet sözleşmesi, Meta veri exchange'in dahili kullanımı yoluyla yürütme sırasında alınır.  
  
 ComCalcClient.vbs istemci uygulaması yine `GetObject` hizmet için bir proxy oluşturmak için işlevi kullanır.  
  
```vbscript  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 Takma alakadar kullanılan parametreler şunları belirtir:  
  
- Hizmet meta veri alışverişi bitiş noktasının adresi.  
  
- Hizmet bitiş noktasının adresi.  
  
- İstemcinin bu uç noktayla bağlantı kurmak için kullanması gereken bağlama ve bu bağlamanın tanımlandığı ad alanı. Bu durumda, `wsHttpBinding_ICalculator` kullanılır.  
  
- Sözleşmenin adı ve ad alanı. WSDL birden fazla sözleşme içerebileceğinden bu tanımlama gereklidir.  
  
 Hizmet lakabını içeren proxy örneğini oluşturan istemci uygulaması, proxy'deki yöntemleri arayabilir ve bu da servis takma altyapısının ilgili hizmet işlemlerini çağırmasıyla sonuçlanır.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Örneği çalıştırdığınızda, işlem yanıtı bir Windows Script Ana Bilgisayar ileti kutusu penceresinde görüntülenir. Bu, bir COM istemcisinin bir WCF hizmetiyle iletişim kurmak için bir MEX sözleşmesi olan takma ad kullanarak COM aramaları yaptığını gösterir.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Örneği ayarlamak ve oluşturmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Visual Studio için Geliştirici Komut Komut Ustem'den, dile özgü klasörün altında \client\bin klasörünü açın.  
  
    > [!NOTE]
    > Windows Vista, Windows Server 2008, Windows 7 veya Windows Server 2008 R2 kullanıyorsanız, komut istemini yönetici ayrıcalıklarıyla çalıştırdığınızdan emin olun.  
  
4. tlb `tlbexp.exe client.dll /out:CalcProxy.tlb` dosyasına dll'yi dışa aktarmak için yazın. Genel tür gerekli olmadığından bir "Tür kitaplığı ihracatçısı uyarısı" beklenir, ancak bir sorun değildir.  
  
5. Türleri `regasm.exe /tlb:CalcProxy.tlb client.dll` COM'a kaydetmek için yazın. Genel tür gerekli olmadığından bir "Tür kitaplığı ihracatçısı uyarısı" beklenir, ancak bir sorun değildir.  
  
6. `gacutil.exe /i client.dll` Derlemeyi Genel Montaj Önbelleğine eklemek için yazın.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için  
  
1. Aşağıdaki adresi yazarak bir tarayıcı kullanarak hizmete erişebileceğinizi test edin: `http://localhost/servicemodelsamples/service.svc`. Yanıt olarak bir onay sayfası görüntülenmelidir.  
  
2. ComCalcClient.vbs'yi \client'dan, dile özgü klasörün altından çalıştırın. İstemci etkinliği ileti kutusu pencerelerinde görüntülenir.  
  
3. İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.  
  
#### <a name="to-run-the-sample-across-computers"></a>Örneği bilgisayarlarda çalıştırmak için  
  
1. Hizmet bilgisayarında ServiceModelSamples adlı sanal bir dizin oluşturun. Örnekle birlikte verilen Setupvroot.bat komut dosyası, disk dizini ve sanal dizini oluşturmak için kullanılabilir.  
  
2. Hizmet programı dosyalarını %SystemDrive%\Inetpub\wwwroot\servicemodelsamples'ten serviceModelSamples sanal dizinine kopyalayın. Dosyaları \bin dizinine eklediğinizden emin olun.  
  
3. İstemci komut dosyası dosyasını dile özgü klasörün altındaki \client klasöründen istemci bilgisayarına kopyalayın.  
  
4. Komut dosyası dosyasında, hizmetinyeni adresiyle eşleşecek şekilde bitiş noktası tanımının adres değerini değiştirin. "Localhost" için yapılan başvuruları adreste tam nitelikli bir etki alanı adı ile değiştirin.  
  
5. WSDL dosyasını istemci bilgisayara kopyalayın. WSDL dosyasında serviceWsdl.xml, "localhost" için yapılan tüm başvuruları adreste tam nitelikli bir etki alanı adı ile değiştirin.  
  
6. İstemci.dll kitaplığını \client\bin klasöründen, dile özgü klasörün altından istemci bilgisayardaki bir dizine kopyalayın.  
  
7. Komut isteminden istemci bilgisayardaki hedef dizine gidin. Windows Vista veya Windows Server 2008 kullanıyorsanız, komut istemini Administrator olarak çalıştırkullandığınızdan emin olun.  
  
8. tlb `tlbexp.exe client.dll /out:CalcProxy.tlb` dosyasına dll'yi dışa aktarmak için yazın. Genel tür gerekli olmadığından bir "Tür kitaplığı ihracatçısı uyarısı" beklenir, ancak bir sorun değildir.  
  
9. Türleri `regasm.exe /tlb:CalcProxy.tlb client.dll` COM'a kaydetmek için yazın. Komutu çalıştırmadan önce yolun içeren `regasm.exe` klasöre ayarlandığını emin olun.  
  
10. `gacutil.exe /i client.dll` Derlemeyi Genel Montaj Önbelleğine eklemek için yazın. Komutu çalıştırmadan önce yolun içeren `gacutil.exe` klasöre ayarlandığını emin olun.  
  
11. Bir tarayıcı kullanarak istemci bilgisayardan hizmete erişebileceğinizi test edin.  
  
12. İstemci bilgisayarında ComCalcClient.vbs'i başlatın.  
  
#### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
- Güvenlik amacıyla, örnekleri bitirdikten sonra kurulum adımlarında verilen sanal dizin tanımını ve izinleri kaldırın.  
