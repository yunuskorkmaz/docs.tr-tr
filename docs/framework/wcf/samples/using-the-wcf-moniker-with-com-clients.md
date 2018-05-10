---
title: WCF Bilinen Adını COM İstemcileri ile Kullanma
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: 6d47b9c655db932bb9a4243533fbd01bcf25e0df
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="using-the-wcf-moniker-with-com-clients"></a>WCF Bilinen Adını COM İstemcileri ile Kullanma
Bu örnek, Windows Communication Foundation (WCF) hizmet bilinen adı Microsoft Office Visual Basic for Applications (Office VBA) veya Visual Basic 6.0 gibi COM tabanlı geliştirme ortamlara Web services tümleştirme için nasıl kullanılacağını gösterir. Bu örnek bir Windows Script Host istemci (.vbs) destekleyen bir istemci kitaplığı (.dll) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı (.dll) oluşur. Hizmeti bir hesaplama hizmetidir ve COM istemcisi matematik işlemleri çağırır — ekleme, çıkarma, çarpma ve bölme — hizmet üzerinde. İstemci etkinliği ileti kutusu pencerelerinde görünür olur.  
  
> [!NOTE]
>  Kurulum yordam ve yapılandırma yönergeleri Bu örneği için bu konunun sonunda yer alır.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 Hizmet uygulayan bir `ICalculator` aşağıdaki kod örneğinde gösterildiği gibi tanımlanan sözleşme.  
  
```  
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
  
 Örnek adı kullanılarak üç alternatif yaklaşımlar gösterir:  
  
-   Yazılı Sözleşme – Sözleşme, istemci bilgisayardaki COM görünebilir tür olarak kaydedilir.  
  
-   WSDL Sözleşme – Sözleşme WSDL Belgesi biçiminde sağlanır.  
  
-   Meta veri değişimi Sözleşme – Sözleşme çalışma zamanında meta veri değişimi (MEX) uç noktasından alınır.  
  
## <a name="typed-contract"></a>Yazılı sözleşme  
 Ad bir yazılı sözleşme ile kullanmayı, hizmet sözleşmesi için uygun şekilde öznitelikli türleri com ile kayıtlı olması gerekir İlk olarak, bir istemci kullanarak oluşturulması gerektiğini [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Yazılı proxy oluşturmak için istemci dizininde bir komut isteminden aşağıdaki komutu çalıştırın.  
  
```  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 Bu sınıf bir proje ile eklenmelidir ve projeyi yapılandırılmalıdır bir COM görünür oluşturmak için derlendiğinde derleme imzalanmamış. Aşağıdaki öznitelik AssemblyInfo.cs dosyasında bulunması gerekir.  
  
```  
[assembly: ComVisible(true)]  
```  
  
 COM görünebilir türler kullanarak kaydedin projesi oluşturduktan sonra `regasm` aşağıdaki örnekte gösterildiği gibi.  
  
```  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 Oluşturulan derleme genel derleme önbelleği eklenmesi gerekir. Kesinlikle olmadığında gerekli ancak bu çalışma zamanı derlemesi bulma işlemini basitleştirir. Aşağıdaki komut derlemeyi genel derleme önbelleği ekler.  
  
```  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
>  Hizmet bilinen adı yalnızca türü kayıt gerektirir ve proxy hizmeti ile iletişim kurmak için kullanmaz.  
  
 ComCalcClient.vbs istemci uygulamanın kullandığı `GetObject` işlev bağlama, adresini belirtmek için hizmet adının sözdizimi kullanarak hizmeti için bir proxy oluşturmak ve hizmet için sözleşme.  
  
