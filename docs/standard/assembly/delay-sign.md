---
title: Derlemeyi gecikmeli imzalama
ms.date: 08/19/2019
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 113df1ad3fc3ac1e27ebfef572494c1f15a3dbb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73733168"
---
# <a name="delay-sign-an-assembly"></a><span data-ttu-id="f2760-102">Derlemeyi gecikmeli imzalama</span><span class="sxs-lookup"><span data-stu-id="f2760-102">Delay-sign an assembly</span></span>

<span data-ttu-id="f2760-103">Bir kuruluş, geliştiricilerin günlük olarak erişemeyebileceği, sıkı korunan bir anahtar çiftine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="f2760-103">An organization can have a closely guarded key pair that developers can't access on a daily basis.</span></span> <span data-ttu-id="f2760-104">Ortak anahtar genellikle kullanılabilir, ancak özel anahtara erişim yalnızca birkaç kişiyle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="f2760-104">The public key is often available, but access to the private key is restricted to only a few individuals.</span></span> <span data-ttu-id="f2760-105">Güçlü adlara sahip derlemeler geliştirirken, güçlü adlandırılmış hedef derlemeye başvuran her derleme, hedef derlemeye güçlü bir ad vermek için kullanılan ortak anahtarın belirteci içerir.</span><span class="sxs-lookup"><span data-stu-id="f2760-105">When developing assemblies with strong names, each assembly that references the strong-named target assembly contains the token of the public key used to give the target assembly a strong name.</span></span> <span data-ttu-id="f2760-106">Bu, geliştirme işlemi sırasında ortak anahtarın kullanılabilir olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f2760-106">This requires that the public key be available during the development process.</span></span>

<span data-ttu-id="f2760-107">Güçlü ad imzası için taşınabilir yürütülebilir (PE) dosyasında yer ayırmak için yapı zamanında gecikmeli veya kısmi imza kullanabilir, ancak gerçek imzayı genellikle derlemeyi göndermeden hemen önce, daha sonraki bir aşamaya erteleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2760-107">You can use delayed or partial signing at build time to reserve space in the portable executable (PE) file for the strong name signature, but defer the actual signing until some later stage, usually just before shipping the assembly.</span></span>

<span data-ttu-id="f2760-108">Bir derlemeyi geciktirmek için:</span><span class="sxs-lookup"><span data-stu-id="f2760-108">To delay-sign an assembly:</span></span>

