---
title: WCF Bilinen Adını COM İstemcileri ile Kullanma
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: 321d59285b0ef86e4631634d90229a0d8e79657b
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424715"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a>WCF Bilinen Adını COM İstemcileri ile Kullanma
Bu örnek, Web hizmetlerini Microsoft Office Visual Basic for Applications (Office VBA) veya Visual Basic 6,0 gibi COM tabanlı geliştirme ortamlarında bütünleştirmek için Windows Communication Foundation (WCF) hizmet bilinen adının nasıl kullanılacağını gösterir. Bu örnek, bir Windows betik ana istemcisi (. vbs), destekleyici istemci kitaplığı (. dll) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı (. dll) içerir. Hizmet bir Hesaplayıcı hizmetidir ve COM istemcisi, hizmet üzerinde matematik işlemlerini (ekleme, çıkarma, çarpma ve bölme) çağırır. İstemci etkinliği ileti kutusu penceresinde görünür.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 Hizmet, aşağıdaki kod örneğinde gösterildiği gibi tanımlanan bir `ICalculator` sözleşme uygular.  
  
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
  
 Örnek, bilinen adı kullanmanın üç farklı yaklaşımını gösterir:  
  
- Yazılı sözleşme – sözleşme, istemci bilgisayarda COM görünebilir bir tür olarak kaydedilir.  
  
- WSDL sözleşmesi – sözleşme, WSDL belgesi biçiminde sağlanır.  
  
- Meta veri değişimi sözleşmesi – sözleşme, meta veri değişimi (MEX) uç noktasından çalışma zamanında alınır.  
  
## <a name="typed-contract"></a>Yazılı sözleşme  
 Bilinen bir sözleşme kullanımıyla bilinen adı kullanmak için, hizmet sözleşmesi için uygun şekilde öznitelikli türler COM ile kaydedilmelidir. İlk olarak, bir istemcinin [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)kullanılarak oluşturulması gerekir. Yazılan proxy 'yi oluşturmak için istemci dizinindeki bir komut isteminden aşağıdaki komutu çalıştırın.  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 Bu sınıf bir projeye dahil edilmelidir ve derlendikten sonra proje, COM görünebilir ve imzalı bir derleme oluşturacak şekilde yapılandırılmalıdır. Aşağıdaki öznitelik AssemblyInfo.cs dosyasına eklenmelidir.  
  
```csharp
[assembly: ComVisible(true)]  
```  
  
 Projeyi oluşturduktan sonra, aşağıdaki örnekte gösterildiği gibi `regasm` kullanarak COM görünebilir türleri kaydedin.  
  
```console  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 Oluşturulan bütünleştirilmiş kod, genel derleme önbelleğine eklenmelidir. Kesinlikle gerekli olmasa da, derlemeyi bulma çalışma zamanının sürecini basitleştirir. Aşağıdaki komut, derlemeyi genel derleme önbelleğine ekler.  
  
```console  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
> Hizmet bilinen adı yalnızca tür kaydı gerektirir ve hizmetle iletişim kurmak için proxy kullanmaz.  
  
 ComCalcClient. vbs istemci uygulaması, hizmet için bir proxy oluşturmak üzere `GetObject` işlevini kullanır ve hizmetin adresini, bağlamayı ve sözleşmesini belirtmek için hizmet bilinen kullanım sözdizimini kullanır.  
  
