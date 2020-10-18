---
title: <namespacename> kök ad alanındaki <fullnamespacename> adı CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: 48e020cb74641279a4f402e47034514d78dfc4fc
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160216"
---
# <a name="bc40039-name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a><span data-ttu-id="a677e-102">BC40039: \<namespacename> kök ad alanındaki ad \<fullnamespacename> CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="a677e-102">BC40039: Name \<namespacename> in the root namespace \<fullnamespacename> is not CLS-compliant</span></span>

<span data-ttu-id="a677e-103">Bir derleme olarak işaretlenir `<CLSCompliant(True)>` , ancak kök ad alanı adının bir öğesi bir alt çizgi () ile başlar `_` .</span><span class="sxs-lookup"><span data-stu-id="a677e-103">An assembly is marked as `<CLSCompliant(True)>`, but an element of the root namespace name begins with an underscore (`_`).</span></span>

 <span data-ttu-id="a677e-104">Bir programlama öğesi bir veya daha fazla alt çizgi içerebilir, ancak [Dil bağımsızlığı ve Language-Independent bileşenleri](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olmak için bir alt çizgiyle başlamamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a677e-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="a677e-105">Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="a677e-105">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

 <span data-ttu-id="a677e-106"><xref:System.CLSCompliantAttribute>' I bir programlama öğesine uyguladığınızda, ya `isCompliant` da `True` `False` Uyumluluk veya uyumsuzluk olduğunu göstermek için özniteliğin parametresini veya olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a677e-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="a677e-107">Bu parametre için varsayılan yoktur ve bir değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a677e-107">There is no default for this parameter, and you must supply a value.</span></span>

 <span data-ttu-id="a677e-108"><xref:System.CLSCompliantAttribute>Öğesini bir öğesine uygulamazsanız, uyumsuz olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="a677e-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>

 <span data-ttu-id="a677e-109">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="a677e-109">By default, this message is a warning.</span></span> <span data-ttu-id="a677e-110">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="a677e-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="a677e-111">**Hata kimliği:** BC40039</span><span class="sxs-lookup"><span data-stu-id="a677e-111">**Error ID:** BC40039</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="a677e-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a677e-112">To correct this error</span></span>

- <span data-ttu-id="a677e-113">CLS uyumluluğu gerekiyorsa, kök ad alanı adını değiştirerek öğelerinden hiçbiri alt çizgiyle başlamaktadır.</span><span class="sxs-lookup"><span data-stu-id="a677e-113">If you require CLS compliance, change the root namespace name so that none of its elements begins with an underscore.</span></span>

- <span data-ttu-id="a677e-114">Ad alanı adının değişmeden kalmasını gerektiriyorsa, <xref:System.CLSCompliantAttribute> derlemeyi derlemeden kaldırın veya olarak işaretleyin `<CLSCompliant(False)>` .</span><span class="sxs-lookup"><span data-stu-id="a677e-114">If you require that the namespace name remain unchanged, then remove the <xref:System.CLSCompliantAttribute> from the assembly or mark it as `<CLSCompliant(False)>`.</span></span>

## <a name="see-also"></a><span data-ttu-id="a677e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a677e-115">See also</span></span>

- [<span data-ttu-id="a677e-116">Namespace Deyimi</span><span class="sxs-lookup"><span data-stu-id="a677e-116">Namespace Statement</span></span>](../statements/namespace-statement.md)
- [<span data-ttu-id="a677e-117">Visual Basic'de Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="a677e-117">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="a677e-118">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="a677e-118">-rootnamespace</span></span>](../../reference/command-line-compiler/rootnamespace.md)
- [<span data-ttu-id="a677e-119">Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a677e-119">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="a677e-120">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="a677e-120">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="a677e-121">Visual Basic Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="a677e-121">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
