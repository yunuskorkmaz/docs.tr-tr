---
title: "'<assembly1>' derlemesinden '<assembly2>' katıştırılmış birlikte çalışma derlemesine dolaylı bir başvuru bulunduğundan, bu birlikte çalışma derlemesine bir başvuru oluşturuldu"
ms.date: 07/20/2015
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
ms.openlocfilehash: 0f7a136abb0e63e4b139b87c8f18ae3fcb99dbf9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947758"
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-assembly1-because-of-an-indirect-reference-to-that-assembly-from-assembly-assembly2"></a><span data-ttu-id="84cc3-102">\<'\<Assembly2 > ' derlemesinden bu derlemeye dolaylı bir başvuru olduğundan, ' Assembly1 > ' katıştırılmış birlikte çalışma derlemesine bir başvuru oluşturuldu</span><span class="sxs-lookup"><span data-stu-id="84cc3-102">A reference was created to embedded interop assembly '\<assembly1>' because of an indirect reference to that assembly from assembly '\<assembly2>'</span></span>
<span data-ttu-id="84cc3-103">\<'\<Assembly2 > ' derlemesinden bu derlemeye dolaylı bir başvuru olduğundan, ' Assembly1 > ' katıştırılmış birlikte çalışma derlemesine bir başvuru oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="84cc3-103">A reference was created to embedded interop assembly '\<assembly1>' because of an indirect reference to that assembly from assembly '\<assembly2>'.</span></span> <span data-ttu-id="84cc3-104">Herhangi bir derlemede ' birlikte çalışma türlerini katıştır ' özelliğini değiştirmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="84cc3-104">Consider changing the 'Embed Interop Types' property on either assembly.</span></span>  
  
 <span data-ttu-id="84cc3-105">`Embed Interop Types` Özelliği olarak`True`ayarlanmış bir derlemeye (Assembly1) bir başvuru eklediniz.</span><span class="sxs-lookup"><span data-stu-id="84cc3-105">You have added a reference to an assembly (assembly1) that has the `Embed Interop Types` property set to `True`.</span></span> <span data-ttu-id="84cc3-106">Bu, derleyiciye, bu derlemeden birlikte çalışma türü bilgilerini katıştırmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="84cc3-106">This instructs the compiler to embed interop type information from that assembly.</span></span> <span data-ttu-id="84cc3-107">Ancak, başvurmuş olduğunuz başka bir derleme (Assembly2) da bu derlemeye (Assembly1) başvurduğundan ve `Embed Interop Types` özelliği olarak ayarlandığı için `False`derleyici, birlikte çalışma türü bilgilerini bu derlemeden katıştıramaz.</span><span class="sxs-lookup"><span data-stu-id="84cc3-107">However, the compiler cannot embed interop type information from that assembly because another assembly that you have referenced (assembly2) also references that assembly (assembly1) and has the `Embed Interop Types` property set to `False`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84cc3-108">' A bir derleme `True` başvurusu üzerinde `/link` özelliğininayarlanması,komutsatırıderleyicisiseçeneğikullanılarakderlemeyebaşvurulmayaeşdeğerdir.`Embed Interop Types`</span><span class="sxs-lookup"><span data-stu-id="84cc3-108">Setting the `Embed Interop Types` property on an assembly reference to `True` is equivalent to referencing the assembly by using the `/link` option for the command-line compiler.</span></span>  
  
 <span data-ttu-id="84cc3-109">**Hata KIMLIĞI:** BC40059</span><span class="sxs-lookup"><span data-stu-id="84cc3-109">**Error ID:** BC40059</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="84cc3-110">Bu uyarıyı çözmek için</span><span class="sxs-lookup"><span data-stu-id="84cc3-110">To address this warning</span></span>  
  
- <span data-ttu-id="84cc3-111">Her iki derleme için birlikte çalışma türü bilgilerini eklemek için, `Embed Interop Types` Assembly1 öğesine tüm başvurularda özelliğini olarak `True`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="84cc3-111">To embed interop type information for both assemblies, set the `Embed Interop Types` property on all references to assembly1 to `True`.</span></span>  
  
- <span data-ttu-id="84cc3-112">Uyarıyı kaldırmak için assembly1 `Embed Interop Types` özelliğini olarak `False`ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84cc3-112">To remove the warning, you can set the `Embed Interop Types` property of assembly1 to `False`.</span></span> <span data-ttu-id="84cc3-113">Bu durumda, birlikte çalışma türü bilgileri bir birincil birlikte çalışma derlemesi (PIA) tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="84cc3-113">In this case, interop type information is provided by a primary interop assembly (PIA).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84cc3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84cc3-114">See also</span></span>

- [<span data-ttu-id="84cc3-115">/Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84cc3-115">/link (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="84cc3-116">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="84cc3-116">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
