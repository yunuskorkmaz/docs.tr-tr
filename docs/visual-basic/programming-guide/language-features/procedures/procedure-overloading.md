---
title: Yordam Aşırı Yüklemesi (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
ms.openlocfilehash: 4d90b81049197fbbf4a767b17399d3e9c80be0f7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975478"
---
# <a name="procedure-overloading-visual-basic"></a><span data-ttu-id="cca16-102">Yordam Aşırı Yüklemesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cca16-102">Procedure Overloading (Visual Basic)</span></span>
<span data-ttu-id="cca16-103">*Aşırı yükleme* bir yordam, birden çok sürümü aynı ada ancak farklı parametre listeleri kullanarak tanımlama anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cca16-103">*Overloading* a procedure means defining it in multiple versions, using the same name but different parameter lists.</span></span> <span data-ttu-id="cca16-104">Aşırı yükleme amacı, ada göre ayırmak zorunda kalmadan bir yordamın birden fazla yakından ilgili sürümünü tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="cca16-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span> <span data-ttu-id="cca16-105">Parametre listesini değiştirerek bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cca16-105">You do this by varying the parameter list.</span></span>  
  
## <a name="overloading-rules"></a><span data-ttu-id="cca16-106">Kuralları aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="cca16-106">Overloading Rules</span></span>  
 <span data-ttu-id="cca16-107">Bir yordamı aşırı yükleme, aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="cca16-107">When you overload a procedure, the following rules apply:</span></span>  
  
-   <span data-ttu-id="cca16-108">**Aynı ada**.</span><span class="sxs-lookup"><span data-stu-id="cca16-108">**Same Name**.</span></span> <span data-ttu-id="cca16-109">Aşırı yüklenen her sürümü aynı yordam adı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cca16-109">Each overloaded version must use the same procedure name.</span></span>  
  
-   <span data-ttu-id="cca16-110">**Farklı imza**.</span><span class="sxs-lookup"><span data-stu-id="cca16-110">**Different Signature**.</span></span> <span data-ttu-id="cca16-111">Her Aşırı yüklenen sürümü, diğer aşırı yüklenmiş sürümleri aşağıdaki bakımdan en az birinde farklı olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="cca16-111">Each overloaded version must differ from all other overloaded versions in at least one of the following respects:</span></span>  
  
    -   <span data-ttu-id="cca16-112">Parametre sayısı</span><span class="sxs-lookup"><span data-stu-id="cca16-112">Number of parameters</span></span>  
  
    -   <span data-ttu-id="cca16-113">Parametre sırası</span><span class="sxs-lookup"><span data-stu-id="cca16-113">Order of the parameters</span></span>  
  
    -   <span data-ttu-id="cca16-114">Parametrelerinin veri türleri</span><span class="sxs-lookup"><span data-stu-id="cca16-114">Data types of the parameters</span></span>  
  
    -   <span data-ttu-id="cca16-115">Tür parametreleri (için genel bir yordam) sayısı</span><span class="sxs-lookup"><span data-stu-id="cca16-115">Number of type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="cca16-116">Dönüş türü (yalnızca bir dönüşüm işleci)</span><span class="sxs-lookup"><span data-stu-id="cca16-116">Return type (only for a conversion operator)</span></span>  
  
     <span data-ttu-id="cca16-117">Yordam adı ile birlikte önceki öğeler toplu olarak adlandırılır *imza* yordamın.</span><span class="sxs-lookup"><span data-stu-id="cca16-117">Together with the procedure name, the preceding items are collectively called the *signature* of the procedure.</span></span> <span data-ttu-id="cca16-118">Aşırı yüklenmiş bir yordamı çağırdığınızda, derleyici imzayı tanımının çağrı doğru eşleşip eşleşmediğini kontrol için kullanır.</span><span class="sxs-lookup"><span data-stu-id="cca16-118">When you call an overloaded procedure, the compiler uses the signature to check that the call correctly matches the definition.</span></span>  
  
-   <span data-ttu-id="cca16-119">**Öğeleri imzasının parçası**.</span><span class="sxs-lookup"><span data-stu-id="cca16-119">**Items Not Part of Signature**.</span></span> <span data-ttu-id="cca16-120">İmza değişen olmadan bir yordamı aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="cca16-120">You cannot overload a procedure without varying the signature.</span></span> <span data-ttu-id="cca16-121">Özellikle, bir veya daha fazla aşağıdaki öğelerin değişen tarafından yalnızca bir yordamı aşırı yüklenemez:</span><span class="sxs-lookup"><span data-stu-id="cca16-121">In particular, you cannot overload a procedure by varying only one or more of the following items:</span></span>  
  
    -   <span data-ttu-id="cca16-122">Yordam değiştiricisi anahtar sözcükler gibi `Public`, `Shared`, ve `Static`</span><span class="sxs-lookup"><span data-stu-id="cca16-122">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span></span>  
  
    -   <span data-ttu-id="cca16-123">Parametresi veya tür parametresi adları</span><span class="sxs-lookup"><span data-stu-id="cca16-123">Parameter or type parameter names</span></span>  
  
    -   <span data-ttu-id="cca16-124">Tür parametresi kısıtlamaları (için genel bir yordam)</span><span class="sxs-lookup"><span data-stu-id="cca16-124">Type parameter constraints (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="cca16-125">Parametre değiştiricisi anahtar sözcükler gibi `ByRef` ve `Optional`</span><span class="sxs-lookup"><span data-stu-id="cca16-125">Parameter modifier keywords, such as `ByRef` and `Optional`</span></span>  
  
    -   <span data-ttu-id="cca16-126">Bir değer olup olmadığını döndürür</span><span class="sxs-lookup"><span data-stu-id="cca16-126">Whether it returns a value</span></span>  
  
    -   <span data-ttu-id="cca16-127">(bir dönüşüm işleci dışında) dönüş değerinin veri türü</span><span class="sxs-lookup"><span data-stu-id="cca16-127">The data type of the return value (except for a conversion operator)</span></span>  
  
     <span data-ttu-id="cca16-128">Yukarıdaki listede öğeleri imzasının bir parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="cca16-128">The items in the preceding list are not part of the signature.</span></span> <span data-ttu-id="cca16-129">Aşırı yüklü sürümler arasında ayırt etmek için kullanamazsınız olsa da, bunların imzalarını tarafından düzgün bir şekilde ayırt edilen aşırı yüklü sürümler arasında farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="cca16-129">Although you cannot use them to differentiate between overloaded versions, you can vary them among overloaded versions that are properly differentiated by their signatures.</span></span>  
  
-   <span data-ttu-id="cca16-130">**Geç bağlama bağımsız değişkenleri**.</span><span class="sxs-lookup"><span data-stu-id="cca16-130">**Late-Bound Arguments**.</span></span> <span data-ttu-id="cca16-131">Geç bir bağımlı nesne değişkeni aşırı yüklenmiş bir sürüme geçirmek istiyorsanız, uygun bir parametre olarak bildirmeniz gerekir <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="cca16-131">If you intend to pass a late bound object variable to an overloaded version, you must declare the appropriate parameter as <xref:System.Object>.</span></span>  
  
## <a name="multiple-versions-of-a-procedure"></a><span data-ttu-id="cca16-132">Bir yordamın birden fazla sürümünü</span><span class="sxs-lookup"><span data-stu-id="cca16-132">Multiple Versions of a Procedure</span></span>  
 <span data-ttu-id="cca16-133">Yazdığınız varsayalım bir `Sub` müşteriye adı veya hesap numarası başvurabileceğiniz istediğiniz bir müşterinin bakiyesi ve karşı bir işlem göndermeniz için yordamı.</span><span class="sxs-lookup"><span data-stu-id="cca16-133">Suppose you are writing a `Sub` procedure to post a transaction against a customer's balance, and you want to be able to refer to the customer either by name or by account number.</span></span> <span data-ttu-id="cca16-134">Bunu yapabilmek için iki farklı tanımlayabilirsiniz `Sub` yordamlar, aşağıdaki örnekte olduğu gibi:</span><span class="sxs-lookup"><span data-stu-id="cca16-134">To accommodate this, you can define two different `Sub` procedures, as in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]  
  
### <a name="overloaded-versions"></a><span data-ttu-id="cca16-135">Aşırı yüklenmiş sürümleri</span><span class="sxs-lookup"><span data-stu-id="cca16-135">Overloaded Versions</span></span>  
 <span data-ttu-id="cca16-136">Aşırı yükleme tek yordam adı için bir alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="cca16-136">An alternative is to overload a single procedure name.</span></span> <span data-ttu-id="cca16-137">Kullanabileceğiniz [aşırı](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğünü bir sürümüne ilişkin yordam her parametre listesi için aşağıdaki gibi tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="cca16-137">You can use the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword to define a version of the procedure for each parameter list, as follows:</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
#### <a name="additional-overloads"></a><span data-ttu-id="cca16-138">Ek aşırı yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="cca16-138">Additional Overloads</span></span>  
 <span data-ttu-id="cca16-139">Ayrıca herhangi bir işlem tutarı kabul etmek istiyorsanız `Decimal` veya `Single`, daha fazla aşırı `post` Bu çeşitleme için izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="cca16-139">If you also wanted to accept a transaction amount in either `Decimal` or `Single`, you could further overload `post` to allow for this variation.</span></span> <span data-ttu-id="cca16-140">Siz yaptıysanız her aşırı yüklemeleri önceki örnekte, dört olurdu `Sub` yordamları, aynı ada sahip tüm ancak dört farklı imzalara sahip.</span><span class="sxs-lookup"><span data-stu-id="cca16-140">If you did this to each of the overloads in the preceding example, you would have four `Sub` procedures, all with the same name but with four different signatures.</span></span>  
  
## <a name="advantages-of-overloading"></a><span data-ttu-id="cca16-141">Aşırı yükleme avantajları</span><span class="sxs-lookup"><span data-stu-id="cca16-141">Advantages of Overloading</span></span>  
 <span data-ttu-id="cca16-142">Bir yordamı aşırı yükleme çağrısının esneklik avantajlarındandır.</span><span class="sxs-lookup"><span data-stu-id="cca16-142">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="cca16-143">Kullanılacak `post` yordamı çağıran kod, müşteri kimliği olarak edinebilirsiniz önceki örnekte bildirilen bir `String` veya `Integer`ve ardından her iki durumda da aynı yordamı çağırın.</span><span class="sxs-lookup"><span data-stu-id="cca16-143">To use the `post` procedure declared in the preceding example, the calling code can obtain the customer identification as either a `String` or an `Integer`, and then call the same procedure in either case.</span></span> <span data-ttu-id="cca16-144">Aşağıdaki örnek bunu göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="cca16-144">The following example illustrates this:</span></span>  
  
 [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
 [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a><span data-ttu-id="cca16-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cca16-145">See also</span></span>
- [<span data-ttu-id="cca16-146">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="cca16-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="cca16-147">Nasıl yapılır: Bir yordamın birden fazla sürümünü tanımlama</span><span class="sxs-lookup"><span data-stu-id="cca16-147">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="cca16-148">Nasıl yapılır: Aşırı yüklenmiş bir yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="cca16-148">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="cca16-149">Nasıl yapılır: İsteğe bağlı parametreler isteyen bir yordamı aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="cca16-149">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="cca16-150">Nasıl yapılır: Belirsiz sayıda parametre isteyen bir yordamı aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="cca16-150">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="cca16-151">Yordamları Aşırı Yüklemeye İlişkin Düşünceler</span><span class="sxs-lookup"><span data-stu-id="cca16-151">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="cca16-152">Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="cca16-152">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="cca16-153">Overloads</span><span class="sxs-lookup"><span data-stu-id="cca16-153">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="cca16-154">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="cca16-154">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
