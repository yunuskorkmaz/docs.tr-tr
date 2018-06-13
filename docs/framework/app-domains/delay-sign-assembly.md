---
title: Derleme İmzalamayı Geciktirme
ms.date: 07/31/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4457bd6d5efd7404cdba6c5fbdbffa9f9eb62141
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743996"
---
# <a name="delay-signing-an-assembly"></a><span data-ttu-id="ec069-102">Derleme İmzalamayı Geciktirme</span><span class="sxs-lookup"><span data-stu-id="ec069-102">Delay Signing an Assembly</span></span>
<span data-ttu-id="ec069-103">Bir kuruluş, geliştiricilerin günlük olarak için erişimi yoktur yakından korumalı bir anahtar çifti olabilir.</span><span class="sxs-lookup"><span data-stu-id="ec069-103">An organization can have a closely guarded key pair that developers do not have access to on a daily basis.</span></span> <span data-ttu-id="ec069-104">Ortak anahtar genellikle kullanılabilir, ancak özel anahtar erişimi yalnızca birkaç kişi sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="ec069-104">The public key is often available, but access to the private key is restricted to only a few individuals.</span></span> <span data-ttu-id="ec069-105">Derlemeleri tanımlayıcı adlar ile geliştirirken, her derleme bu başvurular tanımlayıcı adlı hedef derlemeyi hedef derleme güçlü bir ad vermek için kullanılan ortak anahtar belirteci içeriyor.</span><span class="sxs-lookup"><span data-stu-id="ec069-105">When developing assemblies with strong names, each assembly that references the strong-named target assembly contains the token of the public key used to give the target assembly a strong name.</span></span> <span data-ttu-id="ec069-106">Bu, ortak anahtar geliştirme işlemi sırasında kullanılabilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ec069-106">This requires that the public key be available during the development process.</span></span>  
  
 <span data-ttu-id="ec069-107">Ayrılmış alanı dosyasındaki taşınabilir yürütülebilir (PE) sağlam ad imzası, ancak gerçek imzalama (derleme göndermeden önce genellikle yalnızca) bazı sonraki aşaması kadar erteleme gecikmeli ya da kısmi derleme zamanında imzalama kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec069-107">You can use delayed or partial signing at build time to reserve space in the portable executable (PE) file for the strong name signature, but defer the actual signing until some later stage (typically just before shipping the assembly).</span></span>  
  
 <span data-ttu-id="ec069-108">Aşağıdaki adımları gecikme oturum bütünleştirilmiş sürecini özetlemektedir:</span><span class="sxs-lookup"><span data-stu-id="ec069-108">The following steps outline the process to delay sign an assembly:</span></span>  
  
