---
title: Hizmet Kimliği Örneği
ms.date: 03/30/2017
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
ms.openlocfilehash: 587c1b8f5cd509db343266f5903847d3b94b7460
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664690"
---
# <a name="service-identity-sample"></a>Hizmet Kimliği Örneği
Bu hizmet kimliği örneği bir hizmet için kimlik gösterilmektedir. Tasarım zamanında istemci hizmet meta verileri kullanarak kimliğini alabilir ve ardından çalışma zamanında istemci hizmetin kimliğini doğrulayabilir. Hizmet kimliği kavramı, böylece istemci kimliği doğrulanmamış çağrılarından koruma işlemlerinden birini çağırmadan önce bir hizmet kimlik doğrulaması bir istemci izin vermektir. Güvenli bir bağlantı üzerinden hizmet de istemci kimlik bilgileri erişime izin vermeden önce kimliğini doğrular, ancak bu odak noktası, bu örnek değil. Örnekleri görmek [istemci](../../../../docs/framework/wcf/samples/client.md) sunucu kimlik doğrulaması göster.

> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.

 Bu örnek aşağıdaki özellikleri gösterilmektedir:

- Nasıl bir hizmet için farklı uç noktalar şirket farklı türde kimlik ayarlanır. Kimlik türlerinin farklı özelliklere sahiptir. Uç noktanın bağlamada kullanılan güvenlik kimlik bilgileri türünü kullanmak için kimlik türü bağlıdır.

- Kimlik, ya da yapılandırma veya kesin kod bildirimli olarak ayarlanabilir. Genellikle hem istemci hem de hizmet için kimlik yapılandırma kullanmalısınız.

- Nasıl özel bir kimlik istemci üzerinde ayarlanır. Özel kimlik hizmeti çağırmadan önce yetkilendirme kararları vermek için hizmetin kimlik bilgileri sağlanan başka talep bilgileri incelemek istemci sağlayan kimlik var olan bir tür genellikle bir özelleştirmedir.

    > [!NOTE]
    >  Bu örnek identity.com ve bu sertifikadaki RSA anahtarı adlı belirli bir sertifika kimliği denetler. İstemci yapılandırması sertifika ve RSA kimlik türlerini kullanarak, bu değerleri almak için kolay bir yol hizmeti için WSDL incelemek için bu değerleri nerede serileştirilir andır.

 Aşağıdaki örnek kod, bir hizmet uç noktası kimliği etki alanı adı sunucusu (DNS) ile bir WSHttpBinding kullanarak bir sertifika yapılandırmak gösterilmektedir.

```csharp
//Create a service endpoint and set its identity to the certificate's DNS
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);
// Client are Anonymous to the service
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));
ep.Address = epa;
```

 Kimlik, App.config dosyasında yapılandırmasında de belirtilebilir. Aşağıdaki örnek, bir hizmet uç noktası için UPN (kullanıcı asıl adı) kimliğini ayarlamak gösterilmektedir.

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

 Özel kimlik türeterek istemcide ayarlanabilir <xref:System.ServiceModel.EndpointIdentity> ve <xref:System.ServiceModel.Security.IdentityVerifier> sınıfları. Kavramsal olarak <xref:System.ServiceModel.Security.IdentityVerifier> sınıfı kabul istemci olarak denk olan hizmetin `AuthorizationManager` sınıfı. Aşağıdaki kod örneği uygulanışı gösterilmektedir `OrgEndpointIdentity`, sunucu sertifikasının konu adını eşleştirmek için bir kuruluş adı depolar. Kuruluş adı yetkilendirme denetle oluşuyor `CheckAccess` metodunda `CustomIdentityVerifier` sınıfı.

