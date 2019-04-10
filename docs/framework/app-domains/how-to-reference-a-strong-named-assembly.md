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
ms.openlocfilehash: 281cfa6507d293658e436a95a5ded0174154a13c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59301028"
---
# <a name="how-to-reference-a-strong-named-assembly"></a><span data-ttu-id="286ec-102">Nasıl yapılır: Tanımlayıcı Adlı Bir Derlemeye Başvurma</span><span class="sxs-lookup"><span data-stu-id="286ec-102">How to: Reference a Strong-Named Assembly</span></span>
<span data-ttu-id="286ec-103">Türleri veya bir katı adlı derleme kaynaklara başvuran işlemi genellikle saydamdır.</span><span class="sxs-lookup"><span data-stu-id="286ec-103">The process for referencing types or resources in a strong-named assembly is usually transparent.</span></span> <span data-ttu-id="286ec-104">Başvuru (erken bağlama) derleme zamanında ya da çalışma zamanında yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="286ec-104">You can make the reference either at compile time (early binding) or at run time.</span></span>  
  
 <span data-ttu-id="286ec-105">Derleyiciye belirttiğinizde, derlemenizi açıkça başka bir derlemeye başvuran bir derleme zamanı başvurusu gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="286ec-105">A compile-time reference occurs when you indicate to the compiler that your assembly explicitly references another assembly.</span></span> <span data-ttu-id="286ec-106">Derleme zamanı başvuran kullandığınızda, derleyici otomatik olarak hedeflenen tanımlayıcı adlı bütünleştirilmiş kodunun ortak anahtarı alır ve derlenmiş bütünleştirilmiş kod derleme başvurusu yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="286ec-106">When you use compile-time referencing, the compiler automatically gets the public key of the targeted strong-named assembly and places it in the assembly reference of the assembly being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="286ec-107">Tanımlayıcı adlı bütünleştirilmiş kod, yalnızca diğer güçlü adlı derlemelere türlerinden kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="286ec-107">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="286ec-108">Aksi takdirde, tanımlayıcı adlı bütünleştirilmiş kodun güvenliğini tehlikeye.</span><span class="sxs-lookup"><span data-stu-id="286ec-108">Otherwise, the security of the strong-named assembly would be compromised.</span></span>  
  
### <a name="to-make-a-compile-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="286ec-109">Tanımlayıcı adlı bütünleştirilmiş kod derleme zamanı başvuru yapma</span><span class="sxs-lookup"><span data-stu-id="286ec-109">To make a compile-time reference to a strong-named assembly</span></span>  
  
1. <span data-ttu-id="286ec-110">Komut satırında, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="286ec-110">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="286ec-111">\<*derleyici komut*> **/reference:**\<*derleme adı*></span><span class="sxs-lookup"><span data-stu-id="286ec-111">\<*compiler command*> **/reference:**\<*assembly name*></span></span>  
  
     <span data-ttu-id="286ec-112">Bu komutta *derleyici komut* derleyici komut kullandığınız dil ve *derleme adı* başvurulan tanımlayıcı adlı bütünleştirilmiş kodun adı.</span><span class="sxs-lookup"><span data-stu-id="286ec-112">In this command, *compiler command* is the compiler command for the language you are using, and *assembly name* is the name of the strong-named assembly being referenced.</span></span> <span data-ttu-id="286ec-113">Gibi diğer derleyici seçenekleri kullanabilirsiniz **/t:library** Kitaplık derlemesi oluşturmak için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="286ec-113">You can also use other compiler options, such as the **/t:library** option for creating a library assembly.</span></span>  
  
 <span data-ttu-id="286ec-114">Aşağıdaki örnekte adlı bir derleme oluşturur `myAssembly.dll` adlı bir tanımlayıcı adlı bütünleştirilmiş kod başvuruları `myLibAssembly.dll` adlı kod modülünde `myAssembly.cs`.</span><span class="sxs-lookup"><span data-stu-id="286ec-114">The following example creates an assembly called `myAssembly.dll` that references a strong-named assembly called `myLibAssembly.dll` from a code module called `myAssembly.cs`.</span></span>  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### <a name="to-make-a-run-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="286ec-115">Tanımlayıcı adlı bütünleştirilmiş kod çalışma zamanı başvuru yapma</span><span class="sxs-lookup"><span data-stu-id="286ec-115">To make a run-time reference to a strong-named assembly</span></span>  
  
1. <span data-ttu-id="286ec-116">Bir çalışma zamanı başvurusu bir katı adlı derleme yaptığınızda (kullanarak örneğin, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> yöntemi), başvurulan kesin adlandırılmış derlemenin görünen adını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="286ec-116">When you make a run-time reference to a strong-named assembly (for example, by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> method), you must use the display name of the referenced strong-named assembly.</span></span> <span data-ttu-id="286ec-117">Bir görünen ad sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="286ec-117">The syntax of a display name is as follows:</span></span>  
  
     <span data-ttu-id="286ec-118">\<*derleme adı*>**,** \< *sürüm numarası*>**,** \< *kültürü*  > **,** \< *ortak anahtar belirteci*></span><span class="sxs-lookup"><span data-stu-id="286ec-118">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span></span>  
  
     <span data-ttu-id="286ec-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="286ec-119">For example:</span></span>  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     <span data-ttu-id="286ec-120">Bu örnekte, `PublicKeyToken` onaltılık ortak anahtar belirteci biçimindedir.</span><span class="sxs-lookup"><span data-stu-id="286ec-120">In this example, `PublicKeyToken` is the hexadecimal form of the public key token.</span></span> <span data-ttu-id="286ec-121">Kültür değer yoksa kullanın `Culture=neutral`.</span><span class="sxs-lookup"><span data-stu-id="286ec-121">If there is no culture value, use `Culture=neutral`.</span></span>  
  
 <span data-ttu-id="286ec-122">Aşağıdaki kod örneği bu bilgileri ile nasıl kullanacağınızı gösterir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="286ec-122">The following code example shows how to use this information with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)]
 [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)]
 [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 <span data-ttu-id="286ec-123">Aşağıdakileri kullanarak, belirli bir derleme için ortak anahtar ve ortak anahtar belirteci on altılık biçimde yazdırabilir [tanımlayıcı ad (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="286ec-123">You can print the hexadecimal format of the public key and public key token for a specific assembly by using the following [Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) command:</span></span>  
  
 <span data-ttu-id="286ec-124">**sn - Tp \<**  *derleme* **>**</span><span class="sxs-lookup"><span data-stu-id="286ec-124">**sn -Tp \<** *assembly* **>**</span></span>  
  
 <span data-ttu-id="286ec-125">Bunun yerine ortak anahtar dosyası varsa, aşağıdaki komutu kullanabilirsiniz (komut satırı seçeneğini durumda farka dikkat edin):</span><span class="sxs-lookup"><span data-stu-id="286ec-125">If you have a public key file, you can use the following command instead (note the difference in case on the command-line option):</span></span>  
  
 <span data-ttu-id="286ec-126">**sn - tp \<**  *ortak anahtar dosyası* **>**</span><span class="sxs-lookup"><span data-stu-id="286ec-126">**sn -tp \<** *public key file* **>**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="286ec-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="286ec-127">See also</span></span>

- [<span data-ttu-id="286ec-128">Tanımlayıcı Adlı Derlemeler Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="286ec-128">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
