---
title: "Nasıl yapılır: Korumalı Alanda Kısmen Güvenilen Kodu Çalıştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
caps.latest.revision: "27"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc335bfef4993f6e730dca93cd645d886a9d13b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a>Nasıl yapılır: Korumalı Alanda Kısmen Güvenilen Kodu Çalıştırma
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Korumalı alan kodu için kod erişim izinleri sınırlayan kısıtlı güvenlik ortamı çalışan uygulamadır. Yönetilen bir kitaplık tamamen güvenmediğiniz bir kaynaktan varsa, örneğin, onu tam olarak güvenilir olarak çalıştırılmamalıdır. Bunun yerine, izinlerini gerek beklediğiniz bu sınırlar bir korumalı alanı içinde kodu yerleştirmeniz (örneğin, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> izni).  
  
 Korumalı alan, kısmen güvenilen ortamlarında çalışır, dağıtma kodu test etmek için de kullanabilirsiniz.  
  
 Bir <xref:System.AppDomain> bir korumalı alan yönetilen uygulamaları için sağlama etkili bir yoldur. Kısmen güvenilen kod çalıştırmak için kullanılan uygulama etki alanları, içinde çalışırken kullanılabilir korunan kaynakları tanımlayan izinleriniz <xref:System.AppDomain>. İçinde çalışan kod <xref:System.AppDomain> ilişkili izinler tarafından bağlı <xref:System.AppDomain> ve yalnızca belirtilen kaynakları erişmesine izin verilir. <xref:System.AppDomain> De içeren bir <xref:System.Security.Policy.StrongName> tam olarak güvenilir olarak yüklenmiş olması gerektiğini derlemeleri tanımlamak için kullanılan bir dizi. Oluşturucusu, böylece bir <xref:System.AppDomain> tam olarak güvenilir olması belirli yardımcı derlemeler izin veren yeni bir korumalı etki alanı başlatmak için. Derlemeleri tam olarak yükleme için başka bir güvenilen genel derleme önbelleğinde yerleştirmek için bir seçenektir; Ancak, bu bilgisayarda oluşturulan tüm uygulama etki alanlarında derlemeleri tam güvenilir olarak yükler. Güçlü listesini destekler adları bir başına-<xref:System.AppDomain> sağlayan daha kısıtlayıcı belirleme kararı.  
  
 Kullanabileceğiniz <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> izni belirtmek için yöntemi aşırı yüklemesini ayarlamak korumalı alanda çalışan uygulamalar için. Bu aşırı istediğiniz kod erişim güvenliği tam düzeyini belirtmenize olanak sağlar. İçine yüklenmiş derlemeleri bir <xref:System.AppDomain> Bu aşırı kullanarak ya da sahip olabilirsiniz belirtilen kümesi yalnızca verin veya tam güvenilir olabilir. Derleme genel derleme önbelleğinde ise tam güven veya listelenen verilir `fullTrustAssemblies` ( <xref:System.Security.Policy.StrongName>) dizi parametresi. Yalnızca tam güvenilir olduğu bilinen derlemeler için eklenmesi `fullTrustAssemblies` listesi.  
  
 Aşırı aşağıdaki imzası vardır:  
  
