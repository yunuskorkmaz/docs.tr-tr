---
title: Derlemeyi gecikmeli imzalama
description: Bu makalede, kesin ad imzası için PE dosyasındaki alanı rezerve eden, ancak gerçek imzalamayı erteleyen, Gecikmeli veya kısmi imzalama açıklanır.
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
ms.openlocfilehash: 7b5c8c8463fdc573782fa457bf5671c72a7e25f7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378500"
---
# <a name="delay-sign-an-assembly"></a><span data-ttu-id="a278a-103">Derlemeyi gecikmeli imzalama</span><span class="sxs-lookup"><span data-stu-id="a278a-103">Delay-sign an assembly</span></span>

<span data-ttu-id="a278a-104">Bir kuruluş, geliştiricilerin günlük olarak erişebileceği, daha yakından korunan bir anahtar çiftine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="a278a-104">An organization can have a closely guarded key pair that developers can't access on a daily basis.</span></span> <span data-ttu-id="a278a-105">Ortak anahtar genellikle kullanılabilir, ancak özel anahtara erişim yalnızca birkaç bireyle kısıtlıdır.</span><span class="sxs-lookup"><span data-stu-id="a278a-105">The public key is often available, but access to the private key is restricted to only a few individuals.</span></span> <span data-ttu-id="a278a-106">Tanımlayıcı adlara sahip derlemeler geliştirirken, tanımlayıcı adlı hedef derlemeye başvuran her derleme, hedef derlemeye tanımlayıcı bir ad vermek için kullanılan ortak anahtarın belirtecini içerir.</span><span class="sxs-lookup"><span data-stu-id="a278a-106">When developing assemblies with strong names, each assembly that references the strong-named target assembly contains the token of the public key used to give the target assembly a strong name.</span></span> <span data-ttu-id="a278a-107">Bu, geliştirme sürecinde ortak anahtarın kullanılabilir olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a278a-107">This requires that the public key be available during the development process.</span></span>

<span data-ttu-id="a278a-108">Güçlü ad imzası için Taşınabilir çalıştırılabilir (PE) dosyasında alan ayırmak için derleme zamanında Gecikmeli veya kısmi imzalamayı kullanabilirsiniz, ancak genellikle derlemeyi teslim etmeden önce, daha sonraki bir aşamaya kadar gerçek imzalamayı erteleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a278a-108">You can use delayed or partial signing at build time to reserve space in the portable executable (PE) file for the strong name signature, but defer the actual signing until some later stage, usually just before shipping the assembly.</span></span>

<span data-ttu-id="a278a-109">Bir derlemeyi gecikmeli imzalamak için:</span><span class="sxs-lookup"><span data-stu-id="a278a-109">To delay-sign an assembly:</span></span>

