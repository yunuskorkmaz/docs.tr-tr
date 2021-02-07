---
description: 'Daha fazla bilgi edinin: ANSI (Visual Basic)'
title: Ansi
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: c93472cbf6a8203f05353e0394b52c44686c0070
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701202"
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="325af-103">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="325af-103">Ansi (Visual Basic)</span></span>

<span data-ttu-id="325af-104">Visual Basic, bildirildiği dış yordamın adından bağımsız olarak, tüm dizeleri Amerikan Ulusal Standartlar Enstitüsü (ANSI) değerlerine göre sıralayamaz.</span><span class="sxs-lookup"><span data-stu-id="325af-104">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="325af-105">Projenizin dışında tanımlanan bir yordamı çağırdığınızda, Visual Basic derleyicisinin yordamı doğru bir şekilde çağırması için gereken bilgilere erişimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="325af-105">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="325af-106">Bu bilgiler yordamın nerede bulunduğuna, nasıl tanımlandığınıza, arama sırasının ve dönüş türünün ve kullandığı dize karakter kümesinin nerede olduğunu içerir.</span><span class="sxs-lookup"><span data-stu-id="325af-106">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="325af-107">[Declare bildirimi](../statements/declare-statement.md) , bir dış yordama bir başvuru oluşturur ve bu gerekli bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="325af-107">The [Declare Statement](../statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="325af-108">`charsetmodifier`Deyimindeki bölüm, `Declare` dış yordama yapılan bir çağrı sırasında dizeleri sıralama için karakter kümesi bilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="325af-108">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="325af-109">Ayrıca, dış yordam adı için Visual Basic dış dosyayı nasıl arayacağını da etkiler.</span><span class="sxs-lookup"><span data-stu-id="325af-109">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="325af-110">`Ansi`Değiştirici, Visual Basic tüm DIZELERI ANSI değerlerine göre sıralayamaz ve arama sırasında bu yordamın adını değiştirmeden yordamı araması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="325af-110">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="325af-111">Hiçbir karakter kümesi değiştiricisi belirtilmemişse, `Ansi` varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="325af-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="325af-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="325af-112">Remarks</span></span>  

 <span data-ttu-id="325af-113">`Ansi`Değiştirici Bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="325af-113">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="325af-114">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="325af-114">Declare Statement</span></span>](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="325af-115">Akıllı Cihaz Geliştirici Notları</span><span class="sxs-lookup"><span data-stu-id="325af-115">Smart Device Developer Notes</span></span>  

 <span data-ttu-id="325af-116">Bu anahtar sözcük desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="325af-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="325af-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="325af-117">See also</span></span>

- [<span data-ttu-id="325af-118">Otomatik</span><span class="sxs-lookup"><span data-stu-id="325af-118">Auto</span></span>](auto.md)
- [<span data-ttu-id="325af-119">Unicode</span><span class="sxs-lookup"><span data-stu-id="325af-119">Unicode</span></span>](unicode.md)
- [<span data-ttu-id="325af-120">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="325af-120">Keywords</span></span>](../keywords/index.md)