```vbscript
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,   
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 Bilinen ad tarafından kullanılan parametreler şunları belirtir:  
  
- Hizmet uç noktasının adresi.  
  
- İstemcinin bu uç noktayla bağlanmak için kullanması gereken bağlama. Bu durumda, sistem tarafından tanımlanan wsHttpBinding, istemci yapılandırma dosyalarında özel bağlamalar tanımlanbilse de kullanılır. Windows komut dosyası ana bilgisayarı ile kullanmak için özel bağlama, cscript. exe ile aynı dizindeki bir cscript. exe. config dosyasında tanımlanır.  
  
- Uç noktada desteklenen sözleşmenin türü. Bu, yukarıda oluşturulup kaydedilen türdür. Visual Basic betiği kesin türü belirtilmiş bir COM ortamı sağlamadığından, sözleşmeye yönelik bir tanımlayıcı belirtilmelidir. Bu GUID, OLE/COM Nesne Görüntüleyicisi (OleView. exe) gibi COM araçları kullanılarak görüntülenebilen CalcProxy. tlb dosyasından `interfaceID`. Office VBA veya Visual Basic 6,0 gibi türü kesin belirlenmiş ortamlarda, tür kitaplığına açık bir başvuru eklemek ve ardından Proxy nesnesinin türünü bildirmek, sözleşme parametresinin yerine kullanılabilir. Bu Ayrıca, istemci uygulama geliştirme sırasında IntelliSense desteği sağlar.  
  
 Proxy örneğinin hizmet bilinen adıyla oluşturulması, istemci uygulama proxy üzerinde Yöntemler çağırabilir ve bu da hizmet bilinen hizmet işlemlerini çağıran hizmet adı altyapısına neden olur.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Örneği çalıştırdığınızda, işlem yanıtı bir Windows komut dosyası ana ileti kutusu penceresinde görüntülenir. Bu, bir WCF hizmeti ile iletişim kurmak için yazılan bilinen adı kullanarak COM çağrıları yapan bir COM istemcisini gösterir. İstemci uygulamasında COM kullanımına rağmen hizmetle iletişim yalnızca Web hizmeti çağrılarından oluşur.  
  
## <a name="wsdl-contract"></a>WSDL sözleşmesi  
 Bilinen adı bir WSDL sözleşmesiyle kullanmak için, hiçbir istemci kitaplığı kaydı gerekmez, ancak hizmet için WSDL sözleşmesinin, hizmet için WSDL uç noktasına erişmek üzere bir tarayıcı kullanma gibi bir bant dışı mekanizmadan alınması gerekir. Bilinen ad daha sonra bu sözleşmeye yürütme zamanında erişebilir.  
  
 ComCalcClient. vbs istemci uygulaması, yerel olarak kaydedilen WSDL dosyasına erişmek için `FileSystemObject` kullanır ve ardından hizmet için bir proxy oluşturmak üzere `GetObject` işlevini yeniden kullanır.  
  
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
  
 Bilinen ad tarafından kullanılan parametreler şunları belirtir:  
  
- Hizmet uç noktasının adresi.  
  
- İstemcinin bu uç nokta ile bağlanmak için kullanması gereken bağlama ve bu bağlamanın tanımlandığı ad alanı. Bu durumda `wsHttpBinding_ICalculator` kullanılır.  
  
- Sözleşmeyi tanımlayan WSDL. Bu durumda, serviceWsdl. xml dosyasından okunan dizedir.  
  
- Sözleşmenin adı ve ad alanı. WSDL birden fazla sözleşme içerebileceğinden bu kimlik gereklidir.  
  
    > [!NOTE]
    > Varsayılan olarak, WCF Hizmetleri, kullanılan her ad alanı için ayrı WSDL dosyaları oluşturur. Bunlar, WSDL içeri aktarma yapısının kullanımıyla bağlantılıdır. Bilinen ad tek bir WSDL tanımı beklediği için, bu örnekte gösterildiği gibi hizmetin tek bir ad alanı kullanması gerekir ya da ayrı dosyalar el ile birleştirilmelidir.  
  
 Proxy örneğinin hizmet bilinen adıyla oluşturulması, istemci uygulama proxy üzerinde Yöntemler çağırabilir ve bu da hizmet bilinen hizmet işlemlerini çağıran hizmet adı altyapısına neden olur.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Örneği çalıştırdığınızda, işlem yanıtı bir Windows komut dosyası ana ileti kutusu penceresinde görüntülenir. Bu, bir WCF hizmeti ile iletişim kurmak için bir WSDL sözleşmesinin bilinen adını kullanarak COM çağrısı yapan bir COM istemcisini gösterir.  
  
## <a name="metadata-exchange-contract"></a>Meta veri değişimi sözleşmesi  
 Bilinen adı, WSDL sözleşimiyle birlikte bir MEX sözleşmesiyle birlikte kullanmak için, istemci kaydı gerekmez. Hizmetin sözleşmesi, meta veri değişim iç kullanımı üzerinden yürütme sırasında alınır.  
  
 ComCalcClient. vbs istemci uygulaması, hizmet için bir proxy oluşturmak üzere `GetObject` işlevini kullanır.  
  
```vbscript  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 Bilinen ad tarafından kullanılan parametreler şunları belirtir:  
  
- Hizmet meta veri değişimi uç noktasının adresi.  
  
- Hizmet uç noktasının adresi.  
  
- İstemcinin bu uç nokta ile bağlanmak için kullanması gereken bağlama ve bu bağlamanın tanımlandığı ad alanı. Bu durumda `wsHttpBinding_ICalculator` kullanılır.  
  