1. <span data-ttu-id="a278a-110">Son imzalamayı sağlayacak olan kuruluştan anahtar çiftinin ortak anahtar bölümünü alın.</span><span class="sxs-lookup"><span data-stu-id="a278a-110">Get the public key portion of the key pair from the organization that will do the eventual signing.</span></span> <span data-ttu-id="a278a-111">Genellikle bu anahtar, Windows SDK tarafından belirtilen [tanımlayıcı ad Aracı (sn. exe)](../../framework/tools/sn-exe-strong-name-tool.md) kullanılarak oluşturulabilen bir *. snk* dosyası biçimindedir.</span><span class="sxs-lookup"><span data-stu-id="a278a-111">Typically this key is in the form of an *.snk* file, which can be created using the [Strong Name tool (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) provided by the Windows SDK.</span></span>

2. <span data-ttu-id="a278a-112">İki özel özniteliğe sahip derleme için kaynak koda not ekleyin <xref:System.Reflection> :</span><span class="sxs-lookup"><span data-stu-id="a278a-112">Annotate the source code for the assembly with two custom attributes from <xref:System.Reflection>:</span></span>

   - <span data-ttu-id="a278a-113"><xref:System.Reflection.AssemblyKeyFileAttribute>, ortak anahtarı içeren dosyanın adını oluşturucuya bir parametre olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="a278a-113"><xref:System.Reflection.AssemblyKeyFileAttribute>, which passes the name of the file containing the public key as a parameter to its constructor.</span></span>

   - <span data-ttu-id="a278a-114"><xref:System.Reflection.AssemblyDelaySignAttribute>Bu, gecikme imzasının, oluşturucuya bir parametre olarak **doğru** geçirerek kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a278a-114"><xref:System.Reflection.AssemblyDelaySignAttribute>, which indicates that delay signing is being used by passing **true** as a parameter to its constructor.</span></span>

   <span data-ttu-id="a278a-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a278a-115">For example:</span></span>

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

3. <span data-ttu-id="a278a-116">Derleyici, ortak anahtarı derleme bildirimine ekler ve tam tanımlayıcı ad imzası için PE dosyasındaki alanı ayırır.</span><span class="sxs-lookup"><span data-stu-id="a278a-116">The compiler inserts the public key into the assembly manifest and reserves space in the PE file for the full strong name signature.</span></span> <span data-ttu-id="a278a-117">Derleme derlenirken gerçek ortak anahtarın depolanması gerekir, bu derlemeye başvuran diğer derlemeler kendi derleme başvurusunda depolanacak anahtarı elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="a278a-117">The real public key must be stored while the assembly is built so that other assemblies that reference this assembly can obtain the key to store in their own assembly reference.</span></span>

4. <span data-ttu-id="a278a-118">Derlemenin geçerli bir tanımlayıcı ad imzası olmadığından, bu imzanın doğrulanması kapatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a278a-118">Because the assembly does not have a valid strong name signature, the verification of that signature must be turned off.</span></span> <span data-ttu-id="a278a-119">Bunu, tanımlayıcı ad aracı ile **– VR** seçeneğini kullanarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a278a-119">You can do this by using the **–Vr** option with the Strong Name tool.</span></span>

     <span data-ttu-id="a278a-120">Aşağıdaki örnek, *MyAssembly. dll*adlı bir derleme için doğrulamayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="a278a-120">The following example turns off verification for an assembly called *myAssembly.dll*.</span></span>

   ```console
   sn –Vr myAssembly.dll
   ```

   <span data-ttu-id="a278a-121">Gelişmiş RıSC makinesi (ARM) mikro işlemciler gibi tanımlayıcı ad aracını çalıştıramıyorum platformlarda doğrulamayı devre dışı bırakmak için, **– VK** seçeneğini kullanarak bir kayıt defteri dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a278a-121">To turn off verification on platforms where you can’t run the Strong Name tool, such as Advanced RISC Machine (ARM) microprocessors, use the **–Vk** option to create a registry file.</span></span> <span data-ttu-id="a278a-122">Kayıt defteri dosyasını, doğrulamayı kapatmak istediğiniz bilgisayarda kayıt defterine aktarın.</span><span class="sxs-lookup"><span data-stu-id="a278a-122">Import the registry file into the registry on the computer where you want to turn off verification.</span></span> <span data-ttu-id="a278a-123">Aşağıdaki örnek için bir kayıt defteri dosyası oluşturur `myAssembly.dll` .</span><span class="sxs-lookup"><span data-stu-id="a278a-123">The following example creates a registry file for `myAssembly.dll`.</span></span>

   ```console
   sn –Vk myRegFile.reg myAssembly.dll
   ```

   <span data-ttu-id="a278a-124">**– VR** veya **– VK** seçeneği ile, isteğe bağlı olarak test anahtar imzalama için bir *. snk* dosyası ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a278a-124">With either the **–Vr** or **–Vk** option, you can optionally include an *.snk* file for test key signing.</span></span>

   > [!WARNING]
   > <span data-ttu-id="a278a-125">Güvenlik için tanımlayıcı adlara güvenmeyin.</span><span class="sxs-lookup"><span data-stu-id="a278a-125">Do not rely on strong names for security.</span></span> <span data-ttu-id="a278a-126">Yalnızca benzersiz bir kimlik sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="a278a-126">They provide a unique identity only.</span></span>

   > [!NOTE]
   > <span data-ttu-id="a278a-127">Visual Studio ile geliştirme sırasında gecikme imzalamayı 64 bitlik bir bilgisayarda kullanırsanız ve **herhangi BIR CPU**için derleme derlerseniz, **-VR** seçeneğini iki kez uygulamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="a278a-127">If you use delay signing during development with Visual Studio on a 64-bit computer, and you compile an assembly for **Any CPU**, you might have to apply the **-Vr** option twice.</span></span> <span data-ttu-id="a278a-128">(Visual Studio 'da, **herhangi BIR CPU** **Platform hedefi** derleme özelliğinin bir değeridir; komut satırından derlerken varsayılan değerdir.) Uygulamanızı komut satırından veya dosya Gezgini 'nden çalıştırmak için, **-VR** seçeneğini derlemeye uygulamak için sn. exe ' nin 64 bit sürümünü kullanın [(tanımlayıcı ad aracı)](../../framework/tools/sn-exe-strong-name-tool.md) .</span><span class="sxs-lookup"><span data-stu-id="a278a-128">(In Visual Studio, **Any CPU** is a value of the **Platform Target** build property; when you compile from the command line, it is the default.) To run your application from the command line or from File Explorer, use the 64-bit version of the [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md) to apply the **-Vr** option to the assembly.</span></span> <span data-ttu-id="a278a-129">Tasarım zamanında derlemeyi Visual Studio 'ya yüklemek için (örneğin, derleme uygulamanızdaki diğer derlemeler tarafından kullanılan bileşenleri içeriyorsa), güçlü ad aracının 32 bitlik sürümünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="a278a-129">To load the assembly into Visual Studio at design time (for example, if the assembly contains components that are used by other assemblies in your application), use the 32-bit version of the strong-name tool.</span></span> <span data-ttu-id="a278a-130">Bunun nedeni, Just-In-Time (JıT) derleyicisi derlemeyi komut satırından çalıştırıldığında derlemeyi 64-bit yerel koda derlediğinde ve derleme tasarım zamanı ortamına yüklendiğinde, 32 bit yerel kodda.</span><span class="sxs-lookup"><span data-stu-id="a278a-130">This is because the just-in-time (JIT) compiler compiles the assembly to 64-bit native code when the assembly is run from the command line, and to 32-bit native code when the assembly is loaded into the design-time environment.</span></span>

5. <span data-ttu-id="a278a-131">Daha sonra, genellikle teslim etmeden hemen önce, derlemeyi kuruluşunuzun imza yetkilisine göndererek, tanımlayıcı ad aracı ile **– R** seçeneğini kullanarak gerçek tanımlayıcı ad imzalama.</span><span class="sxs-lookup"><span data-stu-id="a278a-131">Later, usually just before shipping, you submit the assembly to your organization's signing authority for the actual strong name signing using the **–R** option with the Strong Name tool.</span></span>

   <span data-ttu-id="a278a-132">Aşağıdaki örnek, *MyAssembly. dll* adlı bir derlemeyi *sgKey. snk* anahtar çiftini kullanarak tanımlayıcı bir adla imzalar.</span><span class="sxs-lookup"><span data-stu-id="a278a-132">The following example signs an assembly called *myAssembly.dll* with a strong name using the *sgKey.snk* key pair.</span></span>

   ```console
   sn -R myAssembly.dll sgKey.snk
   ```

## <a name="see-also"></a><span data-ttu-id="a278a-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a278a-133">See also</span></span>

- [<span data-ttu-id="a278a-134">Derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="a278a-134">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="a278a-135">Nasıl yapılır: genel-özel anahtar çifti oluşturma</span><span class="sxs-lookup"><span data-stu-id="a278a-135">How to: Create a public-private key pair</span></span>](create-public-private-key-pair.md)
- [<span data-ttu-id="a278a-136">Sn. exe (tanımlayıcı ad aracı)</span><span class="sxs-lookup"><span data-stu-id="a278a-136">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
