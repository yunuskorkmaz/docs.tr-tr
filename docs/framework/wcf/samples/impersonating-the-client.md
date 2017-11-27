---
title: "İstemci Kimliğine Bürünme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
caps.latest.revision: "25"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f4cf1c05c1cbb75796f73f944340e36dbda0d1af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="impersonating-the-client"></a>İstemci Kimliğine Bürünme
Kimliğe bürünme örneği, hizmetin sistem kaynaklarını arayan adına erişebilmesi için hizmet çağıran uygulamayı taklit gösterilmiştir.  
  
 Bu örnek dayanır [kendini barındırma](../../../../docs/framework/wcf/samples/self-host.md) örnek. Hizmet ve istemci yapılandırma dosyalarının aynı olduğundan [kendini barındırma](../../../../docs/framework/wcf/samples/self-host.md) örnek.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Hizmet koduna değiştirilmiş şekilde `Add` hizmetinde yöntemini kullanarak arayana taklit <xref:System.ServiceModel.OperationBehaviorAttribute> aşağıdaki örnek kodda gösterildiği gibi.  
  
```  
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
  
 Sonuç olarak, yürütme iş parçacığı güvenlik bağlamında girmeden önce çağıran kimliğine bürünmek için geçiş yapıldı `Add` yöntemi ve yönteminden çıkılıyor üzerinde geri döndürüldü.  
  
 `DisplayIdentityInformation` Aşağıdaki örnek kodda gösterildiği çağrı sahibinin kimliğini görüntüler bir yardımcı programı işlevi yöntemidir.  
  
```  
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
  
 `Subtract` Hizmetinde yöntemini aşağıdaki örnek kodda gösterildiği gibi kesinlik temelli çağrıları kullanarak arayana temsil eder.  
  
```  
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
  
 Bu durumda çağıran tüm çağrısı için Kimliğine bürünülen değil ancak yalnızca çağrısı bir kısmı için Kimliğine bürünülen unutmayın. Genel olarak, en küçük kapsam için kimliğine bürünmek için tüm işlem kimliğine bürünmek için tercih edilir.  
  
 Diğer yöntemlerini çağıran kimliğine bürünme.  
  
 Kimliğe bürünme düzeyini ayarlamak için istemci kodu değiştirilmiş <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>. İstemci kullanarak hizmeti tarafından kullanılacak kimliğe bürünme düzeyini belirtir <xref:System.Security.Principal.TokenImpersonationLevel> numaralandırması. Aşağıdaki değerleri numaralandırması destekler: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> ve <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. Yerel makinedeki Windows ACL'leri kullanarak korumalı bir sistem kaynağı erişirken bir erişim denetimi gerçekleştirmek için kimliğe bürünme düzeyi ayarlanmalıdır <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, aşağıdaki örnek kodda gösterildiği gibi.  
  
```  
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını hem hizmet hem de istemci konsol pencerelerinde görüntülenir. Her konsol penceresinde hizmet ve istemci kapatmak için ENTER tuşuna basın.  
  
> [!NOTE]
>  Hizmeti ya da bir yönetici hesabı altında çalışmalıdır veya altında çalıştığı hesabın 8000/ServiceModelSamples URI HTTP katmanla kaydetme hakkı verilmesi gerekir. Ayarlama işlemleri tarafından gibi haklar verilebilir bir [Namespace ayırma](http://go.microsoft.com/fwlink/?LinkId=95012) kullanarak [Httpcfg.exe aracı](http://go.microsoft.com/fwlink/?LinkId=95010).  
  
> [!NOTE]
>  Çalıştıran bilgisayarlarda [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], kimliğe bürünme yalnızca Host.exe uygulama kimliğe bürünme ayrıcalığı varsa desteklenir. (Varsayılan olarak, yalnızca Yöneticiler bu izne sahip.) Hizmet olarak çalıştığı bir hesabın bu ayrıcalık eklemek için Git **Yönetimsel Araçlar**açın **yerel güvenlik ilkesi**, açık **yerel ilkeler**, tıklatın**Kullanıcı hakları ataması**seçip **kimlik doğrulamasından sonra istemcinin** çift tıklayın ve **özellikleri** bir kullanıcı veya grup eklemek için.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
4.  Hizmet arayan taklit göstermek için İstemci hizmetinin altında çalışmakta olduğu olandan farklı bir hesap altında çalıştırın. Bunun için komut satırına aşağıdakini yazın:  
  
    ```  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     Ardından bir parola istenir. Önceden belirttiğiniz hesabının parolasını girin.  
  
5.  İstemci çalıştırdığınızda, önce ve farklı kimlik bilgileriyle çalıştırdıktan sonra kimliğini not edin.  
  
## <a name="see-also"></a>Ayrıca Bkz.
