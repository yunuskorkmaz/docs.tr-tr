---
title: 'Nasıl yapılır: Tanımlayıcı Adlı Bir Derlemeye Başvurma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 080d05a27b9e0b6ad4ff52d67ef8d9209dc1c697
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927950"
---
# <a name="how-to-reference-a-strong-named-assembly"></a><span data-ttu-id="7a78c-102">Nasıl yapılır: Tanımlayıcı Adlı Bir Derlemeye Başvurma</span><span class="sxs-lookup"><span data-stu-id="7a78c-102">How to: Reference a Strong-Named Assembly</span></span>
<span data-ttu-id="7a78c-103">Tanımlayıcı adlı bir derlemede tür veya kaynaklara başvurma işlemi genellikle saydamdır.</span><span class="sxs-lookup"><span data-stu-id="7a78c-103">The process for referencing types or resources in a strong-named assembly is usually transparent.</span></span> <span data-ttu-id="7a78c-104">Başvuruyu derleme zamanında (erken bağlama) veya çalışma zamanında yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a78c-104">You can make the reference either at compile time (early binding) or at run time.</span></span>  
  
 <span data-ttu-id="7a78c-105">Derleyiciye, derlemenizin açıkça başka bir derlemeye başvuruda bulunduğunu belirttiğinizde derleme zamanı başvurusu oluşur.</span><span class="sxs-lookup"><span data-stu-id="7a78c-105">A compile-time reference occurs when you indicate to the compiler that your assembly explicitly references another assembly.</span></span> <span data-ttu-id="7a78c-106">Derleme zamanı başvurusu kullandığınızda, derleyici hedeflenen tanımlayıcı adlı derlemenin ortak anahtarını otomatik olarak alır ve derlenen derlemenin derleme başvurusuna koyar.</span><span class="sxs-lookup"><span data-stu-id="7a78c-106">When you use compile-time referencing, the compiler automatically gets the public key of the targeted strong-named assembly and places it in the assembly reference of the assembly being compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7a78c-107">Tanımlayıcı adlı bir derleme, yalnızca diğer tanımlayıcı adlı derlemelerden türleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="7a78c-107">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="7a78c-108">Aksi takdirde, tanımlayıcı adlı derlemenin güvenliği tehlikeye girebilir.</span><span class="sxs-lookup"><span data-stu-id="7a78c-108">Otherwise, the security of the strong-named assembly would be compromised.</span></span>  
  
### <a name="to-make-a-compile-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="7a78c-109">Tanımlayıcı adlı bir derlemeye derleme zamanı başvurusu yapmak için</span><span class="sxs-lookup"><span data-stu-id="7a78c-109">To make a compile-time reference to a strong-named assembly</span></span>  
  
1. <span data-ttu-id="7a78c-110">Komut satırında, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="7a78c-110">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="7a78c-111">\<*Derleyici komutu*>  **/Reference:** \<*derleme adı*></span><span class="sxs-lookup"><span data-stu-id="7a78c-111">\<*compiler command*> **/reference:**\<*assembly name*></span></span>  
  
     <span data-ttu-id="7a78c-112">Bu komutta *derleyici komutu* , kullanmakta olduğunuz dilin derleyici komutu ve *derleme adı* , başvurulmakta olan tanımlayıcı adlı derlemenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="7a78c-112">In this command, *compiler command* is the compiler command for the language you are using, and *assembly name* is the name of the strong-named assembly being referenced.</span></span> <span data-ttu-id="7a78c-113">Ayrıca, bir kitaplık derlemesi oluşturmak için **/t: Library** seçeneği gibi diğer derleyici seçeneklerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a78c-113">You can also use other compiler options, such as the **/t:library** option for creating a library assembly.</span></span>  
  
 <span data-ttu-id="7a78c-114">Aşağıdaki örnek, adlı bir kod modülünden `myAssembly.dll` `myAssembly.cs`çağrılan `myLibAssembly.dll` tanımlayıcı adlı bir derlemeye başvuran adlı bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7a78c-114">The following example creates an assembly called `myAssembly.dll` that references a strong-named assembly called `myLibAssembly.dll` from a code module called `myAssembly.cs`.</span></span>  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### <a name="to-make-a-run-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="7a78c-115">Tanımlayıcı adlı bir derlemeye çalışma zamanı başvurusu yapmak için</span><span class="sxs-lookup"><span data-stu-id="7a78c-115">To make a run-time reference to a strong-named assembly</span></span>  
  
1. <span data-ttu-id="7a78c-116">Tanımlayıcı adlı bir derlemeye (örneğin, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> yöntemini kullanarak) çalışma zamanı başvurusu yaptığınızda, başvurulan tanımlayıcı adlı derlemenin görünen adını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7a78c-116">When you make a run-time reference to a strong-named assembly (for example, by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> method), you must use the display name of the referenced strong-named assembly.</span></span> <span data-ttu-id="7a78c-117">Görünen adın sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="7a78c-117">The syntax of a display name is as follows:</span></span>  
  
     <span data-ttu-id="7a78c-118">\<*bütünleştirilmiş kod adı*> **,** sürümnumarası> , kültür, ortak\<anahtar belirteci> \< \<></span><span class="sxs-lookup"><span data-stu-id="7a78c-118">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span></span>  
  
     <span data-ttu-id="7a78c-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7a78c-119">For example:</span></span>  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     <span data-ttu-id="7a78c-120">Bu örnekte, `PublicKeyToken` ortak anahtar belirtecinin onaltılı biçimidir.</span><span class="sxs-lookup"><span data-stu-id="7a78c-120">In this example, `PublicKeyToken` is the hexadecimal form of the public key token.</span></span> <span data-ttu-id="7a78c-121">Kültür değeri yoksa kullanın `Culture=neutral`.</span><span class="sxs-lookup"><span data-stu-id="7a78c-121">If there is no culture value, use `Culture=neutral`.</span></span>  
  
 <span data-ttu-id="7a78c-122">Aşağıdaki kod örneği, bu bilgileri <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemiyle nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7a78c-122">The following code example shows how to use this information with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)]
 [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)]
 [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 <span data-ttu-id="7a78c-123">Aşağıdaki [tanımlayıcı ad (sn. exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) komutunu kullanarak, belirli bir derleme için ortak anahtar ve ortak anahtar belirtecinin onaltılık biçimini yazdırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7a78c-123">You can print the hexadecimal format of the public key and public key token for a specific assembly by using the following [Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) command:</span></span>  
  
 <span data-ttu-id="7a78c-124">**sn-TP \<**  *derlemesi* **>**</span><span class="sxs-lookup"><span data-stu-id="7a78c-124">**sn -Tp \<** *assembly* **>**</span></span>  
  
 <span data-ttu-id="7a78c-125">Ortak anahtar dosyanız varsa, bunun yerine aşağıdaki komutu kullanabilirsiniz (komut satırı seçeneğinde büyük/küçük harf farkını aklınızda bulabilirsiniz):</span><span class="sxs-lookup"><span data-stu-id="7a78c-125">If you have a public key file, you can use the following command instead (note the difference in case on the command-line option):</span></span>  
  
 <span data-ttu-id="7a78c-126">**sn-TP \<**  *ortak anahtar dosyası* **>**</span><span class="sxs-lookup"><span data-stu-id="7a78c-126">**sn -tp \<** *public key file* **>**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a78c-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a78c-127">See also</span></span>

- [<span data-ttu-id="7a78c-128">Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="7a78c-128">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
