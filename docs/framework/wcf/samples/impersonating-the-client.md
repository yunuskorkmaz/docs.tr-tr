---
title: İstemci Kimliğine Bürünme
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: d79ce0d189fc88310594f356f1901d93b3e1e06f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954979"
---
# <a name="impersonating-the-client"></a>İstemci Kimliğine Bürünme
Kimliğe bürünme örneği, hizmet adına çağıran sistem kaynaklarına erişebilmesi çağıran uygulama hizmetine bürünülecek gösterilmiştir.  
  
 Bu örnek dayanır [barındırma](../../../../docs/framework/wcf/samples/self-host.md) örnek. Hizmet ve istemci yapılandırma dosyalarını, aynı olan [barındırma](../../../../docs/framework/wcf/samples/self-host.md) örnek.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Hizmet kodu değiştirilmiş gibi `Add` yöntemi hizmet kimliğine bürünür, çağrıyı <xref:System.ServiceModel.OperationBehaviorAttribute> aşağıdaki örnek kodda gösterildiği gibi.  
  
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
  
 Sonuç olarak, çalışan bir iş parçacığı güvenlik bağlamında girmeden önce çağıranın kimliğine bürünüp moduna `Add` yöntemi yönteminden çıkılıyor üzerinde geri alındığı bir durumdur.  
  
 `DisplayIdentityInformation` Aşağıdaki örnek kodda gösterilen çağıranının kimliğini görüntüler bir yardımcı program işlevi yöntemidir.  
  
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
  
 `Subtract` Hizmet yöntemi, kesinlik temelli çağrı aşağıdaki örnek kodda gösterildiği gibi çağrıyı temsil eder.  
  
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
  
 Bu durumda arayan için tüm arama temsili değildir ancak yalnızca bir kısmını arama için Kimliğine bürünülen unutmayın. Genel olarak, en küçük kapsam için kimliğine bürünmek için tüm işlem kimliğine bürünmek için tercih edilir.  
  
 Diğer yöntemleri çağıran kimliğine bürünme.  
  
 Kimliğe bürünme düzeyini ayarlamak için istemci kodu değiştirilmiş <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>. İstemcinin kimliğe bürünme düzeyi kullanarak hizmeti tarafından kullanılacak belirtir <xref:System.Security.Principal.TokenImpersonationLevel> sabit listesi. Numaralandırma aşağıdaki değerlerini destekler: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> ve <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. Yerel makinedeki Windows ACL'leri kullanarak korumalı bir sistem kaynağını erişirken bir erişim denetimi gerçekleştirmek için kimliğe bürünme düzeyi ayarlanmalıdır <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>aşağıdaki örnek kodda gösterildiği gibi.  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını hem hizmet hem de istemci konsol pencerelerinde görüntülenir. Her konsol penceresi hizmet ve istemci kapatmak için ENTER tuşuna basın.  
  
> [!NOTE]
>  Bir yönetici hesabı altında ya da çalışan hizmet gerekir veya altında çalıştığı hesabı kaydetme hakkı verilmesi `http://localhost:8000/ServiceModelSamples` URI HTTP katman. Oluşturarak bu hakların verilmesi bir [Namespace ayırma](https://go.microsoft.com/fwlink/?LinkId=95012) kullanarak [Httpcfg.exe aracı](https://go.microsoft.com/fwlink/?LinkId=95010).  
  
> [!NOTE]
>  Çalıştıran bilgisayarlarda [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], kimliğe bürünme, yalnızca Host.exe uygulamanın kimliğe bürünme ayrıcalık varsa desteklenir. (Varsayılan olarak, yalnızca Yöneticiler bu izne sahip.) Hizmet olarak çalıştığı bir hesabın bu ayrıcalığı eklemek için Git **Yönetimsel Araçlar**açın **yerel güvenlik ilkesi**açın **yerel ilkeler**, tıklayın**Kullanıcı hakları ataması**seçip **kimlik doğrulamasından sonra istemcinin özelliklerini al** ve çift **özellikleri** bir kullanıcı veya grup eklemek için.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
4. Hizmet, çağıranın kimliğine bürünür göstermek için İstemci hizmetinin altında çalışmakta olduğu olandan farklı bir hesap altında çalıştırın. Komut isteminde Bunu yapmak için şunu yazın:  
  
    ```  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     Ardından, bir parola istenir. Daha önce belirtilen hesap için parolayı girin.  
  
5. İstemci çalıştırdığınızda, önce ve sonra onu farklı kimlik bilgileri ile çalıştırma kimliğini not edin.  
