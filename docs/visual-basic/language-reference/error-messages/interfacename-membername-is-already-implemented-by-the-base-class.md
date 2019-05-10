---
title: "'<interfacename>. <membername>' taban sınıfı tarafından zaten uygulanmış '<baseclassname>'. Yeniden uygulanmasına <type> varsayıldı"
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 5943eff5fa7e68da9905e3e589eea264c06943c1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593313"
---
# <a name="interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a><span data-ttu-id="8344f-103">'\<InterfaceName >. \<membername >' taban sınıfının tarafından zaten uygulanmış\<baseclassname >'.</span><span class="sxs-lookup"><span data-stu-id="8344f-103">'\<interfacename>.\<membername>' is already implemented by the base class '\<baseclassname>'.</span></span> <span data-ttu-id="8344f-104">Yeniden uygulanmasına \<türü > varsayıldı</span><span class="sxs-lookup"><span data-stu-id="8344f-104">Re-implementation of \<type> assumed</span></span>
<span data-ttu-id="8344f-105">Bir özellik, yordam veya türetilmiş bir sınıf içinde olay kullanan bir `Implements` temel sınıfta zaten uygulanmış bir arabirim üyesi belirleme yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="8344f-105">A property, procedure, or event in a derived class uses an `Implements` clause specifying an interface member that is already implemented in the base class.</span></span>  
  
 <span data-ttu-id="8344f-106">Türetilmiş bir sınıf, taban sınıfı tarafından uygulanan bir arabirim üyesi yeniden uygulayın.</span><span class="sxs-lookup"><span data-stu-id="8344f-106">A derived class can reimplement an interface member that is implemented by its base class.</span></span> <span data-ttu-id="8344f-107">Bu temel sınıf uygulamasına geçersiz kılma ile aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="8344f-107">This is not the same as overriding the base class implementation.</span></span> <span data-ttu-id="8344f-108">Daha fazla bilgi için [uygular](../../../visual-basic/language-reference/statements/implements-clause.md).</span><span class="sxs-lookup"><span data-stu-id="8344f-108">For more information, see [Implements](../../../visual-basic/language-reference/statements/implements-clause.md).</span></span>  
  
 <span data-ttu-id="8344f-109">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="8344f-109">By default, this message is a warning.</span></span> <span data-ttu-id="8344f-110">Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="8344f-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="8344f-111">**Hata Kimliği:** BC42015</span><span class="sxs-lookup"><span data-stu-id="8344f-111">**Error ID:** BC42015</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8344f-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="8344f-112">To correct this error</span></span>  
  
- <span data-ttu-id="8344f-113">Arabirim üyesini yeniden uygulayın yapmak istiyorsanız, herhangi bir eylemde bulunmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8344f-113">If you intend to reimplement the interface member, you do not need to take any action.</span></span> <span data-ttu-id="8344f-114">Türetilmiş sınıfınızın kodda erişen reimplemented üye kullanılmadıkça `MyBase` temel sınıf uygulamasına erişmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="8344f-114">Code in your derived class accesses the reimplemented member unless you use the `MyBase` keyword to access the base class implementation.</span></span>  
  
- <span data-ttu-id="8344f-115">Arabirim üyesini yeniden uygulayın düşünmüyorsanız kaldırmak `Implements` özellik, yordam veya olay bildiriminin from yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="8344f-115">If you do not intend to reimplement the interface member, remove the `Implements` clause from the property, procedure, or event declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8344f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8344f-116">See also</span></span>

- [<span data-ttu-id="8344f-117">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="8344f-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
