---
title: 'Nasıl yapılır: Derlemeyi Tanımlayıcı Adla İmzalama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b109ec82d139e3b3eb321c90d5f41dd1eae216f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927928"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="3d631-102">Nasıl yapılır: Derlemeyi Tanımlayıcı Adla İmzalama</span><span class="sxs-lookup"><span data-stu-id="3d631-102">How to: Sign an Assembly with a Strong Name</span></span>
<span data-ttu-id="3d631-103">Bir derlemeyi katı bir adla imzalamak için çeşitli yollar vardır:</span><span class="sxs-lookup"><span data-stu-id="3d631-103">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
- <span data-ttu-id="3d631-104">Visual Studio 'da bir projenin **Özellikler** Iletişim kutusunda **imzalama** sekmesini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="3d631-104">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="3d631-105">Bu, bir derlemeyi katı bir adla imzalamanın en kolay ve en kullanışlı yoludur.</span><span class="sxs-lookup"><span data-stu-id="3d631-105">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
- <span data-ttu-id="3d631-106">Bir .NET Framework kodu modülünü (. netmodule dosyası) anahtar dosyasıyla bağlamak için [derleme Bağlayıcısı (al. exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) kullanarak.</span><span class="sxs-lookup"><span data-stu-id="3d631-106">By using the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a .netmodule file) with a key file.</span></span>  
  
