---
title: 'Nasıl yapılır: Bir korumalı alanda kısmen güvenilen kod Çalıştır'
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
ms.openlocfilehash: a439e02046e04d8628415237d6717a74b9922371
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910942"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a>Nasıl yapılır: Bir korumalı alanda kısmen güvenilen kod Çalıştır
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Korumalı alana alma, kodu, koda verilen erişim izinlerini sınırlayan kısıtlı bir güvenlik ortamında çalıştırmaya yönelik bir uygulamadır. Örneğin, tam olarak güvenmediğiniz bir kaynaktan yönetilen bir kitaplığınız varsa, bunu tam güvenilir olarak çalıştırmanız gerekir. Bunun yerine, kodu, izinlerini beklediğinizi (örneğin, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> izin) sınırlayan bir korumalı alana yerleştirmeniz gerekir.  
  
 Ayrıca, dağıtmak istediğiniz kodu, kısmen güvenilen ortamlarda çalışacak şekilde test etmek için korumalı alana alma kullanabilirsiniz.  
  
 <xref:System.AppDomain> , Yönetilen uygulamalar için korumalı alan sağlamanın etkili bir yoludur. Kısmen güvenilen kodu çalıştırmak için kullanılan uygulama etki alanları, içinde <xref:System.AppDomain>çalışırken kullanılabilir olan korumalı kaynakları tanımlayan izinlere sahiptir. İçinde <xref:System.AppDomain> çalışan kod, <xref:System.AppDomain> ile ilişkili izinlerle ilişkilidir ve yalnızca belirtilen kaynaklara erişim izni verilir. Ayrıca <xref:System.AppDomain> , tam olarak <xref:System.Security.Policy.StrongName> güvenilir olarak yüklenecek derlemeleri tanımlamak için kullanılan bir dizi içerir. Bu, bir <xref:System.AppDomain> öğesinin, belirli yardımcı derlemelerin tam olarak güvenilir olmasını sağlayan yeni bir korumalı etki alanını başlatmasını sağlar. Derlemeleri tamamen güvenilir olarak yüklemek için başka bir seçenek de bunları genel derleme önbelleğine yerleştirmelidir; Ancak, derlemeleri bu bilgisayarda oluşturulan tüm uygulama etki alanlarında tam güvenilir olarak yükler. Tanımlayıcı adların listesi, daha kısıtlayıcı bir belirleme sağlayan<xref:System.AppDomain> kararların her birini destekler.  
  
 Bir korumalı alanda çalışan <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> uygulamalar için izin kümesini belirtmek üzere yöntem aşırı yüklemesini kullanabilirsiniz. Bu aşırı yükleme, istediğiniz kod erişimi güvenliğinin tam düzeyini belirtmenize olanak sağlar. Bu aşırı yükleme kullanılarak bir <xref:System.AppDomain> öğesine yüklenen derlemeler yalnızca belirtilen izin kümesine sahip olabilir ya da tam güvenilir olabilir. Bütünleştirilmiş kod, genel derleme önbelleğidir veya `fullTrustAssemblies` <xref:System.Security.Policy.StrongName>() dizi parametresinde listeleniyorsa, tam güven verilir. Yalnızca tam güvenilir olarak bilinen derlemeler `fullTrustAssemblies` listeye eklenmelidir.  
  
 Aşırı yükleme aşağıdaki imzaya sahiptir:  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> Yöntem aşırı yüklemesi için parametreler,, için <xref:System.AppDomain> <xref:System.AppDomainSetup> kanıt, korumalı <xref:System.AppDomain>alan için uygulama temelini tanımlayan nesne, kullanılacak izin kümesi ve tanımlayıcı adlar belirler tam güvenilir derlemeler.  
  
 Güvenlik nedenleriyle, `info` parametresinde belirtilen uygulama tabanı, barındırma uygulaması için uygulama temeli olmamalıdır.  
  
 Parametresi için, açıkça oluşturduğunuz bir izin kümesini ya da <xref:System.Security.SecurityManager.GetStandardSandbox%2A> yöntemi tarafından oluşturulan standart bir izin kümesini belirtebilirsiniz. `grantSet`  
  
 Çoğu <xref:System.AppDomain> yüklerden farklı olarak, kısmen güvenilen <xref:System.AppDomain> derlemeler için izin kümesini belirlemede ( `securityInfo` parametresi tarafından sağlanır) için kanıt kullanılmaz. Bunun yerine, `grantSet` parametresi tarafından bağımsız olarak belirtilir. Ancak kanıt, yalıtılmış depolama kapsamını belirleme gibi başka amaçlar için de kullanılabilir.  
  
