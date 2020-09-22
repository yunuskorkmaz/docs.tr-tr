---
title: "'<interfacename>.<membername>', '<baseclassname>' temel sınıfı tarafından zaten uygulandı. <type> öğesinin yeniden uygulandığı varsayılıyor"
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 4056c61bf6556f54276817c1c105ba7a17b6fd5a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873937"
---
# <a name="interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a><span data-ttu-id="e2e1c-103">'\<interfacename>.\<membername>', '\<baseclassname>' temel sınıfı tarafından zaten uygulandı.</span><span class="sxs-lookup"><span data-stu-id="e2e1c-103">'\<interfacename>.\<membername>' is already implemented by the base class '\<baseclassname>'.</span></span> <span data-ttu-id="e2e1c-104">\<type> öğesinin yeniden uygulandığı varsayılıyor</span><span class="sxs-lookup"><span data-stu-id="e2e1c-104">Re-implementation of \<type> assumed</span></span>

<span data-ttu-id="e2e1c-105">Türetilmiş sınıftaki bir özellik, yordam veya olay, `Implements` temel sınıfta zaten uygulanmış olan bir arabirim üyesini belirten bir yan tümce kullanır.</span><span class="sxs-lookup"><span data-stu-id="e2e1c-105">A property, procedure, or event in a derived class uses an `Implements` clause specifying an interface member that is already implemented in the base class.</span></span>  
  
 <span data-ttu-id="e2e1c-106">Türetilmiş bir sınıf, temel sınıfı tarafından uygulanan bir arabirim üyesini yeniden uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="e2e1c-106">A derived class can reimplement an interface member that is implemented by its base class.</span></span> <span data-ttu-id="e2e1c-107">Bu, temel sınıf uygulamasını geçersiz kılma ile aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="e2e1c-107">This is not the same as overriding the base class implementation.</span></span> <span data-ttu-id="e2e1c-108">Daha fazla bilgi için bkz. [Implements](../statements/implements-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e2e1c-108">For more information, see [Implements](../statements/implements-clause.md).</span></span>  
  
 <span data-ttu-id="e2e1c-109">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="e2e1c-109">By default, this message is a warning.</span></span> <span data-ttu-id="e2e1c-110">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="e2e1c-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="e2e1c-111">**Hata kimliği:** BC42015</span><span class="sxs-lookup"><span data-stu-id="e2e1c-111">**Error ID:** BC42015</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e2e1c-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e2e1c-112">To correct this error</span></span>  
  
- <span data-ttu-id="e2e1c-113">Arabirim üyesini yeniden uygulamak istiyorsanız, herhangi bir işlem yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e2e1c-113">If you intend to reimplement the interface member, you do not need to take any action.</span></span> <span data-ttu-id="e2e1c-114">Türetilmiş sınıfınıza ait kod, `MyBase` temel sınıf uygulamasına erişmek için anahtar sözcüğünü kullanmadığınız müddetçe yeniden uygulanan üyeye erişir.</span><span class="sxs-lookup"><span data-stu-id="e2e1c-114">Code in your derived class accesses the reimplemented member unless you use the `MyBase` keyword to access the base class implementation.</span></span>  
  
- <span data-ttu-id="e2e1c-115">Arabirim üyesini yeniden uygulamayı düşünmüyorsanız, `Implements` özelliğinden, yordamdan veya olay bildiriminden yan tümceyi kaldırın.</span><span class="sxs-lookup"><span data-stu-id="e2e1c-115">If you do not intend to reimplement the interface member, remove the `Implements` clause from the property, procedure, or event declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2e1c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2e1c-116">See also</span></span>

- [<span data-ttu-id="e2e1c-117">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="e2e1c-117">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