1. <span data-ttu-id="f2760-109">Anahtar çiftinin ortak anahtar kısmını, nihai imzalamayı yapacak kuruluştan alın.</span><span class="sxs-lookup"><span data-stu-id="f2760-109">Get the public key portion of the key pair from the organization that will do the eventual signing.</span></span> <span data-ttu-id="f2760-110">Genellikle bu anahtar, Windows SDK tarafından sağlanan Güçlü Ad aracı [(Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) kullanılarak oluşturulabilen bir *.snk* dosyası biçimindedir.</span><span class="sxs-lookup"><span data-stu-id="f2760-110">Typically this key is in the form of an *.snk* file, which can be created using the [Strong Name tool (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) provided by the Windows SDK.</span></span>

2. <span data-ttu-id="f2760-111">İki özel öznitelikleri ile derleme için kaynak <xref:System.Reflection>kodu açıklama:</span><span class="sxs-lookup"><span data-stu-id="f2760-111">Annotate the source code for the assembly with two custom attributes from <xref:System.Reflection>:</span></span>

   - <span data-ttu-id="f2760-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, ortak anahtarı içeren dosyanın adını parametre olarak oluşturucuya geçirir.</span><span class="sxs-lookup"><span data-stu-id="f2760-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, which passes the name of the file containing the public key as a parameter to its constructor.</span></span>

   - <span data-ttu-id="f2760-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, geciktirme imzalamanın, oluşturucuya bir parametre olarak **gerçek** olarak geçirilerek kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2760-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, which indicates that delay signing is being used by passing **true** as a parameter to its constructor.</span></span>

   <span data-ttu-id="f2760-114">Örnek:</span><span class="sxs-lookup"><span data-stu-id="f2760-114">For example:</span></span>

   ```cpp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")];
   [assembly:AssemblyDelaySignAttribute(true)];
   ```

   ```csharp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")]
   [assembly:AssemblyDelaySignAttribute(true)]
   ```

   ```vb
   <Assembly:AssemblyKeyFileAttribute("myKey.snk")>
   <Assembly:AssemblyDelaySignAttribute(True)>
   ```

3. <span data-ttu-id="f2760-115">Derleyici ortak anahtarı derleme manifestosuna ekler ve tam güçlü ad imzası için PE dosyasına yer ayırır.</span><span class="sxs-lookup"><span data-stu-id="f2760-115">The compiler inserts the public key into the assembly manifest and reserves space in the PE file for the full strong name signature.</span></span> <span data-ttu-id="f2760-116">Derleme oluşturulurken gerçek ortak anahtar depolanmalıdır, böylece bu derlemeye başvuran diğer derlemeler kendi derleme referanslarında depolanacak anahtarı elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="f2760-116">The real public key must be stored while the assembly is built so that other assemblies that reference this assembly can obtain the key to store in their own assembly reference.</span></span>

4. <span data-ttu-id="f2760-117">Derlemede geçerli bir güçlü ad imzası olmadığından, imzanın doğrulanması kapatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f2760-117">Because the assembly does not have a valid strong name signature, the verification of that signature must be turned off.</span></span> <span data-ttu-id="f2760-118">Bunu Güçlü Ad aracıyla **-Vr** seçeneğini kullanarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2760-118">You can do this by using the **–Vr** option with the Strong Name tool.</span></span>

     <span data-ttu-id="f2760-119">Aşağıdaki örnek *myAssembly.dll*adlı bir derleme için doğrulamayı kapatır.</span><span class="sxs-lookup"><span data-stu-id="f2760-119">The following example turns off verification for an assembly called *myAssembly.dll*.</span></span>

   ```console
   sn –Vr myAssembly.dll
   ```

   <span data-ttu-id="f2760-120">Gelişmiş RISC Machine (ARM) mikroişlemcileri gibi Güçlü Ad aracını çalıştıramadığınız platformlarda doğrulamayı kapatmak için bir kayıt defteri dosyası oluşturmak için **-Vk** seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f2760-120">To turn off verification on platforms where you can’t run the Strong Name tool, such as Advanced RISC Machine (ARM) microprocessors, use the **–Vk** option to create a registry file.</span></span> <span data-ttu-id="f2760-121">Kayıt defteri dosyasını doğrulamayı kapatmak istediğiniz bilgisayardaki kayıt defterine aktarın.</span><span class="sxs-lookup"><span data-stu-id="f2760-121">Import the registry file into the registry on the computer where you want to turn off verification.</span></span> <span data-ttu-id="f2760-122">Aşağıdaki örnek için `myAssembly.dll`bir kayıt defteri dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f2760-122">The following example creates a registry file for `myAssembly.dll`.</span></span>

   ```console
   sn –Vk myRegFile.reg myAssembly.dll
   ```

   <span data-ttu-id="f2760-123">**-Vr** veya **-Vk** seçeneği ile isteğe bağlı olarak test anahtarı imzalama için bir *.snk* dosyası ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2760-123">With either the **–Vr** or **–Vk** option, you can optionally include an *.snk* file for test key signing.</span></span>

   > [!WARNING]
   > <span data-ttu-id="f2760-124">Güvenlik için güçlü isimlere güvenmeyin.</span><span class="sxs-lookup"><span data-stu-id="f2760-124">Do not rely on strong names for security.</span></span> <span data-ttu-id="f2760-125">Yalnızca benzersiz bir kimlik sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="f2760-125">They provide a unique identity only.</span></span>

   > [!NOTE]
   > <span data-ttu-id="f2760-126">Visual Studio ile geliştirme sırasında 64 bit bilgisayarda gecikme imzalamayı kullanırsanız ve Herhangi bir **CPU**için bir derleme derlerseniz, **-Vr** seçeneğini iki kez uygulamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="f2760-126">If you use delay signing during development with Visual Studio on a 64-bit computer, and you compile an assembly for **Any CPU**, you might have to apply the **-Vr** option twice.</span></span> <span data-ttu-id="f2760-127">(Visual Studio'da, Herhangi bir **CPU** **Platform Hedef** yapı özelliğinin bir değeridir; komut satırından derlediğinizde varsayılandır.) Uygulamanızı komut satırından veya Dosya Gezgini'nden çalıştırmak **için, -Vr** seçeneğini derlemeye uygulamak için [Sn.exe'nin (Güçlü Ad aracı)](../../framework/tools/sn-exe-strong-name-tool.md) 64 bit sürümünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="f2760-127">(In Visual Studio, **Any CPU** is a value of the **Platform Target** build property; when you compile from the command line, it is the default.) To run your application from the command line or from File Explorer, use the 64-bit version of the [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md) to apply the **-Vr** option to the assembly.</span></span> <span data-ttu-id="f2760-128">Derlemeyi tasarım zamanında Visual Studio'ya yüklemek için (örneğin, montaj uygulamanızdaki diğer derlemeler tarafından kullanılan bileşenler içeriyorsa), güçlü ad aracının 32 bit sürümünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="f2760-128">To load the assembly into Visual Studio at design time (for example, if the assembly contains components that are used by other assemblies in your application), use the 32-bit version of the strong-name tool.</span></span> <span data-ttu-id="f2760-129">Bunun nedeni, derleme komut satırından çalıştırıldığında derlemeyi 64 bit yerel koda ve derleme tasarım zamanı ortamına yüklendiğinde 32 bit yerel koda derlemesidir.</span><span class="sxs-lookup"><span data-stu-id="f2760-129">This is because the just-in-time (JIT) compiler compiles the assembly to 64-bit native code when the assembly is run from the command line, and to 32-bit native code when the assembly is loaded into the design-time environment.</span></span>

5. <span data-ttu-id="f2760-130">Daha sonra, genellikle sevkiyattan hemen önce, derlemeyi Güçlü Ad aracıyla **–R** seçeneğini kullanarak gerçek güçlü ad imzalama için kuruluşunuzun imzalama yetkisine gönderirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2760-130">Later, usually just before shipping, you submit the assembly to your organization's signing authority for the actual strong name signing using the **–R** option with the Strong Name tool.</span></span>

   <span data-ttu-id="f2760-131">Aşağıdaki örnek, *sgKey.snk* anahtar çiftini kullanarak güçlü bir adla *myAssembly.dll* adlı bir derlemeyi imzalar.</span><span class="sxs-lookup"><span data-stu-id="f2760-131">The following example signs an assembly called *myAssembly.dll* with a strong name using the *sgKey.snk* key pair.</span></span>

   ```console
   sn -R myAssembly.dll sgKey.snk
   ```

## <a name="see-also"></a><span data-ttu-id="f2760-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2760-132">See also</span></span>

- [<span data-ttu-id="f2760-133">Derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="f2760-133">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="f2760-134">Nasıl yapilir: Genel-özel anahtar çifti oluşturma</span><span class="sxs-lookup"><span data-stu-id="f2760-134">How to: Create a public-private key pair</span></span>](create-public-private-key-pair.md)
- [<span data-ttu-id="f2760-135">Sn.exe (Güçlü Ad aracı)</span><span class="sxs-lookup"><span data-stu-id="f2760-135">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
