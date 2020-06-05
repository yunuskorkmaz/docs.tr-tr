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
ms.openlocfilehash: 01f1f7ef5963feeb3fe2b5390244e4e516773bad
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393850"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a><span data-ttu-id="43069-102">Nasıl yapılır: Genel Bir Sınıf Kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43069-102">How to: Use a Generic Class (Visual Basic)</span></span>
<span data-ttu-id="43069-103">*Tür parametreleri* alan bir sınıfa *Genel sınıf*denir.</span><span class="sxs-lookup"><span data-stu-id="43069-103">A class that takes *type parameters* is called a *generic class*.</span></span> <span data-ttu-id="43069-104">Genel bir sınıf kullanıyorsanız, bu parametrelerin her biri için bir *tür bağımsız değişkeni* sağlayarak bundan *oluşturulmuş bir sınıf* oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43069-104">If you are using a generic class, you can generate a *constructed class* from it by supplying a *type argument* for each of these parameters.</span></span> <span data-ttu-id="43069-105">Daha sonra, oluşturulan sınıf türünün bir değişkenini bildirebilir ve oluşturulan sınıfın bir örneğini oluşturabilir ve bu değişkene atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43069-105">You can then declare a variable of the constructed class type, and you can create an instance of the constructed class and assign it to that variable.</span></span>  
  
 <span data-ttu-id="43069-106">Sınıfların yanı sıra genel yapıları, arabirimleri, yordamları ve temsilcileri de tanımlayabilir ve kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43069-106">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
 <span data-ttu-id="43069-107">Aşağıdaki yordam .NET Framework tanımlı bir genel sınıf alır ve bundan bir örnek oluşturur.</span><span class="sxs-lookup"><span data-stu-id="43069-107">The following procedure takes a generic class defined in the .NET Framework and creates an instance from it.</span></span>  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a><span data-ttu-id="43069-108">Bir tür parametresi alan bir sınıfı kullanmak için</span><span class="sxs-lookup"><span data-stu-id="43069-108">To use a class that takes a type parameter</span></span>  
  
1. <span data-ttu-id="43069-109">Kaynak dosyanızın başlangıcında, ad alanını içeri aktarmak için bir [Imports (.net ad alanı ve türü) ifadesini](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) ekleyin <xref:System.Collections.Generic?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="43069-109">At the beginning of your source file, include an [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) to import the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="43069-110">Bu, sınıfını, gibi <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> diğer sıra sınıflarından ayırt etmek için tam olarak nitelendirmek zorunda kalmadan sınıfa başvurmanıza olanak sağlar <xref:System.Collections.Queue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="43069-110">This allows you to refer to the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class without having to fully qualify it to differentiate it from other queue classes such as <xref:System.Collections.Queue?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="43069-111">Nesneyi normal şekilde oluşturun, ancak `(Of type)` sınıf adından hemen sonra ekleyin.</span><span class="sxs-lookup"><span data-stu-id="43069-111">Create the object in the normal way, but add `(Of type)` immediately after the class name.</span></span>  
  
     <span data-ttu-id="43069-112">Aşağıdaki örnek, <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> farklı veri türlerindeki öğeleri tutan iki kuyruk nesnesi oluşturmak için aynı sınıfı () kullanır.</span><span class="sxs-lookup"><span data-stu-id="43069-112">The following example uses the same class (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) to create two queue objects that hold items of different data types.</span></span> <span data-ttu-id="43069-113">Her kuyruğun sonuna öğeler ekler ve sonra her kuyruğun önüne öğeleri kaldırır ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43069-113">It adds items to the end of each queue and then removes and displays items from the front of each queue.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="43069-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43069-114">See also</span></span>

- [<span data-ttu-id="43069-115">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="43069-115">Data Types</span></span>](index.md)
- [<span data-ttu-id="43069-116">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="43069-116">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="43069-117">Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler</span><span class="sxs-lookup"><span data-stu-id="43069-117">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="43069-118">Durumunu</span><span class="sxs-lookup"><span data-stu-id="43069-118">Of</span></span>](../../../language-reference/statements/of-clause.md)
- [<span data-ttu-id="43069-119">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="43069-119">Imports Statement (.NET Namespace and Type)</span></span>](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="43069-120">Nasıl yapılır: Farklı Veri Türlerinde Aynı İşlevselliği Sağlayabilen Bir Sınıf Tanımlama</span><span class="sxs-lookup"><span data-stu-id="43069-120">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](how-to-define-a-class-that-can-provide-identical-functionality.md)
- [<span data-ttu-id="43069-121">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="43069-121">Iterators</span></span>](../../concepts/iterators.md)