- Sözleşmenin adı ve ad alanı. WSDL birden fazla sözleşme içerebileceğinden bu kimlik gereklidir.  
  
 Proxy örneğinin hizmet bilinen adıyla oluşturulması, istemci uygulama proxy üzerinde Yöntemler çağırabilir ve bu da hizmet bilinen hizmet işlemlerini çağıran hizmet adı altyapısına neden olur.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Örneği çalıştırdığınızda, işlem yanıtı bir Windows komut dosyası ana ileti kutusu penceresinde görüntülenir. Bu, bir WCF hizmeti ile iletişim kurmak için bir MEX sözleşmesiyle bilinen bilinen bilinen bilinen bir COM istemcisini gösterir.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Örneği ayarlamak ve derlemek için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Visual Studio için Geliştirici Komut İstemi, dile özgü klasör altında \client\bin klasörünü açın.  
  
    > [!NOTE]
    > [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7 veya Windows Server 2008 R2 kullanıyorsanız, komut istemi 'ni yönetici ayrıcalıklarıyla çalıştırdığınızdan emin olun.  
  
4. Dll 'yi bir TLB dosyasına aktarmak için `tlbexp.exe client.dll /out:CalcProxy.tlb` yazın. Bir "tür kitaplığı verme programı Uyarısı" beklenmektedir, ancak genel tür gerekli olmadığından bir sorun değil.  
  
5. Türleri COM 'a kaydetmek için `regasm.exe /tlb:CalcProxy.tlb client.dll` yazın. Bir "tür kitaplığı verme programı Uyarısı" beklenmektedir, ancak genel tür gerekli olmadığından bir sorun değil.  
  
6. Derlemeyi genel bütünleştirilmiş kod önbelleğine eklemek için `gacutil.exe /i client.dll` yazın.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için  
  
1. Aşağıdaki adresi yazarak hizmete bir tarayıcı kullanarak erişebiliyor musunuz: `http://localhost/servicemodelsamples/service.svc`. Yanıt olarak bir onay sayfası görüntülenmelidir.  
  
2. Dile özgü klasörün altındaki \Client öğesinden ComCalcClient. vbs ' yi çalıştırın. İstemci etkinliği ileti kutusu pencereleri ' nde görüntülenir.  
  
3. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computers"></a>Örneği bilgisayarlar arasında çalıştırmak için  
  
1. Hizmet bilgisayarında, ServiceModelSamples adlı bir sanal dizin oluşturun. Örneğe eklenen Setupvroot. bat betiği disk dizinini ve sanal dizini oluşturmak için kullanılabilir.  
  
2. Hizmet programı dosyalarını%SystemDrive%\Inetpub\wwwroot\servicemodelsamples adresinden hizmet bilgisayarında ServiceModelSamples sanal dizinine kopyalayın. Dosyaları \Bin dizinine dahil ettiğinizden emin olun.  
  
3. İstemci komut dosyasını dile özgü klasör altındaki \İstemci klasöründen istemci bilgisayara kopyalayın.  
  
4. Betik dosyasında, uç nokta tanımının adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin. "Localhost" başvurularını, adreste tam etki alanı adıyla değiştirin.  
  
5. WSDL dosyasını istemci bilgisayara kopyalayın. ServiceWsdl. xml WSDL dosyasında, "localhost" ile ilgili tüm başvuruları adresteki tam etki alanı adıyla değiştirin.  
  
6. Client. dll kitaplığını dile özgü klasörün altındaki \client\bin klasöründen istemci bilgisayardaki bir dizine kopyalayın.  
  
7. Bir komut isteminden, istemci bilgisayardaki bu hedef dizine gidin. [!INCLUDE[wv](../../../../includes/wv-md.md)] veya [!INCLUDE[lserver](../../../../includes/lserver-md.md)]kullanıyorsanız, komut istemi ' ni yönetici olarak çalıştırdığınızdan emin olun.  
  
8. Dll 'yi bir TLB dosyasına aktarmak için `tlbexp.exe client.dll /out:CalcProxy.tlb` yazın. Bir "tür kitaplığı verme programı Uyarısı" beklenmektedir, ancak genel tür gerekli olmadığından bir sorun değil.  
  
9. Türleri COM 'a kaydetmek için `regasm.exe /tlb:CalcProxy.tlb client.dll` yazın. Komutu çalıştırmadan önce yolun `regasm.exe` içeren klasöre ayarlandığından emin olun.  
  
10. Derlemeyi genel bütünleştirilmiş kod önbelleğine eklemek için `gacutil.exe /i client.dll` yazın. Komutu çalıştırmadan önce yolun `gacutil.exe` içeren klasöre ayarlandığından emin olun.  
  
11. Bir tarayıcı kullanarak hizmete istemci bilgisayardan erişebilmeniz için test edin.  
  
12. İstemci bilgisayarda ComCalcClient. vbs ' yi başlatın.  
  
#### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
- Güvenlik nedenleriyle, örnekleri ile işiniz bittiğinde kurulum adımlarında verilen sanal dizin tanımını ve izinleri kaldırın.  
