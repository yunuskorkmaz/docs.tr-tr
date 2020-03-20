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
ms.openlocfilehash: b2f5a72e747f6c71743a7b22fe9f1962ac2f6b53
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181174"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a>Nasıl yapılır: Korumalı Alanda Kısmen Güvenilen Kodu Çalıştırma
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Sandboxing, koda verilen erişim izinlerini sınırlayan, kısıtlanmış bir güvenlik ortamında kod çalıştırma uygulamasıdır. Örneğin, tamamen güvenmediğiniz bir kaynaktan yönetilen bir kitaplığınız varsa, tam olarak güvenilen bir kitaplık çalıştırmamalısınız. Bunun yerine, kodu, izinlerini gereksinim duymasını beklediğiniz kişilerle (örneğin, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> izin) sınırlayan bir kum havuzuna yerleştirmeniz gerekir.  
  
 Dağıtacağınız ve kısmen güvenilen ortamlarda çalışacak kodları sınamak için kum kutulama özelliğini de kullanabilirsiniz.  
  
 Yönetilen <xref:System.AppDomain> uygulamalar için bir kum havuzu sağlamanın etkili bir yoludur. Kısmen güvenilen kodu çalıştırmak için kullanılan uygulama etki alanları, bu <xref:System.AppDomain>kod içinde çalışırken kullanılabilir korumalı kaynakları tanımlayan izinlere sahiptir. İçinde çalışan <xref:System.AppDomain> kod, yalnızca <xref:System.AppDomain> belirtilen kaynaklara erişmesine izin verilen izinlerle bağlıdır. Ayrıca, <xref:System.AppDomain> tam <xref:System.Security.Policy.StrongName> olarak güvenilir olarak yüklenecek derlemeleri tanımlamak için kullanılan bir dizi içerir. Bu, belirli <xref:System.AppDomain> yardımcı derlemelerin tam olarak güvenilmesini sağlayan yeni bir kumhavuzu etki alanının oluşturucusu olmasını sağlar. Derlemeleri tamamen güvenilir olarak yüklemek için başka bir seçenek de bunları genel montaj önbelleğine yerleştirmektir; ancak, bu, bu bilgisayarda oluşturulan tüm uygulama etki alanlarında tam olarak güvenilir olarak derlemeleri yükler. Güçlü adlar listesi, daha<xref:System.AppDomain> kısıtlayıcı belirleme sağlayan bir karar başına destekler.  
  
 Bir kum <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> havuzunda çalışan uygulamalar için izin kümesini belirtmek için aşırı yükleme yöntemini kullanabilirsiniz. Bu aşırı yükleme, istediğiniz kod erişim güvenliğinin tam düzeyini belirtmenizi sağlar. Bu aşırı yükleme kullanılarak <xref:System.AppDomain> bir eve yüklenen derlemeler yalnızca belirtilen hibe kümesine sahip olabilir veya tam olarak güvenilebilir. Derleme, genel montaj önbelleğinde yse veya `fullTrustAssemblies` () <xref:System.Security.Policy.StrongName>dizi parametresinde listelenmişse tam güven verilir. Listeye yalnızca tam olarak güvenilen olduğu `fullTrustAssemblies` bilinen derlemeler eklenmelidir.  
  
 Aşırı yükleme aşağıdaki imzaya sahiptir:  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 Yöntem aşırı yüklemesi için <xref:System.AppDomain>parametreler, kum havuzu <xref:System.AppDomain>için <xref:System.AppDomainSetup> uygulama tabanını tanımlayan nesne, kullanma izni kümesi ve tam olarak güvenilen derlemeler için güçlü adlar için kanıt, adını belirtir. <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29>  
  
 Güvenlik nedenleriyle, `info` parametrede belirtilen uygulama tabanı barındırma uygulamasının uygulama tabanı olmamalıdır.  
  
 `grantSet` Parametre için, açıkça oluşturduğunuz bir izin kümesi ni veya <xref:System.Security.SecurityManager.GetStandardSandbox%2A> yöntem tarafından oluşturulan standart bir izin kümesini belirtebilirsiniz.  
  
 Çoğu <xref:System.AppDomain> yükün aksine, <xref:System.AppDomain> kısmen güvenilen `securityInfo` derlemeler için hibe kümesini belirlemek için (parametre tarafından sağlanan) için kanıt kullanılmaz. Bunun yerine, `grantSet` parametre tarafından bağımsız olarak belirtilir. Ancak, kanıt yalıtılmış depolama kapsamının belirlenmesi gibi başka amaçlar için kullanılabilir.  
  
