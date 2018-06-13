---
title: 'Nasıl yapılır: Genel Bir Sınıf Kullanma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- generic parameters
- data type parameters
- generics [Visual Basic], about generics
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], creating generic types
- data type arguments
- parameters [Visual Basic], data type
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
ms.openlocfilehash: adea9f7e7dbbc2317e5b857a5153e3ec67d63344
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647923"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a><span data-ttu-id="d4b0f-102">Nasıl yapılır: Genel Bir Sınıf Kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4b0f-102">How to: Use a Generic Class (Visual Basic)</span></span>
<span data-ttu-id="d4b0f-103">Alan bir sınıf *tür parametrelerindeki* çağrılır bir *genel bir sınıf*.</span><span class="sxs-lookup"><span data-stu-id="d4b0f-103">A class that takes *type parameters* is called a *generic class*.</span></span> <span data-ttu-id="d4b0f-104">Genel bir sınıf kullanıyorsanız, oluşturabileceğiniz bir *oluşturulan sınıf* dışarı sağlayarak bir *tür bağımsız değişkeni* bu parametrelerin her biri için.</span><span class="sxs-lookup"><span data-stu-id="d4b0f-104">If you are using a generic class, you can generate a *constructed class* from it by supplying a *type argument* for each of these parameters.</span></span> <span data-ttu-id="d4b0f-105">Oluşturulan sınıf türü bir değişken sonra bildirebilir ve oluşturulan sınıfının bir örneği oluşturun ve bu değişkenine atayın.</span><span class="sxs-lookup"><span data-stu-id="d4b0f-105">You can then declare a variable of the constructed class type, and you can create an instance of the constructed class and assign it to that variable.</span></span>  
  
 <span data-ttu-id="d4b0f-106">Sınıfları yanı sıra tanımlayabilir ve genel yapılar, arabirimler, yordamlar ve temsilciler kullanın.</span><span class="sxs-lookup"><span data-stu-id="d4b0f-106">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
 <span data-ttu-id="d4b0f-107">Aşağıdaki yordamda tanımlanan genel bir sınıf gereken [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] ve bir örnek oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d4b0f-107">The following procedure takes a generic class defined in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] and creates an instance from it.</span></span>  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a><span data-ttu-id="d4b0f-108">Bir tür parametresi bir alan bir sınıf kullanma</span><span class="sxs-lookup"><span data-stu-id="d4b0f-108">To use a class that takes a type parameter</span></span>  
  
1.  <span data-ttu-id="d4b0f-109">Kaynak dosyanızı başında dahil bir [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) almak için <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d4b0f-109">At the beginning of your source file, include an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to import the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="d4b0f-110">Bu sayede başvurmak <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> gibi diğer sıra sınıflardan ayırt etmek için tam olarak nitelemek gerek kalmadan sınıfı <xref:System.Collections.Queue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d4b0f-110">This allows you to refer to the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class without having to fully qualify it to differentiate it from other queue classes such as <xref:System.Collections.Queue?displayProperty=nameWithType>.</span></span>  
  
2.  <span data-ttu-id="d4b0f-111">Normal bir şekilde oluşturur, ancak eklemek `(Of` `type``)` hemen sonra sınıf adı.</span><span class="sxs-lookup"><span data-stu-id="d4b0f-111">Create the object in the normal way, but add `(Of` `type``)` immediately after the class name.</span></span>  
  
     <span data-ttu-id="d4b0f-112">Aşağıdaki örnek aynı sınıfını kullanır (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) farklı veri türlerini öğelerinizi tutmak iki sıra nesneleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="d4b0f-112">The following example uses the same class (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) to create two queue objects that hold items of different data types.</span></span> <span data-ttu-id="d4b0f-113">Öğeleri her sırasının sonuna ekler ve ardından kaldırır ve her sıranın önünü öğelerinden görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d4b0f-113">It adds items to the end of each queue and then removes and displays items from the front of each queue.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#9](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-use-a-generic-class_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d4b0f-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4b0f-114">See Also</span></span>  
 [<span data-ttu-id="d4b0f-115">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="d4b0f-115">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="d4b0f-116">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="d4b0f-116">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="d4b0f-117">Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler</span><span class="sxs-lookup"><span data-stu-id="d4b0f-117">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)  
 [<span data-ttu-id="d4b0f-118">,</span><span class="sxs-lookup"><span data-stu-id="d4b0f-118">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)  
 [<span data-ttu-id="d4b0f-119">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="d4b0f-119">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="d4b0f-120">Nasıl yapılır: Farklı Veri Türlerinde Aynı İşlevselliği Sağlayabilen Bir Sınıf Tanımlama</span><span class="sxs-lookup"><span data-stu-id="d4b0f-120">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [<span data-ttu-id="d4b0f-121">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="d4b0f-121">Iterators</span></span>](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)
