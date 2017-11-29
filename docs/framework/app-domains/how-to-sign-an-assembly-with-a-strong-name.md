---
title: "Nasıl yapılır: Derlemeyi Tanımlayıcı Adla İmzalama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: babd0f6a9b1babf02677d6c6c41c664e0a6541b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="d089a-102">Nasıl yapılır: Derlemeyi Tanımlayıcı Adla İmzalama</span><span class="sxs-lookup"><span data-stu-id="d089a-102">How to: Sign an Assembly with a Strong Name</span></span>
<span data-ttu-id="d089a-103">Bir derlemeyi katı bir adla imzalamak için çeşitli yollar vardır:</span><span class="sxs-lookup"><span data-stu-id="d089a-103">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
-   <span data-ttu-id="d089a-104">Kullanarak **imzalama** bir projenin sekmesinde **özellikleri** Visual Studio'da iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="d089a-104">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="d089a-105">Bu, bir derlemeyi katı bir adla imzalamanın en kolay ve en kullanışlı yoludur.</span><span class="sxs-lookup"><span data-stu-id="d089a-105">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
-   <span data-ttu-id="d089a-106">Kullanarak [derleme bağlayıcı (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) bir .NET Framework kod modülüne (.netmodule dosyası) bir anahtar dosya ile ilişkilendirilecek.</span><span class="sxs-lookup"><span data-stu-id="d089a-106">By using the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a .netmodule file) with a key file.</span></span>  
  
-   <span data-ttu-id="d089a-107">Katı ad bilgilerini kodunuza eklemek için derleme özniteliklerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="d089a-107">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="d089a-108">Kullanabilirsiniz <xref:System.Reflection.AssemblyKeyFileAttribute> veya <xref:System.Reflection.AssemblyKeyNameAttribute> bulunduğu konuma bağlı olarak kullanılacak anahtar dosyası özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d089a-108">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
-   <span data-ttu-id="d089a-109">Derleyici seçeneklerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="d089a-109">By using compiler options.</span></span>  
  
 <span data-ttu-id="d089a-110">Bir derlemeye katı bir ad atamak için bir şifreleme anahtarı çiftiniz olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d089a-110">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="d089a-111">Bir anahtar çifti oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir genel-özel anahtar çifti oluşturma](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="d089a-111">For more information about creating a key pair, see [How to: Create a Public-Private Key Pair](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span></span>  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="d089a-112">Visual Studio'yu kullanarak bir derleme oluşturmak ve katı bir adla imzalamak için</span><span class="sxs-lookup"><span data-stu-id="d089a-112">To create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1.  <span data-ttu-id="d089a-113">İçinde **Çözüm Gezgini**projesi için kısayol menüsünü açın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="d089a-113">In **Solution Explorer**, open the shortcut menu for the project, and then choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="d089a-114">Seçin **imzalama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="d089a-114">Choose the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="d089a-115">Seçin **derlemeyi imzalamak** kutusu.</span><span class="sxs-lookup"><span data-stu-id="d089a-115">Select the **Sign the assembly** box.</span></span>  
  
