---
title: 'Nasıl yapılır: Korumalı Alanda Kısmen Güvenilen Kodu Çalıştırma'
description: .NET 'teki bir korumalı alanda kısmen güvenilen kodun nasıl çalıştırılacağını öğrenin. AppDomain sınıfı korumalı alana alma yönetilen uygulamaların etkin bir yoludur.
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
ms.openlocfilehash: 415a42f7c4f4866bb72f19bdd6f02bfdb5158bf8
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855809"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a>Nasıl yapılır: Korumalı Alanda Kısmen Güvenilen Kodu Çalıştırma

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Korumalı alana alma, kodu, koda verilen erişim izinlerini sınırlayan kısıtlı bir güvenlik ortamında çalıştırmaya yönelik bir uygulamadır. Örneğin, tam olarak güvenmediğiniz bir kaynaktan yönetilen bir kitaplığınız varsa, bunu tam güvenilir olarak çalıştırmanız gerekir. Bunun yerine, kodu, izinlerini beklediğinizi (örneğin, izin) sınırlayan bir korumalı alana yerleştirmeniz gerekir <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> .  
  
 Ayrıca, dağıtmak istediğiniz kodu, kısmen güvenilen ortamlarda çalışacak şekilde test etmek için korumalı alana alma kullanabilirsiniz.  
  
 <xref:System.AppDomain>, Yönetilen uygulamalar için korumalı alan sağlamanın etkili bir yoludur. Kısmen güvenilen kodu çalıştırmak için kullanılan uygulama etki alanları, içinde çalışırken kullanılabilir olan korumalı kaynakları tanımlayan izinlere sahiptir <xref:System.AppDomain> . İçinde çalışan kod, <xref:System.AppDomain> ile ilişkili izinlerle ilişkilidir <xref:System.AppDomain> ve yalnızca belirtilen kaynaklara erişim izni verilir. <xref:System.AppDomain>Ayrıca, <xref:System.Security.Policy.StrongName> tam olarak güvenilir olarak yüklenecek derlemeleri tanımlamak için kullanılan bir dizi içerir. Bu, bir öğesinin, <xref:System.AppDomain> belirli yardımcı derlemelerin tam olarak güvenilir olmasını sağlayan yeni bir korumalı etki alanını başlatmasını sağlar. Derlemeleri tamamen güvenilir olarak yüklemek için başka bir seçenek de bunları genel derleme önbelleğine yerleştirmelidir; Ancak, derlemeleri bu bilgisayarda oluşturulan tüm uygulama etki alanlarında tam güvenilir olarak yükler. Tanımlayıcı adların listesi, <xref:System.AppDomain> daha kısıtlayıcı bir belirleme sağlayan kararların her birini destekler.  
  
 <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType>Bir korumalı alanda çalışan uygulamalar için izin kümesini belirtmek üzere yöntem aşırı yüklemesini kullanabilirsiniz. Bu aşırı yükleme, istediğiniz kod erişimi güvenliğinin tam düzeyini belirtmenize olanak sağlar. <xref:System.AppDomain>Bu aşırı yükleme kullanılarak bir öğesine yüklenen derlemeler yalnızca belirtilen izin kümesine sahip olabilir ya da tam güvenilir olabilir. Bütünleştirilmiş kod, genel derleme önbelleğidir veya `fullTrustAssemblies` () dizi parametresinde listeleniyorsa, tam güven verilir <xref:System.Security.Policy.StrongName> . Yalnızca tam güvenilir olarak bilinen derlemeler `fullTrustAssemblies` listeye eklenmelidir.  
  
 Aşırı yükleme aşağıdaki imzaya sahiptir:  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 Yöntem aşırı yüklemesi için parametreler,, <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> <xref:System.AppDomain> için kanıt, <xref:System.AppDomain> <xref:System.AppDomainSetup> korumalı alan için uygulama temelini tanımlayan nesne, kullanılacak izin kümesi ve tam güvenilir derlemeler için tanımlayıcı adlar belirler.  
  
 Güvenlik nedenleriyle, parametresinde belirtilen uygulama tabanı, `info` barındırma uygulaması için uygulama temeli olmamalıdır.  
  
 Parametresi için `grantSet` , açıkça oluşturduğunuz bir izin kümesini ya da yöntemi tarafından oluşturulan standart bir izin kümesini belirtebilirsiniz <xref:System.Security.SecurityManager.GetStandardSandbox%2A> .  
  
 Çoğu <xref:System.AppDomain> yüklerden farklı olarak, <xref:System.AppDomain> `securityInfo` kısmen güvenilen derlemeler için izin kümesini belirlemede (parametresi tarafından sağlanır) için kanıt kullanılmaz. Bunun yerine, parametresi tarafından bağımsız olarak belirtilir `grantSet` . Ancak kanıt, yalıtılmış depolama kapsamını belirleme gibi başka amaçlar için de kullanılabilir.  
  
