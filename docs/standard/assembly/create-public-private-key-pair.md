---
title: 'Nasıl yapilir: Genel-özel anahtar çifti oluşturma'
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73122526"
---
# <a name="how-to-create-a-public-private-key-pair"></a><span data-ttu-id="5aa89-102">Nasıl yapilir: Genel-özel anahtar çifti oluşturma</span><span class="sxs-lookup"><span data-stu-id="5aa89-102">How to: Create a public-private key pair</span></span>

<span data-ttu-id="5aa89-103">Güçlü bir ada sahip bir derlemeyi imzalamak için ortak/özel anahtar çiftiniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5aa89-103">To sign an assembly with a strong name, you must have a public/private key pair.</span></span> <span data-ttu-id="5aa89-104">Bu ortak ve özel şifreleme anahtar çifti derleme sırasında güçlü adlandırılmış bir derleme oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5aa89-104">This public and private cryptographic key pair is used during compilation to create a strong-named assembly.</span></span> <span data-ttu-id="5aa89-105">[Güçlü Ad aracını (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md)kullanarak bir anahtar çifti oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5aa89-105">You can create a key pair using the [Strong Name tool (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span> <span data-ttu-id="5aa89-106">Anahtar çifti dosyaları genellikle bir *.snk* uzantısı vardır.</span><span class="sxs-lookup"><span data-stu-id="5aa89-106">Key pair files usually have an *.snk* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="5aa89-107">Visual Studio'da, C# ve Visual Basic proje özelliği sayfaları, varolan anahtar dosyalarını seçmenizi veya *Sn.exe'yi*kullanmadan yeni anahtar dosyaları oluşturmanızı sağlayan bir **İmzalama** sekmesi içerir.</span><span class="sxs-lookup"><span data-stu-id="5aa89-107">In Visual Studio, the C# and Visual Basic project property pages include a **Signing** tab that enables you to select existing key files or to generate new key files without using *Sn.exe*.</span></span> <span data-ttu-id="5aa89-108">Visual C++'da, **Özellik Sayfaları** penceresinin **Yapılandırma Özellikleri** bölümünün **Bağlayıcı** bölümünde **Gelişmiş** özellik sayfasında varolan bir anahtar dosyasının konumunu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5aa89-108">In Visual C++, you can specify the location of an existing key file in the **Advanced** property page in the **Linker** section of the **Configuration Properties** section of the **Property Pages** window.</span></span> <span data-ttu-id="5aa89-109">Anahtar dosya <xref:System.Reflection.AssemblyKeyFileAttribute> çiftlerini tanımlamak için özniteliğin kullanımı Visual Studio 2005 ile başlayan eski haline getirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5aa89-109">The use of the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute to identify key file pairs was made obsolete beginning with Visual Studio 2005.</span></span>

## <a name="create-a-key-pair"></a><span data-ttu-id="5aa89-110">Anahtar çifti oluşturma</span><span class="sxs-lookup"><span data-stu-id="5aa89-110">Create a key pair</span></span>

<span data-ttu-id="5aa89-111">Bir komut isteminde bir anahtar çifti oluşturmak için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="5aa89-111">To create a key pair, at a command prompt, type the following command:</span></span>

<span data-ttu-id="5aa89-112">**sn –k** \< *dosya adı*></span><span class="sxs-lookup"><span data-stu-id="5aa89-112">**sn –k** \<*file name*></span></span>

<span data-ttu-id="5aa89-113">Bu komutta, *dosya adı* anahtar çiftini içeren çıktı dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="5aa89-113">In this command, *file name* is the name of the output file containing the key pair.</span></span>

<span data-ttu-id="5aa89-114">Aşağıdaki *örneksgKey.snk*adlı bir anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5aa89-114">The following example creates a key pair called *sgKey.snk*.</span></span>

```cmd
sn -k sgKey.snk
```

<span data-ttu-id="5aa89-115">Bir derlemeyi imzalamayı geciktirmek istiyorsanız ve tüm anahtar çiftini denetlerseniz (test senaryoları dışında olası değildir), anahtar çifti oluşturmak için aşağıdaki komutları kullanabilir ve ardından ortak anahtarı ayrı bir dosyaya ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5aa89-115">If you intend to delay sign an assembly and you control the whole key pair (which is unlikely outside test scenarios), you can use the following commands to generate a key pair and then extract the public key from it into a separate file.</span></span> <span data-ttu-id="5aa89-116">İlk olarak, anahtar çiftini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5aa89-116">First, create the key pair:</span></span>

```cmd
sn -k keypair.snk
```

<span data-ttu-id="5aa89-117">Ardından, ortak anahtarı anahtar çiftinden ayıklayın ve ayrı bir dosyaya kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="5aa89-117">Next, extract the public key from the key pair and copy it to a separate file:</span></span>

```cmd
sn -p keypair.snk public.snk
```

<span data-ttu-id="5aa89-118">Anahtar çiftini oluşturduktan sonra, dosyayı güçlü ad imzalama araçlarının bulabileceği bir yere koymanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5aa89-118">Once you create the key pair, you must put the file where the strong name signing tools can find it.</span></span>

<span data-ttu-id="5aa89-119">Güçlü bir ada sahip bir derleme imzalarken, [Derleme Bağlayıcısı (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) anahtar dosyasını geçerli dizine ve çıktı dizine göre arar.</span><span class="sxs-lookup"><span data-stu-id="5aa89-119">When signing an assembly with a strong name, the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) looks for the key file relative to the current directory and to the output directory.</span></span> <span data-ttu-id="5aa89-120">Komut satırı derleyicilerini kullanırken, kod modüllerinizi içeren geçerli dizinin anahtarını kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5aa89-120">When using command-line compilers, you can simply copy the key to the current directory containing your code modules.</span></span>

<span data-ttu-id="5aa89-121">Visual Studio'nun proje özelliklerinde **İmza** sekmesi olmayan önceki bir sürümünü kullanıyorsanız, önerilen anahtar dosyası konumu aşağıdaki gibi belirtilen dosya özniteliği içeren proje dizinidir:</span><span class="sxs-lookup"><span data-stu-id="5aa89-121">If you are using an earlier version of Visual Studio that does not have a **Signing** tab in the project properties, the recommended key file location is the project directory with the file attribute specified as follows:</span></span>

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

## <a name="see-also"></a><span data-ttu-id="5aa89-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5aa89-122">See also</span></span>

- [<span data-ttu-id="5aa89-123">Tanımlayıcı adlı derlemeler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="5aa89-123">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
