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
ms.openlocfilehash: 5d46694d772aed7e92f95cc26da86985d4f8b0ff
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50191070"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="fd74c-102">Nasıl yapılır: Derlemeyi Tanımlayıcı Adla İmzalama</span><span class="sxs-lookup"><span data-stu-id="fd74c-102">How to: Sign an Assembly with a Strong Name</span></span>
<span data-ttu-id="fd74c-103">Bir derlemeyi katı bir adla imzalamak için çeşitli yollar vardır:</span><span class="sxs-lookup"><span data-stu-id="fd74c-103">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
-   <span data-ttu-id="fd74c-104">Kullanarak **imzalama** projenin sekmede **özellikleri** Visual Studio'da iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="fd74c-104">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="fd74c-105">Bu, bir derlemeyi katı bir adla imzalamanın en kolay ve en kullanışlı yoludur.</span><span class="sxs-lookup"><span data-stu-id="fd74c-105">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
-   <span data-ttu-id="fd74c-106">Kullanarak [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) bir .NET Framework kod modülünü (bir .netmodule dosyası) bir anahtar dosyası ile ilişkilendirilecek.</span><span class="sxs-lookup"><span data-stu-id="fd74c-106">By using the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a .netmodule file) with a key file.</span></span>  
  
-   <span data-ttu-id="fd74c-107">Katı ad bilgilerini kodunuza eklemek için derleme özniteliklerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="fd74c-107">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="fd74c-108">Kullanabilirsiniz <xref:System.Reflection.AssemblyKeyFileAttribute> veya <xref:System.Reflection.AssemblyKeyNameAttribute> kullanılacak anahtar dosyasının bulunduğu bağlı olarak özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fd74c-108">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
-   <span data-ttu-id="fd74c-109">Derleyici seçeneklerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="fd74c-109">By using compiler options.</span></span>  
  
 <span data-ttu-id="fd74c-110">Bir derlemeye katı bir ad atamak için bir şifreleme anahtarı çiftiniz olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fd74c-110">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="fd74c-111">Bir anahtar çifti oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir genel-özel anahtar çifti oluşturma](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="fd74c-111">For more information about creating a key pair, see [How to: Create a Public-Private Key Pair](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span></span>  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="fd74c-112">Visual Studio'yu kullanarak bir derleme oluşturmak ve katı bir adla imzalamak için</span><span class="sxs-lookup"><span data-stu-id="fd74c-112">To create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1.  <span data-ttu-id="fd74c-113">İçinde **Çözüm Gezgini**, proje için kısayol menüsünü açın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="fd74c-113">In **Solution Explorer**, open the shortcut menu for the project, and then choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="fd74c-114">Seçin **imzalama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="fd74c-114">Choose the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="fd74c-115">Seçin **derlemeyi imzalamayı** kutusu.</span><span class="sxs-lookup"><span data-stu-id="fd74c-115">Select the **Sign the assembly** box.</span></span>  
  
