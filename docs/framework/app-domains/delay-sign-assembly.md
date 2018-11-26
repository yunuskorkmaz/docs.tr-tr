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
ms.openlocfilehash: 87346b28ff98c453949fe31aea4d0ef1880b0095
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52296344"
---
# <a name="delay-signing-an-assembly"></a><span data-ttu-id="e6239-102">Derleme İmzalamayı Geciktirme</span><span class="sxs-lookup"><span data-stu-id="e6239-102">Delay Signing an Assembly</span></span>
<span data-ttu-id="e6239-103">Bir kuruluş geliştiricileri her gün için erişimi yoktur yakından korumalı bir anahtar çifti olabilir.</span><span class="sxs-lookup"><span data-stu-id="e6239-103">An organization can have a closely guarded key pair that developers do not have access to on a daily basis.</span></span> <span data-ttu-id="e6239-104">Genellikle ortak anahtarı mevcut ancak özel anahtarına erişime yalnızca birkaç kişilerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="e6239-104">The public key is often available, but access to the private key is restricted to only a few individuals.</span></span> <span data-ttu-id="e6239-105">Derlemeleri tanımlayıcı adlarla geliştirirken, her derleme başvuruları tanımlayıcı adlı hedef derlemeye hedef derleme tanımlayıcı bir ad vermek için kullanılan ortak anahtar belirtecini içerir.</span><span class="sxs-lookup"><span data-stu-id="e6239-105">When developing assemblies with strong names, each assembly that references the strong-named target assembly contains the token of the public key used to give the target assembly a strong name.</span></span> <span data-ttu-id="e6239-106">Bu ortak anahtarı geliştirme sürecinde kullanılabilir olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e6239-106">This requires that the public key be available during the development process.</span></span>  
  
 <span data-ttu-id="e6239-107">Taşınabilir yürütülebilir (PE) dosyanın tanımlayıcı ad imzası için alan ayırmak, ancak gerçek imzalama bazı (derleme göndermeden önce genellikle yalnızca) sonraki aşama kadar erteleme, geciken ya da kısmi derleme zamanında imzalama'ı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6239-107">You can use delayed or partial signing at build time to reserve space in the portable executable (PE) file for the strong name signature, but defer the actual signing until some later stage (typically just before shipping the assembly).</span></span>  
  
 <span data-ttu-id="e6239-108">Aşağıdaki adımlar, bir derlemeyi gecikmeli imza işleme özetlemektedir:</span><span class="sxs-lookup"><span data-stu-id="e6239-108">The following steps outline the process to delay sign an assembly:</span></span>  
  
