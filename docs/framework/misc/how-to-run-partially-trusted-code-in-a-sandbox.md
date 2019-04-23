---
title: 'Nasıl yapılır: Korumalı alanda kısmen güvenilen kodu çalıştırma'
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
author: mairaw
ms.author: mairaw
ms.openlocfilehash: caa9afcb1ab2ca53bba849c39651ca4cba3a9c77
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59316537"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a>Nasıl yapılır: Korumalı alanda kısmen güvenilen kodu çalıştırma
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Korumalı alana alma kodu için kod erişim izinleri sınırlar bir kısıtlı güvenlik ortamı çalışan uygulamadır. Tamamen güvenmediğiniz bir kaynaktan bir yönetilen kitaplık varsa, örneğin, bu tam olarak güvenilir olarak çalıştırmamalısınız. Bunun yerine, gerek bekliyorsanız bu izinlerini sınırlayan bir korumalı alan içinde kod yerleştirmeniz gerekir (örneğin, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> izni).  
  
 Korumalı alana alma, dağıtma ve kısmen güvenilen ortamlarda çalışacak kodu test etmek için de kullanabilirsiniz.  
  
 Bir <xref:System.AppDomain> yönetilen uygulamalar için bir korumalı alan sağlayan etkili bir yoludur. Kısmen güvenilen kod çalıştırmak için kullanılan uygulama etki alanları, içinde çalışırken kullanılabilir korumalı kaynakları tanımlayan izinlere sahip <xref:System.AppDomain>. İçinde çalışan kod <xref:System.AppDomain> ilişkili izinler tarafından bağlı <xref:System.AppDomain> ve yalnızca belirtilen kaynaklara erişmesine izin verilir. <xref:System.AppDomain> De içeren bir <xref:System.Security.Policy.StrongName> tam güvenilir olarak yüklenmesi için derlemeleri tanımlamak için kullanılan bir dizi. Oluşturucusu, böylece bir <xref:System.AppDomain> belirli yardımcı derlemeler tam olarak güvenilen veren yeni bir korumalı etki alanı başlatmak için. Derlemeleri tam olarak yüklenmesi için başka bir güvenilir genel derleme önbelleğinde yerleştirileceği bir seçenektir; Ancak, bu bilgisayar üzerinde oluşturulan tüm uygulama etki alanları olarak tam olarak güvenilen derlemelerde yükler. Güçlü listesini adları destekleyen bir başına-<xref:System.AppDomain> sağlayan daha kısıtlayıcı belirleme kararı.  
  
 Kullanabileceğiniz <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> korumalı alanında çalışan uygulamalar için izin belirtmek üzere yöntem aşırı yüklemesini ayarlayın. Bu aşırı yüklemesi, istediğiniz kod erişim güvenliği düzeyini tam olarak belirtmenizi sağlar. İçine yüklenen derlemeler bir <xref:System.AppDomain> Bu aşırı yüklemesi kullanarak ya da sahip olabilirsiniz belirtilen izin kümesine yalnızca veya tam güvenilir olabilir. Derleme genel derleme önbelleğinde ise tam güven veya listelenen verilir `fullTrustAssemblies` ( <xref:System.Security.Policy.StrongName>) dizi parametresi. Sadece tam güvenilir olduğu bilinen derleme eklenmesi `fullTrustAssemblies` listesi.  
  
 Aşağıdaki imza aşırı yüklemesi vardır:  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 Parametreler için <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> yöntemi aşırı yüklemesi adını belirtin <xref:System.AppDomain>, için olan kanıtları <xref:System.AppDomain>, <xref:System.AppDomainSetup> korumalı alan ve izin kümesini kullanmak için tanımlayıcı adlar için uygulama temel tanımlayan nesne tamamen güvenilir derlemelerinin.  
  
 Güvenlik nedeniyle, uygulama tabanı belirtilen `info` barındırma uygulaması için temel uygulama parametresi olmamalıdır.  
  
 İçin `grantSet` parametresi belirtebileceğiniz açıkça oluşturulan bir izin kümesi ya da bir standart izin kümesi tarafından oluşturulan <xref:System.Security.SecurityManager.GetStandardSandbox%2A> yöntemi.  
  
 Çoğu aksine <xref:System.AppDomain> yükler, için olan kanıtları <xref:System.AppDomain> (tarafından sağlanan `securityInfo` parametresi) kısmen güvenilen derlemelerde kodların belirlemek için kullanılmaz. Bunun yerine, bağımsız olarak tarafından belirtilen `grantSet` parametresi. Ancak, kanıt yalıtılmış depolama kapsamı belirleme gibi diğer amaçlar için kullanılabilir.  
  
