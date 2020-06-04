---
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
ms.openlocfilehash: 9b1bc40bb52244deefc0486d3a40c4b961ad1ee5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402687"
---
# <a name="unicode-visual-basic"></a><span data-ttu-id="3fb0a-102">Unicode (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fb0a-102">Unicode (Visual Basic)</span></span>
<span data-ttu-id="3fb0a-103">Visual Basic, belirtilen dış yordamın adından bağımsız olarak, tüm dizeleri Unicode değerlerine göre sıralayamaz.</span><span class="sxs-lookup"><span data-stu-id="3fb0a-103">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="3fb0a-104">Projenizin dışında tanımlanan bir yordamı çağırdığınızda, Visual Basic derleyicisinin yordamı doğru bir şekilde çağırmak için sahip olması gereken bilgilere erişimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="3fb0a-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span></span> <span data-ttu-id="3fb0a-105">Bu bilgiler yordamın nerede bulunduğuna, nasıl tanımlandığınıza, arama sırasının ve dönüş türünün ve kullandığı dize karakter kümesinin nerede olduğunu içerir.</span><span class="sxs-lookup"><span data-stu-id="3fb0a-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="3fb0a-106">[Declare bildirimi](../statements/declare-statement.md) , bir dış yordama bir başvuru oluşturur ve bu gerekli bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3fb0a-106">The [Declare Statement](../statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="3fb0a-107">`charsetmodifier`Deyimdeki bölüm, `Declare` dış yordama yapılan bir çağrı sırasında dizeleri sıralamak için karakter kümesi bilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3fb0a-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span></span> <span data-ttu-id="3fb0a-108">Ayrıca, dış yordam adı için Visual Basic dış dosyayı nasıl arayacağını da etkiler.</span><span class="sxs-lookup"><span data-stu-id="3fb0a-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="3fb0a-109">`Unicode`Değiştirici, Visual Basic tüm dizeleri Unicode değerlerine göre sıralayamaz ve arama sırasında bu yordamın adını değiştirmeden yordamı araması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3fb0a-109">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="3fb0a-110">Hiçbir karakter kümesi değiştiricisi belirtilmemişse, `Ansi` varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="3fb0a-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fb0a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3fb0a-111">Remarks</span></span>  
 <span data-ttu-id="3fb0a-112">`Unicode`Değiştirici Bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="3fb0a-112">The `Unicode` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="3fb0a-113">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="3fb0a-113">Declare Statement</span></span>](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="3fb0a-114">Akıllı Cihaz Geliştirici Notları</span><span class="sxs-lookup"><span data-stu-id="3fb0a-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="3fb0a-115">Bu anahtar sözcük desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="3fb0a-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fb0a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fb0a-116">See also</span></span>

- [<span data-ttu-id="3fb0a-117">Ansi</span><span class="sxs-lookup"><span data-stu-id="3fb0a-117">Ansi</span></span>](ansi.md)
- [<span data-ttu-id="3fb0a-118">Otomatik</span><span class="sxs-lookup"><span data-stu-id="3fb0a-118">Auto</span></span>](auto.md)
- [<span data-ttu-id="3fb0a-119">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="3fb0a-119">Keywords</span></span>](../keywords/index.md)
