---
title: Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: 2b60d732b260ad0477946e41ece4cd182de541ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649769"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a><span data-ttu-id="1b7b2-102">Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b7b2-102">Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)</span></span>
<span data-ttu-id="1b7b2-103">Bir yordam çağrısı, genellikle bir veya daha fazla bağımsız değişken için geçirdiğiniz.</span><span class="sxs-lookup"><span data-stu-id="1b7b2-103">When you call a procedure, you typically pass one or more arguments to it.</span></span> <span data-ttu-id="1b7b2-104">Her bağımsız bir temel programlama öğeye karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="1b7b2-104">Each argument corresponds to an underlying programming element.</span></span> <span data-ttu-id="1b7b2-105">Temel alınan öğeleri ve bağımsız değişkenler kendilerini değiştirilebilir veya değiştirilemez olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b7b2-105">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span></span>  
  
## <a name="modifiable-and-nonmodifiable-elements"></a><span data-ttu-id="1b7b2-106">Değiştirilebilir ve değiştirilemez öğeleri</span><span class="sxs-lookup"><span data-stu-id="1b7b2-106">Modifiable and Nonmodifiable Elements</span></span>  
 <span data-ttu-id="1b7b2-107">Bir programlama öğesi ya da olabilir bir *değiştirilebilir öğesi*, değişti, değeri olabilir veya bir *değiştirilemez öğesi*, oluşturulduktan sonra bir sabit değere sahip.</span><span class="sxs-lookup"><span data-stu-id="1b7b2-107">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span></span>  
  
 <span data-ttu-id="1b7b2-108">Aşağıdaki tabloda, değiştirilebilir ve değiştirilemez programlama öğeleri listeler.</span><span class="sxs-lookup"><span data-stu-id="1b7b2-108">The following table lists modifiable and nonmodifiable programming elements.</span></span>  
  
|<span data-ttu-id="1b7b2-109">Değiştirilebilir öğeleri</span><span class="sxs-lookup"><span data-stu-id="1b7b2-109">Modifiable elements</span></span>|<span data-ttu-id="1b7b2-110">Değiştirilemez öğeleri</span><span class="sxs-lookup"><span data-stu-id="1b7b2-110">Nonmodifiable elements</span></span>|  
|-------------------------|----------------------------|  
|<span data-ttu-id="1b7b2-111">Salt okunur dışında nesne değişkenleri (yordamların içinde bildirilen), yerel değişkenleri dahil</span><span class="sxs-lookup"><span data-stu-id="1b7b2-111">Local variables (declared inside procedures), including object variables, except for read-only</span></span>|<span data-ttu-id="1b7b2-112">Salt okunur değişkenler, alanlar ve Özellikler</span><span class="sxs-lookup"><span data-stu-id="1b7b2-112">Read-only variables, fields, and properties</span></span>|  
|<span data-ttu-id="1b7b2-113">Salt okunur dışında alanları (üye değişkenleri) modülleri, sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="1b7b2-113">Fields (member variables of modules, classes, and structures), except for read-only</span></span>|<span data-ttu-id="1b7b2-114">Sabit ve değişmez değerleri</span><span class="sxs-lookup"><span data-stu-id="1b7b2-114">Constants and literals</span></span>|  
|<span data-ttu-id="1b7b2-115">Salt okunur dışında özellikleri</span><span class="sxs-lookup"><span data-stu-id="1b7b2-115">Properties, except for read-only</span></span>|<span data-ttu-id="1b7b2-116">Numaralandırma üyeleri</span><span class="sxs-lookup"><span data-stu-id="1b7b2-116">Enumeration members</span></span>|  
|<span data-ttu-id="1b7b2-117">Dizi öğeleri</span><span class="sxs-lookup"><span data-stu-id="1b7b2-117">Array elements</span></span>|<span data-ttu-id="1b7b2-118">Deyimler (öğelerini değiştirilebilir olsa bile)</span><span class="sxs-lookup"><span data-stu-id="1b7b2-118">Expressions (even if their elements are modifiable)</span></span>|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a><span data-ttu-id="1b7b2-119">Değiştirilebilir ve değiştirilemez bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="1b7b2-119">Modifiable and Nonmodifiable Arguments</span></span>  
 <span data-ttu-id="1b7b2-120">A *değiştirilebilir bağımsız değişkeni* değiştirilebilir ve temel bir öğesiyle biridir.</span><span class="sxs-lookup"><span data-stu-id="1b7b2-120">A *modifiable argument* is one with a modifiable underlying element.</span></span> <span data-ttu-id="1b7b2-121">Çağrıyı yapan kod herhangi bir zamanda yeni bir değer depolayabilir ve bağımsız değişken geçirirseniz [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), yordamdaki kod çağıran kodu temel alınan öğe de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b7b2-121">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="1b7b2-122">A *değiştirilemez bağımsız değişkeni* değiştirilemez bir temel öğeye sahip ya da geçirilen [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="1b7b2-122">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="1b7b2-123">Değiştirilebilir öğesi olsa bile, yordamı çağıran kodu, temel alınan öğe değiştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="1b7b2-123">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span></span> <span data-ttu-id="1b7b2-124">Bunu değiştirilemez bir öğeyse, çağrıyı yapan kod onu değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b7b2-124">If it is a nonmodifiable element, the calling code itself cannot modify it.</span></span>  
  
 <span data-ttu-id="1b7b2-125">Değişiklik çağıran kodu temel alınan öğe etkilemez ancak bu adlı yordamı değiştirilemez bağımsız değişkeni yerel kopyasını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b7b2-125">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b7b2-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1b7b2-126">See Also</span></span>  
 [<span data-ttu-id="1b7b2-127">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="1b7b2-127">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="1b7b2-128">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="1b7b2-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="1b7b2-129">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme</span><span class="sxs-lookup"><span data-stu-id="1b7b2-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="1b7b2-130">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="1b7b2-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="1b7b2-131">Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="1b7b2-131">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [<span data-ttu-id="1b7b2-132">Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="1b7b2-132">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)  
 [<span data-ttu-id="1b7b2-133">Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma</span><span class="sxs-lookup"><span data-stu-id="1b7b2-133">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [<span data-ttu-id="1b7b2-134">Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama</span><span class="sxs-lookup"><span data-stu-id="1b7b2-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [<span data-ttu-id="1b7b2-135">Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="1b7b2-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="1b7b2-136">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="1b7b2-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
