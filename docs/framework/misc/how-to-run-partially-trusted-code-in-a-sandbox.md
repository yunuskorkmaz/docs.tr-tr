---
title: 'Nasıl yapılır: Korumalı Alanda Kısmen Güvenilen Kodu Çalıştırma'
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
ms.openlocfilehash: 0191846f5589b0162ba342161fb5919ff20099d4
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215855"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a>Nasıl yapılır: Korumalı Alanda Kısmen Güvenilen Kodu Çalıştırma
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Korumalı alana alma, kodu, koda verilen erişim izinlerini sınırlayan kısıtlı bir güvenlik ortamında çalıştırmaya yönelik bir uygulamadır. Örneğin, tam olarak güvenmediğiniz bir kaynaktan yönetilen bir kitaplığınız varsa, bunu tam güvenilir olarak çalıştırmanız gerekir. Bunun yerine, kodu, izinlerini beklediğinizi (örneğin, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> izin) sınırlayan bir korumalı alana yerleştirmeniz gerekir.  
  
 Ayrıca, dağıtmak istediğiniz kodu, kısmen güvenilen ortamlarda çalışacak şekilde test etmek için korumalı alana alma kullanabilirsiniz.  
  
 <xref:System.AppDomain>, yönetilen uygulamalar için korumalı alan sağlamanın etkili bir yoludur. Kısmen güvenilen kodu çalıştırmak için kullanılan uygulama etki alanları, bu <xref:System.AppDomain>içinde çalışırken kullanılabilir olan korumalı kaynakları tanımlayan izinlere sahiptir. <xref:System.AppDomain> içinde çalışan kod, <xref:System.AppDomain> ilişkili izinlerle ilişkilidir ve yalnızca belirtilen kaynaklara erişmesine izin verilir. <xref:System.AppDomain> Ayrıca, tam güvenilir olarak yüklenecek derlemeleri tanımlamak için kullanılan bir <xref:System.Security.Policy.StrongName> dizisi içerir. Bu, bir <xref:System.AppDomain> oluşturucusunun belirli yardımcı derlemelerin tam olarak güvenilir olmasını sağlayan yeni bir korumalı etki alanı başlatmasını sağlar. Derlemeleri tamamen güvenilir olarak yüklemek için başka bir seçenek de bunları genel derleme önbelleğine yerleştirmelidir; Ancak, derlemeleri bu bilgisayarda oluşturulan tüm uygulama etki alanlarında tam güvenilir olarak yükler. Tanımlayıcı adların listesi, daha kısıtlayıcı belirleme sağlayan<xref:System.AppDomain> başına bir kararı destekler.  
  
 Bir korumalı alanda çalışan uygulamalar için izin kümesini belirtmek üzere <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> yöntemi aşırı yüklemesini kullanabilirsiniz. Bu aşırı yükleme, istediğiniz kod erişimi güvenliğinin tam düzeyini belirtmenize olanak sağlar. Bu aşırı yükleme kullanılarak bir <xref:System.AppDomain> yüklenen derlemeler yalnızca belirtilen izin kümesine sahip olabilir veya tam olarak güvenilir olabilir. Bütünleştirilmiş kod, genel derleme önbelleğiyle veya `fullTrustAssemblies` (<xref:System.Security.Policy.StrongName>) dizi parametresinde listeleniyorsa, tam güven verilir. Yalnızca tam güvenilir olarak bilinen derlemeler `fullTrustAssemblies` listesine eklenmelidir.  
  
 Aşırı yükleme aşağıdaki imzaya sahiptir:  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> yöntemi aşırı yüklemesi için parametreler, <xref:System.AppDomain>adını, <xref:System.AppDomain>için kanıt, korumalı alan için uygulama temeli tanımlayan <xref:System.AppDomainSetup> nesnesini, izin olarak ayarlandığını ve tam güvenilir derlemeler için tanımlayıcı adlarını belirtir.  
  
 Güvenlik nedenleriyle, `info` parametresinde belirtilen uygulama tabanı, barındırma uygulaması için uygulama temeli olmamalıdır.  
  
 `grantSet` parametresinde, açıkça oluşturduğunuz bir izin kümesini ya da <xref:System.Security.SecurityManager.GetStandardSandbox%2A> yöntemi tarafından oluşturulan standart bir izin kümesini belirtebilirsiniz.  
  
 <xref:System.AppDomain> yüklemelerinin aksine, kısmen güvenilen derlemeler için izin kümesini belirlemede <xref:System.AppDomain> (`securityInfo` parametresi tarafından sağlanır) için kanıt kullanılmaz. Bunun yerine, `grantSet` parametresi tarafından bağımsız olarak belirtilir. Ancak kanıt, yalıtılmış depolama kapsamını belirleme gibi başka amaçlar için de kullanılabilir.  
  
