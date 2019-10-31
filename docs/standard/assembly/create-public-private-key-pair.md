---
title: 'Nasıl yapılır: genel-özel anahtar çifti oluşturma'
ms.date: 08/20/2019
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
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 8a9845e3cd18ff86ec04216ad0e9c5606186b113
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122526"
---
# <a name="how-to-create-a-public-private-key-pair"></a><span data-ttu-id="3b4ec-102">Nasıl yapılır: genel-özel anahtar çifti oluşturma</span><span class="sxs-lookup"><span data-stu-id="3b4ec-102">How to: Create a public-private key pair</span></span>

<span data-ttu-id="3b4ec-103">Bir derlemeyi güçlü bir adla imzalamak için ortak/özel anahtar çiftiniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3b4ec-103">To sign an assembly with a strong name, you must have a public/private key pair.</span></span> <span data-ttu-id="3b4ec-104">Bu ortak ve özel şifreleme anahtarı çifti derleme sırasında, tanımlayıcı adlı bir derleme oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3b4ec-104">This public and private cryptographic key pair is used during compilation to create a strong-named assembly.</span></span> <span data-ttu-id="3b4ec-105">[Tanımlayıcı ad Aracı (sn. exe)](../../framework/tools/sn-exe-strong-name-tool.md)kullanarak bir anahtar çifti oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b4ec-105">You can create a key pair using the [Strong Name tool (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span> <span data-ttu-id="3b4ec-106">Anahtar çifti dosyaları genellikle *. snk* uzantısına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3b4ec-106">Key pair files usually have an *.snk* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="3b4ec-107">Visual Studio 'da, C# ve Visual Basic proje özelliği sayfaları, var olan anahtar dosyaları seçmenize veya *sn. exe*' yi kullanmadan yeni anahtar dosyaları oluşturmanıza olanak sağlayan bir **imzalama** sekmesi içerir.</span><span class="sxs-lookup"><span data-stu-id="3b4ec-107">In Visual Studio, the C# and Visual Basic project property pages include a **Signing** tab that enables you to select existing key files or to generate new key files without using *Sn.exe*.</span></span> <span data-ttu-id="3b4ec-108">Görsel C++' de, varolan bir anahtar dosyasının konumunu, **Özellik sayfaları** penceresinin **yapılandırma özellikleri** bölümünün **bağlayıcı** bölümünde bulunan **Gelişmiş** Özellik sayfasında belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b4ec-108">In Visual C++, you can specify the location of an existing key file in the **Advanced** property page in the **Linker** section of the **Configuration Properties** section of the **Property Pages** window.</span></span> <span data-ttu-id="3b4ec-109">Anahtar dosya çiftlerini tanımlamak için <xref:System.Reflection.AssemblyKeyFileAttribute> özniteliğinin kullanımı, Visual Studio 2005 ' den itibaren artık kullanılmıyor olarak yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3b4ec-109">The use of the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute to identify key file pairs was made obsolete beginning with Visual Studio 2005.</span></span>

## <a name="create-a-key-pair"></a><span data-ttu-id="3b4ec-110">Anahtar çifti oluşturma</span><span class="sxs-lookup"><span data-stu-id="3b4ec-110">Create a key pair</span></span>

<span data-ttu-id="3b4ec-111">Bir anahtar çifti oluşturmak için, komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="3b4ec-111">To create a key pair, at a command prompt, type the following command:</span></span>

<span data-ttu-id="3b4ec-112">**sn – k** \<*dosya adı*></span><span class="sxs-lookup"><span data-stu-id="3b4ec-112">**sn –k** \<*file name*></span></span>

<span data-ttu-id="3b4ec-113">Bu komutta *dosya adı* , anahtar çiftini içeren çıkış dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="3b4ec-113">In this command, *file name* is the name of the output file containing the key pair.</span></span>

<span data-ttu-id="3b4ec-114">Aşağıdaki örnek, *sgKey. snk*adlı bir anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3b4ec-114">The following example creates a key pair called *sgKey.snk*.</span></span>

```cmd
sn -k sgKey.snk
```

<span data-ttu-id="3b4ec-115">Bir derlemeyi imzalamayı ve tüm anahtar çiftini (test senaryolarından çok önemli olmayan) denetlemeniz gerekiyorsa, bir anahtar çifti oluşturmak için aşağıdaki komutları kullanabilir ve sonra ortak anahtarı ayrı bir dosyaya ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b4ec-115">If you intend to delay sign an assembly and you control the whole key pair (which is unlikely outside test scenarios), you can use the following commands to generate a key pair and then extract the public key from it into a separate file.</span></span> <span data-ttu-id="3b4ec-116">İlk olarak, anahtar çiftini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="3b4ec-116">First, create the key pair:</span></span>

```cmd
sn -k keypair.snk
```

<span data-ttu-id="3b4ec-117">Sonra, ortak anahtarı anahtar çiftinden ayıklayın ve ayrı bir dosyaya kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="3b4ec-117">Next, extract the public key from the key pair and copy it to a separate file:</span></span>

```cmd
sn -p keypair.snk public.snk
```

<span data-ttu-id="3b4ec-118">Anahtar çiftini oluşturduktan sonra, tanımlayıcı ad imzalama araçlarının bulabileceği dosyayı yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3b4ec-118">Once you create the key pair, you must put the file where the strong name signing tools can find it.</span></span>

<span data-ttu-id="3b4ec-119">Bir derlemeyi tanımlayıcı bir adla imzalarken, [derleme Bağlayıcısı (al. exe)](../../framework/tools/al-exe-assembly-linker.md) , geçerli dizine ve çıkış dizinine göre anahtar dosyasını arar.</span><span class="sxs-lookup"><span data-stu-id="3b4ec-119">When signing an assembly with a strong name, the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) looks for the key file relative to the current directory and to the output directory.</span></span> <span data-ttu-id="3b4ec-120">Komut satırı derleyicileri kullanırken, anahtarı kod modüllerinizi içeren geçerli dizine kopyalamanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="3b4ec-120">When using command-line compilers, you can simply copy the key to the current directory containing your code modules.</span></span>

<span data-ttu-id="3b4ec-121">Visual Studio 'nun proje özelliklerinde **imzalama** sekmesi olmayan önceki bir sürümünü kullanıyorsanız, önerilen anahtar dosyası konumu aşağıdaki şekilde belirtilen dosya özniteliğine sahip proje dizinidir:</span><span class="sxs-lookup"><span data-stu-id="3b4ec-121">If you are using an earlier version of Visual Studio that does not have a **Signing** tab in the project properties, the recommended key file location is the project directory with the file attribute specified as follows:</span></span>

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

## <a name="see-also"></a><span data-ttu-id="3b4ec-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b4ec-122">See also</span></span>

- [<span data-ttu-id="3b4ec-123">Tanımlayıcı adlı derlemeler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="3b4ec-123">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