### <a name="to-run-an-application-in-a-sandbox"></a>Bir korumalı alanda uygulama çalıştırmak için  
  
1. Güvenilmeyen uygulamaya verilecek izin kümesini oluşturun. İzin verdiğiniz en düşük izin <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> izinidir. Ayrıca, güvenilir olmayan kod için güvenli olabileceğini düşündüğünüz ek izinler verebilirsiniz; Örneğin, <xref:System.Security.Permissions.IsolatedStorageFilePermission> . Aşağıdaki kod yalnızca izne sahip yeni bir izin kümesi oluşturur <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> .  
  
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
  
     <xref:System.Security.SecurityManager.GetStandardSandbox%2A>Yöntemi, `Internet` `LocalIntranet` kanıt içindeki bölgeye bağlı olarak bir izin kümesi veya bir izin kümesi döndürür. <xref:System.Security.SecurityManager.GetStandardSandbox%2A>Ayrıca, başvuru olarak geçirilen bazı kanıt nesneleri için kimlik izinleri oluşturur.  
  
2. Güvenilmeyen kodu çağıran barındırma sınıfını (Bu örnekte adlandırılır) içeren derlemeyi imzalayın `Sandboxer` . <xref:System.Security.Policy.StrongName>Derlemeyi <xref:System.Security.Policy.StrongName> çağrının parametresinin dizisine imzalamak için kullanılan öğesini ekleyin `fullTrustAssemblies` <xref:System.AppDomain.CreateDomain%2A> . Barındırma sınıfının, kısmi güven kodunun yürütülmesini sağlamak veya kısmi güven uygulamasına hizmet sunmak için tam olarak güvenilir olarak çalıştırılması gerekir. Bu, <xref:System.Security.Policy.StrongName> bir derlemenin türünü okuduğunuzdan oluşur:  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     Mscorlib ve System.dll gibi .NET Framework derlemelerin tam güven listesine eklenmesi gerekmez, çünkü genel derleme önbelleğinden tam güvenilir olarak yüklenirler.  
  