4.  <span data-ttu-id="d089a-116">İçinde **güçlü ad anahtar dosyası seçin** kutusunda, seçin  **\<Gözat... >**ve ardından anahtar dosyasına gidin.</span><span class="sxs-lookup"><span data-stu-id="d089a-116">In the **Choose a strong name key file** box, choose **\<Browse…>**, and then navigate to the key file.</span></span> <span data-ttu-id="d089a-117">Yeni bir anahtar dosyası oluşturmak için seçtiğiniz  **\<yeni... >** ve adını girin **güçlü ad anahtarı oluştur** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="d089a-117">To create a new key file, choose **\<New…>** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="d089a-118">Derleme Bağlayıcısı'nı kullanarak bir derleme oluşturmak ve derlemeyi güçlü bir adla imzalamak için</span><span class="sxs-lookup"><span data-stu-id="d089a-118">To create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
-   <span data-ttu-id="d089a-119">Konumundaki [Visual Studio komut istemi](../../../docs/framework/tools/developer-command-prompt-for-vs.md), aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="d089a-119">At the [Visual Studio Command Prompt](../../../docs/framework/tools/developer-command-prompt-for-vs.md), type the following command:</span></span>  
  
     <span data-ttu-id="d089a-120">**Al** **/out:**\<*assemblyName*> *\<moduleName >* **/keyfile:** \<  *keyfileName*></span><span class="sxs-lookup"><span data-stu-id="d089a-120">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  
  
     <span data-ttu-id="d089a-121">burada:</span><span class="sxs-lookup"><span data-stu-id="d089a-121">where:</span></span>  
  
     <span data-ttu-id="d089a-122">*assemblyName*</span><span class="sxs-lookup"><span data-stu-id="d089a-122">*assemblyName*</span></span>  
     <span data-ttu-id="d089a-123">Assembly Linker'in yayacağı katı imzalı derlemenin (.dll veya .exe dosyası) adı.</span><span class="sxs-lookup"><span data-stu-id="d089a-123">The name of the strongly signed assembly (a .dll or .exe file) that Assembly Linker will emit.</span></span>  
  
     <span data-ttu-id="d089a-124">*Modül adı*</span><span class="sxs-lookup"><span data-stu-id="d089a-124">*moduleName*</span></span>  
     <span data-ttu-id="d089a-125">Bir veya birden çok tür içeren bir .NET Framework kod modülünün (bir .netmodule dosyası) adı.</span><span class="sxs-lookup"><span data-stu-id="d089a-125">The name of a .NET Framework code module (a .netmodule file) that includes one or more types.</span></span> <span data-ttu-id="d089a-126">Kodunuzu derlerken tarafından .netmodule dosyası oluşturabilirsiniz `/target:module` C# veya Visual Basic geçiş yapın.</span><span class="sxs-lookup"><span data-stu-id="d089a-126">You can create a .netmodule file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>  
  
     <span data-ttu-id="d089a-127">*keyfileName*</span><span class="sxs-lookup"><span data-stu-id="d089a-127">*keyfileName*</span></span>  
     <span data-ttu-id="d089a-128">Anahtar çiftini içeren kapsayıcının veya dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="d089a-128">The name of the container or file that contains the key pair.</span></span> <span data-ttu-id="d089a-129">Assembly Linker, geçerli dizinle ilişki içindeki bir göreli yolu yorumlar.</span><span class="sxs-lookup"><span data-stu-id="d089a-129">Assembly Linker interprets a relative path in relationship to the current directory.</span></span>  
  
 <span data-ttu-id="d089a-130">Aşağıdaki örnek derleme imzalar `MyAssembly.dll` anahtar dosyası kullanarak bir güçlü ad ile `sgKey.snk`.</span><span class="sxs-lookup"><span data-stu-id="d089a-130">The following example signs the assembly `MyAssembly.dll` with a strong name by using the key file `sgKey.snk`.</span></span>  
  
