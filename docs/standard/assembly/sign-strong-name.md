---
title: 'Nasıl yapılır: Bir derlemeyi güçlü bir adla imzala'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 527fd68ef40e152b57a1fc98113094d3b41fbaae
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973063"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="279d8-102">Nasıl yapılır: Bir derlemeyi güçlü bir adla imzala</span><span class="sxs-lookup"><span data-stu-id="279d8-102">How to: Sign an assembly with a strong name</span></span>

> [!NOTE]
> <span data-ttu-id="279d8-103">.NET Core, tanımlayıcı adlı derlemeleri desteklese de, .NET Core kitaplığındaki tüm derlemeler imzalansa da, üçüncü taraf derlemelerin çoğunluğunun tanımlayıcı adlara ihtiyacı yoktur.</span><span class="sxs-lookup"><span data-stu-id="279d8-103">Although .NET Core supports strong-named assemblies, and all assemblies in the .NET Core library are signed, the majority of third-party assemblies do not need strong names.</span></span> <span data-ttu-id="279d8-104">Daha fazla bilgi için bkz. GitHub 'da [tanımlayıcı ad imzalama](https://github.com/dotnet/corefx/blob/master/Documentation/project-docs/strong-name-signing.md) .</span><span class="sxs-lookup"><span data-stu-id="279d8-104">For more information, see [Strong Name Signing](https://github.com/dotnet/corefx/blob/master/Documentation/project-docs/strong-name-signing.md) on GitHub.</span></span>

<span data-ttu-id="279d8-105">Bir derlemeyi katı bir adla imzalamak için çeşitli yollar vardır:</span><span class="sxs-lookup"><span data-stu-id="279d8-105">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
- <span data-ttu-id="279d8-106">Visual Studio 'da bir projenin **Özellikler** Iletişim kutusunda **imzalama** sekmesini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="279d8-106">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="279d8-107">Bu, bir derlemeyi katı bir adla imzalamanın en kolay ve en kullanışlı yoludur.</span><span class="sxs-lookup"><span data-stu-id="279d8-107">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
- <span data-ttu-id="279d8-108">Bir .NET Framework kodu modülünü ( *. netmodule* dosyası) anahtar dosyasıyla bağlamak Için [derleme Bağlayıcısı (al. exe)](../../framework/tools/al-exe-assembly-linker.md) kullanarak.</span><span class="sxs-lookup"><span data-stu-id="279d8-108">By using the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a *.netmodule* file) with a key file.</span></span>  
  
