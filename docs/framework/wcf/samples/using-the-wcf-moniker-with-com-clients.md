---
title: WCF Bilinen Adını COM İstemcileri ile Kullanma
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: f052504648d381d6fb19fb6db0ebb1dd1086ed3c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515725"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a>WCF Bilinen Adını COM İstemcileri ile Kullanma
Bu örnek, Windows Communication Foundation (WCF) hizmet bilinen adını COM tabanlı geliştirme ortamlarına uygulamaları (Office VBA) için Microsoft Office Visual Basic veya Visual Basic 6.0 gibi Web Hizmetleri Tümleştirme için nasıl kullanılacağını gösterir. Bu örnek bir Windows komut dosyası ana bilgisayarı istemci (.vbs) destekleyen bir istemci kitaplığı (.dll) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı (.dll) oluşur. Hizmet hesap makinesi hizmetidir ve COM istemcisi matematik işlemlerini çağıran — ekleme, çıkarma, çarpma ve bölme — hizmet. İleti kutusu windows istemci etkinliği görülebilir.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergeleri Bu konunun sonunda yer alır.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 Hizmet uygulayan bir `ICalculator` sözleşme aşağıdaki kod örneğinde gösterildiği gibi tanımlanır.  
  
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
  
 Örneği için bilinen ad kullanarak üç alternatif yaklaşımlar gösterir:  
  
-   Yazılı Sözleşme – Sözleşme, istemci bilgisayarda bir COM görünür türü olarak kaydedilir.  
  
-   WSDL sözleşme – sözleşmenin bir WSDL Belgesi biçiminde sağlanır.  
  
-   Çalışma zamanında bir meta veri değişimi (MEX) uç noktasından metadata Exchange Sözleşme – Sözleşme alınır.  
  