### <a name="to-run-an-application-in-a-sandbox"></a>Bir korumalı alan içinde bir uygulamayı çalıştırmak için  
  
1. İzin güvenilmeyen uygulamanın verilecek kümesini oluşturun. En düşük izin vermesi <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> izni. Ayrıca, ek izinler düşündüğünüz güvenilmeyen kod için güvenli verebilirsiniz; Örneğin, <xref:System.Security.Permissions.IsolatedStorageFilePermission>. Aşağıdaki kod ile yalnızca olarak yeni bir izin oluşturur <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> izni.  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     Alternatif olarak, Internet gibi mevcut bir adlandırılmış izin kümesi kullanabilirsiniz.  
  
    ```  
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <xref:System.Security.SecurityManager.GetStandardSandbox%2A> Yöntemi döndürür ya da bir `Internet` izin kümesi veya `LocalIntranet` izin dilimine bağlı olarak bir kanıt kümesi. <xref:System.Security.SecurityManager.GetStandardSandbox%2A> Ayrıca bazı başvurular geçirilen kanıt nesneler kimlik izinlerini oluşturur.  
  
2. Barındırma sınıfı içeren derlemeyi imzalamayı (adlı `Sandboxer` Bu örnekte), güvenilmeyen kod çağırır. Ekleme <xref:System.Security.Policy.StrongName> için derlemeyi imzalamak için kullanılan <xref:System.Security.Policy.StrongName> dizisi `fullTrustAssemblies` parametresinin <xref:System.AppDomain.CreateDomain%2A> çağırın. Barındıran sınıf çalıştırmalısınız kısmi güven kodunun yürütülmesini etkinleştirmek veya kısmi güven uygulama hizmet sunmak için tam olarak güvenilen olarak. Bu, nasıl olduğunu okuyun, <xref:System.Security.Policy.StrongName> derleme:  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     Mscorlib ve System.dll gibi .NET framework derlemeleri genel bütünleştirilmiş kod önbelleğinden tam güvenilir yüklü oldukları için tam güven listesine eklenmesi gerekmez.  
  
3. Başlatma <xref:System.AppDomainSetup> parametresinin <xref:System.AppDomain.CreateDomain%2A> yöntemi. Bu parametre ile yeni ayarların birçoğunu denetleyebilirsiniz <xref:System.AppDomain>. <xref:System.AppDomainSetup.ApplicationBase%2A> Özelliği önemli bir ayardır ve farklı olmalıdır <xref:System.AppDomainSetup.ApplicationBase%2A> özelliği <xref:System.AppDomain> barındırma uygulaması. Varsa <xref:System.AppDomainSetup.ApplicationBase%2A> ayarların aynı olduğundan, kısmi güven uygulama tanımlar, böylece kötüye kullanan bir özel durum (tam olarak güvenilir) yüklemek için barındırma uygulaması elde edebilirsiniz. Neden bir catch (özel durum) önerilmez başka bir nedeni budur. Uygulama ayarı tabanı konaktan farklı uygulama tabanı koruma alanlı uygulama açıkları riski azaltır.  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. Çağrı <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> belirtilen parametreleri kullanarak uygulama etki alanı oluşturmak için yöntem aşırı yüklemesi.  
  
     Bu yöntem imzası verilmiştir:  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     Ek bilgiler:  
  
    -   Bu, yalnızca aşırı yüklemesini <xref:System.AppDomain.CreateDomain%2A> gereken yöntemini bir <xref:System.Security.PermissionSet> bir parametre ve bu nedenle sağlayan tek bir aşırı yükleme bir kısmi güven ortamında bir uygulama yüklemek gibi.  
  
    -   `evidence` Parametresi bir izin kümesi hesaplamak için kullanılan değil; kimlik doğrulaması için .NET Framework'ün diğer özellikler tarafından kullanılır.  
  
    -   Ayarı <xref:System.AppDomainSetup.ApplicationBase%2A> özelliği `info` için bu aşırı yükleme parametresi zorunludur.  
  
    -   `fullTrustAssemblies` Parametresinin `params` oluşturmak gerekli değildir, yani anahtar sözcüğü bir <xref:System.Security.Policy.StrongName> dizi. 0, 1 veya daha fazla tanımlayıcı adlar parametre olarak geçirmeyi izin verilir.  
  
    -   Uygulama etki alanı oluşturmak için kod yer almaktadır:  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. Kod içinde korumalı alana alma yüklemeye <xref:System.AppDomain> oluşturduğunuz. Bu iki şekilde gerçekleştirilebilir:  
  
    -   Çağrı <xref:System.AppDomain.ExecuteAssembly%2A> derleme için yöntemi.  
  
    -   Kullanım <xref:System.Activator.CreateInstanceFrom%2A> sınıfından türetilen bir sınıfın bir örneğini oluşturmak için gereken yöntemini <xref:System.MarshalByRefObject> yeni <xref:System.AppDomain>.  
  
     Yeni parametreleri geçirmek kolaylaştırır ikinci yöntem tercih, çünkü <xref:System.AppDomain> örneği. <xref:System.Activator.CreateInstanceFrom%2A> Yöntemi iki önemli özellikleri sağlar:  
  
    -   Derlemenizi içermeyen bir konumu gösteren bir kod tabanına kullanabilirsiniz.  
  
    -   Oluşturma aşamasında yapabileceğiniz bir <xref:System.Security.CodeAccessPermission.Assert%2A> tam güven için (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), kritik bir sınıf örneği oluşturmanızı sağlar. (Derlemenizi hiçbir saydamlık işaretler sahip ve tamamen güvenilir olarak yüklenen her meydana gelir.) Bu nedenle, bu işlevle yalnızca güvendiğiniz kod oluşturmak dikkatli olmak zorunda ve yeni uygulama etki alanında yalnızca tam olarak güvenilen sınıfların örneklerini oluşturmanızı öneririz.  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     Yeni bir etki alanında bir sınıfın bir örneğini oluşturmak için sınıf genişletmek sahip olduğuna dikkat edin <xref:System.MarshalByRefObject> sınıfı  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. Yeni etki alanı örneğe bir başvuru bu etki alanında sarmalamadan çıkarma. Bu başvuru, güvenilmeyen kod yürütmek için kullanılır.  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. Çağrı `ExecuteUntrustedCode` örneğinde yöntemi `Sandboxer` oluşturduğunuz sınıfı.  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     Bu çağrı, sınırlı izinlere sahip koruma alanlı uygulama etki alanında yürütülür.  
  
    ```csharp
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
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
    ```  
  
     <xref:System.Reflection> kısmen güvenilen bir derleme içinde bir yöntemin bir tanıtıcı almak için kullanılır. Tanıtıcı, en düşük izinleri ile güvenli bir şekilde kod yürütmek için kullanılabilir.  
  
     Önceki kodda, Not <xref:System.Security.PermissionSet.Assert%2A> yazdırmadan önce tam güven izni <xref:System.Security.SecurityException>.  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     Genişletilmiş bilgileri elde etmek için kullanılan tam güven assert <xref:System.Security.SecurityException>. Olmadan <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.SecurityException.ToString%2A> yöntemi <xref:System.Security.SecurityException> yığında kısmen güvenilen kod olduğunu bulacak ve döndürülen bilgileri kısıtlar. Bu bilgiler, ancak bu riski azaltılabilir vermeyerek tarafından kısmi güven kodu okuyabilir, bu güvenlik sorunlarına neden olabileceği <xref:System.Security.Permissions.UIPermission>. Tam güven assert kullanılmamalıdır ve yalnızca, eminseniz, kısmi güven kodu için tam güven yükseltmesine izin. Bir kural olarak, aynı işlevde ve tam güven için bir onay olarak adlandırılan sonra kod yazmadan çağırmayın. Assert kullanmayı bitirdiğinizde her zaman geri dönmek için iyi bir uygulamadır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, önceki bölümde yordamı uygular. Örnekte, bir proje adlı `Sandboxer` Visual Studio'da Çözüm ayrıca adlı bir proje içeren `UntrustedCode`, sınıf uygulayan `UntrustedClass`. Bu senaryo dönmesi beklenen bir yöntem içeren bir kitaplık derlemesine yüklediğiniz varsayılır `true` veya `false` sayı, Fibonacci sayı sağlanıp sağlanmadığını belirtmek için. Bunun yerine, bilgisayarınızda bir dosyayı okumak yöntem çalışır. Aşağıdaki örnek, güvenilmeyen kod gösterir.  
  
```csharp
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
  
 Aşağıdaki örnekte gösterildiği `Sandboxer` güvenilmeyen kod yürüten bir uygulama kodu.  
  
```csharp
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
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