### <a name="to-run-an-application-in-a-sandbox"></a>Bir korumalı alanda uygulama çalıştırmak için  
  
1. Güvenilmeyen uygulamaya verilecek izin kümesini oluşturun. <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> İzin verdiğiniz en düşük izin izinidir. Ayrıca, güvenilir olmayan kod için güvenli olabileceğini düşündüğünüz ek izinler verebilirsiniz; Örneğin, <xref:System.Security.Permissions.IsolatedStorageFilePermission>. Aşağıdaki kod yalnızca <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> izne sahip yeni bir izin kümesi oluşturur.  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     Alternatif olarak, Internet gibi var olan bir adlandırılmış izin kümesini de kullanabilirsiniz.  
  
    ```  
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     Yöntemi <xref:System.Security.SecurityManager.GetStandardSandbox%2A> , kanıt içindeki bölgeye `Internet` bağlı olarak bir izin `LocalIntranet` kümesi veya bir izin kümesi döndürür. <xref:System.Security.SecurityManager.GetStandardSandbox%2A>Ayrıca, başvuru olarak geçirilen bazı kanıt nesneleri için kimlik izinleri oluşturur.  
  
2. Güvenilmeyen kodu çağıran barındırma sınıfını (Bu örnekte adlandırılır `Sandboxer` ) içeren derlemeyi imzalayın. <xref:System.Security.Policy.StrongName> Derlemeyi çağrının<xref:System.AppDomain.CreateDomain%2A> parametresinin dizisine imzalamak için kullanılan öğesini ekleyin. <xref:System.Security.Policy.StrongName> `fullTrustAssemblies` Barındırma sınıfının, kısmi güven kodunun yürütülmesini sağlamak veya kısmi güven uygulamasına hizmet sunmak için tam olarak güvenilir olarak çalıştırılması gerekir. Bu, <xref:System.Security.Policy.StrongName> bir derlemenin türünü okuduğunuzdan oluşur:  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     Mscorlib ve System. dll gibi .NET Framework derlemelerin tam güven listesine eklenmesi gerekmez, çünkü genel derleme önbelleğinden tam güvenilir olarak yüklenirler.  
  
3. <xref:System.AppDomain.CreateDomain%2A> Yönteminin <xref:System.AppDomainSetup> parametresini başlatın. Bu parametreyle, yeni <xref:System.AppDomain>' nin birçok ayarını kontrol edebilirsiniz. Özelliği önemli bir ayardır ve barındırma uygulamasının <xref:System.AppDomainSetup.ApplicationBase%2A> özelliğinden <xref:System.AppDomain> farklı olmalıdır. <xref:System.AppDomainSetup.ApplicationBase%2A> <xref:System.AppDomainSetup.ApplicationBase%2A> Ayarlar aynıysa, kısmi güven uygulaması, ana bilgisayar uygulamasının tanımladığı özel durumu (tam olarak güvenilir olarak) tarafından daha sonra onu kötüye yükleyebilir. Bu, bir catch (özel durum) kullanılması önerilmez. Konağın uygulama tabanının, korumalı uygulamanın uygulama tabanından farklı ayarlanması, yararlanma riskini azaltır.  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. Belirttiğimiz parametreleri kullanarak uygulama etki alanı oluşturmak için yöntemaşırıyüklemesiniçağırın.<xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29>  
  
     Bu yöntemin imzası:  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     Ek bilgiler:  
  
    - Bu, <xref:System.AppDomain.CreateDomain%2A> yöntemi parametresi <xref:System.Security.PermissionSet> olarak alan tek aşırı yüktür ve bu nedenle kısmi güven ayarında bir uygulamayı yüklemenize imkan tanıyan tek aşırı yükleme.  
  
    - `evidence` Parametresi, bir izin kümesini hesaplamak için kullanılmaz; .NET Framework diğer özelliklerinin tanımlanması için kullanılır.  
  
    - `info` Parametresinin özelliğinin ayarlanması bu aşırı yükleme için zorunludur. <xref:System.AppDomainSetup.ApplicationBase%2A>  
  
    - Parametresi, `params` anahtar sözcüğüne sahiptir, yani bir <xref:System.Security.Policy.StrongName> dizi oluşturmak için gerekli değildir. `fullTrustAssemblies` Parametre olarak 0, 1 veya daha fazla tanımlayıcı ad geçirmek için izin verilir.  
  
    - Uygulama etki alanı oluşturma kodu:  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. Kodu oluşturduğunuz korumalı alana alma <xref:System.AppDomain> içine yükleyin. Bu, iki şekilde yapılabilir:  
  
    - Derleme için <xref:System.AppDomain.ExecuteAssembly%2A> yöntemini çağırın.  
  
    - <xref:System.Activator.CreateInstanceFrom%2A> Yeni <xref:System.MarshalByRefObject> içinde türetilmiş bir sınıfın örneğini oluşturmak için yöntemini kullanın. <xref:System.AppDomain>  
  
     İkinci yöntem tercih edilir, çünkü parametreleri yeni <xref:System.AppDomain> örneğe geçirmek daha kolay hale getirir. <xref:System.Activator.CreateInstanceFrom%2A> Yöntemi iki önemli özellik sağlar:  
  
    - Derlemenizi içermeyen bir konuma işaret eden bir kod tabanı kullanabilirsiniz.  
  
    - Bir <xref:System.Security.CodeAccessPermission.Assert%2A> kritik sınıfın örneğini oluşturmanızı sağlayan tam güven (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>) için oluşturma ' yı kullanabilirsiniz. (Bu, derlemenizin saydamlık işaretlerini yoksa ve tamamen güvenilir olarak yüklendiğinde gerçekleşir.) Bu nedenle, yalnızca bu işlevle güvendiğiniz kodu oluşturmak için dikkatli olmanız gerekir ve yeni uygulama etki alanında yalnızca tam olarak güvenilen sınıfların örneklerini oluşturmanız önerilir.  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     Yeni bir etki alanında sınıfın bir örneğini oluşturmak için sınıfın <xref:System.MarshalByRefObject> sınıfı genişletmesine sahip olduğunu unutmayın.  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. Yeni etki alanı örneğinin bu etki alanındaki bir başvuruya sarmalaması geri alınıyor. Bu başvuru güvenilmeyen kodu yürütmek için kullanılır.  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. Yeni oluşturduğunuz `Sandboxer` sınıfın örneğindeki yöntemiçağırın.`ExecuteUntrustedCode`  
  
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
  
     Önceki kodda, ' yi <xref:System.Security.PermissionSet.Assert%2A> <xref:System.Security.SecurityException>yazdırmadan önce tam güven izni için ' a göz önüne alın.  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     Tam güven onayı, <xref:System.Security.SecurityException>' dan genişletilmiş bilgileri elde etmek için kullanılır. <xref:System.Security.PermissionSet.Assert%2A> Olmadan<xref:System.Security.SecurityException.ToString%2A> yöntemi ,<xref:System.Security.SecurityException> yığın üzerinde kısmen güvenilen kod olduğunu ve döndürülen bilgileri kısıtlayamayacağını keşfeder. Kısmi güven kodu bu bilgileri okuyabiliyorsanız ve risk verilmemesine <xref:System.Security.Permissions.UIPermission>göre azaltıldığında, bu güvenlik sorunlarına neden olabilir. Tam güven onayı, az önce ve yalnızca kısmi güven kodunun tam güvene yükseltilmesine izin vermediğinizden emin olduğunuzda kullanılmalıdır. Kural olarak, aynı işlevde güvenmediğiniz ve tam güven için bir onay çağırdıktan sonra kodu çağırmayın. Kullanmayı bitirdikten sonra her zaman onayı döndürmenizde iyi bir uygulamadır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, önceki bölümde yordamı uygular. Örnekte, Visual Studio çözümünde adlı `Sandboxer` bir proje, sınıfını `UntrustedClass`uygulayan adlı `UntrustedCode`bir projeyi de içerir. Bu senaryoda, döndürmesi `true` beklenen bir yöntemi içeren bir kitaplık derlemesini indirdiğiniz veya `false` girdiğiniz sayının bir fibonaccı numarası olup olmadığını belirtmesi gerektiğini varsaymaktadır. Bunun yerine, yöntemi bilgisayarınızdan bir dosyayı okumaya çalışır. Aşağıdaki örnek güvenilmeyen kodu gösterir.  
  
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
  
 Aşağıdaki örnek, güvenilmeyen kodu `Sandboxer` yürüten uygulama kodunu gösterir.  
  
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
