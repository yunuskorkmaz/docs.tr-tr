---
title: Hizmet Kimliği Örneği
ms.date: 03/30/2017
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
ms.openlocfilehash: 868bd6e0ac7429224462c973c1c48132ec3860ba
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76919371"
---
# <a name="service-identity-sample"></a>Hizmet Kimliği Örneği
Bu hizmet kimliği örneği, bir hizmetin kimliğini nasıl ayarlayabileceğinizi gösterir. Tasarım zamanında, istemci, hizmetin meta verilerini kullanarak kimliği alabilir ve çalışma zamanında istemci hizmetin kimliğini doğrulayabilir. Hizmet kimliği kavramı, bir istemcinin işlemlerini çağırmadan önce bir hizmetin kimliğini doğrulamasına izin ver, böylelikle de istemciyi kimliği doğrulanmamış çağrılardan koruyor. Güvenli bir bağlantıda hizmet, erişim izni vermeden önce bir istemcinin kimlik bilgilerini doğrular, ancak bu, bu örneğin odağı değildir. [İstemcide](../../../../docs/framework/wcf/samples/client.md) sunucu kimlik doğrulamasını gösteren örneklere bakın.

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

 Kimlik, App. config dosyasındaki yapılandırmada de belirtilebilir. Aşağıdaki örnekte, bir hizmet uç noktası için UPN (Kullanıcı asıl adı) kimliğinin nasıl ayarlanacağı gösterilmektedir.

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

 <xref:System.ServiceModel.EndpointIdentity> ve <xref:System.ServiceModel.Security.IdentityVerifier> sınıflarından türeterek, istemci üzerinde özel bir kimlik ayarlanabilir. Kavramsal olarak <xref:System.ServiceModel.Security.IdentityVerifier> sınıfı, hizmetin `AuthorizationManager` sınıfının istemci eşdeğeri olarak kabul edilebilir. Aşağıdaki kod örneği, bir kuruluş adını sunucu sertifikasının konu adı ile eşleşecek şekilde depolayan `OrgEndpointIdentity`bir uygulamasını gösterir. Kuruluş adı için yetkilendirme denetimi, `CustomIdentityVerifier` sınıfındaki `CheckAccess` yönteminde oluşur.

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

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.

3. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.

### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için

1. Windows XP veya Windows Vista 'da, kimlik çözüm klasöründeki Identity. pfx sertifika dosyasını, MMC ek bileşeni aracını kullanarak LocalMachine/My (Personal) sertifika deposuna aktarın. Bu dosya parola korumalıdır. İçeri aktarma sırasında sizden bir parola istenir. Parola kutusuna `xyz` yazın. Daha fazla bilgi için bkz. [nasıl yapılır: MMC ek bileşeni Ile sertifikaları görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) konusuna bakın. Bu işlem tamamlandıktan sonra, bu sertifikayı istemcide kullanılmak üzere geçerli kullanıcı/güvenilir kişiler deposuna kopyalayan yönetici ayrıcalıklarına sahip Visual Studio için Geliştirici Komut İstemi Setup. bat dosyasını çalıştırın.

2. Windows Server 2003 ' de, yönetici ayrıcalıklarıyla bir Visual Studio 2012 komut istemi içindeki örnek yükleme klasöründen Setup. bat dosyasını çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.

    > [!NOTE]
    > Setup. bat toplu iş dosyası bir Visual Studio 2012 komut Isteminden çalıştırılmak üzere tasarlanmıştır. Visual Studio 2012 komut Isteminde ayarlanan PATH ortam değişkeni Setup. bat betiği için gereken yürütülebilir dosyaları içeren dizine işaret eder. Örnek ile işiniz bittiğinde Cleanup. bat dosyasını çalıştırarak sertifikaları kaldırtığınızdan emin olun. Diğer güvenlik örnekleri aynı sertifikaları kullanır.  
  
3. \Service\bin dizininden Service. exe ' yi başlatın. Hizmetin hazırlandığını belirttiğinden emin olun ve hizmeti sonlandırmak için > \<ENTER tuşuna basarak bir istem görüntüler.  
  
4. Oluşturmak ve çalıştırmak için, \client\bin dizininden veya Visual Studio 'daki F5 tuşuna basarak Client. exe ' yi başlatın. İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
5. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Örneği bilgisayarlar arasında çalıştırmak için  
  
1. Örneğin istemci bölümünü oluşturmadan önce, `CallServiceCustomClientIdentity` yöntemindeki Client.cs dosyasında hizmetin uç nokta adresinin değerini değiştirdiğinizden emin olun. Ardından örnek oluşturun.  
  
2. Hizmet bilgisayarında bir dizin oluşturun.  
  
3. Hizmet programı dosyalarını service\bin konumundan hizmet bilgisayarındaki dizine kopyalayın. Ayrıca Setup. bat ve Cleanup. bat dosyalarını da hizmet bilgisayarına kopyalayın.  
  
4. İstemci bilgisayarda istemci ikilileri için bir dizin oluşturun.  
  
5. İstemci programı dosyalarını istemci bilgisayardaki istemci dizinine kopyalayın. Ayrıca Setup. bat, Cleanup. bat ve ImportServiceCert. bat dosyalarını istemciye kopyalayın.  
  
6. Hizmette, yönetici ayrıcalıklarıyla açılmış bir Visual Studio Geliştirici Komut İstemi `setup.bat service` çalıştırın. `setup.bat` `service` bağımsız değişkeniyle çalıştırmak, bilgisayarın tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service. cer adlı bir dosyaya aktarır.  
  
7. Service. cer dosyasını hizmet dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.  
  
8. İstemci bilgisayardaki Client. exe. config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin. Değiştirilmesi gereken birden çok örnek vardır.  
  
9. İstemcide, yönetici ayrıcalıklarıyla açılan bir Geliştirici Komut İstemi Visual Studio için ImportServiceCert. bat dosyasını çalıştırın. Bu, hizmet sertifikasını Service. cer dosyasından CurrentUser-Trustedkişiler deposuna aktarır.  
  
10. Hizmet bilgisayarında, komut isteminden Service. exe ' yi başlatın.  
  
11. İstemci bilgisayarda, bir komut isteminden Client. exe ' yi başlatın. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
- Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. bat dosyasını çalıştırın.  
  
    > [!NOTE]
    > Bu betik, bilgisayarlar arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz. Bilgisayarlar arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun. Bunu yapmak için şu komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.