1.  <span data-ttu-id="ec069-109">Anahtar çiftini ortak anahtar kısmını nihai imzalama yapan kuruluşlardan.</span><span class="sxs-lookup"><span data-stu-id="ec069-109">Obtain the public key portion of the key pair from the organization that will do the eventual signing.</span></span> <span data-ttu-id="ec069-110">Genellikle bu anahtarı kullanılarak oluşturulan bir .snk dosya biçimindedir [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) tarafından sağlanan [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ec069-110">Typically this key is in the form of an .snk file, which can be created using the [Strong Name tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
2.  <span data-ttu-id="ec069-111">Kaynak kodu derleme iki özel öznitelikleri için ek açıklama <xref:System.Reflection>:</span><span class="sxs-lookup"><span data-stu-id="ec069-111">Annotate the source code for the assembly with two custom attributes from <xref:System.Reflection>:</span></span>  
  
    -   <span data-ttu-id="ec069-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, kendi oluşturucusunu bir parametre olarak genel anahtarını içeren dosyanın adını geçirir.</span><span class="sxs-lookup"><span data-stu-id="ec069-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, which passes the name of the file containing the public key as a parameter to its constructor.</span></span>  
  
    -   <span data-ttu-id="ec069-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, bu gecikme imzalama belirten geçirerek kullanılıyor **true** kurucusu parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="ec069-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, which indicates that delay signing is being used by passing **true** as a parameter to its constructor.</span></span> <span data-ttu-id="ec069-114">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ec069-114">For example:</span></span>  
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
         [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
         [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3.  <span data-ttu-id="ec069-115">Derleyici derleme bildirimine ortak anahtar ekler ve tam sağlam ad imzası PE dosyasında alan ayırır.</span><span class="sxs-lookup"><span data-stu-id="ec069-115">The compiler inserts the public key into the assembly manifest and reserves space in the PE file for the full strong name signature.</span></span> <span data-ttu-id="ec069-116">Bu derleme başvurusu diğer derlemelerden kendi derleme başvurusu'nda depolamak için anahtar alabilmesi adına, derlemeyi sırada gerçek ortak anahtarı depolanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ec069-116">The real public key must be stored while the assembly is built so that other assemblies that reference this assembly can obtain the key to store in their own assembly reference.</span></span>  
  
4.  <span data-ttu-id="ec069-117">Derleme geçerli sağlam ad imzası sahip olmadığından, bu imza doğrulaması kapatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ec069-117">Because the assembly does not have a valid strong name signature, the verification of that signature must be turned off.</span></span> <span data-ttu-id="ec069-118">Kullanarak bunu yapabilirsiniz **– Vr** tanımlayıcı ad aracı seçeneğiyle.</span><span class="sxs-lookup"><span data-stu-id="ec069-118">You can do this by using the **–Vr** option with the Strong Name tool.</span></span>  
  
     <span data-ttu-id="ec069-119">Doğrulama adlı bir derleme için aşağıdaki örneği kapatır `myAssembly.dll`.</span><span class="sxs-lookup"><span data-stu-id="ec069-119">The following example turns off verification for an assembly called `myAssembly.dll`.</span></span>  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     <span data-ttu-id="ec069-120">Gelişmiş RISC makinesi (ARM) mikro gibi tanımlayıcı ad aracı çalıştırdığı olamaz doğrulama platformlarda devre dışı bırakmak üzere kullanmak **– Vk** seçeneği kayıt defteri dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ec069-120">To turn off verification on platforms where you can’t run the Strong Name tool, such as Advanced RISC Machine (ARM) microprocessors, use the **–Vk** option to create a registry file.</span></span> <span data-ttu-id="ec069-121">Kayıt defteri dosyasını doğrulamayı kapatmak istediğiniz bilgisayarda kayıt defterini alın.</span><span class="sxs-lookup"><span data-stu-id="ec069-121">Import the registry file into the registry on the computer where you want to turn off verification.</span></span> <span data-ttu-id="ec069-122">Aşağıdaki örnek için bir kayıt defteri dosyası oluşturur `myAssembly.dll`.</span><span class="sxs-lookup"><span data-stu-id="ec069-122">The following example creates a registry file for `myAssembly.dll`.</span></span>  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     <span data-ttu-id="ec069-123">Ya da ile **– Vr** veya **– Vk** seçeneği, isteğe bağlı olarak test anahtar imzalama için bir .snk dosyası içerebilir.</span><span class="sxs-lookup"><span data-stu-id="ec069-123">With either the **–Vr** or **–Vk** option, you can optionally include an .snk file for test key signing.</span></span>  
  
    > [!WARNING]
    > <span data-ttu-id="ec069-124">Güvenlik tanımlayıcı adlar kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="ec069-124">Do not rely on strong names for security.</span></span> <span data-ttu-id="ec069-125">Yalnızca benzersiz bir kimlik sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="ec069-125">They provide a unique identity only.</span></span>
  
    > [!NOTE]
    >  <span data-ttu-id="ec069-126">Bir 64-bit bilgisayarda Visual Studio ile geliştirme sırasında imzalamayı geciktirme kullanırsanız ve bir derleme için derleme **herhangi bir CPU**, uygulanacak olabilir **- Vr** iki kez seçeneği.</span><span class="sxs-lookup"><span data-stu-id="ec069-126">If you use delay signing during development with Visual Studio on a 64-bit computer, and you compile an assembly for **Any CPU**, you might have to apply the **-Vr** option twice.</span></span> <span data-ttu-id="ec069-127">(Visual Studio'da **herhangi bir CPU** bir değeri **Platform hedefi** özelliği yapı; komut satırından derlerken varsayılan değer.) Komut satırından veya dosya Gezgini'nden uygulamanızı çalıştırmak için 64-bit sürümünü kullanmanız [Sn.exe (tanımlayıcı ad aracı)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) uygulamak için **- Vr** derleme seçeneği.</span><span class="sxs-lookup"><span data-stu-id="ec069-127">(In Visual Studio, **Any CPU** is a value of the **Platform Target** build property; when you compile from the command line, it is the default.) To run your application from the command line or from File Explorer, use the 64-bit version of the [Sn.exe (Strong Name Tool)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) to apply the **-Vr** option to the assembly.</span></span> <span data-ttu-id="ec069-128">(Örneğin, derleme, uygulamanızda diğer derlemeleri tarafından kullanılan bileşenleri içeriyorsa) tasarım zamanında Visual Studio'ya derlemeyi yüklemek için tanımlayıcı ad aracı 32-bit sürümünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec069-128">To load the assembly into Visual Studio at design time (for example, if the assembly contains components that are used by other assemblies in your application), use the 32-bit version of the strong-name tool.</span></span> <span data-ttu-id="ec069-129">Tasarım zamanı ortamına derleme yüklendiğinde tam zamanında (JIT) derleyici komut satırından derleme çalıştırdığınızda yerel kod 64-bit ve 32-bit yerel kodu derleme derler olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="ec069-129">This is because the just-in-time (JIT) compiler compiles the assembly to 64-bit native code when the assembly is run from the command line, and to 32-bit native code when the assembly is loaded into the design-time environment.</span></span>  
  
5.  <span data-ttu-id="ec069-130">Daha sonra genellikle tam sevkiyat önce kuruluşunuz derlemeye kullanarak imzalama gerçek güçlü ad için yetkili imzalama gönderme **– R** tanımlayıcı ad aracı seçeneğiyle.</span><span class="sxs-lookup"><span data-stu-id="ec069-130">Later, usually just before shipping, you submit the assembly to your organization's signing authority for the actual strong name signing using the **–R** option with the Strong Name tool.</span></span>  
  
     <span data-ttu-id="ec069-131">Aşağıdaki örnek olarak adlandırılan bir derlemeyi imzalar `myAssembly.dll` kullanarak bir güçlü ad ile `sgKey.snk` anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="ec069-131">The following example signs an assembly called `myAssembly.dll` with a strong name using the `sgKey.snk` key pair.</span></span>  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ec069-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ec069-132">See Also</span></span>  
 [<span data-ttu-id="ec069-133">Bütünleştirilmiş Kodlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ec069-133">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="ec069-134">Nasıl yapılır: Genel-Özel Anahtar Çifti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ec069-134">How to: Create a Public-Private Key Pair</span></span>](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [<span data-ttu-id="ec069-135">Sn.exe (Tanımlayıcı Ad Aracı)</span><span class="sxs-lookup"><span data-stu-id="ec069-135">Sn.exe (Strong Name Tool)</span></span>](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [<span data-ttu-id="ec069-136">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="ec069-136">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
