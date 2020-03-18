---
title: 'Nasıl yapilir: Güçlü bir ada sahip bir derlemeyi imzalama'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 9998e69e8bf1505bcfc7a9103e9d89616dad9633
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160319"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="8b5c3-102">Nasıl yapilir: Güçlü bir ada sahip bir derlemeyi imzalama</span><span class="sxs-lookup"><span data-stu-id="8b5c3-102">How to: Sign an assembly with a strong name</span></span>

> [!NOTE]
> <span data-ttu-id="8b5c3-103">.NET Core güçlü adlandırılmış derlemeleri desteklese ve .NET Core kitaplığındaki tüm derlemeler imzalanmış olsa da, üçüncü taraf derlemelerin çoğunluğugüçlü adlara ihtiyaç duymaz.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-103">Although .NET Core supports strong-named assemblies, and all assemblies in the .NET Core library are signed, the majority of third-party assemblies do not need strong names.</span></span> <span data-ttu-id="8b5c3-104">Daha fazla bilgi için GitHub'da [Güçlü Ad İmzalama'ya](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-104">For more information, see [Strong Name Signing](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) on GitHub.</span></span>

<span data-ttu-id="8b5c3-105">Bir derlemeyi katı bir adla imzalamak için çeşitli yollar vardır:</span><span class="sxs-lookup"><span data-stu-id="8b5c3-105">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
- <span data-ttu-id="8b5c3-106">Visual Studio'da projenin **Özellikler** iletişim kutusunda **İmzalama** sekmesini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-106">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="8b5c3-107">Bu, bir derlemeyi katı bir adla imzalamanın en kolay ve en kullanışlı yoludur.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-107">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
- <span data-ttu-id="8b5c3-108">Bir .NET Framework kod modüllerini *(.netmodule* dosyası) anahtar dosyasına bağlamak için [Derleme Bağlantı Cısı'nı (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) kullanarak.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-108">By using the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a *.netmodule* file) with a key file.</span></span>  
  
- <span data-ttu-id="8b5c3-109">Katı ad bilgilerini kodunuza eklemek için derleme özniteliklerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-109">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="8b5c3-110">Kullanılacak anahtar dosyasının <xref:System.Reflection.AssemblyKeyFileAttribute> <xref:System.Reflection.AssemblyKeyNameAttribute> bulunduğu yere bağlı olarak özniteliği veya özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-110">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
- <span data-ttu-id="8b5c3-111">Derleyici seçeneklerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-111">By using compiler options.</span></span>  
  
 <span data-ttu-id="8b5c3-112">Bir derlemeye katı bir ad atamak için bir şifreleme anahtarı çiftiniz olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-112">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="8b5c3-113">Anahtar çifti oluşturma hakkında daha fazla bilgi için [bkz.](create-public-private-key-pair.md)</span><span class="sxs-lookup"><span data-stu-id="8b5c3-113">For more information about creating a key pair, see [How to: Create a public-private key pair](create-public-private-key-pair.md).</span></span>  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="8b5c3-114">Visual Studio'u kullanarak güçlü bir ada sahip bir derleme oluşturma ve imzalama</span><span class="sxs-lookup"><span data-stu-id="8b5c3-114">Create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1. <span data-ttu-id="8b5c3-115">**Çözüm Gezgini'nde,** proje için kısayol menüsünü açın ve ardından **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-115">In **Solution Explorer**, open the shortcut menu for the project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="8b5c3-116">**İmzala** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-116">Choose the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="8b5c3-117">Montaj kutusunu **Imzala'yı** seçin.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-117">Select the **Sign the assembly** box.</span></span>  
  
4. <span data-ttu-id="8b5c3-118">Güçlü **bir ad anahtarı dosya** kutusunu seçin, **Gözat'ı**seçin ve ardından anahtar dosyasına gidin.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-118">In the **Choose a strong name key file** box, choose **Browse**, and then navigate to the key file.</span></span> <span data-ttu-id="8b5c3-119">Yeni bir anahtar dosyası oluşturmak için **Yeni'yi** seçin ve **Adını Güçlü Ad Anahtarı Oluştur** iletişim kutusuna girin.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-119">To create a new key file, choose **New** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b5c3-120">[Bir derlemeyi imzalamayı geciktirmek](delay-sign.md)için ortak anahtar dosyası seçin.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-120">In order to [delay sign an assembly](delay-sign.md), choose a public key file.</span></span>  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="8b5c3-121">Derleme Bağlantı Cılız'ı kullanarak güçlü bir ada sahip bir derleme oluşturma ve imzalama</span><span class="sxs-lookup"><span data-stu-id="8b5c3-121">Create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
<span data-ttu-id="8b5c3-122">Visual [Studio için Geliştirici Komut Komut Ustem'inde](../../framework/tools/developer-command-prompt-for-vs.md)aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="8b5c3-122">At the [Developer Command Prompt for Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), enter the following command:</span></span>  

<span data-ttu-id="8b5c3-123">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span><span class="sxs-lookup"><span data-stu-id="8b5c3-123">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  

<span data-ttu-id="8b5c3-124">Konumlar:</span><span class="sxs-lookup"><span data-stu-id="8b5c3-124">Where:</span></span>  

- <span data-ttu-id="8b5c3-125">*assemblyName,* Assembly Linker'ın yarayacağı güçlü bir şekilde imzalanmış derlemenin *(.dll* veya *.exe* dosyası) adıdır.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-125">*assemblyName* is the name of the strongly signed assembly (a *.dll* or *.exe* file) that Assembly Linker will emit.</span></span>  
  
- <span data-ttu-id="8b5c3-126">*moduleName,* bir veya daha fazla tür içeren bir .NET Framework kod modülünün *(.netmodule* dosyası) adıdır.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-126">*moduleName* is the name of a .NET Framework code module (a *.netmodule* file) that includes one or more types.</span></span> <span data-ttu-id="8b5c3-127">C# veya Visual `/target:module` Basic'teki anahtarla kodunuzu derleyerek bir *.netmodule* dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-127">You can create a *.netmodule* file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>
  
- <span data-ttu-id="8b5c3-128">*keyfileName* anahtar çiftini içeren kapsayıcı veya dosyanın adıdır.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-128">*keyfileName* is the name of the container or file that contains the key pair.</span></span> <span data-ttu-id="8b5c3-129">Derleme Bağlantıcısı, geçerli dizine göre göreli bir yolu yorumlar.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-129">Assembly Linker interprets a relative path in relation to the current directory.</span></span>  

<span data-ttu-id="8b5c3-130">Aşağıdaki örnek anahtar *dosyasgKey.snk*kullanarak güçlü bir ad ile derleme *MyAssembly.dll* imzalar.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-130">The following example signs the assembly *MyAssembly.dll* with a strong name by using the key file *sgKey.snk*.</span></span>  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
<span data-ttu-id="8b5c3-131">Bu araç hakkında daha fazla bilgi için [Derleme Bağlantı Cısı'na](../../framework/tools/al-exe-assembly-linker.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-131">For more information about this tool, see [Assembly Linker](../../framework/tools/al-exe-assembly-linker.md).</span></span>  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="8b5c3-132">Öznitelikleri kullanarak güçlü bir ada sahip bir derleme yi imzalama</span><span class="sxs-lookup"><span data-stu-id="8b5c3-132">Sign an assembly with a strong name by using attributes</span></span>  
  
1. <span data-ttu-id="8b5c3-133">Kaynak <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> kod <xref:System.Reflection.AssemblyKeyNameAttribute> dosyanıza veya özniteliğinizi ekleyin ve derlemeyi güçlü bir adla imzalarken kullanılacak anahtar çiftini içeren dosyanın veya kapsayıcının adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-133">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  

2. <span data-ttu-id="8b5c3-134">Kaynak kodu normal şekilde derleyin.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-134">Compile the source code file normally.</span></span>  

   > [!NOTE]
   > <span data-ttu-id="8b5c3-135">C# ve Visual Basic derleyicileri, kaynak kodundaki <xref:System.Reflection.AssemblyKeyFileAttribute> veya <xref:System.Reflection.AssemblyKeyNameAttribute> öznitelikteki öznitelikle karşılaştıklarında derleyici uyarıları (sırasıyla CS1699 ve BC41008) verirler.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-135">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="8b5c3-136">Uyarıları gözardı edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-136">You can ignore the warnings.</span></span>  

<span data-ttu-id="8b5c3-137">Aşağıdaki örnek, <xref:System.Reflection.AssemblyKeyFileAttribute> derlemenin derlendiği dizinde bulunan *keyfile.snk*adlı anahtar dosyasıyla özniteliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-137">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called *keyfile.snk*, which is located in the directory where the assembly is compiled.</span></span>  

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

<span data-ttu-id="8b5c3-138">Ayrıca kaynak dosyanızı derlerken bir derlemeyi imzalamayı erteleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-138">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="8b5c3-139">Daha fazla bilgi için bir [derlemeyi Geciktir-imzalayın.](delay-sign.md)</span><span class="sxs-lookup"><span data-stu-id="8b5c3-139">For more information, see [Delay-sign an assembly](delay-sign.md).</span></span>  

## <a name="sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="8b5c3-140">Derleyiciyi kullanarak güçlü bir ada sahip bir derleme yi imzalama</span><span class="sxs-lookup"><span data-stu-id="8b5c3-140">Sign an assembly with a strong name by using the compiler</span></span>  

<span data-ttu-id="8b5c3-141">Kaynak kod dosyanızı veya dosyalarınızı C# ve Visual Basic'teki `/keyfile` veya C++'daki `/delaysign` `/KEYFILE` veya `/DELAYSIGN` bağlayıcı seçeneğinde veya derleyici seçeneğiyle derleyin.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-141">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="8b5c3-142">Seçenek adından sonra, iki nokta işareti ve anahtar dosyasının adını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-142">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="8b5c3-143">Komut satırı derleyicileri kullanırken, anahtar dosyasını kaynak kodu dosyalarınızı içeren dizine kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-143">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  

<span data-ttu-id="8b5c3-144">Gecikme imzalama hakkında bilgi için, [bir derlemeyi Geciktir-imzalayın'](delay-sign.md)a bakın.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-144">For information on delay signing, see [Delay-sign an assembly](delay-sign.md).</span></span>  

<span data-ttu-id="8b5c3-145">Aşağıdaki örnek, C# derleyicisini kullanır ve *anahtar dosyasgKey.snk*kullanarak güçlü bir adla derleme *UtilityLibrary.dll* imzalar.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-145">The following example uses the C# compiler and signs the assembly *UtilityLibrary.dll* with a strong name by using the key file *sgKey.snk*.</span></span>  

```cmd
csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
```  

## <a name="see-also"></a><span data-ttu-id="8b5c3-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b5c3-146">See also</span></span>

- [<span data-ttu-id="8b5c3-147">Tanımlayıcı adlı derlemeler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="8b5c3-147">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="8b5c3-148">Nasıl yapilir: Genel-özel anahtar çifti oluşturma</span><span class="sxs-lookup"><span data-stu-id="8b5c3-148">How to: Create a public-private key pair</span></span>](create-public-private-key-pair.md)
- [<span data-ttu-id="8b5c3-149">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="8b5c3-149">Al.exe (Assembly Linker)</span></span>](../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="8b5c3-150">Derlemeyi gecikmeli imzalama</span><span class="sxs-lookup"><span data-stu-id="8b5c3-150">Delay-sign an assembly</span></span>](delay-sign.md)
- [<span data-ttu-id="8b5c3-151">Derleme ve bildirim imzalamayı yönetme</span><span class="sxs-lookup"><span data-stu-id="8b5c3-151">Manage assembly and manifest signing</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [<span data-ttu-id="8b5c3-152">İmza lama sayfası, Proje Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="8b5c3-152">Signing page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
