---
title: 'Nasıl yapılsın: Güçlü bir derlemeye başvuru'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: adda4ed2ab5c59e3518b8e724044529a79840ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156484"
---
# <a name="how-to-reference-a-strong-named-assembly"></a><span data-ttu-id="2427e-102">Nasıl yapılsın: Güçlü bir derlemeye başvuru</span><span class="sxs-lookup"><span data-stu-id="2427e-102">How to: Reference a strong-named assembly</span></span>
<span data-ttu-id="2427e-103">Güçlü adlandırılmış bir derlemede başvuru türleri veya kaynakları için işlem genellikle saydamdır.</span><span class="sxs-lookup"><span data-stu-id="2427e-103">The process for referencing types or resources in a strong-named assembly is usually transparent.</span></span> <span data-ttu-id="2427e-104">Başvuruyu derleme zamanında (erken bağlama) veya çalışma zamanında yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2427e-104">You can make the reference either at compile time (early binding) or at run time.</span></span>  
  
<span data-ttu-id="2427e-105">Derleyiciye derlemesi için derlenecek derlemenin başka bir derlemeye açıkça atıfta bulunulmasını belirttiğiniz zaman derleme zamanı başvurusu oluşur.</span><span class="sxs-lookup"><span data-stu-id="2427e-105">A compile-time reference occurs when you indicate to the compiler that the assembly to be compiled explicitly references another assembly.</span></span> <span data-ttu-id="2427e-106">Derleme zamanı başvurularını kullandığınızda, derleyici hedeflenen güçlü adı verilen derlemenin ortak anahtarını otomatik olarak alır ve derlenen derlemenin derleme başvurusuna yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="2427e-106">When you use compile-time referencing, the compiler automatically gets the public key of the targeted strong-named assembly and places it in the assembly reference of the assembly being compiled.</span></span>
  
> [!NOTE]
> <span data-ttu-id="2427e-107">Güçlü adlandırılmış derleme yalnızca diğer güçlü adlandırılmış derlemelerden türleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="2427e-107">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="2427e-108">Aksi takdirde, güçlü adlı derlemenin güvenliği tehlikeye girer.</span><span class="sxs-lookup"><span data-stu-id="2427e-108">Otherwise, the security of the strong-named assembly would be compromised.</span></span>  
  
## <a name="make-a-compile-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="2427e-109">Güçlü adlandırılmış derlemeiçin derleme zamanı başvurusu yapma</span><span class="sxs-lookup"><span data-stu-id="2427e-109">Make a compile-time reference to a strong-named assembly</span></span>  

<span data-ttu-id="2427e-110">Komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="2427e-110">At a command prompt, type the following command:</span></span>  

<span data-ttu-id="2427e-111">\<*derleyici komutu*> **/başvuru:**\<*derleme adı*></span><span class="sxs-lookup"><span data-stu-id="2427e-111">\<*compiler command*> **/reference:**\<*assembly name*></span></span>  

<span data-ttu-id="2427e-112">Bu komutta *derleyici komutu* kullandığınız dilin derleyici komutudur ve *derleme adı* başvurulan güçlü adlandırılmış derlemenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="2427e-112">In this command, *compiler command* is the compiler command for the language you are using, and *assembly name* is the name of the strong-named assembly being referenced.</span></span> <span data-ttu-id="2427e-113">Kitaplık derlemesi oluşturmak için **/t:kitaplık** seçeneği gibi diğer derleyici seçeneklerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2427e-113">You can also use other compiler options, such as the **/t:library** option for creating a library assembly.</span></span>  

<span data-ttu-id="2427e-114">Aşağıdaki örnek, *myAssembly.cs*adlı bir kod modülünden *myLibAssembly.dll* adlı güçlü bir derlemeye başvuran *myAssembly.dll* adlı bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2427e-114">The following example creates an assembly called *myAssembly.dll* that references a strong-named assembly called *myLibAssembly.dll* from a code module called *myAssembly.cs*.</span></span>  

```cmd
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  

## <a name="make-a-run-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="2427e-115">Güçlü adlandırılmış derlemeye çalışma zamanı başvurusu yapma</span><span class="sxs-lookup"><span data-stu-id="2427e-115">Make a run-time reference to a strong-named assembly</span></span>  
  
<span data-ttu-id="2427e-116">Örneğin, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> güçlü <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> adlı bir derlemeye çalışma zamanı başvurusu yaptığınızda, örneğin veya yöntemi ni kullanarak, başvurulan güçlü adlandırılmış derlemenin görüntü adını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2427e-116">When you make a run-time reference to a strong-named assembly, for example by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> method, you must use the display name of the referenced strong-named assembly.</span></span> <span data-ttu-id="2427e-117">Görüntü adının sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="2427e-117">The syntax of a display name is as follows:</span></span>  

<span data-ttu-id="2427e-118">\<*derleme adı*>**,** \< *sürüm numarası*>**,** \< *kültür*>**,** \< *ortak anahtar belirteci*></span><span class="sxs-lookup"><span data-stu-id="2427e-118">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span></span>  

<span data-ttu-id="2427e-119">Örnek:</span><span class="sxs-lookup"><span data-stu-id="2427e-119">For example:</span></span>  

```console
myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33
```  

<span data-ttu-id="2427e-120">Bu örnekte, `PublicKeyToken` ortak anahtar belirteci hexadecimal şeklidir.</span><span class="sxs-lookup"><span data-stu-id="2427e-120">In this example, `PublicKeyToken` is the hexadecimal form of the public key token.</span></span> <span data-ttu-id="2427e-121">Kültür değeri yoksa, kullanın. `Culture=neutral`</span><span class="sxs-lookup"><span data-stu-id="2427e-121">If there is no culture value, use `Culture=neutral`.</span></span>  

<span data-ttu-id="2427e-122">Aşağıdaki kod örneği, yöntemle bu <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> bilgilerin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2427e-122">The following code example shows how to use this information with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  

```cpp
Assembly^ myDll =
    Assembly::Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```csharp
Assembly myDll =
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```vb
Dim myDll As Assembly = _
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1")
```

<span data-ttu-id="2427e-123">Aşağıdaki [Güçlü Ad (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) komutunu kullanarak belirli bir derleme için ortak anahtarın ve ortak anahtar belirtecisinin hexadecimal biçimini yazdırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2427e-123">You can print the hexadecimal format of the public key and public key token for a specific assembly by using the following [Strong Name (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) command:</span></span>  

<span data-ttu-id="2427e-124">**sn \< -Tp** *montajı\*\*\*>*\*</span><span class="sxs-lookup"><span data-stu-id="2427e-124">**sn -Tp \<** *assembly* **>**</span></span>  

<span data-ttu-id="2427e-125">Ortak anahtar dosyanız varsa, bunun yerine aşağıdaki komutu kullanabilirsiniz (komut satırı seçeneğindeki duruma ilişkin farkı not edin):</span><span class="sxs-lookup"><span data-stu-id="2427e-125">If you have a public key file, you can use the following command instead (note the difference in case on the command-line option):</span></span>  

<span data-ttu-id="2427e-126">\**sn -tp \< \*\* *genel anahtar dosyası\*\*\*>**</span><span class="sxs-lookup"><span data-stu-id="2427e-126">**sn -tp \<** *public key file* **>**</span></span>  

## <a name="see-also"></a><span data-ttu-id="2427e-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2427e-127">See also</span></span>

- [<span data-ttu-id="2427e-128">Tanımlayıcı adlı derlemeler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="2427e-128">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
