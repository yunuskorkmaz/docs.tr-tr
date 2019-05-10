---
title: 'Nasıl yapılır: -Arabirim üyelerini açıkça uygulama C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 8cef6c840bf6afff8ccbf7d02012990e11d47991
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595366"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="b2e78-102">Nasıl yapılır: Arabirim üyelerini açıkça uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b2e78-102">How to: Explicitly Implement Interface Members (C# Programming Guide)</span></span>
<span data-ttu-id="b2e78-103">Bu örnek bildirir bir [arabirimi](../../../csharp/language-reference/keywords/interface.md), `IDimensions`ve bir sınıf, `Box`, arabirim üyelerini açıkça uygulayan `getLength` ve `getWidth`.</span><span class="sxs-lookup"><span data-stu-id="b2e78-103">This example declares an [interface](../../../csharp/language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `getLength` and `getWidth`.</span></span> <span data-ttu-id="b2e78-104">Üye arabirim örneğinin erişilen `dimensions`.</span><span class="sxs-lookup"><span data-stu-id="b2e78-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2e78-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="b2e78-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="b2e78-106">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="b2e78-106">Robust Programming</span></span>  
  
- <span data-ttu-id="b2e78-107">Aşağıdaki satırları, buna dikkat edin `Main` yöntemi, derleme hataya neden çünkü derleme dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="b2e78-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="b2e78-108">Açıkça uygulanan bir arabirim üyesi erişilemez bir [sınıfı](../../../csharp/language-reference/keywords/class.md) örneği:</span><span class="sxs-lookup"><span data-stu-id="b2e78-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../../csharp/language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="b2e78-109">Ayrıca, aşağıdaki satırları dikkat `Main` yöntem, yöntem bir arabirim örneğinden çağrılmadığından başarıyla yazdırma kutusunun boyutları:</span><span class="sxs-lookup"><span data-stu-id="b2e78-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="b2e78-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2e78-110">See also</span></span>

- [<span data-ttu-id="b2e78-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b2e78-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="b2e78-112">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="b2e78-112">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="b2e78-113">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="b2e78-113">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
- [<span data-ttu-id="b2e78-114">Nasıl yapılır: İki arabirimin üyelerini açıkça uygulama</span><span class="sxs-lookup"><span data-stu-id="b2e78-114">How to: Explicitly Implement Members of Two Interfaces</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)