```  
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 Parametrelerini <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> yöntemi aşırı yüklemesini belirtin adını <xref:System.AppDomain>, kanıt için <xref:System.AppDomain>, <xref:System.AppDomainSetup> korumalı alan, kullanmak üzere ayarlanmış izni ve güçlü adlar uygulama temel tanımlayan nesne tam güvenilir derlemeler.  
  
 Uygulama temel güvenlik nedeniyle, belirtilen `info` parametresi barındırma uygulama için temel uygulama olmalıdır.  
  
 İçin `grantSet` parametresini açıkça oluşturulan bir izin kümesi veya standart izin belirtebilirsiniz kümesi tarafından oluşturulan <xref:System.Security.SecurityManager.GetStandardSandbox%2A> yöntemi.  
  
 Çoğu aksine <xref:System.AppDomain> yükler, kanıt için <xref:System.AppDomain> (tarafından sağlanan `securityInfo` parametresi) kısmen güvenilir derlemeler için ayarlanmış grant belirlemek için kullanılmaz. Bunun yerine, bu bağımsız olarak tarafından belirtilen `grantSet` parametresi. Ancak, kanıt yalıtılmış depolama kapsamı belirleme gibi diğer amaçlar için kullanılabilir.  
  
### <a name="to-run-an-application-in-a-sandbox"></a>Korumalı alanda bir uygulamayı çalıştırmak için  
  
1.  Güvenilmeyen uygulamaya verilebilmesi için izni oluşturun. Vermek en az izni <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> izni. Ayrıca, ek izinler düşündüğünüz güvenilmeyen kod için güvenli verebilirsiniz; Örneğin, <xref:System.Security.Permissions.IsolatedStorageFilePermission>. Aşağıdaki kod yalnızca kümesiyle yeni bir izin oluşturur <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> izni.  
  
    ```  
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     Alternatif olarak, Internet gibi mevcut bir adlandırılmış izin kümesini kullanabilirsiniz.  
  
    ```  
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <xref:System.Security.SecurityManager.GetStandardSandbox%2A> Yöntemi döndürür ya da bir `Internet` izin kümesi veya `LocalIntranet` izni kanıt bölge bağlı olarak ayarlandı. <xref:System.Security.SecurityManager.GetStandardSandbox%2A>Ayrıca bazı başvuru olarak geçirilen kanıt nesneler kimlik izinlerini oluşturur.  
  
2.  Barındırma sınıfı içeren bütünleştirilmiş kodun oturum (adlı `Sandboxer` Bu örnekte) güvenilmeyen kod çağırır. Ekleme <xref:System.Security.Policy.StrongName> derlemeye imzalamak için kullanılan <xref:System.Security.Policy.StrongName> dizisi `fullTrustAssemblies` parametresinin <xref:System.AppDomain.CreateDomain%2A> çağırın. Barındırma sınıfı çalıştırmalısınız, kısmi güven kodunun yürütülmesini etkinleştirmek veya kısmi güven uygulama hizmet sunmak için tam olarak güvenilir olarak. Nasıl okuma budur <xref:System.Security.Policy.StrongName> derleme:  
  
    ```  
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     Mscorlib ve System.dll gibi .NET framework derlemeleri genel derleme önbelleğinden tam olarak güvenilir olarak yüklenen oldukları için tam güven listesine eklenmesi gerekmez.  
  