### <a name="to-run-an-application-in-a-sandbox"></a>Bir uygulamayı kum havuzunda çalıştırmak için  
  
1. Güvenilmeyen uygulamaya verilecek izin kümesini oluşturun. Verebileceğiniz minimum izin, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> izindir. Ayrıca, güvenilmeyen kod için güvenli olabileceğini düşündüğünüz ek izinler de verebilirsiniz; örneğin, <xref:System.Security.Permissions.IsolatedStorageFilePermission>. Aşağıdaki kod, yalnızca <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> izinle yeni bir izin kümesi oluşturur.  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     Alternatif olarak, Internet gibi varolan bir adlandırılmış izin kümesini kullanabilirsiniz.  
  
    ```csharp
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     Yöntem, <xref:System.Security.SecurityManager.GetStandardSandbox%2A> kanıttaki `Internet` bölgeye bağlı `LocalIntranet` olarak bir izin kümesi veya izin kümesi döndürür. <xref:System.Security.SecurityManager.GetStandardSandbox%2A>ayrıca, başvuru olarak geçirilen bazı kanıt nesneleri için kimlik izinleri de kurar.  
  
2. Güvenilmeyen kodu çağıran barındırma sınıfını (bu örnekte adlandırılmış) `Sandboxer` içeren derlemeyi imzalayın. Çağrının <xref:System.Security.Policy.StrongName> <xref:System.Security.Policy.StrongName> `fullTrustAssemblies` parametre <xref:System.AppDomain.CreateDomain%2A> dizisini derlemeyi imzalamak için kullanılanı ekleyin. Barındırma sınıfı, kısmi güven kodunun yürütülmesini etkinleştirmek veya kısmi güven uygulamasına hizmet sunmak için tam olarak güvenilir olarak çalıştırılmalıdır. Bir derlemenin <xref:System.Security.Policy.StrongName> okuması şöyledir:  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     .NET Framework derlemeleri mscorlib ve System.dll gibi tam güven listesine eklenmek zorunda değildir, çünkü bunlar genel montaj önbelleğinden tam olarak güvenilir olarak yüklenir.  
  
3. Yöntemin <xref:System.AppDomainSetup> parametresini <xref:System.AppDomain.CreateDomain%2A> başlangıç olarak karşın. Bu parametre ile, yeni <xref:System.AppDomain>ayarların çoğunu kontrol edebilirsiniz. Özellik <xref:System.AppDomainSetup.ApplicationBase%2A> önemli bir ayardır ve barındırma <xref:System.AppDomainSetup.ApplicationBase%2A> uygulaması için <xref:System.AppDomain> özellik farklı olmalıdır. <xref:System.AppDomainSetup.ApplicationBase%2A> Ayarlar aynıysa, kısmi güven uygulaması barındırma uygulamasını tanımladığı bir özel durumu (tam olarak güvenilen) yükleyerek ve böylece bu uygulamadan yararlanabilir. Bu, bir yakalama (özel durum) tavsiye edilmez başka bir nedenidir. Ana bilgisayar uygulama tabanını, kum havuzu uygulamasının uygulama tabanından farklı bir şekilde ayarlamak, yararlanma riskini azaltır.  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. Belirlediğimiz <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> parametreleri kullanarak uygulama etki alanını oluşturmak için aşırı yükleme yöntemini arayın.  
  
     Bu yöntemin imzası:  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     Ek bilgiler:  
  
    - Bu, bir <xref:System.Security.PermissionSet> parametre <xref:System.AppDomain.CreateDomain%2A> olarak alan yöntemin tek aşırı yüklemesi ve böylece bir uygulamayı kısmi güven ayarında yüklemenize olanak tanıyan tek aşırı yüklemedir.  
  
    - Parametre `evidence` bir izin kümesini hesaplamak için kullanılmaz; .NET Framework'ün diğer özellikleri tarafından tanımlama için kullanılır.  
  
    - Bu <xref:System.AppDomainSetup.ApplicationBase%2A> aşırı yükleme `info` için parametrenin özelliğinin ayarlanması zorunludur.  
  
    - `fullTrustAssemblies` Parametrede anahtar sözcük vardır, bu da bir <xref:System.Security.Policy.StrongName> dizi oluşturmanın gerekli olmadığı anlamına `params` gelir. Parametreler olarak 0, 1 veya daha fazla güçlü ad lar geçirin.  
  
    - Uygulama etki alanını oluşturmak için kod:  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. Kodu oluşturduğunuz kum kutulamına <xref:System.AppDomain> yükleyin. Bu iki şekilde yapılabilir:  
  
    - Derleme <xref:System.AppDomain.ExecuteAssembly%2A> yöntemini arayın.  
  
    - Yeni'den <xref:System.Activator.CreateInstanceFrom%2A> <xref:System.MarshalByRefObject> <xref:System.AppDomain>türetilen bir sınıfın örneğini oluşturmak için yöntemi kullanın.  
  
     Parametrelerin yeni <xref:System.AppDomain> örne geçirilmesini kolaylaştırdığından, ikinci yöntem tercih edilir. Yöntem <xref:System.Activator.CreateInstanceFrom%2A> iki önemli özellik sağlar:  
  
    - Derlemenizi içermeyen bir konuma işaret eden bir kod tabanı kullanabilirsiniz.  
  
    - Oluşturmayı, kritik bir <xref:System.Security.CodeAccessPermission.Assert%2A> sınıfın bir<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>örneğini oluşturmanızı sağlayan tam güven (), altında yapabilirsiniz. (Bu, derlemenizde saydamlık işareti olmadığında ve tam olarak güvenilir olarak yüklendiğinde gerçekleşir.) Bu nedenle, yalnızca bu işlevle güvendiğiniz kodu oluşturmak için dikkatli olun ve yeni uygulama etki alanında yalnızca tam olarak güvenilen sınıfların örneklerini oluşturmanızı öneririz.  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     Yeni bir etki alanında bir sınıfın örneğini oluşturmak için sınıfın sınıfı <xref:System.MarshalByRefObject> genişletmesi gerektiğini unutmayın  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. Yeni etki alanı örneğini bu etki alanında bir başvuruya dönüştürün. Bu başvuru, güvenilmeyen kodu yürütmek için kullanılır.  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. Yeni `ExecuteUntrustedCode` oluşturduğunuz `Sandboxer` sınıf örneğinde yöntemi arayın.  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     Bu çağrı, kısıtlı izinleri olan zAndBoxed uygulama etki alanında yürütülür.  
  
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
  
     <xref:System.Reflection>kısmen güvenilen derlemede bir yöntemin bir kolu almak için kullanılır. Tanıtıcı, kodu minimum izinlerle güvenli bir şekilde yürütmek için kullanılabilir.  
  
     Önceki kodda, yazdırmadan önce tam güven <xref:System.Security.PermissionSet.Assert%2A> izniiçin <xref:System.Security.SecurityException>not.  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     Tam güven assert' <xref:System.Security.SecurityException>i, 'den genişletilmiş bilgi elde etmek için kullanılır. <xref:System.Security.PermissionSet.Assert%2A>Olmadan , <xref:System.Security.SecurityException.ToString%2A> yöntemi <xref:System.Security.SecurityException> yığının üzerinde kısmen güvenilen kod olduğunu keşfedeceksiniz ve döndürülen bilgileri kısıtlar. Kısmi güven kodu bu bilgileri okuyabildiyse, bu durum güvenlik sorunlarına <xref:System.Security.Permissions.UIPermission>neden olabilir, ancak risk, '' verilmemesi yle azaltılır. Tam güven iddiası, yalnızca kısmi güven kodunun tam güvene yükseltilmesine izin vermemeniz gerektiğinden emin olduğunuzda dikkatli kullanılmalıdır. Kural olarak, aynı işlevde güvenmediğiniz ve tam güven için bir assert çağırdıktan sonra kod aramayın. Kullanımı bittiğinde her zaman iddiayı geri almak iyi bir uygulamadır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, önceki bölümde yordamı uygular. Örnekte, Visual Studio `Sandboxer` çözümünde adı geçen bir `UntrustedCode`proje, sınıfı `UntrustedClass`uygulayan bir proje de içerir. Bu senaryo, döndürülmesi `true` beklenen veya `false` sağladığınız sayının Fibonacci numarası olup olmadığını belirtmek için bir yöntem içeren bir kitaplık derlemesi karşıdan yüklediğinizi varsayar. Bunun yerine, yöntem bilgisayarınızdan bir dosyayı okumaya çalışır. Aşağıdaki örnek, güvenilmeyen kodu gösterir.  
  
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
  
 Aşağıdaki örnek, `Sandboxer` güvenilmeyen kodu çalıştıran uygulama kodunu gösterir.  
  
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