1.  <span data-ttu-id="e6239-109">Anahtar çiftinden ortak anahtar kısmını nihai imzalama işlemi gerçekleştirecek kuruluşlardan.</span><span class="sxs-lookup"><span data-stu-id="e6239-109">Obtain the public key portion of the key pair from the organization that will do the eventual signing.</span></span> <span data-ttu-id="e6239-110">Genellikle bu anahtarı kullanılarak oluşturulan bir .snk dosyası biçiminde olan [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) tarafından sağlanan [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e6239-110">Typically this key is in the form of an .snk file, which can be created using the [Strong Name tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
2.  <span data-ttu-id="e6239-111">Kaynak kodu derlemeyi iki özel öznitelikleri ile için ek açıklama <xref:System.Reflection>:</span><span class="sxs-lookup"><span data-stu-id="e6239-111">Annotate the source code for the assembly with two custom attributes from <xref:System.Reflection>:</span></span>  
  
    -   <span data-ttu-id="e6239-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, oluşturucusuna bir parametre olarak ortak anahtarı içeren dosyanın adını geçirir.</span><span class="sxs-lookup"><span data-stu-id="e6239-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, which passes the name of the file containing the public key as a parameter to its constructor.</span></span>  
  
    -   <span data-ttu-id="e6239-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, söz konusu Gecikmeli imzalama gösteren geçirerek kullanılıyor **true** oluşturucusuna bir parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="e6239-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, which indicates that delay signing is being used by passing **true** as a parameter to its constructor.</span></span> <span data-ttu-id="e6239-114">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e6239-114">For example:</span></span>  
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
         [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
         [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3.  <span data-ttu-id="e6239-115">Derleyici ortak anahtarı derleme bildirimine ekler ve PE dosyasının tam tanımlayıcı ad imzası için alan ayırır.</span><span class="sxs-lookup"><span data-stu-id="e6239-115">The compiler inserts the public key into the assembly manifest and reserves space in the PE file for the full strong name signature.</span></span> <span data-ttu-id="e6239-116">Bu derlemeye başvuran diğer derlemeler, kendi derleme başvurusu depolamak için anahtar alabilmesi derlemeyi sırada gerçek ortak anahtarı depolanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e6239-116">The real public key must be stored while the assembly is built so that other assemblies that reference this assembly can obtain the key to store in their own assembly reference.</span></span>  
  
4.  <span data-ttu-id="e6239-117">Derleme geçerli bir tanımlayıcı ad imzası olmadığından, bu imza doğrulaması kapatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e6239-117">Because the assembly does not have a valid strong name signature, the verification of that signature must be turned off.</span></span> <span data-ttu-id="e6239-118">Kullanarak bunu yapabilirsiniz **– Vr** tanımlayıcı ad aracı seçeneği.</span><span class="sxs-lookup"><span data-stu-id="e6239-118">You can do this by using the **–Vr** option with the Strong Name tool.</span></span>  
  
     <span data-ttu-id="e6239-119">Aşağıdaki örnekte adlı bir derleme için doğrulama kapatır `myAssembly.dll`.</span><span class="sxs-lookup"><span data-stu-id="e6239-119">The following example turns off verification for an assembly called `myAssembly.dll`.</span></span>  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     <span data-ttu-id="e6239-120">Tanımlayıcı ad aracı gibi gelişmiş RISC makinesi (ARM) mikro çalıştırdığı olamaz platformları doğrulamayı kapatmak için kullanmak **– Vk** seçeneği kayıt defteri dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e6239-120">To turn off verification on platforms where you can’t run the Strong Name tool, such as Advanced RISC Machine (ARM) microprocessors, use the **–Vk** option to create a registry file.</span></span> <span data-ttu-id="e6239-121">Kayıt defteri dosyasını doğrulamayı kapatmak istediğiniz bilgisayarda kayıt defterini alın.</span><span class="sxs-lookup"><span data-stu-id="e6239-121">Import the registry file into the registry on the computer where you want to turn off verification.</span></span> <span data-ttu-id="e6239-122">Aşağıdaki örnek için bir kayıt defteri dosyası oluşturur `myAssembly.dll`.</span><span class="sxs-lookup"><span data-stu-id="e6239-122">The following example creates a registry file for `myAssembly.dll`.</span></span>  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     <span data-ttu-id="e6239-123">Ya da ile **– Vr** veya **– Vk** seçeneği, isteğe bağlı olarak test anahtar imzalamak için bir .snk dosyası içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e6239-123">With either the **–Vr** or **–Vk** option, you can optionally include an .snk file for test key signing.</span></span>  
  
    > [!WARNING]
    > <span data-ttu-id="e6239-124">Güvenlik için tanımlayıcı adlar güvenmeyin.</span><span class="sxs-lookup"><span data-stu-id="e6239-124">Do not rely on strong names for security.</span></span> <span data-ttu-id="e6239-125">Benzersiz bir kimliğe sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="e6239-125">They provide a unique identity only.</span></span>
  
    > [!NOTE]
    >  <span data-ttu-id="e6239-126">Bir 64 bit bilgisayarda Visual Studio ile geliştirme sırasında imzalamayı geciktirme kullanıyorsanız ve bir derleme için derleme **herhangi bir CPU**, uygulamak gerekebilir **- Vr** iki kez seçeneği.</span><span class="sxs-lookup"><span data-stu-id="e6239-126">If you use delay signing during development with Visual Studio on a 64-bit computer, and you compile an assembly for **Any CPU**, you might have to apply the **-Vr** option twice.</span></span> <span data-ttu-id="e6239-127">(Visual Studio'da **herhangi bir CPU** bir değeri **Platform hedefi** özellik oluşturun; varsayılan olarak, komut satırından derlerken, etkin.) Komut satırından veya dosya Gezgini'nden uygulamanızı çalıştırmak için 64 bit sürümünü kullanan [Sn.exe (tanımlayıcı ad aracı)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) uygulanacak **- Vr** derleme seçeneği.</span><span class="sxs-lookup"><span data-stu-id="e6239-127">(In Visual Studio, **Any CPU** is a value of the **Platform Target** build property; when you compile from the command line, it is the default.) To run your application from the command line or from File Explorer, use the 64-bit version of the [Sn.exe (Strong Name Tool)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) to apply the **-Vr** option to the assembly.</span></span> <span data-ttu-id="e6239-128">(Örneğin, uygulamanızdaki diğer derlemeler tarafından kullanılan bileşenleri derlemeyi içeren) tasarım zamanında, Visual Studio'ya derlemeyi yüklemek için tanımlayıcı ad Aracı'nın 32-bit sürümü kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6239-128">To load the assembly into Visual Studio at design time (for example, if the assembly contains components that are used by other assemblies in your application), use the 32-bit version of the strong-name tool.</span></span> <span data-ttu-id="e6239-129">Derleme tasarım zamanı ortamına yüklendiğinde, just-ın-time (JIT) derleyici derleme komut satırından çalıştırdığınızda yerel kod 64-bit ve 32 bit yerel kod için derleme derler olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="e6239-129">This is because the just-in-time (JIT) compiler compiles the assembly to 64-bit native code when the assembly is run from the command line, and to 32-bit native code when the assembly is loaded into the design-time environment.</span></span>  
  
5.  <span data-ttu-id="e6239-130">Daha sonra genellikle tam aktarmadan önce kuruluşunuz derlemeye projenin yetkilisi kullanarak imzalama gerçek tanımlayıcı ad imzalama gönderme **– R** tanımlayıcı ad aracı seçeneği.</span><span class="sxs-lookup"><span data-stu-id="e6239-130">Later, usually just before shipping, you submit the assembly to your organization's signing authority for the actual strong name signing using the **–R** option with the Strong Name tool.</span></span>  
  
     <span data-ttu-id="e6239-131">Aşağıdaki örnek olarak adlandırılan bir derlemeyi imzalar `myAssembly.dll` kullanarak bir tanımlayıcı ad ile `sgKey.snk` anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="e6239-131">The following example signs an assembly called `myAssembly.dll` with a strong name using the `sgKey.snk` key pair.</span></span>  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e6239-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e6239-132">See Also</span></span>  
- [<span data-ttu-id="e6239-133">Bütünleştirilmiş Kodlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e6239-133">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
- [<span data-ttu-id="e6239-134">Nasıl yapılır: Genel-Özel Anahtar Çifti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e6239-134">How to: Create a Public-Private Key Pair</span></span>](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)  
- [<span data-ttu-id="e6239-135">Sn.exe (Tanımlayıcı Ad Aracı)</span><span class="sxs-lookup"><span data-stu-id="e6239-135">Sn.exe (Strong Name Tool)</span></span>](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
- [<span data-ttu-id="e6239-136">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="e6239-136">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
