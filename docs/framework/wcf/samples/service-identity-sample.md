---
title: "Hizmet Kimliği Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a89839294f74d733ec7f607a0afda53148fbd57
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="service-identity-sample"></a>Hizmet Kimliği Örneği
Bu hizmet kimliği örneği, bir hizmetin kimliğini ayarlamak gösterilmiştir. Tasarım zamanında bir istemci hizmetin meta verileri kullanarak kimlik alabilir ve ardından çalışma zamanında istemci hizmetin kimliğini doğrulayabilir. Hizmet kimliği kavramı, böylece istemci gelen kimliği doğrulanmamış çağrıları koruma işlemlerinden birini çağırmadan önce bir hizmetin kimliğini doğrulamak bir istemci izin vermektir. Güvenli bir bağlantı üzerinden hizmet ayrıca bir istemcinin kimlik bilgileri erişime izin vermeden önce kimliğini doğrular, ancak bu odak noktası, bu örnek değil. Örnekleri görmek [istemci](../../../../docs/framework/wcf/samples/client.md) sunucu kimlik doğrulaması göster.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Bu örneği aşağıdaki özellikleri gösterir:  
  
-   Kimlik farklı türde bir hizmet için farklı uç noktalar ayarlamak nasıl. Kimlik türlerinin farklı özellikleri vardır. Kullanılacak kimlik türü, uç noktanın bağlama üzerinde kullanılan güvenlik kimlik bilgileri türünü bağımlıdır.  
  
-   Kimlik, ya da yapılandırma veya imperatively kodu bildirimli olarak ayarlanmış olabilir. Genellikle hem istemci hem de hizmet için yapılandırma kimliğini ayarlamak için kullanmanız gerekir.  
  
-   Nasıl özel bir kimlik istemci üzerinde ayarlanır. Özel bir kimlik mevcut bir türle hizmet çağırmadan önce yetkilendirme kararları için hizmetin kimlik bilgileri bölümünde sağlanan diğer talep bilgilerini inceleyin olanak tanır kimlik, genellikle bir özelleştirmedir.  
  
    > [!NOTE]
    >  Bu örnek identity.com ve bu sertifikadaki RSA anahtarı olarak adlandırılan belirli bir sertifika kimliğini denetler. Sertifika ve RSA kimlik türlerinin istemcide yapılandırmasında, bu değerleri almak için kolay bir yol hizmeti WSDL incelemek için bu değerleri nerede serileştirilir kullanıldığında.  
  
 Aşağıdaki örnek kod, etki alanı ad sunucusu (DNS) ile bir WSHttpBinding kullanarak bir sertifika, hizmet uç noktası kimliğini yapılandırmak gösterilmiştir.  
  
```  
//Create a service endpoint and set its identity to the certificate's DNS                 
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);  
// Client are Anonymous to the service  
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;  
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);  
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));  
ep.Address = epa;  
```  
  
 Kimlik, App.config dosyasında yapılandırmasında de belirtilebilir. Aşağıdaki örnek, bir hizmet uç noktası için UPN (kullanıcı asıl adı) kimliğini ayarlamak gösterilmiştir.  
  
```xml  
<endpoint address="upnidentity"  
        behaviorConfiguration=""  
        binding="wsHttpBinding"  
        bindingConfiguration="WSHttpBinding_Windows"  
        name="WSHttpBinding_ICalculator_Windows"  
        contract="Microsoft.ServiceModel.Samples.ICalculator">  
  <!-- Set the UPN identity for this endpoint -->  
  <identity>  
      <userPrincipalName value="host\myservice.com" />  
  </identity >  
</endpoint>  
```  
  
 Özel bir kimlik türetme tarafından istemcide ayarlanabilir <xref:System.ServiceModel.EndpointIdentity> ve <xref:System.ServiceModel.Security.IdentityVerifier> sınıfları. Kavramsal olarak <xref:System.ServiceModel.Security.IdentityVerifier> sınıfı, istemci sayılabileceğini hizmetin karşılığıdır `AuthorizationManager` sınıfı. Aşağıdaki kod örneğinde uygulaması gösterir `OrgEndpointIdentity`, sunucu sertifikasının konu adı ile eşleşmesi için bir kuruluş adı depolar. Kuruluş adı yetkilendirme denetle oluşuyor `CheckAccess` yöntemi `CustomIdentityVerifier` sınıfı.  
  
