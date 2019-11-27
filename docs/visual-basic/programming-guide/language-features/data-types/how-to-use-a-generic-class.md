---
title: 'Nasıl yapılır: Genel Bir Sınıf Kullanma'
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
ms.openlocfilehash: 87ca0da5095484615666cda505b4f7678d8160de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350055"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a><span data-ttu-id="157ae-102">Nasıl yapılır: Genel Bir Sınıf Kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="157ae-102">How to: Use a Generic Class (Visual Basic)</span></span>
<span data-ttu-id="157ae-103">*Tür parametreleri* alan bir sınıfa *Genel sınıf*denir.</span><span class="sxs-lookup"><span data-stu-id="157ae-103">A class that takes *type parameters* is called a *generic class*.</span></span> <span data-ttu-id="157ae-104">Genel bir sınıf kullanıyorsanız, bu parametrelerin her biri için bir *tür bağımsız değişkeni* sağlayarak bundan *oluşturulmuş bir sınıf* oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="157ae-104">If you are using a generic class, you can generate a *constructed class* from it by supplying a *type argument* for each of these parameters.</span></span> <span data-ttu-id="157ae-105">Daha sonra, oluşturulan sınıf türünün bir değişkenini bildirebilir ve oluşturulan sınıfın bir örneğini oluşturabilir ve bu değişkene atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="157ae-105">You can then declare a variable of the constructed class type, and you can create an instance of the constructed class and assign it to that variable.</span></span>  
  
 <span data-ttu-id="157ae-106">Sınıfların yanı sıra genel yapıları, arabirimleri, yordamları ve temsilcileri de tanımlayabilir ve kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="157ae-106">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
 <span data-ttu-id="157ae-107">Aşağıdaki yordam .NET Framework tanımlı bir genel sınıf alır ve bundan bir örnek oluşturur.</span><span class="sxs-lookup"><span data-stu-id="157ae-107">The following procedure takes a generic class defined in the .NET Framework and creates an instance from it.</span></span>  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a><span data-ttu-id="157ae-108">Bir tür parametresi alan bir sınıfı kullanmak için</span><span class="sxs-lookup"><span data-stu-id="157ae-108">To use a class that takes a type parameter</span></span>  
  
1. <span data-ttu-id="157ae-109">Kaynak dosyanızın başlangıcında, <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanını içeri aktarmak için bir [Imports (.net ad alanı ve türü) ifadesini](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="157ae-109">At the beginning of your source file, include an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to import the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="157ae-110">Bu, <xref:System.Collections.Queue?displayProperty=nameWithType>gibi diğer sıra sınıflarından ayırt etmek için tam olarak nitelendirmek zorunda kalmadan <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> sınıfına başvurmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="157ae-110">This allows you to refer to the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class without having to fully qualify it to differentiate it from other queue classes such as <xref:System.Collections.Queue?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="157ae-111">Nesneyi normal şekilde oluşturun, ancak sınıf adından hemen sonra `(Of type)` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="157ae-111">Create the object in the normal way, but add `(Of type)` immediately after the class name.</span></span>  
  
     <span data-ttu-id="157ae-112">Aşağıdaki örnek, farklı veri türlerindeki öğeleri tutan iki kuyruk nesnesi oluşturmak için aynı sınıfı (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) kullanır.</span><span class="sxs-lookup"><span data-stu-id="157ae-112">The following example uses the same class (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) to create two queue objects that hold items of different data types.</span></span> <span data-ttu-id="157ae-113">Her kuyruğun sonuna öğeler ekler ve sonra her kuyruğun önüne öğeleri kaldırır ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="157ae-113">It adds items to the end of each queue and then removes and displays items from the front of each queue.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="157ae-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="157ae-114">See also</span></span>

- [<span data-ttu-id="157ae-115">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="157ae-115">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="157ae-116">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="157ae-116">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="157ae-117">Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler</span><span class="sxs-lookup"><span data-stu-id="157ae-117">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="157ae-118">Durumunu</span><span class="sxs-lookup"><span data-stu-id="157ae-118">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)
- [<span data-ttu-id="157ae-119">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="157ae-119">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="157ae-120">Nasıl yapılır: Farklı Veri Türlerinde Aynı İşlevselliği Sağlayabilen Bir Sınıf Tanımlama</span><span class="sxs-lookup"><span data-stu-id="157ae-120">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [<span data-ttu-id="157ae-121">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="157ae-121">Iterators</span></span>](../../../../visual-basic/programming-guide/concepts/iterators.md)