4.  <span data-ttu-id="fd74c-116">İçinde **bir tanımlayıcı ad anahtar dosyası seç** kutusunda  **\<Gözat … >** ve ardından anahtar dosyasına gidin.</span><span class="sxs-lookup"><span data-stu-id="fd74c-116">In the **Choose a strong name key file** box, choose **\<Browse…>**, and then navigate to the key file.</span></span> <span data-ttu-id="fd74c-117">Yeni bir anahtar dosyası oluşturmak için seçin  **\<yeni … >** ve adını girin **katı ad anahtarı oluştur** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="fd74c-117">To create a new key file, choose **\<New…>** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="fd74c-118">Derleme Bağlayıcısı'nı kullanarak bir derleme oluşturmak ve derlemeyi güçlü bir adla imzalamak için</span><span class="sxs-lookup"><span data-stu-id="fd74c-118">To create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
-   <span data-ttu-id="fd74c-119">Konumunda [Visual Studio komut istemi](../../../docs/framework/tools/developer-command-prompt-for-vs.md), aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="fd74c-119">At the [Visual Studio Command Prompt](../../../docs/framework/tools/developer-command-prompt-for-vs.md), type the following command:</span></span>  
  
     <span data-ttu-id="fd74c-120">**Al** **/out:**\<*assemblyName*> *\<moduleName >* **/keyfile:** \<  *keyfileName*></span><span class="sxs-lookup"><span data-stu-id="fd74c-120">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  
  
     <span data-ttu-id="fd74c-121">burada:</span><span class="sxs-lookup"><span data-stu-id="fd74c-121">where:</span></span>  
  
     <span data-ttu-id="fd74c-122">*AssemblyName*</span><span class="sxs-lookup"><span data-stu-id="fd74c-122">*assemblyName*</span></span>  
     <span data-ttu-id="fd74c-123">Assembly Linker'in yayacağı katı imzalı derlemenin (.dll veya .exe dosyası) adı.</span><span class="sxs-lookup"><span data-stu-id="fd74c-123">The name of the strongly signed assembly (a .dll or .exe file) that Assembly Linker will emit.</span></span>  
  
     <span data-ttu-id="fd74c-124">*Modül adı*</span><span class="sxs-lookup"><span data-stu-id="fd74c-124">*moduleName*</span></span>  
     <span data-ttu-id="fd74c-125">Bir veya birden çok tür içeren bir .NET Framework kod modülünün (bir .netmodule dosyası) adı.</span><span class="sxs-lookup"><span data-stu-id="fd74c-125">The name of a .NET Framework code module (a .netmodule file) that includes one or more types.</span></span> <span data-ttu-id="fd74c-126">Kodunuzu derlemek tarafından bir .netmodule dosyası oluşturabilirsiniz `/target:module` C# veya Visual Basic'te geçiş yapın.</span><span class="sxs-lookup"><span data-stu-id="fd74c-126">You can create a .netmodule file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>  
  
     <span data-ttu-id="fd74c-127">*keyfileName*</span><span class="sxs-lookup"><span data-stu-id="fd74c-127">*keyfileName*</span></span>  
     <span data-ttu-id="fd74c-128">Anahtar çiftini içeren kapsayıcının veya dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="fd74c-128">The name of the container or file that contains the key pair.</span></span> <span data-ttu-id="fd74c-129">Assembly Linker, geçerli dizinle ilişki içindeki bir göreli yolu yorumlar.</span><span class="sxs-lookup"><span data-stu-id="fd74c-129">Assembly Linker interprets a relative path in relationship to the current directory.</span></span>  
  
 <span data-ttu-id="fd74c-130">Aşağıdaki örnek, derlemeyi imzalar `MyAssembly.dll` anahtar dosyasını kullanarak bir katı adla `sgKey.snk`.</span><span class="sxs-lookup"><span data-stu-id="fd74c-130">The following example signs the assembly `MyAssembly.dll` with a strong name by using the key file `sgKey.snk`.</span></span>  
  