```  
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,   
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 Bilinen ad tarafından kullanılan parametreleri belirtin:  
  
-   Hizmet uç noktası adresi.  
  
-   İstemci bu bitiş noktası ile bağlanmak için kullanması gereken bağlama. Özel bağlamalar istemci yapılandırma dosyalarında tanımlanabilir ancak bu durumda, sistem tarafından tanımlanan wsHttpBinding kullanılır. Windows Script Host ile kullanım için özel bağlama Cscript.exe aynı dizine Cscript.exe.config dosyasında tanımlanır.  
  
-   Uç noktada desteklenen sözleşme türü. Bu, oluşturulan ve yukarıdaki kayıtlı türüdür. Visual Basic komut dosyası türü kesin belirlenmiş bir COM ortamı sağlamadığından sözleşme için bir tanımlayıcı belirtilmelidir. Bu GUID `interfaceID` CalcProxy.tlb hangi görüntülenebilir COM OLE/COM Nesne Görüntüleyicisi'ni (OleView.exe) gibi araçları kullanarak. Kesin türü belirtilmiş Office VBA veya Visual Basic 6.0 gibi ortamları için tür kitaplığı için açık bir başvuru ekleyerek ve proxy nesne türünü bildirme yerine sözleşme parametresinde kullanılabilir. Bu aynı zamanda istemci uygulama geliştirme sırasında IntelliSense desteği sağlar.  
  
 Hizmet adının proxy örneğiyle oluşturulmamalıdır istemci uygulaması, karşılık gelen hizmet işlemlerini çağırma hizmet bilinen adı altyapısında sonuçları proxy yöntemleri çağırabilir.  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 İşlem yanıtı örneği çalıştırdığınızda, Windows Script Host ileti kutusu penceresinde görüntülenir. Bu bir WCF Hizmeti ile iletişim kurmak için yazılan ad kullanarak COM çağrıları yapma COM istemcisi gösterir. Kullanımı COM rağmen istemci uygulamasında, yalnızca Web hizmeti çağrıları hizmet ile iletişim oluşur.  
  
## <a name="wsdl-contract"></a>WSDL sözleşme  
 Ad WSDL sözleşme ile kullanmak için istemci kitaplığı kayıt gerekli değil ancak hizmet WSDL sözleşmesini hizmeti WSDL uç noktasına erişmek için bir tarayıcı kullanarak gibi bir bant dışı mekanizması aracılığıyla alınması gerekir. Ad, daha sonra bu sözleşme, yürütme esnasında erişebilirsiniz.  
  
 ComCalcClient.vbs istemci uygulamanın kullandığı `FileSystemObject` yerel olarak kaydedilmiş WSDL dosyaya erişmek için ve daha sonra tekrar kullanır `GetObject` hizmeti için bir proxy oluşturmak için işlevi.  
  
```  
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
  
 Bilinen ad tarafından kullanılan parametreleri belirtin:  
  
-   Hizmet uç noktası adresi.  
  
-   İstemci bu uç hem de bu bağlamayı tanımlandığı ad alanı ile bağlanmak için kullanması gereken bağlama. Bu durumda, `wsHttpBinding_ICalculator` kullanılır.  
  
-   Sözleşmesini tanımlayan WSDL. Bu durumda serviceWsdl.xml dosyadan okunan dize budur.  
  
-   Ad alanı sözleşmenin ve adını. WSDL birden fazla sözleşme içerebileceğinden bu kimliği gereklidir.  
  
    > [!NOTE]
    >  Varsayılan olarak, her ad alanı için ayrı WSDL dosyası WCF hizmetleri oluşturmak, kullanın. Bunlar WSDL içe aktarma yapı kullanımı ile bağlanır. Tek bir WSDL tanımı ad beklediği için bu örnekte gösterildiği gibi hizmet ya da tek bir ad alanı kullanmalısınız veya ayrı dosyalarını el ile birleştirilmesi gerekir.  
  
 Hizmet adının proxy örneğiyle oluşturulmamalıdır istemci uygulaması, karşılık gelen hizmet işlemlerini çağırma hizmet bilinen adı altyapısında sonuçları proxy yöntemleri çağırabilir.  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 İşlem yanıtı örneği çalıştırdığınızda, Windows Script Host ileti kutusu penceresinde görüntülenir. Bu ad, bir WCF Hizmeti ile iletişim kurmak için WSDL sözleşmeyle kullanarak COM aramaları yapmadan COM istemcisi gösterir.  
  
## <a name="metadata-exchange-contract"></a>Meta veri değişimi sözleşme  
 WSDL sözleşme olarak bilinen ad MEX sözleşme ile kullanmak için istemci kayıt gerekli değil. Hizmet sözleşmesini meta veri değişimi iç kullanımı aracılığıyla yürütme zamanında alınır.  
  
 Yeniden ComCalcClient.vbs istemci uygulamanın kullandığı `GetObject` hizmeti için bir proxy oluşturmak için işlevi.  
  
