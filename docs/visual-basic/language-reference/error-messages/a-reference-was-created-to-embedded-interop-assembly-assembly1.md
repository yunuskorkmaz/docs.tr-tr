---
title: Gömülü birlikte çalışma derlemesine bir başvuru oluşturuldu &#39; &lt;assembly1&gt; &#39; derlemeden derlemeye dolaylı başvurudan dolayı &#39; &lt;assembly2&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
ms.openlocfilehash: fe04742e0a3be5e1d19ab4017e55f2293988a671
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560028"
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-39ltassembly1gt39-because-of-an-indirect-reference-to-that-assembly-from-assembly-39ltassembly2gt39"></a><span data-ttu-id="f80d9-102">Gömülü birlikte çalışma derlemesine bir başvuru oluşturuldu &#39; &lt;assembly1&gt; &#39; derlemeden derlemeye dolaylı başvurudan dolayı &#39; &lt;assembly2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="f80d9-102">A reference was created to embedded interop assembly &#39;&lt;assembly1&gt;&#39; because of an indirect reference to that assembly from assembly &#39;&lt;assembly2&gt;&#39;</span></span>
<span data-ttu-id="f80d9-103">Gömülü birlikte çalışma derlemesine bir başvuru oluşturuldu '\<assembly1 >' derlemesinden derlemeye dolaylı başvurudan dolayı '\<assembly2 >'.</span><span class="sxs-lookup"><span data-stu-id="f80d9-103">A reference was created to embedded interop assembly '\<assembly1>' because of an indirect reference to that assembly from assembly '\<assembly2>'.</span></span> <span data-ttu-id="f80d9-104">İki derlemeden birinde 'Embed Interop Types' özelliğini değiştirmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="f80d9-104">Consider changing the 'Embed Interop Types' property on either assembly.</span></span>  
  
 <span data-ttu-id="f80d9-105">Sahip (assembly1) derlemeye bir başvuru eklediğiniz `Embed Interop Types` özelliğini `True`.</span><span class="sxs-lookup"><span data-stu-id="f80d9-105">You have added a reference to an assembly (assembly1) that has the `Embed Interop Types` property set to `True`.</span></span> <span data-ttu-id="f80d9-106">Bu, derlemesinden birlikte çalışma tür bilgisini katıştırmak için derleyiciye.</span><span class="sxs-lookup"><span data-stu-id="f80d9-106">This instructs the compiler to embed interop type information from that assembly.</span></span> <span data-ttu-id="f80d9-107">Ancak, başka bir derleme (assembly2) başvurulan de (assembly1) derlemeye başvuruyor ve sahip olduğundan bu derlemesinden birlikte çalışma tür bilgisini derleyici katıştırılamıyor `Embed Interop Types` özelliğini `False`.</span><span class="sxs-lookup"><span data-stu-id="f80d9-107">However, the compiler cannot embed interop type information from that assembly because another assembly that you have referenced (assembly2) also references that assembly (assembly1) and has the `Embed Interop Types` property set to `False`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f80d9-108">Ayarı `Embed Interop Types` bir bütünleştirilmiş kod başvurusu özelliği `True` kullanarak derlemeye başvurmak için eşdeğer bir gruba `/link` komut satırı derleyicisi seçeneği.</span><span class="sxs-lookup"><span data-stu-id="f80d9-108">Setting the `Embed Interop Types` property on an assembly reference to `True` is equivalent to referencing the assembly by using the `/link` option for the command-line compiler.</span></span>  
  
 <span data-ttu-id="f80d9-109">**Hata Kimliği:** BC40059</span><span class="sxs-lookup"><span data-stu-id="f80d9-109">**Error ID:** BC40059</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="f80d9-110">Bu uyarıyı gidermek için</span><span class="sxs-lookup"><span data-stu-id="f80d9-110">To address this warning</span></span>  
  
-   <span data-ttu-id="f80d9-111">Birlikte çalışma türünden bilgiler hem derlemeler için katıştırmak için `Embed Interop Types` assembly1 için yapılan tüm başvurular özelliği `True`.</span><span class="sxs-lookup"><span data-stu-id="f80d9-111">To embed interop type information for both assemblies, set the `Embed Interop Types` property on all references to assembly1 to `True`.</span></span>  
  
-   <span data-ttu-id="f80d9-112">Bu uyarıyı kaldırmak için ayarlayabileceğiniz `Embed Interop Types` assembly1'özelliği `False`.</span><span class="sxs-lookup"><span data-stu-id="f80d9-112">To remove the warning, you can set the `Embed Interop Types` property of assembly1 to `False`.</span></span> <span data-ttu-id="f80d9-113">Bu durumda, birlikte çalışma türünden bilgiler bir birincil birlikte çalışma derlemesi (PIA) tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f80d9-113">In this case, interop type information is provided by a primary interop assembly (PIA).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f80d9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f80d9-114">See also</span></span>
- [<span data-ttu-id="f80d9-115">/ Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f80d9-115">/link (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="f80d9-116">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="f80d9-116">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
