---
title: "Nasıl yapılır: Tanımlayıcı Adlı Bir Derlemeye Başvurma"
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
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b005926f99b7c151e5916a95a9852dd8b448a928
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-reference-a-strong-named-assembly"></a><span data-ttu-id="afe56-102">Nasıl yapılır: Tanımlayıcı Adlı Bir Derlemeye Başvurma</span><span class="sxs-lookup"><span data-stu-id="afe56-102">How to: Reference a Strong-Named Assembly</span></span>
<span data-ttu-id="afe56-103">Başvuran türleri veya kesin adlandırılmış bir derleme kaynaklarında işlemi genellikle saydamdır.</span><span class="sxs-lookup"><span data-stu-id="afe56-103">The process for referencing types or resources in a strong-named assembly is usually transparent.</span></span> <span data-ttu-id="afe56-104">Başvuru (erken bağlama) derleme zamanında ya da çalışma zamanında yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="afe56-104">You can make the reference either at compile time (early binding) or at run time.</span></span>  
  
 <span data-ttu-id="afe56-105">Derleme zamanı referans derlemenizi açıkça başka bir derlemeye başvuran derleyiciye belirtmek oluşur.</span><span class="sxs-lookup"><span data-stu-id="afe56-105">A compile-time reference occurs when you indicate to the compiler that your assembly explicitly references another assembly.</span></span> <span data-ttu-id="afe56-106">Derleme zamanı başvuran kullandığınızda, derleyici, otomatik olarak hedeflenen tanımlayıcı adlı derleme ortak anahtarını alır ve derlenmiş derlemenin derleme başvurusu yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="afe56-106">When you use compile-time referencing, the compiler automatically gets the public key of the targeted strong-named assembly and places it in the assembly reference of the assembly being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="afe56-107">Tanımlayıcı adlı bir derleme yalnızca diğer tanımlayıcı adlı derlemeler türlerinden kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="afe56-107">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="afe56-108">Aksi takdirde, tanımlayıcı adlı derleme güvenliğini tehlikeye.</span><span class="sxs-lookup"><span data-stu-id="afe56-108">Otherwise, the security of the strong-named assembly would be compromised.</span></span>  
  
### <a name="to-make-a-compile-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="afe56-109">Tanımlayıcı adlı bir derleme zamanı başvuru yapma</span><span class="sxs-lookup"><span data-stu-id="afe56-109">To make a compile-time reference to a strong-named assembly</span></span>  
  
1.  <span data-ttu-id="afe56-110">Komut satırında, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="afe56-110">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="afe56-111">\<*derleyici komut*> **/reference:**\<*derleme adı*></span><span class="sxs-lookup"><span data-stu-id="afe56-111">\<*compiler command*> **/reference:**\<*assembly name*></span></span>  
  
     <span data-ttu-id="afe56-112">Bu komutta *derleyici komut* derleyici komut kullanıyorsanız, dil ve *derleme adı* başvurulan tanımlayıcı adlı derleme adıdır.</span><span class="sxs-lookup"><span data-stu-id="afe56-112">In this command, *compiler command* is the compiler command for the language you are using, and *assembly name* is the name of the strong-named assembly being referenced.</span></span> <span data-ttu-id="afe56-113">Gibi diğer derleyici seçenekleri kullanabilir **/t:library** Kitaplık derlemesi oluşturma seçeneği.</span><span class="sxs-lookup"><span data-stu-id="afe56-113">You can also use other compiler options, such as the **/t:library** option for creating a library assembly.</span></span>  
  
 <span data-ttu-id="afe56-114">Aşağıdaki örnek adlı bir derleme oluşturur `myAssembly.dll` adlı güçlü adlı bir derlemeye başvuruyor `myLibAssembly.dll` kod modülünden adlı `myAssembly.cs`.</span><span class="sxs-lookup"><span data-stu-id="afe56-114">The following example creates an assembly called `myAssembly.dll` that references a strong-named assembly called `myLibAssembly.dll` from a code module called `myAssembly.cs`.</span></span>  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### <a name="to-make-a-run-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="afe56-115">Tanımlayıcı adlı bir derleme çalışma zamanı başvuru yapma</span><span class="sxs-lookup"><span data-stu-id="afe56-115">To make a run-time reference to a strong-named assembly</span></span>  
  
1.  <span data-ttu-id="afe56-116">Tanımlayıcı adlı bir derleme çalışma zamanı başvuru yaptığınızda (kullanarak örneğin, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> yöntemi), başvurulan derlemeyi tanımlayıcı adlı görünen adını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="afe56-116">When you make a run-time reference to a strong-named assembly (for example, by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> method), you must use the display name of the referenced strong-named assembly.</span></span> <span data-ttu-id="afe56-117">Bir görünen ad söz dizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="afe56-117">The syntax of a display name is as follows:</span></span>  
  
     <span data-ttu-id="afe56-118">\<*derleme adı*>**,** \< *sürüm numarası*>**,** \<  *kültür*>**,** \< *ortak anahtar belirteci*></span><span class="sxs-lookup"><span data-stu-id="afe56-118">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span></span>  
  
     <span data-ttu-id="afe56-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="afe56-119">For example:</span></span>  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     <span data-ttu-id="afe56-120">Bu örnekte, `PublicKeyToken` onaltılık ortak anahtar belirteci biçimidir.</span><span class="sxs-lookup"><span data-stu-id="afe56-120">In this example, `PublicKeyToken` is the hexadecimal form of the public key token.</span></span> <span data-ttu-id="afe56-121">Kültür değer yoksa kullanmak `Culture=neutral`.</span><span class="sxs-lookup"><span data-stu-id="afe56-121">If there is no culture value, use `Culture=neutral`.</span></span>  
  
 <span data-ttu-id="afe56-122">Aşağıdaki kod örneğinde bu bilgilerle kullanmayı gösterir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="afe56-122">The following code example shows how to use this information with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)]
 [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)]
 [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 <span data-ttu-id="afe56-123">Aşağıdaki kullanarak belirli bir derleme için ortak anahtar ve ortak anahtar belirteci, onaltılık biçimde yazdırabilirsiniz [tanımlayıcı ad (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="afe56-123">You can print the hexadecimal format of the public key and public key token for a specific assembly by using the following [Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) command:</span></span>  
  
 <span data-ttu-id="afe56-124">**sn - Tp \<**  *derleme***>**</span><span class="sxs-lookup"><span data-stu-id="afe56-124">**sn -Tp \<** *assembly* **>**</span></span>  
  
 <span data-ttu-id="afe56-125">Ortak bir anahtar dosyası varsa, bunun yerine aşağıdaki komutu kullanın (komut satırı seçeneğini kasasındaki fark unutmayın):</span><span class="sxs-lookup"><span data-stu-id="afe56-125">If you have a public key file, you can use the following command instead (note the difference in case on the command-line option):</span></span>  
  
 <span data-ttu-id="afe56-126">**sn - tp \<**  *derleme***>**</span><span class="sxs-lookup"><span data-stu-id="afe56-126">**sn -tp \<** *assembly* **>**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afe56-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="afe56-127">See Also</span></span>  
 [<span data-ttu-id="afe56-128">Oluşturma ve tanımlayıcı adlı derlemeler kullanma</span><span class="sxs-lookup"><span data-stu-id="afe56-128">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
