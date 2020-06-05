---
title: Ansi
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: 67792e52c21555bef46548e9ab0a6ebd32061071
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373206"
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="faf46-102">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="faf46-102">Ansi (Visual Basic)</span></span>
<span data-ttu-id="faf46-103">Visual Basic, bildirildiği dış yordamın adından bağımsız olarak, tüm dizeleri Amerikan Ulusal Standartlar Enstitüsü (ANSI) değerlerine göre sıralayamaz.</span><span class="sxs-lookup"><span data-stu-id="faf46-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="faf46-104">Projenizin dışında tanımlanan bir yordamı çağırdığınızda, Visual Basic derleyicisinin yordamı doğru bir şekilde çağırması için gereken bilgilere erişimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="faf46-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="faf46-105">Bu bilgiler yordamın nerede bulunduğuna, nasıl tanımlandığınıza, arama sırasının ve dönüş türünün ve kullandığı dize karakter kümesinin nerede olduğunu içerir.</span><span class="sxs-lookup"><span data-stu-id="faf46-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="faf46-106">[Declare bildirimi](../statements/declare-statement.md) , bir dış yordama bir başvuru oluşturur ve bu gerekli bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="faf46-106">The [Declare Statement](../statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="faf46-107">`charsetmodifier`Deyimindeki bölüm, `Declare` dış yordama yapılan bir çağrı sırasında dizeleri sıralama için karakter kümesi bilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="faf46-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="faf46-108">Ayrıca, dış yordam adı için Visual Basic dış dosyayı nasıl arayacağını da etkiler.</span><span class="sxs-lookup"><span data-stu-id="faf46-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="faf46-109">`Ansi`Değiştirici, Visual Basic tüm DIZELERI ANSI değerlerine göre sıralayamaz ve arama sırasında bu yordamın adını değiştirmeden yordamı araması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="faf46-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="faf46-110">Hiçbir karakter kümesi değiştiricisi belirtilmemişse, `Ansi` varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="faf46-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="faf46-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="faf46-111">Remarks</span></span>  
 <span data-ttu-id="faf46-112">`Ansi`Değiştirici Bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="faf46-112">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="faf46-113">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="faf46-113">Declare Statement</span></span>](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="faf46-114">Akıllı Cihaz Geliştirici Notları</span><span class="sxs-lookup"><span data-stu-id="faf46-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="faf46-115">Bu anahtar sözcük desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="faf46-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faf46-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="faf46-116">See also</span></span>

- [<span data-ttu-id="faf46-117">Otomatik</span><span class="sxs-lookup"><span data-stu-id="faf46-117">Auto</span></span>](auto.md)
- [<span data-ttu-id="faf46-118">Unicode</span><span class="sxs-lookup"><span data-stu-id="faf46-118">Unicode</span></span>](unicode.md)
- [<span data-ttu-id="faf46-119">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="faf46-119">Keywords</span></span>](../keywords/index.md)
