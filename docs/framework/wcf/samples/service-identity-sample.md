---
title: Hizmet Kimliği Örneği
ms.date: 03/30/2017
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
ms.openlocfilehash: e3365b8e17d847e6e1dc42062dc7fd5c1e4de80d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558140"
---
# <a name="service-identity-sample"></a>Hizmet Kimliği Örneği
Bu hizmet kimliği örneği, bir hizmetin kimliğini nasıl ayarlayabileceğinizi gösterir. Tasarım zamanında, istemci, hizmetin meta verilerini kullanarak kimliği alabilir ve çalışma zamanında istemci hizmetin kimliğini doğrulayabilir. Hizmet kimliği kavramı, bir istemcinin işlemlerini çağırmadan önce bir hizmetin kimliğini doğrulamasına izin ver, böylelikle de istemciyi kimliği doğrulanmamış çağrılardan koruyor. Güvenli bir bağlantıda hizmet, erişim izni vermeden önce bir istemcinin kimlik bilgilerini doğrular, ancak bu, bu örneğin odağı değildir. [İstemcide](client.md) sunucu kimlik doğrulamasını gösteren örneklere bakın.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

 Bu örnek aşağıdaki özellikleri göstermektedir:

- Bir hizmetin farklı uç noktalarında farklı kimlik türlerini ayarlama. Her kimlik türünün farklı becerileri vardır. Kullanılacak kimliğin türü, uç noktanın bağlamasında kullanılan güvenlik kimlik bilgilerinin türüne bağlıdır.

- Kimlik, yapılandırmada veya imperatively kodunda bildirimli olarak ayarlanabilir. Genellikle, hem istemci hem de hizmet için, kimliği ayarlamak için yapılandırmayı kullanmanız gerekir.

- İstemci üzerinde özel bir kimlik ayarlama. Özel kimlik, genellikle istemcinin hizmeti çağırmadan önce yetkilendirme kararları vermek için hizmetin kimlik bilgilerinde belirtilen diğer talep bilgilerini incelemesini sağlayan mevcut bir kimlik türünün özelleştirilmesine olanak sağlar.

    > [!NOTE]
    > Bu örnek, identity.com adlı belirli bir sertifikanın kimliğini ve bu sertifika içinde bulunan RSA anahtarını denetler. İstemci üzerindeki yapılandırmada sertifika ve RSA Kimlik türleri kullanılırken, bu değerleri almanın kolay bir yolu, bu değerlerin serileştirildiği hizmet için WSDL 'yi incelekullanmaktır.

 Aşağıdaki örnek kod, bir hizmet uç noktasının kimliğini bir WSHttpBinding kullanarak bir sertifikanın etki alanı adı sunucusu (DNS) ile yapılandırmayı gösterir.

```csharp
//Create a service endpoint and set its identity to the certificate's DNS
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);
// Client are Anonymous to the service
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));
ep.Address = epa;
```

 Kimlik, App.config dosyasındaki yapılandırmada de belirtilebilir. Aşağıdaki örnekte, bir hizmet uç noktası için UPN (Kullanıcı asıl adı) kimliğinin nasıl ayarlanacağı gösterilmektedir.

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

 Özel bir kimlik, ve sınıflarından türeterek istemci üzerinde ayarlanabilir <xref:System.ServiceModel.EndpointIdentity> <xref:System.ServiceModel.Security.IdentityVerifier> . Kavramsal olarak <xref:System.ServiceModel.Security.IdentityVerifier> sınıf, hizmetin sınıfının istemci eşdeğeri olarak düşünülebilir `AuthorizationManager` . Aşağıdaki kod örneğinde `OrgEndpointIdentity` , bir kuruluş adını, sunucu sertifikasının konu adı ile eşleşecek şekilde depolayan bir uygulamasını gösterilmektedir. Kuruluş adı için yetkilendirme denetimi, `CheckAccess` sınıfındaki yönteminde oluşur `CustomIdentityVerifier` .

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

 Bu örnek, dile özgü kimlik çözüm klasöründeki identity.com adlı bir sertifika kullanır.

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.

3. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.

### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için

1. Windows XP veya Windows Vista 'da, kimlik çözüm klasöründeki Identity. pfx sertifika dosyasını, MMC ek bileşeni aracını kullanarak LocalMachine/My (Personal) sertifika deposuna aktarın. Bu dosya parola korumalıdır. İçeri aktarma sırasında sizden bir parola istenir. `xyz`Parola kutusuna yazın. Daha fazla bilgi için bkz. [nasıl yapılır: MMC ek bileşeni Ile sertifikaları görüntüleme](../feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) konusuna bakın. Bu işlem tamamlandıktan sonra, bu sertifikayı istemcide kullanılmak üzere geçerli kullanıcı/güvenilir kişiler deposuna kopyalayan yönetici ayrıcalıklarına sahip bir Visual Studio Geliştirici Komut İstemi Setup.bat çalıştırın.

2. Windows Server 2003 ' de, yönetici ayrıcalıklarıyla bir Visual Studio 2012 komut istemi içindeki örnek install klasöründen Setup.bat ' yi çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.

    > [!NOTE]
    > Setup.bat Batch dosyası bir Visual Studio 2012 komut Isteminden çalıştırılmak üzere tasarlanmıştır. Visual Studio 2012 komut Isteminde ayarlanan PATH ortam değişkeni, Setup.bat betiği için gereken yürütülebilir dosyaları içeren dizine işaret eder. Örnek ile işiniz bittiğinde Cleanup.bat çalıştırarak sertifikaları kaldırtığınızdan emin olun. Diğer güvenlik örnekleri aynı sertifikaları kullanır.  
  
3. \Service\bin dizininden Service.exe başlatın. Hizmetin hazırlandığını belirttiğinden emin olun ve hizmeti sonlandırmak için basılacak bir istem görüntüler \<Enter> .  
  
4. Oluşturmak ve çalıştırmak için, \client\bin dizininden veya Visual Studio 'daki F5 'e basarak Client.exe başlatın. İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
5. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Örneği bilgisayarlar arasında çalıştırmak için  
  
1. Örneğin istemci bölümünü oluşturmadan önce, yöntemin Client.cs dosyasındaki hizmetin uç nokta adresinin değerini değiştirdiğinizden emin olun `CallServiceCustomClientIdentity` . Ardından örnek oluşturun.  
  
2. Hizmet bilgisayarında bir dizin oluşturun.  
  
3. Hizmet programı dosyalarını service\bin konumundan hizmet bilgisayarındaki dizine kopyalayın. Ayrıca, Setup.bat ve Cleanup.bat dosyalarını hizmet bilgisayarına kopyalayın.  
  
4. İstemci bilgisayarda istemci ikilileri için bir dizin oluşturun.  
  
5. İstemci programı dosyalarını istemci bilgisayardaki istemci dizinine kopyalayın. Ayrıca Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını istemciye kopyalayın.  
  
6. Hizmette, `setup.bat service` yönetici ayrıcalıklarıyla açılan bir Visual Studio için geliştirici komut istemi çalıştırın. `setup.bat`Bağımsız değişkeniyle birlikte çalıştırmak, `service` bilgisayarın tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service. cer adlı bir dosyaya aktarır.  
  
7. Service. cer dosyasını hizmet dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.  
  
8. İstemci bilgisayardaki Client.exe.config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin. Değiştirilmesi gereken birden çok örnek vardır.  
  
9. İstemcisinde ImportServiceCert.bat, yönetici ayrıcalıklarıyla açılmış bir Visual Studio Geliştirici Komut İstemi çalıştırın. Bu, hizmet sertifikasını Service. cer dosyasından CurrentUser-Trustedkişiler deposuna aktarır.  
  
10. Hizmet bilgisayarında, komut isteminden Service.exe başlatın.  
  
11. İstemci bilgisayarda, bir komut isteminden Client.exe başlatın. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
- Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup.bat çalıştırın.  
  
    > [!NOTE]
    > Bu betik, bilgisayarlar arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz. Bilgisayarlar arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun. Bunu yapmak için şu komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` .