```  
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
 <span data-ttu-id="fd74c-131">Bu araç hakkında daha fazla bilgi için bkz. [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="fd74c-131">For more information about this tool, see [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span>  
  
#### <a name="to-sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="fd74c-132">Bir derlemeyi öznitelikleri kullanarak bir katı adla imzalamak için</span><span class="sxs-lookup"><span data-stu-id="fd74c-132">To sign an assembly with a strong name by using attributes</span></span>  
  
1.  <span data-ttu-id="fd74c-133">Ekleme <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> veya <xref:System.Reflection.AssemblyKeyNameAttribute> özniteliğini kaynak kod dosyanızın ve dosya veya derlemeyi bir katı adla imzalarken kullanılacak anahtar çiftini içeren kapsayıcının adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="fd74c-133">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  
  
2.  <span data-ttu-id="fd74c-134">Kaynak kodu normal şekilde derleyin.</span><span class="sxs-lookup"><span data-stu-id="fd74c-134">Compile the source code file normally.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd74c-135">C# ve Visual Basic derleyicileri sorun derleyici uyarıları (sırasıyla, CS1699 ve BC41008 sırasıyla) karşılaştıklarında <xref:System.Reflection.AssemblyKeyFileAttribute> veya <xref:System.Reflection.AssemblyKeyNameAttribute> kaynak kodundaki özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fd74c-135">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="fd74c-136">Uyarıları gözardı edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd74c-136">You can ignore the warnings.</span></span>  
  
 <span data-ttu-id="fd74c-137">Aşağıdaki örnekte <xref:System.Reflection.AssemblyKeyFileAttribute> adlı bir anahtar dosyasıyla özniteliğiyle `keyfile.snk`, burada derlemenin derlendiği dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="fd74c-137">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called `keyfile.snk`, which is located in the directory where the assembly is compiled.</span></span>  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
 <span data-ttu-id="fd74c-138">Ayrıca kaynak dosyanızı derlerken bir derlemeyi imzalamayı erteleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd74c-138">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="fd74c-139">Daha fazla bilgi için [derlemeyi imzalamayı geciktirme](../../../docs/framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="fd74c-139">For more information, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="fd74c-140">Bir derlemeyi derleyiciyi kullanarak bir katı adla imzalamak için</span><span class="sxs-lookup"><span data-stu-id="fd74c-140">To sign an assembly with a strong name by using the compiler</span></span>  
  
-   <span data-ttu-id="fd74c-141">Kaynak kod dosyanız veya dosyalarınız ile derleme `/keyfile` veya `/delaysign` C# ve Visual Basic derleyici seçeneğini veya `/KEYFILE` veya `/DELAYSIGN` c++ bağlayıcı seçeneği.</span><span class="sxs-lookup"><span data-stu-id="fd74c-141">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="fd74c-142">Seçenek adından sonra, iki nokta işareti ve anahtar dosyasının adını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fd74c-142">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="fd74c-143">Komut satırı derleyicileri kullanırken, anahtar dosyasını kaynak kodu dosyalarınızı içeren dizine kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd74c-143">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  
  
     <span data-ttu-id="fd74c-144">Gecikmeli imzalama hakkında daha fazla bilgi için bkz: [derlemeyi imzalamayı geciktirme](../../../docs/framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="fd74c-144">For information on delay signing, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
     <span data-ttu-id="fd74c-145">Aşağıdaki örnek C# derleyicisini kullanır ve derlemeyi imzalar `UtilityLibrary.dll` anahtar dosyasını kullanarak bir katı adla `sgKey.snk`.</span><span class="sxs-lookup"><span data-stu-id="fd74c-145">The following example uses the C# compiler and signs the assembly `UtilityLibrary.dll` with a strong name by using the key file `sgKey.snk`.</span></span>  
  
    ```  
    csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fd74c-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fd74c-146">See Also</span></span>  
- [<span data-ttu-id="fd74c-147">Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="fd74c-147">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
- [<span data-ttu-id="fd74c-148">Nasıl yapılır: Genel-Özel Anahtar Çifti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fd74c-148">How to: Create a Public-Private Key Pair</span></span>](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)  
- [<span data-ttu-id="fd74c-149">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="fd74c-149">Al.exe (Assembly Linker)</span></span>](../../../docs/framework/tools/al-exe-assembly-linker.md)  
- [<span data-ttu-id="fd74c-150">Bütünleştirilmiş Kod İmzalamayı Geciktirme</span><span class="sxs-lookup"><span data-stu-id="fd74c-150">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)  
- [<span data-ttu-id="fd74c-151">Derleme ve Bildirim İmzalamayı Yönetme</span><span class="sxs-lookup"><span data-stu-id="fd74c-151">Managing Assembly and Manifest Signing</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing)  
- [<span data-ttu-id="fd74c-152">İmzalama Sayfası, Proje Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="fd74c-152">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