- <span data-ttu-id="279d8-109">Katı ad bilgilerini kodunuza eklemek için derleme özniteliklerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="279d8-109">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="279d8-110">Kullanılacak anahtar dosyasının bulunduğu yere <xref:System.Reflection.AssemblyKeyFileAttribute> bağlı olarak <xref:System.Reflection.AssemblyKeyNameAttribute> ya da özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="279d8-110">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
- <span data-ttu-id="279d8-111">Derleyici seçeneklerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="279d8-111">By using compiler options.</span></span>  
  
 <span data-ttu-id="279d8-112">Bir derlemeye katı bir ad atamak için bir şifreleme anahtarı çiftiniz olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="279d8-112">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="279d8-113">Anahtar çifti oluşturma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Ortak özel anahtar çifti](create-public-private-key-pair.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="279d8-113">For more information about creating a key pair, see [How to: Create a public-private key pair](create-public-private-key-pair.md).</span></span>  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="279d8-114">Visual Studio 'Yu kullanarak tanımlayıcı ad ile derleme oluşturma ve imzalama</span><span class="sxs-lookup"><span data-stu-id="279d8-114">Create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1. <span data-ttu-id="279d8-115">**Çözüm Gezgini**' de, proje için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="279d8-115">In **Solution Explorer**, open the shortcut menu for the project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="279d8-116">**İmzalama** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="279d8-116">Choose the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="279d8-117">**Derlemeyi imzala** kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="279d8-117">Select the **Sign the assembly** box.</span></span>  
  
4. <span data-ttu-id="279d8-118">**Tanımlayıcı ad seçin anahtar dosyası** kutusunda, **Araştır**' ı seçin ve ardından anahtar dosyasına gidin.</span><span class="sxs-lookup"><span data-stu-id="279d8-118">In the **Choose a strong name key file** box, choose **Browse**, and then navigate to the key file.</span></span> <span data-ttu-id="279d8-119">Yeni bir anahtar dosyası oluşturmak için **Yeni** ' yi seçin ve **tanımlayıcı ad anahtarı oluştur** iletişim kutusuna adını girin.</span><span class="sxs-lookup"><span data-stu-id="279d8-119">To create a new key file, choose **New** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="279d8-120">[Bir derlemeyi imzalamayı geciktirmek](delay-sign.md)için bir ortak anahtar dosyası seçin.</span><span class="sxs-lookup"><span data-stu-id="279d8-120">In order to [delay sign an assembly](delay-sign.md), choose a public key file.</span></span>  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="279d8-121">Derleme bağlayıcı kullanarak tanımlayıcı ad ile derleme oluşturma ve imzalama</span><span class="sxs-lookup"><span data-stu-id="279d8-121">Create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
<span data-ttu-id="279d8-122">[Visual Studio için geliştirici komut istemi](../../framework/tools/developer-command-prompt-for-vs.md), aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="279d8-122">At the [Developer Command Prompt for Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), enter the following command:</span></span>  

<span data-ttu-id="279d8-123">**Al** **/Out:** \<AssemblyNameModuleName> > **/keyfile**:keyfilename\< *\<* ></span><span class="sxs-lookup"><span data-stu-id="279d8-123">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  

<span data-ttu-id="279d8-124">Konum:</span><span class="sxs-lookup"><span data-stu-id="279d8-124">Where:</span></span>  

- <span data-ttu-id="279d8-125">*AssemblyName* , derleme bağlayıcının Yayladığı, kesin imzalı derlemenin (bir *. dll* veya *. exe* dosyası) adıdır.</span><span class="sxs-lookup"><span data-stu-id="279d8-125">*assemblyName* is the name of the strongly signed assembly (a *.dll* or *.exe* file) that Assembly Linker will emit.</span></span>  
  
- <span data-ttu-id="279d8-126">*ModuleName* bir veya daha fazla tür içeren bir .NET Framework kod modülünün ( *. netmodule* dosyası) adıdır.</span><span class="sxs-lookup"><span data-stu-id="279d8-126">*moduleName* is the name of a .NET Framework code module (a *.netmodule* file) that includes one or more types.</span></span> <span data-ttu-id="279d8-127">Kodunuzu`/target:module` veya Visual Basic içindeki C# anahtarla derleyerek bir *. netmodule* dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="279d8-127">You can create a *.netmodule* file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>
  
- <span data-ttu-id="279d8-128">*Keyfilename* , anahtar çiftini içeren kapsayıcının veya dosyanın adıdır.</span><span class="sxs-lookup"><span data-stu-id="279d8-128">*keyfileName* is the name of the container or file that contains the key pair.</span></span> <span data-ttu-id="279d8-129">Derleme Bağlayıcı, geçerli dizinle ilişkili bir göreli yolu yorumlar.</span><span class="sxs-lookup"><span data-stu-id="279d8-129">Assembly Linker interprets a relative path in relation to the current directory.</span></span>  

<span data-ttu-id="279d8-130">Aşağıdaki örnek, *sgKey. snk*anahtar dosyasını kullanarak *MyAssembly. dll* derlemesini tanımlayıcı bir adla imzalar.</span><span class="sxs-lookup"><span data-stu-id="279d8-130">The following example signs the assembly *MyAssembly.dll* with a strong name by using the key file *sgKey.snk*.</span></span>  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
<span data-ttu-id="279d8-131">Bu araç hakkında daha fazla bilgi için bkz. [derleme Bağlayıcısı](../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="279d8-131">For more information about this tool, see [Assembly Linker](../../framework/tools/al-exe-assembly-linker.md).</span></span>  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="279d8-132">Öznitelikleri kullanarak bir derlemeyi tanımlayıcı adla imzalama</span><span class="sxs-lookup"><span data-stu-id="279d8-132">Sign an assembly with a strong name by using attributes</span></span>  
  
1. <span data-ttu-id="279d8-133">Kaynak kodu dosyanıza <xref:System.Reflection.AssemblyKeyNameAttribute>orözniteliğini ekleyin ve derlemeyi tanımlayıcı bir adla imzalarken kullanılacak anahtar çiftini içeren dosya veya kapsayıcının adını belirtin. <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="279d8-133">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  
   
2. <span data-ttu-id="279d8-134">Kaynak kodu normal şekilde derleyin.</span><span class="sxs-lookup"><span data-stu-id="279d8-134">Compile the source code file normally.</span></span>  
   
   > [!NOTE]
   > <span data-ttu-id="279d8-135">C# Ve Visual Basic derleyicileri, kaynak kodundaki <xref:System.Reflection.AssemblyKeyFileAttribute> veya <xref:System.Reflection.AssemblyKeyNameAttribute> özniteliğiyle karşılaştığında derleyici uyarılarını (sırasıyla CS1699 ve BC41008) yayınlarlar.</span><span class="sxs-lookup"><span data-stu-id="279d8-135">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="279d8-136">Uyarıları gözardı edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="279d8-136">You can ignore the warnings.</span></span>  

<span data-ttu-id="279d8-137">Aşağıdaki örnek <xref:System.Reflection.AssemblyKeyFileAttribute> özniteliğini, derlemenin derlendiği dizinde bulunan *keyfile. snk*adlı anahtar dosyasıyla birlikte kullanır.</span><span class="sxs-lookup"><span data-stu-id="279d8-137">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called *keyfile.snk*, which is located in the directory where the assembly is compiled.</span></span>  

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

<span data-ttu-id="279d8-138">Ayrıca kaynak dosyanızı derlerken bir derlemeyi imzalamayı erteleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="279d8-138">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="279d8-139">Daha fazla bilgi için bkz. [bir derlemeyi Gecikmeli imzalama](delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="279d8-139">For more information, see [Delay-sign an assembly](delay-sign.md).</span></span>  

## <a name="sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="279d8-140">Derleyici kullanarak bir derlemeyi tanımlayıcı adla imzalama</span><span class="sxs-lookup"><span data-stu-id="279d8-140">Sign an assembly with a strong name by using the compiler</span></span>  

<span data-ttu-id="279d8-141">Kaynak `/keyfile` kodu dosyanızı veya dosyalarınızı, veya Visual Basic içindeki C# or `/delaysign` derleyici seçeneğiyle veya `/KEYFILE` ' de `/DELAYSIGN` C++veya bağlayıcı seçeneğinde derleyin.</span><span class="sxs-lookup"><span data-stu-id="279d8-141">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="279d8-142">Seçenek adından sonra, iki nokta işareti ve anahtar dosyasının adını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="279d8-142">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="279d8-143">Komut satırı derleyicileri kullanırken, anahtar dosyasını kaynak kodu dosyalarınızı içeren dizine kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="279d8-143">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  

<span data-ttu-id="279d8-144">Gecikmeli imzalama hakkında daha fazla bilgi için bkz. [bir derlemeyi gecikmeli](delay-sign.md)imzalama.</span><span class="sxs-lookup"><span data-stu-id="279d8-144">For information on delay signing, see [Delay-sign an assembly](delay-sign.md).</span></span>  

<span data-ttu-id="279d8-145">Aşağıdaki örnek, C# derleyicisini kullanır ve *bir derlemeyi,* *sgKey. snk*anahtar dosyasını kullanarak tanımlayıcı bir adla imzalar.</span><span class="sxs-lookup"><span data-stu-id="279d8-145">The following example uses the C# compiler and signs the assembly *UtilityLibrary.dll* with a strong name by using the key file *sgKey.snk*.</span></span>  

```cmd
csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
```  

## <a name="see-also"></a><span data-ttu-id="279d8-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="279d8-146">See also</span></span>

- [<span data-ttu-id="279d8-147">Tanımlayıcı adlı derlemeler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="279d8-147">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="279d8-148">Nasıl yapılır: Ortak özel anahtar çifti oluşturma</span><span class="sxs-lookup"><span data-stu-id="279d8-148">How to: Create a public-private key pair</span></span>](create-public-private-key-pair.md)
- [<span data-ttu-id="279d8-149">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="279d8-149">Al.exe (Assembly Linker)</span></span>](../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="279d8-150">Bir derlemeyi gecikmeli imzala</span><span class="sxs-lookup"><span data-stu-id="279d8-150">Delay-sign an assembly</span></span>](delay-sign.md)
- [<span data-ttu-id="279d8-151">Derleme ve bildirim imzalamayı yönetme</span><span class="sxs-lookup"><span data-stu-id="279d8-151">Manage assembly and manifest signing</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [<span data-ttu-id="279d8-152">İmzalama sayfası, proje Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="279d8-152">Signing page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