3. <xref:System.AppDomainSetup>Yönteminin parametresini başlatın <xref:System.AppDomain.CreateDomain%2A> . Bu parametreyle, yeni ' nin birçok ayarını kontrol edebilirsiniz <xref:System.AppDomain> . <xref:System.AppDomainSetup.ApplicationBase%2A>Özelliği önemli bir ayardır ve <xref:System.AppDomainSetup.ApplicationBase%2A> barındırma uygulamasının özelliğinden farklı olmalıdır <xref:System.AppDomain> . <xref:System.AppDomainSetup.ApplicationBase%2A>Ayarlar aynıysa, kısmi güven uygulaması, ana bilgisayar uygulamasının tanımladığı özel durumu (tam olarak güvenilir olarak) tarafından daha sonra onu kötüye yükleyebilir. Bu, bir catch (özel durum) kullanılması önerilmez. Konağın uygulama tabanının, korumalı uygulamanın uygulama tabanından farklı ayarlanması, yararlanma riskini azaltır.  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29>Belirttiğimiz parametreleri kullanarak uygulama etki alanı oluşturmak için yöntem aşırı yüklemesini çağırın.  
  
     Bu yöntemin imzası:  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     Ek bilgiler:  
  
    - Bu, <xref:System.AppDomain.CreateDomain%2A> yöntemi parametresi olarak alan tek aşırı <xref:System.Security.PermissionSet> yüktür ve bu nedenle kısmi güven ayarında bir uygulamayı yüklemenize imkan tanıyan tek aşırı yükleme.  
  
    - `evidence`Parametresi, bir izin kümesini hesaplamak için kullanılmaz; .NET Framework diğer özelliklerinin tanımlanması için kullanılır.  
  
    - <xref:System.AppDomainSetup.ApplicationBase%2A>Parametresinin özelliğinin ayarlanması `info` Bu aşırı yükleme için zorunludur.  
  
    - `fullTrustAssemblies`Parametresi, `params` anahtar sözcüğüne sahiptir, yani bir dizi oluşturmak için gerekli değildir <xref:System.Security.Policy.StrongName> . Parametre olarak 0, 1 veya daha fazla tanımlayıcı ad geçirmek için izin verilir.  
  
    - Uygulama etki alanı oluşturma kodu:  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. Kodu oluşturduğunuz korumalı alana alma içine yükleyin <xref:System.AppDomain> . Bu, iki şekilde yapılabilir:  
  
    - <xref:System.AppDomain.ExecuteAssembly%2A>Derleme için yöntemini çağırın.  
  
    - <xref:System.Activator.CreateInstanceFrom%2A>Yeni içinde türetilmiş bir sınıfın örneğini oluşturmak için yöntemini kullanın <xref:System.MarshalByRefObject> <xref:System.AppDomain> .  
  
     İkinci yöntem tercih edilir, çünkü parametreleri yeni örneğe geçirmek daha kolay hale getirir <xref:System.AppDomain> . <xref:System.Activator.CreateInstanceFrom%2A>Yöntemi iki önemli özellik sağlar:  
  
    - Derlemenizi içermeyen bir konuma işaret eden bir kod tabanı kullanabilirsiniz.  
  
    - Bir <xref:System.Security.CodeAccessPermission.Assert%2A> <xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType> kritik sınıfın örneğini oluşturmanızı sağlayan tam güven () için oluşturma ' yı kullanabilirsiniz. (Bu, derlemenizin saydamlık işaretlerini yoksa ve tamamen güvenilir olarak yüklendiğinde gerçekleşir.) Bu nedenle, yalnızca bu işlevle güvendiğiniz kodu oluşturmak için dikkatli olmanız gerekir ve yeni uygulama etki alanında yalnızca tam olarak güvenilen sınıfların örneklerini oluşturmanız önerilir.  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     Yeni bir etki alanındaki sınıfın bir örneğini oluşturmak için, sınıfı sınıfını genişletmelidir <xref:System.MarshalByRefObject> .
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. Yeni etki alanı örneğinin bu etki alanındaki bir başvuruya sarmalaması geri alınıyor. Bu başvuru güvenilmeyen kodu yürütmek için kullanılır.  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. `ExecuteUntrustedCode` `Sandboxer` Yeni oluşturduğunuz sınıfın örneğindeki yöntemi çağırın.  
  
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
  
     <xref:System.Reflection>kısmen güvenilen derlemedeki bir yöntemin tanıtıcısını almak için kullanılır. Tanıtıcı, kodu minimum izinlerle güvenli bir şekilde yürütmek için kullanılabilir.  
  
     Önceki kodda, ' yi <xref:System.Security.PermissionSet.Assert%2A> yazdırmadan önce tam güven izni için ' a göz önüne alın <xref:System.Security.SecurityException> .  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     Tam güven onayı, ' dan genişletilmiş bilgileri elde etmek için kullanılır <xref:System.Security.SecurityException> . Olmadan <xref:System.Security.PermissionSet.Assert%2A> <xref:System.Security.SecurityException.ToString%2A> yöntemi, <xref:System.Security.SecurityException> yığın üzerinde kısmen güvenilen kod olduğunu ve döndürülen bilgileri kısıtlayamayacağını keşfeder. Kısmi güven kodu bu bilgileri okuyabiliyorsanız ve risk verilmemesine göre azaltıldığında, bu güvenlik sorunlarına neden olabilir <xref:System.Security.Permissions.UIPermission> . Tam güven onayı, az önce ve yalnızca kısmi güven kodunun tam güvene yükseltilmesine izin vermediğinizden emin olduğunuzda kullanılmalıdır. Kural olarak, aynı işlevde güvenmediğiniz ve tam güven için bir onay çağırdıktan sonra kodu çağırmayın. Kullanmayı bitirdikten sonra her zaman onayı döndürmenizde iyi bir uygulamadır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, önceki bölümde yordamı uygular. Örnekte, `Sandboxer` Visual Studio çözümünde adlı bir proje, sınıfını uygulayan adlı bir projeyi de içerir `UntrustedCode` `UntrustedClass` . Bu senaryoda, döndürmesi beklenen bir yöntemi içeren bir kitaplık derlemesini indirdiğiniz `true` veya `false` girdiğiniz sayının bir Fibonaccı numarası olup olmadığını belirtmesi gerektiğini varsaymaktadır. Bunun yerine, yöntemi bilgisayarınızdan bir dosyayı okumaya çalışır. Aşağıdaki örnek güvenilmeyen kodu gösterir.  
  
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
  
 Aşağıdaki örnek, `Sandboxer` Güvenilmeyen kodu yürüten uygulama kodunu gösterir.  
  
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
