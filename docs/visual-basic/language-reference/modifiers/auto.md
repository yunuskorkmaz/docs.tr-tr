---
title: Otomatik
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: b9bdeed55788252c71b8fb1c995c140cbfdf60eb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373134"
---
# <a name="auto-visual-basic"></a><span data-ttu-id="13111-102">Otomatik (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13111-102">Auto (Visual Basic)</span></span>
<span data-ttu-id="13111-103">Visual Basic, bildirildiği dış yordamın dış adına göre .NET Framework kurallara göre dizeleri sıralaması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="13111-103">Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="13111-104">Projenizin dışında tanımlanan bir yordamı çağırdığınızda, Visual Basic derleyicisinin yordamı doğru bir şekilde çağırmak için sahip olması gereken bilgilere erişimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="13111-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly.</span></span> <span data-ttu-id="13111-105">Bu bilgiler yordamın nerede bulunduğuna, nasıl tanımlandığınıza, arama sırasının ve dönüş türünün ve kullandığı dize karakter kümesinin nerede olduğunu içerir.</span><span class="sxs-lookup"><span data-stu-id="13111-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="13111-106">[Declare bildirimi](../statements/declare-statement.md) , bir dış yordama bir başvuru oluşturur ve bu gerekli bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="13111-106">The [Declare Statement](../statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="13111-107">`charsetmodifier`Deyimindeki bölüm, `Declare` dış yordama yapılan bir çağrı sırasında dizeleri sıralama için karakter kümesi bilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="13111-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="13111-108">Ayrıca, dış yordam adı için Visual Basic dış dosyayı nasıl arayacağını da etkiler.</span><span class="sxs-lookup"><span data-stu-id="13111-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="13111-109">`Auto`Değiştirici, Visual Basic .NET Framework kurallarına göre dizeleri sıralaması gerektiğini ve çalışma zamanı platformunun temel karakter kümesini saptamalıdır ve ilk arama başarısız olursa dış yordam adını değiştirmektir.</span><span class="sxs-lookup"><span data-stu-id="13111-109">The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails.</span></span> <span data-ttu-id="13111-110">Daha fazla bilgi için, [Declare bildiriminde](../statements/declare-statement.md)"karakter kümeleri" başlığına bakın.</span><span class="sxs-lookup"><span data-stu-id="13111-110">For more information, see "Character Sets" in [Declare Statement](../statements/declare-statement.md).</span></span>  
  
 <span data-ttu-id="13111-111">Hiçbir karakter kümesi değiştiricisi belirtilmemişse, `Ansi` varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="13111-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13111-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13111-112">Remarks</span></span>  
 <span data-ttu-id="13111-113">`Auto`Değiştirici Bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="13111-113">The `Auto` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="13111-114">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="13111-114">Declare Statement</span></span>](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="13111-115">Akıllı Cihaz Geliştirici Notları</span><span class="sxs-lookup"><span data-stu-id="13111-115">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="13111-116">Bu anahtar sözcük desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="13111-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13111-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13111-117">See also</span></span>

- [<span data-ttu-id="13111-118">Ansi</span><span class="sxs-lookup"><span data-stu-id="13111-118">Ansi</span></span>](ansi.md)
- [<span data-ttu-id="13111-119">Unicode</span><span class="sxs-lookup"><span data-stu-id="13111-119">Unicode</span></span>](unicode.md)
- [<span data-ttu-id="13111-120">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="13111-120">Keywords</span></span>](../keywords/index.md)
