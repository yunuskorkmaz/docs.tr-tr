---
title: "Nasıl yapılır: bir genel-özel anahtar çifti oluşturma"
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
- key pairs for strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- cryptographic key pairs
- snk files (key pair files)
- public-private key pairs
- .snk files
- strong-named assemblies, key pairs
ms.assetid: 05026813-f3bd-4d7c-9e0b-fc588eb3d114
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b8076f5ed713c88f8f538959855408a8c542705a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-public-private-key-pair"></a><span data-ttu-id="73203-102">Nasıl yapılır: bir genel-özel anahtar çifti oluşturma</span><span class="sxs-lookup"><span data-stu-id="73203-102">How to: Create a Public-Private Key Pair</span></span>
<span data-ttu-id="73203-103">Derlemeyi tanımlayıcı adla imzalamak için ortak/özel anahtar çifti olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73203-103">To sign an assembly with a strong name, you must have a public/private key pair.</span></span> <span data-ttu-id="73203-104">Bu ortak ve özel şifreleme anahtar çiftinin derleme sırasında kesin adlandırılmış bir derleme oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="73203-104">This public and private cryptographic key pair is used during compilation to create a strong-named assembly.</span></span> <span data-ttu-id="73203-105">Kullanarak bir anahtar çifti oluşturma [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="73203-105">You can create a key pair using the [Strong Name tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).</span></span> <span data-ttu-id="73203-106">Anahtar çifti dosyaları genellikle .snk uzantısına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="73203-106">Key pair files usually have an .snk extension.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="73203-107">İçinde [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], C# ve Visual Basic proje özellik sayfalarını içeren bir **imzalama** , var olan anahtar dosyaları seçmek veya Sn.exe kullanmadan yeni anahtar dosyaları oluşturmak için sağlar sekmesi.</span><span class="sxs-lookup"><span data-stu-id="73203-107">In [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], the C# and Visual Basic project property pages include a **Signing** tab that enables you to select existing key files or to generate new key files without using Sn.exe.</span></span> <span data-ttu-id="73203-108">Visual C++'da, var olan bir anahtar dosyasının konumunu belirtebilirsiniz **Gelişmiş** özellik sayfasında **bağlayıcı** bölümünü **yapılandırma özellikleri** bölümü **Özellik sayfaları** penceresi.</span><span class="sxs-lookup"><span data-stu-id="73203-108">In Visual C++, you can specify the location of an existing key file in the **Advanced** property page in the **Linker** section of the **Configuration Properties** section of the **Property Pages** window.</span></span> <span data-ttu-id="73203-109">Kullanımını <xref:System.Reflection.AssemblyKeyFileAttribute> anahtar dosyası çiftleri tanımlamak için öznitelik eski başlayarak sağlandıktan [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="73203-109">The use of the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute to identify key file pairs has been made obsolete beginning with [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)].</span></span>  
  
### <a name="to-create-a-key-pair"></a><span data-ttu-id="73203-110">Bir anahtar çifti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="73203-110">To create a key pair</span></span>  
  
1.  <span data-ttu-id="73203-111">Komut satırında, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="73203-111">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="73203-112">**sn – k** \< *dosya adı*></span><span class="sxs-lookup"><span data-stu-id="73203-112">**sn –k** \<*file name*></span></span>  
  
     <span data-ttu-id="73203-113">Bu komutta *dosya adı* anahtar çiftini içeren çıkış dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="73203-113">In this command, *file name* is the name of the output file containing the key pair.</span></span>  
  
 <span data-ttu-id="73203-114">Aşağıdaki örnek adlı bir anahtar çifti oluşturur `sgKey.snk`.</span><span class="sxs-lookup"><span data-stu-id="73203-114">The following example creates a key pair called `sgKey.snk`.</span></span>  
  
```  
sn -k sgKey.snk  
```  
  
 <span data-ttu-id="73203-115">Bir anahtar çifti oluşturmak ve sonra ortak anahtarı buradan ayrı bir dosyaya ayıklamak için oturum bütünleştirilmiş gecikme istiyorsanız ve (hangi test senaryoları olası değil) tüm anahtar çifti denetlemek, kullanabileceğiniz aşağıdaki komutları.</span><span class="sxs-lookup"><span data-stu-id="73203-115">If you intend to delay sign an assembly and you control the whole key pair (which is unlikely outside test scenarios), you can use the following commands to generate a key pair and then extract the public key from it into a separate file.</span></span> <span data-ttu-id="73203-116">İlk olarak, anahtar çifti oluşturun:</span><span class="sxs-lookup"><span data-stu-id="73203-116">First, create the key pair:</span></span>  
  
```  
sn -k keypair.snk  
```  
  
 <span data-ttu-id="73203-117">Ardından, ortak anahtarın anahtar çifti ayıklamak ve ayrı bir dosyaya kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="73203-117">Next, extract the public key from the key pair and copy it to a separate file:</span></span>  
  
```  
sn -p keypair.snk public.snk  
```  
  
 <span data-ttu-id="73203-118">Anahtar çiftini oluşturduktan sonra Araçlar imzalama güçlü ad bulabileceğiniz bir yerde dosya konulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73203-118">Once you create the key pair, you must put the file where the strong name signing tools can find it.</span></span>  
  
 <span data-ttu-id="73203-119">Güçlü bir ada sahip bir derleme imzalarken [derleme bağlayıcı (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) geçerli dizin ve çıktı dizinine göreli dosya anahtarı arar.</span><span class="sxs-lookup"><span data-stu-id="73203-119">When signing an assembly with a strong name, the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) looks for the key file relative to the current directory and to the output directory.</span></span> <span data-ttu-id="73203-120">Komut satırı derleyicileri kullanırken, yalnızca kod modülleri içeren geçerli dizin anahtarı kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73203-120">When using command-line compilers, you can simply copy the key to the current directory containing your code modules.</span></span>  
  
 <span data-ttu-id="73203-121">Önceki bir sürümünü kullanıyorsanız, [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] , yok bir **imzalama** sekmesi proje özelliklerinde önerilen anahtar dosyası konumu proje gibi belirtilen dosya özniteliği ile dizindir:</span><span class="sxs-lookup"><span data-stu-id="73203-121">If you are using an earlier version of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] that does not have a **Signing** tab in the project properties, the recommended key file location is the project directory with the file attribute specified as follows:</span></span>  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="73203-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="73203-122">See Also</span></span>  
 [<span data-ttu-id="73203-123">Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="73203-123">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