## <a name="typed-contract"></a>Yazılı sözleşme  
 Bilinen ad yazılı sözleşme ile kullanma için hizmet sözleşmesi için uygun şekilde öznitelikli türleri com ile kayıtlı olması gerekir İlk olarak, bir istemci kullanarak oluşturulmalıdır [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Türü belirtilmiş bir proxy oluşturmak için istemci dizininde bir komut isteminden aşağıdaki komutu çalıştırın.  
  
```  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 Bu sınıf, bir projede eklenmelidir ve proje yapılandırılmalıdır bir COM görünür oluşturmak için derlendiğinde derleme imzalanmış. AssemblyInfo.cs dosyasında aşağıdaki öznitelik eklenmelidir.  
  
```  
[assembly: ComVisible(true)]  
```  
  
 COM görünür türü kullanarak kaydedin projeyi oluşturduktan sonra `regasm` aşağıdaki örnekte gösterildiği gibi.  
  
```  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 Oluşturulan derleme Genel Derleme Önbelleği'ne eklenmesi gerekir. Ancak bu gerekli kesinlikle olmadığında, bu çalışma zamanının bütünleştirilmiş bulma işlemini basitleştirir. Aşağıdaki komut, derleme Genel Derleme Önbelleği'ne ekler.  
  
```  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
>  Hizmet bilinen adı, yalnızca tür kaydı gerektirir ve proxy hizmeti ile iletişim kurmak için kullanmaz.  
  
 ComCalcClient.vbs istemci uygulamanın kullandığı `GetObject` bağlamayı adresini belirtmek için hizmet bilinen adı sözdizimini kullanarak bir proxy hizmeti oluşturun ve hizmet için sözleşme işlevi.  
  
```  
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,   
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 Bilinen ad tarafından kullanılan parametreleri belirtin:  
  
-   Hizmet uç noktası adresi.  
  
-   İstemci uç noktasına bağlanmak için kullanması gereken bağlama. İstemci yapılandırma dosyalarında özel bağlamalar tanımlanabilir, ancak bu durumda, sistem tarafından tanımlanan wsHttpBinding kullanılır. Windows Script Host ile kullanım için özel bağlama Cscript.exe aynı dizine Cscript.exe.config dosyasında tanımlanır.  
  
-   Uç noktada desteklenen sözleşme türü. Bu, oluşturulan ve yukarıda kayıtlı türüdür. Visual Basic komut dosyası türü kesin belirlenmiş bir COM ortam sağlamadığından, sözleşme için bir tanımlayıcı belirtilmelidir. Bu GUID `interfaceID` CalcProxy.tlb hangi görüntülenebilir OLE/COM Nesne Görüntüleyicisi'ni (OleView.exe) gibi COM araçlarını kullanarak. Kesin tür belirtilmiş Office VBA veya Visual Basic 6.0 gibi ortamları için açık bir tür kitaplığı başvuru ekleme ve ardından proxy nesnesinin türü bildirmek yerine sözleşme parametresi kullanılabilir. Bu da istemci uygulama geliştirme sırasında IntelliSense desteği sunar.  
  
 Hizmet bilinen adı proxy örneğiyle çağrılamadığından istemci uygulama, hizmet bilinen adı altyapısında karşılık gelen hizmet işlemleri çağırma sonuçları proxy yöntemleri çağırabilir.  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Örneği çalıştırdığınızda, işlem yanıtı Windows Script Host ileti kutusu penceresinde görüntülenir. Bu, bir WCF Hizmeti ile iletişim kurmak için belirlenmiş bilinen adını kullanarak COM aramaları yapmadan bir COM istemcisi gösterir. Kullanımını COM rağmen istemci uygulama, hizmet ile iletişim yalnızca Web hizmeti çağrıları oluşur.  
  
## <a name="wsdl-contract"></a>WSDL Sözleşmesi  
 WSDL sözleşme bilinen ad kullanmak için istemci kitaplığı kayıt gerekli değil ancak WSDL hizmet sözleşmesini hizmeti için WSDL uç noktasına erişmek için bir tarayıcı kullanarak gibi bir bant dışı mekanizması aracılığıyla alınması gerekir. Bilinen ad, daha sonra bu sözleşme yürütme zamanında erişebilirsiniz.  
  
 ComCalcClient.vbs istemci uygulamanın kullandığı `FileSystemObject` yerel olarak kaydedilmiş bir WSDL dosyasına erişmek için ve daha sonra tekrar kullanır `GetObject` bir proxy hizmeti oluşturmak için işlev.  
  
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
  
-   İstemci bu uç nokta ve bu bağlama tanımlandığı ad alanı ile bağlanmak için kullanması gereken bağlama. Bu durumda, `wsHttpBinding_ICalculator` kullanılır.  
  
-   Sözleşme tanımlayan bir WSDL. Bu durumda serviceWsdl.xml dosyadan okunan dize budur.  
  
-   Sözleşme ad alanı ve adı. WSDL birden fazla sözleşme içeriyor olabileceğinden, bu kimliği gereklidir.  
  
    > [!NOTE]
    >  Varsayılan olarak, her ad alanı için ayrı bir WSDL dosyası WCF hizmetleri oluşturun, kullanın. Bu, WSDL içeri aktarma yapısı kullanımı ile bağlantılıdır. Tek bir WSDL tanımı ad beklediği için bu örnekte gösterildiği gibi hizmeti ya da tek bir ad kullanmalısınız veya ayrı dosyaları el ile birleştirilmesi gerekir.  
  
 Hizmet bilinen adı proxy örneğiyle çağrılamadığından istemci uygulama, hizmet bilinen adı altyapısında karşılık gelen hizmet işlemleri çağırma sonuçları proxy yöntemleri çağırabilir.  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Örneği çalıştırdığınızda, işlem yanıtı Windows Script Host ileti kutusu penceresinde görüntülenir. Bu bir COM istemcisi bir WCF Hizmeti ile iletişim kurmak için WSDL sözleşme bilinen adını kullanarak COM çağrıları yapma gösterir.  
  
## <a name="metadata-exchange-contract"></a>Meta veri değişimi Sözleşmesi  
 WSDL sözleşmesi gibi bilinen ad MEX sözleşme ile kullanmak için istemci kayıt gerekli değil. Hizmet sözleşmesini meta veri değişimi iç kullanımı aracılığıyla yürütme zamanında alınır.  
  
 ComCalcClient.vbs istemci uygulamaya yeniden kullanan `GetObject` bir proxy hizmeti oluşturmak için işlev.  
  
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
  
-   Hizmet meta veri değişimi uç noktası adresi.  
  
-   Hizmet uç noktası adresi.  
  
-   İstemci bu uç nokta ve bu bağlama tanımlandığı ad alanı ile bağlanmak için kullanması gereken bağlama. Bu durumda, `wsHttpBinding_ICalculator` kullanılır.  
  
-   Sözleşme ad alanı ve adı. WSDL birden fazla sözleşme içeriyor olabileceğinden, bu kimliği gereklidir.  
  
 Hizmet bilinen adı proxy örneğiyle çağrılamadığından istemci uygulama, hizmet bilinen adı altyapısında karşılık gelen hizmet işlemleri çağırma sonuçları proxy yöntemleri çağırabilir.  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Örneği çalıştırdığınızda, işlem yanıtı Windows Script Host ileti kutusu penceresinde görüntülenir. Bu ad, bir WCF Hizmeti ile iletişim kurmak için MEX sözleşme kullanarak COM çağrıları yapma bir COM istemcisi gösterir.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Ayarlama ve örneği oluşturmak için  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Bir Visual Studio Komut İstemi'nden dile özgü klasörü altında \client\bin klasörü açın.  
  
    > [!NOTE]
    >  Kullanıyorsanız [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7 veya Windows Server 2008 R2'de, yönetici ayrıcalıklarına sahip komut isteminden çalıştırdığınızdan emin olun.  
  
4.  Yazın `tlbexp.exe client.dll /out:CalcProxy.tlb` dll tlb dosyasına dışarı aktarmak için. Bir "tür kitaplığı dışarı Aktarıcı Uyarısı" bekleniyordu, ancak genel tür gerekli olmadığından bir sorun değildir.  
  
5.  Yazın `regasm.exe /tlb:CalcProxy.tlb client.dll` türleri com ile kaydetmek için Bir "tür kitaplığı dışarı Aktarıcı Uyarısı" bekleniyordu, ancak genel tür gerekli olmadığından bir sorun değildir.  
  
6.  Yazın `gacutil.exe /i client.dll` derlemesi Genel Derleme Önbelleği'ne ekleme.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için  
  
1.  Hizmeti şu adreste yazarak bir tarayıcı kullanarak erişebileceğiniz test: `http://localhost/servicemodelsamples/service.svc`. Yanıtta bir onay sayfası gösterilmelidir.  
  
2.  ComCalcClient.vbs \client, dile özgü klasörü altında çalıştırın. İleti kutusu windows istemci etkinliği görüntülenir.  
  
3.  İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Hizmet bilgisayarda ServiceModelSamples adlı sanal bir dizin oluşturun. Disk dizini ve sanal dizin oluşturmak için örnek ile dahil Setupvroot.bat betiği kullanılabilir.  
  
2.  Hizmet program dosyaları %SystemDrive%\Inetpub\wwwroot\servicemodelsamples hizmeti bilgisayarında ServiceModelSamples sanal dizinine kopyalayın. \Bin dizinine dosyaları eklemeyi unutmayın.  
  
3.  Dile özgü klasörü altında \client klasöründen istemci komut dosyasını istemci bilgisayara kopyalayın.  
  
4.  Betik dosyasında adresi uç nokta tanımı hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin. "Localhost" yönelik tüm başvuruları adresindeki bir tam etki alanı adı ile değiştirin.  
  
5.  WSDL dosyasını istemci bilgisayara kopyalayın. WSDL dosyasındaki serviceWsdl.xml, "localhost" yönelik tüm başvuruları adresindeki bir tam etki alanı adı ile değiştirin.  
  
6.  Dile özgü klasörü altında \client\bin klasör Client.dll kitaplık istemci bilgisayardaki bir dizine kopyalayın.  
  
7.  Bir komut istemi'nden istemci bilgisayarda, hedef dizine gidin. Kullanıyorsanız [!INCLUDE[wv](../../../../includes/wv-md.md)] veya [!INCLUDE[lserver](../../../../includes/lserver-md.md)], komut istemini yönetici olarak çalıştırdığınızdan emin olun.  
  
8.  Yazın `tlbexp.exe client.dll /out:CalcProxy.tlb` dll tlb dosyasına dışarı aktarmak için. Bir "tür kitaplığı dışarı Aktarıcı Uyarısı" bekleniyordu, ancak genel tür gerekli olmadığından bir sorun değildir.  
  
9. Yazın `regasm.exe /tlb:CalcProxy.tlb client.dll` türleri com ile kaydetmek için Bu yolu içeren klasöre ayarlandı olun `regasm.exe` komutu çalıştırmadan önce.  
  
10. Yazın `gacutil.exe /i client.dll` derlemesi Genel Derleme Önbelleği'ne ekleme. Bu yolu içeren klasöre ayarlandı olun `gacutil.exe` komutu çalıştırmadan önce.  
  
11. Test bir tarayıcı kullanarak istemci bilgisayardan hizmete erişebilir.  
  
12. İstemci bilgisayarda ComCalcClient.vbs başlatın.  
  
#### <a name="to-clean-up-after-the-sample"></a>Sonra örnek temizlemek için  
  
-   Güvenlik nedenleriyle, sanal dizin tanımını ve örneklerle tamamladığınızda Kurulumu adımları verilen izinler kaldırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.