```  
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
 <span data-ttu-id="d089a-131">Bu araç hakkında daha fazla bilgi için bkz: [derleme bağlayıcı](../../../docs/framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="d089a-131">For more information about this tool, see [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span>  
  
#### <a name="to-sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="d089a-132">Bir derlemeyi öznitelikleri kullanarak bir katı adla imzalamak için</span><span class="sxs-lookup"><span data-stu-id="d089a-132">To sign an assembly with a strong name by using attributes</span></span>  
  
1.  <span data-ttu-id="d089a-133">Ekleme <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> veya <xref:System.Reflection.AssemblyKeyNameAttribute> özniteliği, kaynak kodu dosyasına ve derlemeyi tanımlayıcı adla imzalama sırasında kullanmak için anahtar çiftini içeren kapsayıcı ve dosya adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="d089a-133">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  
  
2.  <span data-ttu-id="d089a-134">Kaynak kodu normal şekilde derleyin.</span><span class="sxs-lookup"><span data-stu-id="d089a-134">Compile the source code file normally.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d089a-135">C# ve Visual Basic derleyicileri derleyici uyarıları sorun (CS1699 ve BC41008, sırasıyla) ne zaman karşılaştıkları <xref:System.Reflection.AssemblyKeyFileAttribute> veya <xref:System.Reflection.AssemblyKeyNameAttribute> kaynak kodunda özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d089a-135">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="d089a-136">Uyarıları gözardı edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d089a-136">You can ignore the warnings.</span></span>  
  
 <span data-ttu-id="d089a-137">Aşağıdaki örnek kullanır <xref:System.Reflection.AssemblyKeyFileAttribute> adlı bir anahtar dosyası özniteliğiyle `keyfile.snk`, derleme derlenmiş burada dizininde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d089a-137">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called `keyfile.snk`, which is located in the directory where the assembly is compiled.</span></span>  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
 <span data-ttu-id="d089a-138">Ayrıca kaynak dosyanızı derlerken bir derlemeyi imzalamayı erteleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d089a-138">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="d089a-139">Daha fazla bilgi için bkz: [Gecikmeli bir derleme imzalama](../../../docs/framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="d089a-139">For more information, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="d089a-140">Bir derlemeyi derleyiciyi kullanarak bir katı adla imzalamak için</span><span class="sxs-lookup"><span data-stu-id="d089a-140">To sign an assembly with a strong name by using the compiler</span></span>  
  
-   <span data-ttu-id="d089a-141">Kaynak kodu dosyasının veya dosyaları derleme `/keyfile` veya `/delaysign` C# ve Visual Basic derleyici seçeneği veya `/KEYFILE` veya `/DELAYSIGN` c++ bağlayıcı seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d089a-141">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="d089a-142">Seçenek adından sonra, iki nokta işareti ve anahtar dosyasının adını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d089a-142">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="d089a-143">Komut satırı derleyicileri kullanırken, anahtar dosyasını kaynak kodu dosyalarınızı içeren dizine kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d089a-143">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  
  
     <span data-ttu-id="d089a-144">Gecikmeli imzalama hakkında daha fazla bilgi için bkz: [Gecikmeli bir derleme imzalama](../../../docs/framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="d089a-144">For information on delay signing, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
     <span data-ttu-id="d089a-145">Aşağıdaki örnek C# Derleyici kullanır ve derleme imzalar `UtilityLibrary.dll` anahtar dosyası kullanarak bir güçlü ad ile `sgKey.snk`.</span><span class="sxs-lookup"><span data-stu-id="d089a-145">The following example uses the C# compiler and signs the assembly `UtilityLibrary.dll` with a strong name by using the key file `sgKey.snk`.</span></span>  
  
    ```  
    csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d089a-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d089a-146">See Also</span></span>  
 [<span data-ttu-id="d089a-147">Oluşturma ve tanımlayıcı adlı derlemeler kullanma</span><span class="sxs-lookup"><span data-stu-id="d089a-147">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [<span data-ttu-id="d089a-148">Nasıl yapılır: bir genel-özel anahtar çifti oluşturma</span><span class="sxs-lookup"><span data-stu-id="d089a-148">How to: Create a Public-Private Key Pair</span></span>](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [<span data-ttu-id="d089a-149">Al.exe (derleme bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="d089a-149">Al.exe (Assembly Linker)</span></span>](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [<span data-ttu-id="d089a-150">Derleme imzalamayı geciktirme</span><span class="sxs-lookup"><span data-stu-id="d089a-150">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 [<span data-ttu-id="d089a-151">Derleme ve bildirim imzalamayı yönetme</span><span class="sxs-lookup"><span data-stu-id="d089a-151">Managing Assembly and Manifest Signing</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing)  
 [<span data-ttu-id="d089a-152">İmzalama sayfası, Proje Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="d089a-152">Signing Page, Project Designer</span></span>](https://msdn.microsoft.com/library/0k50fs3b)