3.  Initialize <xref:System.AppDomainSetup> parametresinin <xref:System.AppDomain.CreateDomain%2A> yöntemi. Yeni ayarların çoğu denetim bu parametreyle <xref:System.AppDomain>. <xref:System.AppDomainSetup.ApplicationBase%2A> Özelliği önemli bir ayardır ve farklı olmalıdır <xref:System.AppDomainSetup.ApplicationBase%2A> özelliği için <xref:System.AppDomain> barındırma uygulamasının. Varsa <xref:System.AppDomainSetup.ApplicationBase%2A> ayarların aynı olduğundan, kısmi güven uygulama (tam olarak güvenilen) bir özel durum, tanımlar, böylece yararlanmasını yüklemek için barındırma uygulama elde edebilirsiniz. Neden bir catch (özel) önerilmez başka bir neden de budur. Uygulama ayarı korumalı uygulamanın uygulama temel konaktan farklı tabanı açıkları riskini azaltır.  
  
    ```  
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4.  Çağrı <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> belirtilen parametreleri kullanarak uygulama etki alanı oluşturmak için yöntemi aşırı yüklemesini.  
  
     Bu yöntem için imza şöyledir:  
  
    ```  
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     Ek bilgiler:  
  
    -   Bu, yalnızca aşırı yüklemesi, <xref:System.AppDomain.CreateDomain%2A> yönteminin alan bir <xref:System.Security.PermissionSet> bir kısmi güven ayarı uygulamada bir parametre ve böylece olanak sağlayan yalnızca aşırı yük.  
  
    -   `evidence` Parametresi bir izin kümesi hesaplamak için kullanılan değil; tanımlama için .NET Framework'ün diğer özellikler tarafından kullanılır.  
  
    -   Ayarı <xref:System.AppDomainSetup.ApplicationBase%2A> özelliği `info` için bu aşırı parametresi zorunludur.  
  
    -   `fullTrustAssemblies` Parametresine sahip `params` oluşturmak için gerekli olmadığı anlamına gelir anahtar sözcüğü bir <xref:System.Security.Policy.StrongName> dizi. 0, 1 veya daha fazla tanımlayıcı adlar parametre olarak geçirme izin verilir.  
  
    -   Uygulama etki alanı oluşturmak için kodu verilmiştir:  
  
    ```  
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5.  Korumalı alan kod yüklenemiyor <xref:System.AppDomain> oluşturduğunuz. Bu iki yolla yapılabilir:  
  
    -   Çağrı <xref:System.AppDomain.ExecuteAssembly%2A> derleme için yöntem.  
  
    -   Kullanım <xref:System.Activator.CreateInstanceFrom%2A> sınıfının bir örneği oluşturmak için yöntemi türetilen <xref:System.MarshalByRefObject> yeni <xref:System.AppDomain>.  
  
     Yeni parametreleri kolaylaştırır ikinci yöntem tercih, çünkü <xref:System.AppDomain> örneği. <xref:System.Activator.CreateInstanceFrom%2A> Yöntemi iki önemli özellikleri sağlar:  
  
    -   Derlemenizi içermeyen bir konuma işaret eden bir kod temeli kullanabilirsiniz.  
  
    -   Oluşturma altında yapabileceğiniz bir <xref:System.Security.CodeAccessPermission.Assert%2A> tam güven için (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), kritik sınıfının bir örneği oluşturmanıza olanak sağlar. (Derlemenizi hiçbir saydamlık işaretler varsa ve tam olarak güvenilir olarak yüklü olduğu her meydana gelir.) Bu nedenle, bu işlev yalnızca güvendiğiniz kodu oluşturmak dikkatli olmak zorunda ve yeni uygulama etki alanında yalnızca tam olarak güvenilmeyen sınıfların örnekleri oluşturmanızı öneririz.  
  
    ```  
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     Yeni bir etki alanı sınıfının bir örneği oluşturmak için sınıfı genişletmek sahip olduğuna dikkat edin <xref:System.MarshalByRefObject> sınıfı  
  
    ```  
    class Sandboxer:MarshalByRefObject  
    ```  
  
6.  Bu etki alanındaki bir başvuru yeni etki alanı örneğine açılacak. Bu başvuru, güvenilmeyen kod yürütmek için kullanılır.  
  
    ```  
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7.  Çağrı `ExecuteUntrustedCode` örneğini yönteminde `Sandboxer` oluşturduğunuz sınıfı.  
  
    ```  
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     Bu çağrı, sınırlı izinlere sahip korumalı uygulama etki alanında yürütülür.  
  
    ```  
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
        {  
            //Load the MethodInfo for a method in the new assembly. This might be a method you know, or   
            //you can use Assembly.EntryPoint to get to the entry point in an executable.  
            MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
            try  
            {  
                // Invoke the method.  
                target.Invoke(null, parameters);  
            }  
            catch (Exception ex)  
            {  
            //When information is obtained from a SecurityException extra information is provided if it is   
            //accessed in full-trust.  
                (new PermissionSet(PermissionState.Unrestricted)).Assert();  
                Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
    CodeAccessPermission.RevertAssert();  
                Console.ReadLine();  
            }  
        }  
    ```  
  
     <xref:System.Reflection>kısmen güvenilen bütünleştirilmiş kodunda bir yöntem tanıtıcısı almak için kullanılır. Tanıtıcı minimum izinleri ile güvenli bir şekilde kod yürütmek için kullanılabilir.  
  
     Önceki kodda Not <xref:System.Security.PermissionSet.Assert%2A> yazdırma önce tam güven izni <xref:System.Security.SecurityException>.  
  
    ```  
    new PermissionSet(PermissionState.Unrestricted)).Assert()  
    ```  
  
     Tam güven assert genişletilmiş bilgileri elde etmek için kullanılan <xref:System.Security.SecurityException>. Olmadan <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.SecurityException.ToString%2A> yöntemi <xref:System.Security.SecurityException> yığında kısmen güvenilen kod olduğunu keşfeder ve dönen bilgiyi kısıtlar. Kısmi güven kodunun bu bilgileri, ancak riski getirdiği değil vererek okuyabilir, bu güvenlik sorunlarına neden olabileceği <xref:System.Security.Permissions.UIPermission>. Tam güven assert olabildiğince az kullanılmalıdır ve yalnızca, eminseniz, tam güven yükseltmesine kısmi güven kodunun izin. Bir kural olarak, aynı işlevde ve assert için tam güven adlı sonra güvenmediğiniz kod çağırmayın. Bunu kullanmayı bitirdikten sonra her zaman assert dönmek için iyi bir uygulamadır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yordam önceki bölümde uygular. Örnekte, bir proje adlı `Sandboxer` Visual Studio'da Çözüm ayrıca adlı bir proje içeren `UntrustedCode`, sınıf uygulayan `UntrustedClass`. Bu senaryo döndürmek için beklenen bir yöntem içeren Kitaplık derlemesi indirmiş varsayar `true` veya `false` sayı Fibonacci sayı sağladığınız olup olmadığını belirtmek için. Bunun yerine, yöntemi, bir dosyayı bilgisayarınızdan okumaya çalışır. Aşağıdaki örnek, güvenilmeyen kodu gösterir.  
  
