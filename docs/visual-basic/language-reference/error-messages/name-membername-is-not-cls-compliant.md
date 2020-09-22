---
title: <membername> adı CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: 33b60b2212d25737330dc93d7ba2715e4d5865b7
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873709"
---
# <a name="name-membername-is-not-cls-compliant"></a><span data-ttu-id="64db3-102">\<membername> adı CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="64db3-102">Name \<membername> is not CLS-compliant</span></span>

<span data-ttu-id="64db3-103">Bir derleme olarak işaretlenir, `<CLSCompliant(True)>` ancak alt çizgi () ile başlayan bir ada sahip bir üye ortaya koyar `_` .</span><span class="sxs-lookup"><span data-stu-id="64db3-103">An assembly is marked as `<CLSCompliant(True)>` but exposes a member with a name that begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="64db3-104">Bir programlama öğesi bir veya daha fazla alt çizgi içerebilir, ancak [Dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olmak için bir alt çizgiyle başlamamalıdır.</span><span class="sxs-lookup"><span data-stu-id="64db3-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="64db3-105">Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="64db3-105">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="64db3-106"><xref:System.CLSCompliantAttribute>' I bir programlama öğesine uyguladığınızda, ya `isCompliant` da `True` `False` Uyumluluk veya uyumsuzluk olduğunu göstermek için özniteliğin parametresini veya olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="64db3-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="64db3-107">Bu parametre için varsayılan yoktur ve bir değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="64db3-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="64db3-108"><xref:System.CLSCompliantAttribute>Öğesini bir öğesine uygulamazsanız, uyumsuz olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="64db3-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="64db3-109">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="64db3-109">By default, this message is a warning.</span></span> <span data-ttu-id="64db3-110">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="64db3-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="64db3-111">**Hata kimliği:** BC40031</span><span class="sxs-lookup"><span data-stu-id="64db3-111">**Error ID:** BC40031</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="64db3-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="64db3-112">To correct this error</span></span>  
  
- <span data-ttu-id="64db3-113">Kaynak kodu üzerinde denetiminiz varsa, üye adını alt çizgiyle başlamayan şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="64db3-113">If you have control over the source code, change the member name so that it does not begin with an underscore.</span></span>  
  
- <span data-ttu-id="64db3-114">Üye adının değişmeden kalmasını gerektiriyorsa, öğesini <xref:System.CLSCompliantAttribute> tanımından kaldırın veya olarak işaretleyin `<CLSCompliant(False)>` .</span><span class="sxs-lookup"><span data-stu-id="64db3-114">If you require that the member name remain unchanged, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span> <span data-ttu-id="64db3-115">Derlemeyi hala olarak işaretleyebilirsiniz `<CLSCompliant(True)>` .</span><span class="sxs-lookup"><span data-stu-id="64db3-115">You can still mark the assembly as `<CLSCompliant(True)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64db3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64db3-116">See also</span></span>

- [<span data-ttu-id="64db3-117">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="64db3-117">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="64db3-118">Visual Basic Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="64db3-118">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
