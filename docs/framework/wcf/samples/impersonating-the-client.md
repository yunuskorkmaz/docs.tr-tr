---
title: İstemci Kimliğine Bürünme
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: 61befdcaf1381120dba6f72ba592dade09d0490a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968338"
---
# <a name="impersonating-the-client"></a>İstemci Kimliğine Bürünme
Kimliğe bürünme örneği, hizmetin çağıran adına sistem kaynaklarına erişebilmesi için çağıran uygulamanın nasıl taklit edilebilir olduğunu gösterir.  
  
 Bu örnek, [self-Host](../../../../docs/framework/wcf/samples/self-host.md) örneğine dayalıdır. Hizmet ve istemci yapılandırma dosyaları, [self-Host](../../../../docs/framework/wcf/samples/self-host.md) örneğindeki ile aynıdır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Hizmet kodu, hizmette `Add` yöntemi aşağıdaki örnek kodda gösterildiği <xref:System.ServiceModel.OperationBehaviorAttribute> gibi kullanarak çağıran tarafından taklit edilecek şekilde değiştirilmiştir.  
  
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
  
 Aşağıdaki örnek kodda gösterilen yöntemi,arayanınkimliğinigösterenbiryardımcıprogramdır.`DisplayIdentityInformation`  
  
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
  
 Hizmetindeki `Subtract` yöntemi, aşağıdaki örnek kodda gösterildiği gibi, çağrıyı yapanın zorunlu çağrıları kullanarak taklit eder.  
  
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
  
 İstemci kodu, kimliğe bürünme düzeyini olarak <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>ayarlanacak şekilde değiştirilmiştir. İstemci, <xref:System.Security.Principal.TokenImpersonationLevel> sabit listesini kullanarak hizmet tarafından kullanılacak kimliğe bürünme düzeyini belirtir. Sabit listesi şu değerleri destekler: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification> <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> ve <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. Windows ACL 'leri kullanılarak korunan yerel makinedeki bir sistem kaynağına erişirken erişim denetimi gerçekleştirmek için, aşağıdaki örnek kodda gösterildiği gibi kimliğe bürünme düzeyi olarak <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>ayarlanmalıdır.  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol penceresinde görüntülenir. Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.  
  
> [!NOTE]
> Hizmetin bir yönetim hesabı altında çalışması veya altında çalıştığı hesaba, `http://localhost:8000/ServiceModelSamples` URI 'yi http katmanıyla kaydetmek için haklar verilmelidir. Bu tür haklar, [Httpcfg. exe aracı](https://go.microsoft.com/fwlink/?LinkId=95010)kullanılarak bir [ad alanı ayırması](https://go.microsoft.com/fwlink/?LinkId=95012) ayarlanarak verilebilir.  
  
> [!NOTE]
> Çalıştıran [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]bilgisayarlarda, kimliğe bürünme yalnızca Host. exe uygulamasının kimliğe bürünme ayrıcalığına sahip olması durumunda desteklenir. (Varsayılan olarak, yalnızca Yöneticiler bu izne sahiptir.) Bu ayrıcalığı hizmetin çalıştığı bir hesaba eklemek için, **Yönetimsel Araçlar**' a gidin, **yerel güvenlik ilkesi**' ni açın, **Yerel Ilkeler**' i açın, **Kullanıcı hakları ataması**' nı seçin ve **sonra istemcinin özelliklerini Al ' ı seçin.** Kullanıcı veya grup eklemek için kimlik doğrulaması ve çift tıklama **özellikleri** .  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
4. Hizmetin çağıran tarafından taklit olduğunu göstermek için, istemciyi hizmetin altında çalıştığı farklı bir hesap altında çalıştırın. Bunu yapmak için, komut isteminde şunu yazın:  
  
    ```  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     Daha sonra parola girmeniz istenir. Daha önce belirttiğiniz hesabın parolasını girin.  
  
5. İstemcisini çalıştırdığınızda, kimliği farklı kimlik bilgileriyle çalıştırmadan önce ve sonra kimliği aklınızda edin.  