```  
using System;  
using System.IO;  
namespace UntrustedCode  
{  
    public class UntrustedClass  
    {  
        // Pretend to be a method checking if a number is a Fibonacci  
        // but which actually attempts to read a file.  
        public static bool IsFibonacci(int number)  
        {  
           File.ReadAllText("C:\\Temp\\file.txt");  
           return false;  
        }  
    }  
}  
```  
  
 Aşağıdaki örnekte gösterildiği `Sandboxer` güvenilmeyen kodu yürütür uygulama kodu.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Security;  
using System.Security.Policy;  
using System.Security.Permissions;  
using System.Reflection;  
using System.Runtime.Remoting;  
  
//The Sandboxer class needs to derive from MarshalByRefObject so that we can create it in another   
// AppDomain and refer to it from the default AppDomain.  
class Sandboxer : MarshalByRefObject  
{  
    const string pathToUntrusted = @"..\..\..\UntrustedCode\bin\Debug";  
    const string untrustedAssembly = "UntrustedCode";  
    const string untrustedClass = "UntrustedCode.UntrustedClass";  
    const string entryPoint = "IsFibonacci";  
    private static Object[] parameters = { 45 };  
    static void Main()  
    {  
        //Setting the AppDomainSetup. It is very important to set the ApplicationBase to a folder   
        //other than the one in which the sandboxer resides.  
        AppDomainSetup adSetup = new AppDomainSetup();  
        adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
  
        //Setting the permissions for the AppDomain. We give the permission to execute and to   
        //read/discover the location where the untrusted code is loaded.  
        PermissionSet permSet = new PermissionSet(PermissionState.None);  
        permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
  
        //We want the sandboxer assembly's strong name, so that we can add it to the full trust list.  
        StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
  
        //Now we have everything we need to create the AppDomain, so let's create it.  
        AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
  
        //Use CreateInstanceFrom to load an instance of the Sandboxer class into the  
        //new AppDomain.   
        ObjectHandle handle = Activator.CreateInstanceFrom(  
            newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
            typeof(Sandboxer).FullName  
            );  
        //Unwrap the new domain instance into a reference in this domain and use it to execute the   
        //untrusted code.  
        Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
        newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    }  
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new Assembly. This might be a method you know, or   
        //you can use Assembly.EntryPoint to get to the main function in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            //Now invoke the method.  
            bool retVal = (bool)target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
            // When we print informations from a SecurityException extra information can be printed if we are   
            //calling it with a full-trust stack.  
            (new PermissionSet(PermissionState.Unrestricted)).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