### <a name="to-run-an-application-in-a-sandbox"></a>Bir korumalı alanda uygulama çalıştırmak için  
  
1. Güvenilmeyen uygulamaya verilecek izin kümesini oluşturun. İzin verdiğiniz en düşük izin <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> izindir. Ayrıca, güvenilir olmayan kod için güvenli olabileceğini düşündüğünüz ek izinler verebilirsiniz; Örneğin, <xref:System.Security.Permissions.IsolatedStorageFilePermission>. Aşağıdaki kod yalnızca <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> iznine sahip yeni bir izin kümesi oluşturur.  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     Alternatif olarak, Internet gibi var olan bir adlandırılmış izin kümesini de kullanabilirsiniz.  
  
    ```csharp
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <xref:System.Security.SecurityManager.GetStandardSandbox%2A> yöntemi, kanıt içindeki bölgeye bağlı olarak bir `Internet` izin kümesi veya `LocalIntranet` izin kümesi döndürür. <xref:System.Security.SecurityManager.GetStandardSandbox%2A> Ayrıca, başvuru olarak geçirilen bazı kanıt nesneleri için kimlik izinleri oluşturur.  
  
2. Güvenilmeyen kodu çağıran barındırma sınıfını (Bu örnekteki `Sandboxer` adlı) içeren derlemeyi imzalayın. Derlemeyi <xref:System.AppDomain.CreateDomain%2A> çağrısının `fullTrustAssemblies` parametresinin <xref:System.Security.Policy.StrongName> dizisine imzalamak için kullanılan <xref:System.Security.Policy.StrongName> ekleyin. Barındırma sınıfının, kısmi güven kodunun yürütülmesini sağlamak veya kısmi güven uygulamasına hizmet sunmak için tam olarak güvenilir olarak çalıştırılması gerekir. Bir derlemenin <xref:System.Security.Policy.StrongName> okuyabilirsiniz:  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     Mscorlib ve System. dll gibi .NET Framework derlemelerin tam güven listesine eklenmesi gerekmez, çünkü genel derleme önbelleğinden tam güvenilir olarak yüklenirler.  
  
3. <xref:System.AppDomain.CreateDomain%2A> yönteminin <xref:System.AppDomainSetup> parametresini başlatın. Bu parametreyle, yeni <xref:System.AppDomain>ayarlarının birçoğunu denetleyebilirsiniz. <xref:System.AppDomainSetup.ApplicationBase%2A> özelliği önemli bir ayardır ve barındırma uygulamasının <xref:System.AppDomain> için <xref:System.AppDomainSetup.ApplicationBase%2A> özelliğinden farklı olmalıdır. <xref:System.AppDomainSetup.ApplicationBase%2A> ayarları aynıysa, kısmi güven uygulaması, ana bilgisayar uygulamasının tanımladığı bir özel durumu (tam olarak güvenilir), bu sayede onu kötüye yükleyebilir. Bu, bir catch (özel durum) kullanılması önerilmez. Konağın uygulama tabanının, korumalı uygulamanın uygulama tabanından farklı ayarlanması, yararlanma riskini azaltır.  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. Belirttiğimiz parametreleri kullanarak uygulama etki alanını oluşturmak için <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> yöntemi aşırı yüklemesini çağırın.  
  
     Bu yöntemin imzası:  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     Ek bilgiler:  
  
    - Bu, bir <xref:System.Security.PermissionSet> parametresi olarak alan <xref:System.AppDomain.CreateDomain%2A> yönteminin tek aşırı yüktür ve bu nedenle kısmi güven ayarında bir uygulamayı yüklemenize imkan tanıyan tek aşırı yükleme.  
  
    - `evidence` parametresi bir izin kümesini hesaplamak için kullanılmaz; .NET Framework diğer özelliklerinin tanımlanması için kullanılır.  
  
    - `info` parametresinin <xref:System.AppDomainSetup.ApplicationBase%2A> özelliğinin ayarlanması bu aşırı yükleme için zorunludur.  
  
    - `fullTrustAssemblies` parametresi `params` anahtar sözcüğüne sahiptir, yani <xref:System.Security.Policy.StrongName> bir dizi oluşturmak için bu gerekli değildir. Parametre olarak 0, 1 veya daha fazla tanımlayıcı ad geçirmek için izin verilir.  
  
    - Uygulama etki alanı oluşturma kodu:  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. Kodu, oluşturduğunuz korumalı alana alma <xref:System.AppDomain> yükleyin. Bu, iki şekilde yapılabilir:  
  
    - Derleme için <xref:System.AppDomain.ExecuteAssembly%2A> yöntemini çağırın.  
  
    - Yeni <xref:System.AppDomain><xref:System.MarshalByRefObject> türetilmiş bir sınıfın örneğini oluşturmak için <xref:System.Activator.CreateInstanceFrom%2A> yöntemini kullanın.  
  
     İkinci yöntem tercih edilir, çünkü parametreleri yeni <xref:System.AppDomain> örneğine geçirmek daha kolay hale getirir. <xref:System.Activator.CreateInstanceFrom%2A> yöntemi iki önemli özellik sağlar:  
  
    - Derlemenizi içermeyen bir konuma işaret eden bir kod tabanı kullanabilirsiniz.  
  
    - Bir <xref:System.Security.CodeAccessPermission.Assert%2A>, bir kritik sınıfın örneğini oluşturmanıza olanak sağlayan tam güven (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>) için oluşturma yapabilirsiniz. (Bu, derlemenizin saydamlık işaretlerini yoksa ve tamamen güvenilir olarak yüklendiğinde gerçekleşir.) Bu nedenle, yalnızca bu işlevle güvendiğiniz kodu oluşturmak için dikkatli olmanız gerekir ve yeni uygulama etki alanında yalnızca tam olarak güvenilen sınıfların örneklerini oluşturmanız önerilir.  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     Yeni bir etki alanında sınıfın bir örneğini oluşturmak için sınıfın <xref:System.MarshalByRefObject> sınıfını genişletecek olması gerektiğini unutmayın.  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. Yeni etki alanı örneğinin bu etki alanındaki bir başvuruya sarmalaması geri alınıyor. Bu başvuru güvenilmeyen kodu yürütmek için kullanılır.  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. Yeni oluşturduğunuz `Sandboxer` sınıfının örneğinde `ExecuteUntrustedCode` yöntemini çağırın.  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     Bu çağrı, sınırlı izinlere sahip olan korumalı uygulama etki alanında yürütülür.  
  
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
  
     <xref:System.Reflection> kısmen güvenilen derlemedeki bir yöntemin tanıtıcısını almak için kullanılır. Tanıtıcı, kodu minimum izinlerle güvenli bir şekilde yürütmek için kullanılabilir.  
  
     Önceki kodda, <xref:System.Security.SecurityException>yazdırmadan önce tam güven izninin <xref:System.Security.PermissionSet.Assert%2A> göz önünde önüne alın.  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     Tam güven onayı <xref:System.Security.SecurityException>genişletilmiş bilgileri elde etmek için kullanılır. <xref:System.Security.PermissionSet.Assert%2A>olmadan, <xref:System.Security.SecurityException> <xref:System.Security.SecurityException.ToString%2A> yöntemi yığında kısmen güvenilen kod olduğunu ve döndürülen bilgileri kısıtlayamayacağını keşfeder. Bu, kısmi güven kodu bu bilgileri okuyabiliyorsanız güvenlik sorunlarına neden olabilir, ancak risk <xref:System.Security.Permissions.UIPermission>verilmemesine göre azaltılmalıdır. Tam güven onayı, az önce ve yalnızca kısmi güven kodunun tam güvene yükseltilmesine izin vermediğinizden emin olduğunuzda kullanılmalıdır. Kural olarak, aynı işlevde güvenmediğiniz ve tam güven için bir onay çağırdıktan sonra kodu çağırmayın. Kullanmayı bitirdikten sonra her zaman onayı döndürmenizde iyi bir uygulamadır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, önceki bölümde yordamı uygular. Örnekte, Visual Studio çözümünde `Sandboxer` adlı bir proje aynı zamanda sınıf `UntrustedClass`uygulayan `UntrustedCode`adlı bir proje içerir. Bu senaryoda, `true` döndürmesi beklenen bir yöntemi içeren bir kitaplık derlemesini indirdiğinizi varsayar veya belirttiğiniz sayının bir Fibonaccı numarası olup olmadığını belirtmek için `false`. Bunun yerine, yöntemi bilgisayarınızdan bir dosyayı okumaya çalışır. Aşağıdaki örnek güvenilmeyen kodu gösterir.  
  
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
  
 Aşağıdaki örnek, güvenilmeyen kodu yürüten `Sandboxer` uygulama kodunu gösterir.  
  
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

- [Güvenli Kodlama Yönergeleri](../../standard/security/secure-coding-guidelines.md)