- <span data-ttu-id="3d631-107">Katı ad bilgilerini kodunuza eklemek için derleme özniteliklerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="3d631-107">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="3d631-108">Kullanılacak anahtar dosyasının bulunduğu yere <xref:System.Reflection.AssemblyKeyFileAttribute> bağlı olarak <xref:System.Reflection.AssemblyKeyNameAttribute> ya da özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d631-108">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
- <span data-ttu-id="3d631-109">Derleyici seçeneklerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="3d631-109">By using compiler options.</span></span>  
  
 <span data-ttu-id="3d631-110">Bir derlemeye katı bir ad atamak için bir şifreleme anahtarı çiftiniz olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3d631-110">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="3d631-111">Anahtar çifti oluşturma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Ortak özel anahtar çifti](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3d631-111">For more information about creating a key pair, see [How to: Create a Public-Private Key Pair](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span></span>  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="3d631-112">Visual Studio'yu kullanarak bir derleme oluşturmak ve katı bir adla imzalamak için</span><span class="sxs-lookup"><span data-stu-id="3d631-112">To create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1. <span data-ttu-id="3d631-113">**Çözüm Gezgini**' de, proje için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="3d631-113">In **Solution Explorer**, open the shortcut menu for the project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="3d631-114">**İmzalama** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="3d631-114">Choose the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="3d631-115">**Derlemeyi imzala** kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="3d631-115">Select the **Sign the assembly** box.</span></span>  
  
4. <span data-ttu-id="3d631-116">**Tanımlayıcı ad seçin anahtar dosyası** kutusunda,  **\<araştır... ' ı seçin. >** ve ardından anahtar dosyasına gidin.</span><span class="sxs-lookup"><span data-stu-id="3d631-116">In the **Choose a strong name key file** box, choose **\<Browse…>**, and then navigate to the key file.</span></span> <span data-ttu-id="3d631-117">Yeni bir anahtar dosyası oluşturmak için  **\<yeni... öğesini seçin. >** ve adını **tanımlayıcı ad anahtarı oluştur** iletişim kutusuna girin.</span><span class="sxs-lookup"><span data-stu-id="3d631-117">To create a new key file, choose **\<New…>** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d631-118">[Bir derlemeyi imzalamayı geciktirmek](../../../docs/framework/app-domains/delay-sign-assembly.md)için bir ortak anahtar dosyası seçin.</span><span class="sxs-lookup"><span data-stu-id="3d631-118">In order to [delay sign an assembly](../../../docs/framework/app-domains/delay-sign-assembly.md), choose a public key file.</span></span>  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="3d631-119">Derleme Bağlayıcısı'nı kullanarak bir derleme oluşturmak ve derlemeyi güçlü bir adla imzalamak için</span><span class="sxs-lookup"><span data-stu-id="3d631-119">To create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
- <span data-ttu-id="3d631-120">[Visual Studio için geliştirici komut istemi](../../../docs/framework/tools/developer-command-prompt-for-vs.md), aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="3d631-120">At the [Developer Command Prompt for Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), type the following command:</span></span>  
  
     <span data-ttu-id="3d631-121">**Al** **/Out:** \<AssemblyNameModuleName> > **/keyfile**:keyfilename\< *\<* ></span><span class="sxs-lookup"><span data-stu-id="3d631-121">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  
  
     <span data-ttu-id="3d631-122">burada:</span><span class="sxs-lookup"><span data-stu-id="3d631-122">where:</span></span>  
  
     <span data-ttu-id="3d631-123">*assemblyName*</span><span class="sxs-lookup"><span data-stu-id="3d631-123">*assemblyName*</span></span>  
     <span data-ttu-id="3d631-124">Assembly Linker'in yayacağı katı imzalı derlemenin (.dll veya .exe dosyası) adı.</span><span class="sxs-lookup"><span data-stu-id="3d631-124">The name of the strongly signed assembly (a .dll or .exe file) that Assembly Linker will emit.</span></span>  
  
     <span data-ttu-id="3d631-125">*Ladı*</span><span class="sxs-lookup"><span data-stu-id="3d631-125">*moduleName*</span></span>  
     <span data-ttu-id="3d631-126">Bir veya birden çok tür içeren bir .NET Framework kod modülünün (bir .netmodule dosyası) adı.</span><span class="sxs-lookup"><span data-stu-id="3d631-126">The name of a .NET Framework code module (a .netmodule file) that includes one or more types.</span></span> <span data-ttu-id="3d631-127">Kodunuzu `/target:module` veya Visual Basic içindeki C# anahtarla derleyerek bir. netmodule dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d631-127">You can create a .netmodule file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>  
  
     <span data-ttu-id="3d631-128">*Anahtar dosya adı*</span><span class="sxs-lookup"><span data-stu-id="3d631-128">*keyfileName*</span></span>  
     <span data-ttu-id="3d631-129">Anahtar çiftini içeren kapsayıcının veya dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="3d631-129">The name of the container or file that contains the key pair.</span></span> <span data-ttu-id="3d631-130">Assembly Linker, geçerli dizinle ilişki içindeki bir göreli yolu yorumlar.</span><span class="sxs-lookup"><span data-stu-id="3d631-130">Assembly Linker interprets a relative path in relationship to the current directory.</span></span>  
  
 <span data-ttu-id="3d631-131">Aşağıdaki örnek, anahtar dosyasını `MyAssembly.dll` `sgKey.snk`kullanarak derlemeyi tanımlayıcı bir adla imzalar.</span><span class="sxs-lookup"><span data-stu-id="3d631-131">The following example signs the assembly `MyAssembly.dll` with a strong name by using the key file `sgKey.snk`.</span></span>  
  
```  
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
 <span data-ttu-id="3d631-132">Bu araç hakkında daha fazla bilgi için bkz. [derleme Bağlayıcısı](../../../docs/framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="3d631-132">For more information about this tool, see [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span>  
  
#### <a name="to-sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="3d631-133">Bir derlemeyi öznitelikleri kullanarak bir katı adla imzalamak için</span><span class="sxs-lookup"><span data-stu-id="3d631-133">To sign an assembly with a strong name by using attributes</span></span>  
  
1. <span data-ttu-id="3d631-134">Kaynak kodu dosyanıza <xref:System.Reflection.AssemblyKeyNameAttribute>orözniteliğini ekleyin ve derlemeyi tanımlayıcı bir adla imzalarken kullanılacak anahtar çiftini içeren dosya veya kapsayıcının adını belirtin. <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3d631-134">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  
  
2. <span data-ttu-id="3d631-135">Kaynak kodu normal şekilde derleyin.</span><span class="sxs-lookup"><span data-stu-id="3d631-135">Compile the source code file normally.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d631-136">C# Ve Visual Basic derleyicileri, kaynak kodundaki <xref:System.Reflection.AssemblyKeyFileAttribute> veya <xref:System.Reflection.AssemblyKeyNameAttribute> özniteliğiyle karşılaştığında derleyici uyarılarını (sırasıyla CS1699 ve BC41008) yayınlarlar.</span><span class="sxs-lookup"><span data-stu-id="3d631-136">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="3d631-137">Uyarıları gözardı edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d631-137">You can ignore the warnings.</span></span>  
  
 <span data-ttu-id="3d631-138">Aşağıdaki örnek <xref:System.Reflection.AssemblyKeyFileAttribute> özniteliği, derlemenin derlendiği dizinde bulunan adlı `keyfile.snk`bir anahtar dosyası ile kullanır.</span><span class="sxs-lookup"><span data-stu-id="3d631-138">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called `keyfile.snk`, which is located in the directory where the assembly is compiled.</span></span>  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
 <span data-ttu-id="3d631-139">Ayrıca kaynak dosyanızı derlerken bir derlemeyi imzalamayı erteleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d631-139">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="3d631-140">Daha fazla bilgi için bkz. [bir derlemeyi IMZALAMAYı geciktirme](../../../docs/framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="3d631-140">For more information, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="3d631-141">Bir derlemeyi derleyiciyi kullanarak bir katı adla imzalamak için</span><span class="sxs-lookup"><span data-stu-id="3d631-141">To sign an assembly with a strong name by using the compiler</span></span>  
  
- <span data-ttu-id="3d631-142">Kaynak `/keyfile` kodu dosyanızı veya dosyalarınızı, veya Visual Basic içindeki C# or `/delaysign` derleyici seçeneğiyle veya `/KEYFILE` ' de `/DELAYSIGN` C++veya bağlayıcı seçeneğinde derleyin.</span><span class="sxs-lookup"><span data-stu-id="3d631-142">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="3d631-143">Seçenek adından sonra, iki nokta işareti ve anahtar dosyasının adını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3d631-143">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="3d631-144">Komut satırı derleyicileri kullanırken, anahtar dosyasını kaynak kodu dosyalarınızı içeren dizine kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d631-144">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  
  
     <span data-ttu-id="3d631-145">Gecikmeli imzalama hakkında daha fazla bilgi için bkz. [bir derlemeyi IMZALAMAYı geciktirme](../../../docs/framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="3d631-145">For information on delay signing, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
     <span data-ttu-id="3d631-146">Aşağıdaki örnek, C# derleyicisini kullanır ve anahtar dosyasını `UtilityLibrary.dll` `sgKey.snk`kullanarak derlemeyi tanımlayıcı bir adla imzalar.</span><span class="sxs-lookup"><span data-stu-id="3d631-146">The following example uses the C# compiler and signs the assembly `UtilityLibrary.dll` with a strong name by using the key file `sgKey.snk`.</span></span>  
  
    ```  
    csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3d631-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d631-147">See also</span></span>

- [<span data-ttu-id="3d631-148">Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="3d631-148">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [<span data-ttu-id="3d631-149">Nasıl yapılır: Ortak özel anahtar çifti oluşturma</span><span class="sxs-lookup"><span data-stu-id="3d631-149">How to: Create a Public-Private Key Pair</span></span>](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [<span data-ttu-id="3d631-150">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="3d631-150">Al.exe (Assembly Linker)</span></span>](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="3d631-151">Bütünleştirilmiş Kod İmzalamayı Geciktirme</span><span class="sxs-lookup"><span data-stu-id="3d631-151">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)
- [<span data-ttu-id="3d631-152">Derleme ve Bildirim İmzalamayı Yönetme</span><span class="sxs-lookup"><span data-stu-id="3d631-152">Managing Assembly and Manifest Signing</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [<span data-ttu-id="3d631-153">İmzalama Sayfası, Proje Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="3d631-153">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
