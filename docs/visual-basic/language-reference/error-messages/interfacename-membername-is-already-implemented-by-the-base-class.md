---
title: "'<interfacename>.<membername>', '<baseclassname>' temel sınıfı tarafından zaten uygulandı. <type> öğesinin yeniden uygulandığı varsayılıyor"
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 8137f6b1712b6a0752a991f5a3d598b5f958252c
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162823"
---
# <a name="bc42015-interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a><span data-ttu-id="732e2-103">BC42015: ' \<interfacename> . \<membername> ', ' ' temel sınıfı tarafından zaten uygulandı \<baseclassname> .</span><span class="sxs-lookup"><span data-stu-id="732e2-103">BC42015: '\<interfacename>.\<membername>' is already implemented by the base class '\<baseclassname>'.</span></span> <span data-ttu-id="732e2-104">\<type> öğesinin yeniden uygulandığı varsayılıyor</span><span class="sxs-lookup"><span data-stu-id="732e2-104">Re-implementation of \<type> assumed</span></span>

<span data-ttu-id="732e2-105">Türetilmiş sınıftaki bir özellik, yordam veya olay, `Implements` temel sınıfta zaten uygulanmış olan bir arabirim üyesini belirten bir yan tümce kullanır.</span><span class="sxs-lookup"><span data-stu-id="732e2-105">A property, procedure, or event in a derived class uses an `Implements` clause specifying an interface member that is already implemented in the base class.</span></span>

 <span data-ttu-id="732e2-106">Türetilmiş bir sınıf, temel sınıfı tarafından uygulanan bir arabirim üyesini yeniden uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="732e2-106">A derived class can reimplement an interface member that is implemented by its base class.</span></span> <span data-ttu-id="732e2-107">Bu, temel sınıf uygulamasını geçersiz kılma ile aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="732e2-107">This is not the same as overriding the base class implementation.</span></span> <span data-ttu-id="732e2-108">Daha fazla bilgi için bkz. [Implements](../statements/implements-clause.md).</span><span class="sxs-lookup"><span data-stu-id="732e2-108">For more information, see [Implements](../statements/implements-clause.md).</span></span>

 <span data-ttu-id="732e2-109">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="732e2-109">By default, this message is a warning.</span></span> <span data-ttu-id="732e2-110">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="732e2-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="732e2-111">**Hata kimliği:** BC42015</span><span class="sxs-lookup"><span data-stu-id="732e2-111">**Error ID:** BC42015</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="732e2-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="732e2-112">To correct this error</span></span>

- <span data-ttu-id="732e2-113">Arabirim üyesini yeniden uygulamak istiyorsanız, herhangi bir işlem yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="732e2-113">If you intend to reimplement the interface member, you do not need to take any action.</span></span> <span data-ttu-id="732e2-114">Türetilmiş sınıfınıza ait kod, `MyBase` temel sınıf uygulamasına erişmek için anahtar sözcüğünü kullanmadığınız müddetçe yeniden uygulanan üyeye erişir.</span><span class="sxs-lookup"><span data-stu-id="732e2-114">Code in your derived class accesses the reimplemented member unless you use the `MyBase` keyword to access the base class implementation.</span></span>

- <span data-ttu-id="732e2-115">Arabirim üyesini yeniden uygulamayı düşünmüyorsanız, `Implements` özelliğinden, yordamdan veya olay bildiriminden yan tümceyi kaldırın.</span><span class="sxs-lookup"><span data-stu-id="732e2-115">If you do not intend to reimplement the interface member, remove the `Implements` clause from the property, procedure, or event declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="732e2-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="732e2-116">See also</span></span>

- [<span data-ttu-id="732e2-117">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="732e2-117">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
