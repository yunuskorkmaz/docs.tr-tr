---
description: 'Daha fazla bilgi edinin: Unicode (Visual Basic)'
title: Unicode
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: b0c71d8fdefe3f0d240201e0d57265e5c6081d50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700721"
---
# <a name="unicode-visual-basic"></a><span data-ttu-id="c318a-103">Unicode (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c318a-103">Unicode (Visual Basic)</span></span>

<span data-ttu-id="c318a-104">Visual Basic, belirtilen dış yordamın adından bağımsız olarak, tüm dizeleri Unicode değerlerine göre sıralayamaz.</span><span class="sxs-lookup"><span data-stu-id="c318a-104">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="c318a-105">Projenizin dışında tanımlanan bir yordamı çağırdığınızda, Visual Basic derleyicisinin yordamı doğru bir şekilde çağırmak için sahip olması gereken bilgilere erişimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c318a-105">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span></span> <span data-ttu-id="c318a-106">Bu bilgiler yordamın nerede bulunduğuna, nasıl tanımlandığınıza, arama sırasının ve dönüş türünün ve kullandığı dize karakter kümesinin nerede olduğunu içerir.</span><span class="sxs-lookup"><span data-stu-id="c318a-106">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="c318a-107">[Declare bildirimi](../statements/declare-statement.md) , bir dış yordama bir başvuru oluşturur ve bu gerekli bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c318a-107">The [Declare Statement](../statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="c318a-108">`charsetmodifier`Deyimdeki bölüm, `Declare` dış yordama yapılan bir çağrı sırasında dizeleri sıralamak için karakter kümesi bilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c318a-108">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span></span> <span data-ttu-id="c318a-109">Ayrıca, dış yordam adı için Visual Basic dış dosyayı nasıl arayacağını da etkiler.</span><span class="sxs-lookup"><span data-stu-id="c318a-109">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="c318a-110">`Unicode`Değiştirici, Visual Basic tüm dizeleri Unicode değerlerine göre sıralayamaz ve arama sırasında bu yordamın adını değiştirmeden yordamı araması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c318a-110">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="c318a-111">Hiçbir karakter kümesi değiştiricisi belirtilmemişse, `Ansi` varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="c318a-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c318a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c318a-112">Remarks</span></span>  

 <span data-ttu-id="c318a-113">`Unicode`Değiştirici Bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="c318a-113">The `Unicode` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="c318a-114">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="c318a-114">Declare Statement</span></span>](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="c318a-115">Akıllı Cihaz Geliştirici Notları</span><span class="sxs-lookup"><span data-stu-id="c318a-115">Smart Device Developer Notes</span></span>  

 <span data-ttu-id="c318a-116">Bu anahtar sözcük desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="c318a-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c318a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c318a-117">See also</span></span>

- [<span data-ttu-id="c318a-118">Ansi</span><span class="sxs-lookup"><span data-stu-id="c318a-118">Ansi</span></span>](ansi.md)
- [<span data-ttu-id="c318a-119">Otomatik</span><span class="sxs-lookup"><span data-stu-id="c318a-119">Auto</span></span>](auto.md)
- [<span data-ttu-id="c318a-120">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="c318a-120">Keywords</span></span>](../keywords/index.md)