```  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 Bilinen ad tarafından kullanılan parametreleri belirtin:  
  
-   Hizmet meta verileri exchange uç adresidir.  
  
-   Hizmet uç noktası adresi.  
  
-   İstemci bu uç hem de bu bağlamayı tanımlandığı ad alanı ile bağlanmak için kullanması gereken bağlama. Bu durumda, `wsHttpBinding_ICalculator` kullanılır.  
  
-   Ad alanı sözleşmenin ve adını. WSDL birden fazla sözleşme içerebileceğinden bu kimliği gereklidir.  
  
 Hizmet adının proxy örneğiyle oluşturulmamalıdır istemci uygulaması, karşılık gelen hizmet işlemlerini çağırma hizmet bilinen adı altyapısında sonuçları proxy yöntemleri çağırabilir.  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 İşlem yanıtı örneği çalıştırdığınızda, Windows Script Host ileti kutusu penceresinde görüntülenir. Bu ad, bir WCF Hizmeti ile iletişim kurmak için MEX sözleşmeyle kullanarak COM aramaları yapmadan COM istemcisi gösterir.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Ayarlamak ve örneği oluşturmak için  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Visual Studio komut isteminden, dile özgü klasörü altında \client\bin klasörünü açın.  
  
    > [!NOTE]
    >  Kullanıyorsanız [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7 veya Windows Server 2008 R2, komut istemini yönetici ayrıcalıklarıyla çalıştırın emin olun.  
  
4.  Yazın `tlbexp.exe client.dll /out:CalcProxy.tlb` dll tlb dosyaya vermek için. Bir "tür kitaplığı dışarı Aktarıcı Uyarısı" bekleniyordu, ancak genel tür gerekli olmadığı için bir sorun değildir.  
  
5.  Yazın `regasm.exe /tlb:CalcProxy.tlb client.dll` türleri com ile kaydetmek için Bir "tür kitaplığı dışarı Aktarıcı Uyarısı" bekleniyordu, ancak genel tür gerekli olmadığı için bir sorun değildir.  
  
6.  Yazın `gacutil.exe /i client.dll` derleme genel derleme önbelleğine eklemek için.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Aynı bilgisayara örneği çalıştırmak için  
  
1.  Hizmeti aşağıdaki adresi yazarak bir tarayıcı kullanarak erişebilirsiniz test: `http://localhost/servicemodelsamples/service.svc`. Bir onay sayfasına yanıtta görüntülenmesi gerekir.  
  
2.  Dile özgü klasörü altında \client ComCalcClient.vbs çalıştırın. İstemci etkinliği ileti kutusu Windows'da görüntülenir.  
  
3.  İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Hizmet bilgisayarda ServiceModelSamples adlı bir sanal dizini oluşturun. Örnekle dahil Setupvroot.bat komut dosyası disk dizini ve sanal dizini oluşturmak için kullanılabilir.  
  
2.  Hizmet program dosyalarını %SystemDrive%\Inetpub\wwwroot\servicemodelsamples hizmeti bilgisayarında ServiceModelSamples sanal dizinine kopyalayın. Dosyaları \bin dizinine eklediğinizden emin olun.  
  
3.  İstemci komut dosyası \client klasöründen dile özgü klasörü altında istemci bilgisayara kopyalayın.  
  
4.  Komut dosyasında hizmetinizin yeni adresi ile eşleşmesi için uç nokta tanımındaki adresi değerini değiştirin. Tüm başvuruları "localhost" adresi bir tam etki alanı adıyla değiştirin.  
  
5.  WSDL dosyasını istemci bilgisayara kopyalayın. WSDL dosyasında serviceWsdl.xml, "localhost" yönelik tüm başvuruları adresindeki bir tam etki alanı adı ile değiştirin.  
  
6.  Dile özgü klasörü altındaki \client\bin klasöründen Client.dll kitaplığı istemci bilgisayarda bir dizine kopyalayın.  
  
7.  Bir komut isteminden, istemci bilgisayarda, hedef dizinine gidin. Kullanıyorsanız [!INCLUDE[wv](../../../../includes/wv-md.md)] veya [!INCLUDE[lserver](../../../../includes/lserver-md.md)], komut istemini yönetici olarak çalıştırdığınızdan emin olun.  
  
8.  Yazın `tlbexp.exe client.dll /out:CalcProxy.tlb` dll tlb dosyaya vermek için. Bir "tür kitaplığı dışarı Aktarıcı Uyarısı" bekleniyordu, ancak genel tür gerekli olmadığı için bir sorun değildir.  
  
9. Yazın `regasm.exe /tlb:CalcProxy.tlb client.dll` türleri com ile kaydetmek için Bu yolu içeren klasöre ayarlanmış olun `regasm.exe` komutu çalıştırmadan önce.  
  
10. Yazın `gacutil.exe /i client.dll` derleme genel derleme önbelleğine eklemek için. Bu yolu içeren klasöre ayarlanmış olun `gacutil.exe` komutu çalıştırmadan önce.  
  
11. Test, hizmet istemci bilgisayar ile bir tarayıcı kullanarak erişebilirsiniz.  
  
12. İstemci bilgisayarda ComCalcClient.vbs başlatın.  
  
#### <a name="to-clean-up-after-the-sample"></a>Örnek sonra temizlemek için  
  
-   Güvenlik nedeniyle, sanal dizin tanımı ve örnekleri ile işiniz bittiğinde Kurulum adımlarında'ı izinler kaldırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.
