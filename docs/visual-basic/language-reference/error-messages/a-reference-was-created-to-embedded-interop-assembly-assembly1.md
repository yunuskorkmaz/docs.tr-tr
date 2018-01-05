---
title: "Bir başvuru katıştırılmış birlikte çalışma derlemesi &#39;oluşturuldu; &lt;assembly1&gt;&#39; bu derleme için dolaylı bir başvuru derleme &#39; nedeniyle&lt; assembly2&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aaaa7460ade00ad4232807ce11ee125e270742bf
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-39ltassembly1gt39-because-of-an-indirect-reference-to-that-assembly-from-assembly-39ltassembly2gt39"></a><span data-ttu-id="cf807-102">Bir başvuru katıştırılmış birlikte çalışma derlemesi &#39;oluşturuldu; &lt;assembly1&gt;&#39; bu derleme için dolaylı bir başvuru derleme &#39; nedeniyle&lt; assembly2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="cf807-102">A reference was created to embedded interop assembly &#39;&lt;assembly1&gt;&#39; because of an indirect reference to that assembly from assembly &#39;&lt;assembly2&gt;&#39;</span></span>
<span data-ttu-id="cf807-103">Bir başvuru katıştırılmış birlikte çalışma derlemesi için oluşturulan '\<assembly1 >' o derleme dolaylı bir başvuru derlemesinden '\<assembly2 >'.</span><span class="sxs-lookup"><span data-stu-id="cf807-103">A reference was created to embedded interop assembly '\<assembly1>' because of an indirect reference to that assembly from assembly '\<assembly2>'.</span></span> <span data-ttu-id="cf807-104">Herhangi bir derleme üzerinde 'Birlikte çalışma türlerini katıştır' özelliği değiştirmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="cf807-104">Consider changing the 'Embed Interop Types' property on either assembly.</span></span>  
  
 <span data-ttu-id="cf807-105">Bir derlemeye (assembly1) başvuru eklediğiniz `Embed Interop Types` özelliğini `True`.</span><span class="sxs-lookup"><span data-stu-id="cf807-105">You have added a reference to an assembly (assembly1) that has the `Embed Interop Types` property set to `True`.</span></span> <span data-ttu-id="cf807-106">Bu bütünleştirilmiş birlikte çalışma tür bilgilerini katıştırma derleyiciye.</span><span class="sxs-lookup"><span data-stu-id="cf807-106">This instructs the compiler to embed interop type information from that assembly.</span></span> <span data-ttu-id="cf807-107">Ancak, başka bir derleme (assembly2) başvurulan de bu derlemeye (assembly1) başvuruyor ve olduğundan bu derleme birlikte çalışma tür bilgilerini derleyici eklenemiyor `Embed Interop Types` özelliğini `False`.</span><span class="sxs-lookup"><span data-stu-id="cf807-107">However, the compiler cannot embed interop type information from that assembly because another assembly that you have referenced (assembly2) also references that assembly (assembly1) and has the `Embed Interop Types` property set to `False`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf807-108">Ayarlama `Embed Interop Types` derleme başvurusunun özellikte `True` kullanarak bütünleştirilmiş başvurma için eşdeğer bir gruba `/link` seçeneği için komut satırı derleyicisi.</span><span class="sxs-lookup"><span data-stu-id="cf807-108">Setting the `Embed Interop Types` property on an assembly reference to `True` is equivalent to referencing the assembly by using the `/link` option for the command-line compiler.</span></span>  
  
 <span data-ttu-id="cf807-109">**Hata Kimliği:** BC40059</span><span class="sxs-lookup"><span data-stu-id="cf807-109">**Error ID:** BC40059</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="cf807-110">Bu uyarıyı gidermek için</span><span class="sxs-lookup"><span data-stu-id="cf807-110">To address this warning</span></span>  
  
-   <span data-ttu-id="cf807-111">Her iki derlemeler için birlikte çalışma türü bilgileri katıştırmak için `Embed Interop Types` assembly1 için yapılan tüm başvuruları özellikte `True`.</span><span class="sxs-lookup"><span data-stu-id="cf807-111">To embed interop type information for both assemblies, set the `Embed Interop Types` property on all references to assembly1 to `True`.</span></span>  
  
-   <span data-ttu-id="cf807-112">Uyarıyı kaldırmak için ayarlayabileceğiniz `Embed Interop Types` assembly1'özelliğinin `False`.</span><span class="sxs-lookup"><span data-stu-id="cf807-112">To remove the warning, you can set the `Embed Interop Types` property of assembly1 to `False`.</span></span> <span data-ttu-id="cf807-113">Bu durumda, birlikte çalışma türü bilgileri birincil birlikte çalışma derlemesi (PIA) tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="cf807-113">In this case, interop type information is provided by a primary interop assembly (PIA).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf807-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf807-114">See Also</span></span>  
 [<span data-ttu-id="cf807-115">/ Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf807-115">/link (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/link.md)  
 [<span data-ttu-id="cf807-116">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="cf807-116">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
