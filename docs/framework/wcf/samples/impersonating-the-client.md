---
title: İstemci Kimliğine Bürünme
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: 10a8d243b3f053879f183864e955d9260c07865b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183606"
---
# <a name="impersonating-the-client"></a>İstemci Kimliğine Bürünme
Kimliğe Bürünme örneği, hizmetin arayan adına sistem kaynaklarına erişebilmeleri için servisteki arayan uygulamasının nasıl taklit edilebildiğini gösterir.  
  
 Bu örnek [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) örneğine dayanmaktadır. Hizmet ve istemci yapılandırma dosyaları [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) örneği ile aynıdır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Hizmet kodu, hizmetteki `Add` yöntemin aşağıdaki örnek kodda gösterildiği <xref:System.ServiceModel.OperationBehaviorAttribute> gibi kullanarak arayanın kimliğine büründiyi olacak şekilde değiştirildi.  
  
```csharp
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    Console.WriteLine("Received Add({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
    DisplayIdentityInformation();  
    return result;  
}  
```  
  
 Sonuç olarak, yürütme iş parçacığının güvenlik bağlamı `Add` yönteme girmeden önce arayanın kimliğine göre değiştirilir ve yöntemden çıkarken döndürüldü.  
  
 Aşağıdaki `DisplayIdentityInformation` örnek kodda gösterilen yöntem, arayanın kimliğini görüntüleyen bir yardımcı program işlevidir.  
  
```csharp
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tThread Identity            :{0}",  
         WindowsIdentity.GetCurrent().Name);  
    Console.WriteLine("\t\tThread Identity level  :{0}",
         WindowsIdentity.GetCurrent().ImpersonationLevel);  
    Console.WriteLine("\t\thToken                     :{0}",  
         WindowsIdentity.GetCurrent().Token.ToString());  
    return;  
}  
```  
  
 Hizmetteki yöntem, `Subtract` aşağıdaki örnek kodda gösterildiği gibi zorunlu çağrıları kullanarak arayanın kimliğine bürünmüş olur.  
  
```csharp
public double Subtract(double n1, double n2)  
{  
    double result = n1 - n2;  
    Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
    Console.WriteLine("Before impersonating");  
    DisplayIdentityInformation();  
  
    if (ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Impersonation ||  
        ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Delegation)  
    {  
        // Impersonate.  
        using (ServiceSecurityContext.Current.WindowsIdentity.Impersonate())  
        {  
            // Make a system call in the caller's context and ACLs
            // on the system resource are enforced in the caller's context.
            Console.WriteLine("Impersonating the caller imperatively");  
            DisplayIdentityInformation();  
        }  
    }  
    else  
    {  
        Console.WriteLine("ImpersonationLevel is not high enough to perform this operation.");  
    }  
  
    Console.WriteLine("After reverting");  
    DisplayIdentityInformation();  
    return result;  
}  
```  
  
 Bu durumda, arayanın tüm arama için taklit olmadığını, yalnızca aramanın bir bölümü için taklit edildiğini unutmayın. Genel olarak, en küçük kapsam için taklit tüm işlem için taklit etmek tercih edilir.  
  
 Diğer yöntemler arayanın kimliğine bürünmez.  
  
 İstemci kodu, kimliğe bürünme <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>düzeyini ' olarak ayarlamak üzere değiştirildi İstemci, numaralandırmayı kullanarak <xref:System.Security.Principal.TokenImpersonationLevel> hizmet tarafından kullanılacak kimliğe bürünme düzeyini belirtir. Numaralandırma <xref:System.Security.Principal.TokenImpersonationLevel.None>aşağıdaki değerleri destekler: , <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>ve . Windows ALA'ları kullanılarak korunan yerel makinedeki bir sistem kaynağına erişirken bir erişim denetimi <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>gerçekleştirmek için, kimliğe bürünme düzeyi aşağıdaki örnek kodda gösterildiği gibi ayarlanmalıdır.  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol pencerelerinde görüntülenir. Hizmeti ve istemciyi kapatmak için her konsol penceresinde ENTER tuşuna basın.  
  
> [!NOTE]
> Hizmet, idari bir hesap altında çalışmalı veya çalıştığı hesabın `http://localhost:8000/ServiceModelSamples` URI'yi HTTP katmanına kaydetme hakkı verilmelidir. Bu tür [haklar, Httpcfg.exe aracını](/windows/win32/http/httpcfg-exe)kullanarak bir [Namespace Rezervasyonu](/windows/win32/http/namespace-reservations-registrations-and-routing) ayarlayarak verilebilir.  
  
> [!NOTE]
> Windows Server 2003 çalıştıran bilgisayarlarda, kimliğe bürünme yalnızca Host.exe uygulaması Kimliğe Bürünme ayrıcalığına sahipse desteklenir. (Varsayılan olarak, yalnızca yöneticiler bu izne sahiptir.) Bu ayrıcalığı bir hesaba eklemek için hizmet, Yönetim Araçları'na gidin, Yerel Güvenlik **İlkesi'ni**açın, **Yerel** **İlkeler'i**açın, **Kullanıcı Hakları Ataması'nı**tıklatın ve Kimlik **Doğrulama'dan sonra İstemcili'yi taklit** etmeyi seçin ve kullanıcı veya grup eklemek için **Özellikleri** çift tıklatın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
4. Hizmetin arayanın kimliğine büründiyi göstermek için istemciyi, hizmetin altında çalıştırdığı hesaptan farklı bir hesap altında çalıştırın. Bunu yapmak için, komut istemi, yazın:  
  
    ```console  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     Daha sonra bir parola istenir. Daha önce belirttiğiniz hesabın parolasını girin.  
  
5. İstemciyi çalıştırdığınızda, farklı kimlik bilgileriyle çalıştırmadan önce ve sonra kimliği not edin.  
