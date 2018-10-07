---
title: 'Nasıl yapılır: genel-özel anahtar çifti oluşturma'
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08715f2824dcb7dbc2c6aa26fd3bd8bd71b97038
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845092"
---
# <a name="how-to-create-a-public-private-key-pair"></a><span data-ttu-id="e24f8-102">Nasıl yapılır: genel-özel anahtar çifti oluşturma</span><span class="sxs-lookup"><span data-stu-id="e24f8-102">How to: Create a Public-Private Key Pair</span></span>

<span data-ttu-id="e24f8-103">Bir derlemeyi katı bir adla imzalamak için ortak/özel anahtar çifti olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e24f8-103">To sign an assembly with a strong name, you must have a public/private key pair.</span></span> <span data-ttu-id="e24f8-104">Bu ortak ve özel şifreleme anahtar çifti, derleme sırasında bir tanımlayıcı adlı bütünleştirilmiş kod oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e24f8-104">This public and private cryptographic key pair is used during compilation to create a strong-named assembly.</span></span> <span data-ttu-id="e24f8-105">Anahtar çiftini kullanarak oluşturabileceğiniz [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="e24f8-105">You can create a key pair using the [Strong Name tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).</span></span> <span data-ttu-id="e24f8-106">Anahtar çifti dosyaları .snk uzantı genellikle sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e24f8-106">Key pair files usually have an .snk extension.</span></span>

> [!NOTE]
> <span data-ttu-id="e24f8-107">Visual Studio'da C# ve Visual Basic proje özellik sayfaları dahil bir **imzalama** sağlar, mevcut anahtar dosya seçin veya Sn.exe kullanmadan yeni anahtar dosyaları oluşturmak için sekmesinde.</span><span class="sxs-lookup"><span data-stu-id="e24f8-107">In Visual Studio, the C# and Visual Basic project property pages include a **Signing** tab that enables you to select existing key files or to generate new key files without using Sn.exe.</span></span> <span data-ttu-id="e24f8-108">Visual C++'da, mevcut bir anahtar dosyasının konumunu belirtebilirsiniz **Gelişmiş** özellik sayfasında **bağlayıcı** bölümünü **yapılandırma özellikleri** bölümü **Özellik sayfaları** penceresi.</span><span class="sxs-lookup"><span data-stu-id="e24f8-108">In Visual C++, you can specify the location of an existing key file in the **Advanced** property page in the **Linker** section of the **Configuration Properties** section of the **Property Pages** window.</span></span> <span data-ttu-id="e24f8-109">Kullanımını <xref:System.Reflection.AssemblyKeyFileAttribute> anahtar dosyası çifti tanımlamak için öznitelik Visual Studio 2005 ve sonraki eski sürümlerinde hale getirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e24f8-109">The use of the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute to identify key file pairs has been made obsolete beginning with Visual Studio 2005.</span></span>

## <a name="to-create-a-key-pair"></a><span data-ttu-id="e24f8-110">Bir anahtar çifti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e24f8-110">To create a key pair</span></span>

1.  <span data-ttu-id="e24f8-111">Komut satırında, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="e24f8-111">At the command prompt, type the following command:</span></span>

     <span data-ttu-id="e24f8-112">**sn – k** \< *dosya adı*></span><span class="sxs-lookup"><span data-stu-id="e24f8-112">**sn –k** \<*file name*></span></span>

     <span data-ttu-id="e24f8-113">Bu komutta *dosya adı* anahtar çiftini içeren çıkış dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="e24f8-113">In this command, *file name* is the name of the output file containing the key pair.</span></span>

 <span data-ttu-id="e24f8-114">Aşağıdaki örnekte adlı bir anahtar çifti oluşturur `sgKey.snk`.</span><span class="sxs-lookup"><span data-stu-id="e24f8-114">The following example creates a key pair called `sgKey.snk`.</span></span>

```
sn -k sgKey.snk
```

 <span data-ttu-id="e24f8-115">Bir anahtar çifti oluşturmak ve ardından ortak anahtarı bundan farklı bir dosyaya ayıklamak için derlemeyi imzala geciktirmek istediğinize ve (hangi test senaryoları dışında düşüktür) tüm anahtar çiftini denetlemek, kullanabileceğiniz aşağıdaki komutları.</span><span class="sxs-lookup"><span data-stu-id="e24f8-115">If you intend to delay sign an assembly and you control the whole key pair (which is unlikely outside test scenarios), you can use the following commands to generate a key pair and then extract the public key from it into a separate file.</span></span> <span data-ttu-id="e24f8-116">İlk olarak, bir anahtar çifti oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e24f8-116">First, create the key pair:</span></span>

```
sn -k keypair.snk
```

 <span data-ttu-id="e24f8-117">Ardından, anahtar çiftinden ortak anahtarı ayıklar ve ayrı bir dosyaya kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="e24f8-117">Next, extract the public key from the key pair and copy it to a separate file:</span></span>

```
sn -p keypair.snk public.snk
```

 <span data-ttu-id="e24f8-118">Anahtar çiftini oluşturduktan sonra kesin ad imzalama araçları, nerede bulabileceğiniz bir dosya yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e24f8-118">Once you create the key pair, you must put the file where the strong name signing tools can find it.</span></span>

 <span data-ttu-id="e24f8-119">Bir derlemeyi katı bir adla imzalarken [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) geçerli dizin ve çıkış dizini göreli dosya anahtar arar.</span><span class="sxs-lookup"><span data-stu-id="e24f8-119">When signing an assembly with a strong name, the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) looks for the key file relative to the current directory and to the output directory.</span></span> <span data-ttu-id="e24f8-120">Komut satırı derleyicilerini kullanırken anahtarı kod modüllerinizi içeren geçerli dizine yalnızca kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e24f8-120">When using command-line compilers, you can simply copy the key to the current directory containing your code modules.</span></span>

 <span data-ttu-id="e24f8-121">Olmayan Visual Studio'nun önceki bir sürümü kullanıyorsanız, bir **imzalama** sekmesini Proje Özellikleri'nde proje dizini gibi belirtilen dosya özniteliği ile önerilen anahtar dosyası konumudur:</span><span class="sxs-lookup"><span data-stu-id="e24f8-121">If you are using an earlier version of Visual Studio that does not have a **Signing** tab in the project properties, the recommended key file location is the project directory with the file attribute specified as follows:</span></span>

 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]

## <a name="see-also"></a><span data-ttu-id="e24f8-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e24f8-122">See Also</span></span>

- [<span data-ttu-id="e24f8-123">Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="e24f8-123">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
