---
title: İstemci Kimliğine Bürünme
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: b5272d8b4dbac60e14fe87accbb08a2073ed65ab
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594640"
---
# <a name="impersonating-the-client"></a>İstemci Kimliğine Bürünme
Kimliğe bürünme örneği, hizmetin çağıran adına sistem kaynaklarına erişebilmesi için çağıran uygulamanın nasıl taklit edilebilir olduğunu gösterir.  
  
 Bu örnek, [self-Host](self-host.md) örneğine dayalıdır. Hizmet ve istemci yapılandırma dosyaları, [self-Host](self-host.md) örneğindeki ile aynıdır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Hizmet kodu, `Add` hizmette yöntemi <xref:System.ServiceModel.OperationBehaviorAttribute> Aşağıdaki örnek kodda gösterildiği gibi kullanarak çağıran tarafından taklit edilecek şekilde değiştirilmiştir.  
  
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
  
 Sonuç olarak, çalışan iş parçacığının güvenlik bağlamı, `Add` yöntemi girmeden ve yönteminden çıkmadan geri döndürülmeden önce çağıranın kimliğine bürünülecek.  
  
 `DisplayIdentityInformation`Aşağıdaki örnek kodda gösterilen yöntemi, arayanın kimliğini gösteren bir yardımcı programdır.  
  
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
  
 `Subtract`Hizmetindeki yöntemi, aşağıdaki örnek kodda gösterildiği gibi, çağrıyı yapanın zorunlu çağrıları kullanarak taklit eder.  
  
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
  
 Bu durumda çağıranın tüm çağrı için kimliğe bürünmediğini ancak yalnızca çağrının bir bölümü için kimliğe bürünülmüş olduğunu unutmayın. Genel olarak, en küçük kapsam için kimliğe bürünme işleminin tamamı için kimliğe bürünme tercih edilir.  
  
 Diğer yöntemler çağıranın kimliğine bürünemez.  
  
 İstemci kodu, kimliğe bürünme düzeyini olarak ayarlanacak şekilde değiştirilmiştir <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> . İstemci, sabit listesini kullanarak hizmet tarafından kullanılacak kimliğe bürünme düzeyini belirtir <xref:System.Security.Principal.TokenImpersonationLevel> . Sabit listesi şu değerleri destekler: <xref:System.Security.Principal.TokenImpersonationLevel.None> , <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> , <xref:System.Security.Principal.TokenImpersonationLevel.Identification> <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> ve <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> . Windows ACL 'Leri kullanılarak korunan yerel makinedeki bir sistem kaynağına erişirken erişim denetimi gerçekleştirmek için, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> Aşağıdaki örnek kodda gösterildiği gibi kimliğe bürünme düzeyi olarak ayarlanmalıdır.  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol penceresinde görüntülenir. Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.  
  
> [!NOTE]
> Hizmetin bir yönetim hesabı altında çalışması veya altında çalıştığı hesaba, URI 'yi HTTP katmanıyla kaydetmek için haklar verilmelidir `http://localhost:8000/ServiceModelSamples` . Bu tür haklar, [Httpcfg. exe aracı](/windows/win32/http/httpcfg-exe)kullanılarak bir [ad alanı ayırması](/windows/win32/http/namespace-reservations-registrations-and-routing) ayarlanarak verilebilir.  
  
> [!NOTE]
> Windows Server 2003 çalıştıran bilgisayarlarda, kimliğe bürünme yalnızca Host. exe uygulamasının kimliğe bürünme ayrıcalığına sahip olması durumunda desteklenir. (Varsayılan olarak, yalnızca Yöneticiler bu izne sahiptir.) Bu ayrıcalığı hizmetin çalıştığı bir hesaba eklemek için, **Yönetimsel Araçlar**' a gidin, **yerel güvenlik ilkesi**' ni açın, **Yerel Ilkeler**' i açın, **Kullanıcı hakları ataması**' nı seçin ve **kimlik doğrulamasından sonra istemcinin özelliklerini al** ' ı seçin ve **Özellikler** ' i çift tıklatarak bir kullanıcı veya grup ekleyin.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
4. Hizmetin çağıran tarafından taklit olduğunu göstermek için, istemciyi hizmetin altında çalıştığı farklı bir hesap altında çalıştırın. Bunu yapmak için, komut isteminde şunu yazın:  
  
    ```console  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     Daha sonra parola girmeniz istenir. Daha önce belirttiğiniz hesabın parolasını girin.  
  
5. İstemcisini çalıştırdığınızda, kimliği farklı kimlik bilgileriyle çalıştırmadan önce ve sonra kimliği aklınızda edin.  