```csharp
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

 Bu örnek için dile özgü kimlik Çözüm klasörü içinde olan identity.com adı verilen bir sertifika kullanır.

### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma

1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için

1. Üzerinde [!INCLUDE[wxp](../../../../includes/wxp-md.md)] veya [!INCLUDE[wv](../../../../includes/wv-md.md)], kimlik Çözüm klasörü'ndeki Identity.pfx sertifika dosyası MMC ek bileşenini aracını kullanarak LocalMachine/My (Kişisel) sertifika deposuna aktarın. Parola korumalı dosyasıdır. İçeri aktarma sırasında parola istenir. Tür `xyz` parola kutusu içine. Daha fazla bilgi için [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) konu. Bunu yaptıktan sonra Setup.bat bir geliştirici Komut İstemi'nde Visual Studio için yönetici ayrıcalıklarına sahip, bu sertifika, istemcide kullanılmak CurrentUser/güvenilir Kişiler deposuna kopyalar çalıştırın.

2. Üzerinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Setup.bat örnek yükleme klasörü içinde bir Visual Studio 2012 komut istemini yönetici ayrıcalıklarıyla çalıştırın. Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.

    > [!NOTE]
    >  Setup.bat toplu iş dosyası, bir Visual Studio 2012 komut isteminden çalıştırılması için tasarlanmıştır. PATH ortam değişkenine içinde Visual Studio 2012 komut istemi noktaları Setup.bat betiği tarafından gereken yürütülebilir dosyaları içeren dizine ayarlayın. Örnek ile tamamladığınızda Cleanup.bat çalıştırarak, sertifikaları kaldırdığınızdan emin olun. Diğer güvenlik örnekleri aynı sertifikalarını kullanın.  
  
3. Service.exe \service\bin dizinden başlatın. Hizmet hazır olduğunda ve bir istem görüntüler tuşuna gösterdiğini olun \<Enter > hizmeti sonlandırmak için.  
  
4. Client.exe \client\bin dizinden veya derlemek ve çalıştırmak için Visual Studio'da F5 tuşuna basarak başlatın. İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
5. İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1. İstemci parçası oluşturmadan önce Client.cs dosyasında hizmetin uç nokta adresi değerini değiştirmek mutlaka `CallServiceCustomClientIdentity` yöntemi. Ardından örnek oluşturun.  
  
2. Hizmet bilgisayarda bir dizin oluşturun.  
  
3. Hizmet program dosyaları service\bin hizmeti bilgisayarında dizinine kopyalayın. Ayrıca Setup.bat ve Cleanup.bat dosyaları hizmet bilgisayara kopyalayın.  
  
4. İstemci ikili dosyaları için istemci bilgisayarda bir dizin oluşturun.  
  
5. İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın. Aynı zamanda istemciye Setup.bat Cleanup.bat ve ImportServiceCert.bat dosyaları kopyalayın.  
  
6. Hizmette çalıştıracak `setup.bat service` Geliştirici komut istemi için Visual Studio yönetici ayrıcalıklarıyla açılmış. Çalışan `setup.bat` ile `service` bağımsız değişkeni bilgisayarın tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya dışarı aktarır.  
  
7. Service.cer dosya hizmeti dizinden istemci bilgisayarda istemci dizinine kopyalayın.  
  
8. İstemci bilgisayarda Client.exe.config dosyasında hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin. Değiştirilmesi gereken birden çok örneği vardır.  
  
9. İstemcide ImportServiceCert.bat yönetici ayrıcalıklarıyla açılan bir Visual Studio için geliştirici komut isteminden çalıştırın. Bu hizmet sertifikası Service.cer dosyasından CurrentUser - TrustedPeople deposuna aktarır.  
  
10. Hizmet bilgisayarda Service.exe komut istemini başlatın.  
  
11. İstemci bilgisayarda bir komut istemi'nden Client.exe başlatın. İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Sonra örnek temizlemek için  
  
- Bu örneği çalıştırmadan tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.  
  
    > [!NOTE]
    >  Bu betik, bu örnek, bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz. Bilgisayarlar arasında sertifikaları kullanan bir Windows Communication Foundation (WCF) örnekleri çalıştırırsanız, CurrentUser - TrustedPeople deposu yüklü hizmet sertifikalarını Temizle emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.