```  
// This custom EndpointIdentity stores an organization name   
public class OrgEndpointIdentity : EndpointIdentity  
{  
    private string orgClaim;  
    public OrgEndpointIdentity(string orgName)  
    {  
        orgClaim = orgName;  
    }  
    public string OrganizationClaim  
    {  
        get { return orgClaim; }  
        set { orgClaim = value; }  
    }  
}  
  
//This custom IdentityVerifier uses the supplied OrgEndpointIdentity to  
//check that X.509 certificate's distinguished name claim contains  
//the organization name e.g. the string value "O=Contoso"   
class CustomIdentityVerifier : IdentityVerifier  
{  
    public override bool CheckAccess(EndpointIdentity identity, AuthorizationContext authContext)  
    {  
        bool returnvalue = false;  
        foreach (ClaimSet claimset in authContext.ClaimSets)  
        {  
            foreach (Claim claim in claimset)  
            {  
                if (claim.ClaimType == "http://schemas.microsoft.com/ws/2005/05/identity/claims/x500distinguishedname")  
                {  
                    X500DistinguishedName name = (X500DistinguishedName)claim.Resource;  
                    if (name.Name.Contains(((OrgEndpointIdentity)identity).OrganizationClaim))  
                    {  
                        Console.WriteLine("Claim Type: {0}",claim.ClaimType);  
                        Console.WriteLine("Right: {0}", claim.Right);  
                        Console.WriteLine("Resource: {0}",claim.Resource);  
                        Console.WriteLine();  
                        returnvalue = true;  
                    }  
                }  
            }  
        }  
        return returnvalue;  
    }  
}  
```  
  
 Bu örnek dile özgü kimlik çözüm klasöründe olan identity.com adlı bir sertifika kullanıyor.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Aynı bilgisayara örneği çalıştırmak için  
  
1.  Üzerinde [!INCLUDE[wxp](../../../../includes/wxp-md.md)] veya [!INCLUDE[wv](../../../../includes/wv-md.md)], kimlik çözümü klasöründeki Identity.pfx sertifika dosyasını MMC ek bileşen aracını kullanarak LocalMachine/My (Kişisel) sertifika deposuna aktarın. Parola korumalı dosyasıdır. İçeri aktarma sırasında için bir parola sorulur. Tür `xyz` parola kutusuna. Daha fazla bilgi için bkz: [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) konu. Bunu yaptıktan sonra Setup.bat bir Visual Studio komut istemindeki Currentuser'a/güvenilir Kişiler deposuna istemcide kullanmak için bu sertifikayı kopyaladığı yönetici ayrıcalıklarıyla çalıştırın.  
  
2.  Üzerinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], içinde örnek yükleme klasöründen Setup.bat çalıştırmak bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemini yönetici ayrıcalıklarına sahip. Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.  
  
    > [!NOTE]
    >  Setup.bat toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi. İçinde PATH ortam değişkeni ayarlamak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi Setup.bat komut dosyası için gereken yürütülebilir dosyalar içeren dizine işaret eder. Örnekle tamamladığınızda Cleanup.bat çalıştırarak sertifikaları kaldırdığınızdan emin olun. Diğer güvenlik örnekleri aynı sertifikaları kullanır.  
  
3.  Service.exe \service\bin dizininden başlatın. Hizmet hazır olduğunu bildirir ve tuşuna bir istem görüntüler gösterir sağlamak \<Enter > Hizmet sonlandırılacak.  
  
4.  Client.exe \client\bin dizinden veya derlemek ve çalıştırmak için Visual Studio'da F5'e basarak başlatın. İstemci etkinliği istemci konsol uygulaması görüntülenir.  
  
5.  İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Örnek istemci parçası oluşturmadan önce hizmet uç noktası adresi Client.cs dosyasında değeri değiştirdiğinizden emin olun `CallServiceCustomClientIdentity` yöntemi. Ardından örnek oluşturun.  
  
2.  Hizmet bilgisayarda bir dizin oluşturun.  
  
3.  Hizmet program dosyalarını service\bin hizmeti bilgisayarında dizinine kopyalayın. Ayrıca Setup.bat ve Cleanup.bat dosyalarını hizmet bilgisayara kopyalayın.  
  
4.  İstemci ikili dosyalarının için istemci bilgisayarda bir dizin oluşturun.  
  
5.  İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın. Ayrıca istemciye Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını kopyalayın.  
  
6.  Hizmeti, Çalıştır `setup.bat service` yönetici ayrıcalıklarına sahip bir Visual Studio Komut İstemi'nde açılır. Çalışan `setup.bat` ile `service` bağımsız değişkeni bilgisayarın tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya aktarır.  
  
7.  Service.cer dosya hizmeti dizininden istemci bilgisayarda istemci dizinine kopyalayın.  
  
8.  İstemci bilgisayardaki Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin. Değiştirilmelidir birden çok örneği vardır.  
  
9. İstemci üzerinde yönetici ayrıcalıklarına sahip açılan bir Visual Studio komut istemi ImportServiceCert.bat çalıştırın. Bu hizmet sertifikası Service.cer dosyadan Currentuser'a - TrustedPeople deposunu alır.  
  
10. Hizmet bilgisayarda komut isteminden Service.exe başlatın.  
  
11. İstemci bilgisayarda bir komut isteminden Client.exe başlatın. İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Örnek sonra temizlemek için  
  
-   Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın.  
  
    > [!NOTE]
    >  Bu komut, bu örnek bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz. Çalıştırırsanız [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bilgisayarlar arasında sertifikaları kullanma örnekleri Currentuser'a - TrustedPeople deposu yüklü hizmet sertifikalarını temizlemek emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Ayrıca Bkz.
