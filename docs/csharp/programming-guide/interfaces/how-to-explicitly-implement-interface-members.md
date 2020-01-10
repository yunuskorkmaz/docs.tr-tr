---
title: Arabirim üyelerini açıkça uygulama- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: d006db2a7501a3273f5cd11e82bc589b21e1ce9f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712097"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="ee242-102">Arabirim üyelerini açıkça uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ee242-102">How to explicitly implement interface members (C# Programming Guide)</span></span>
<span data-ttu-id="ee242-103">Bu örnek, `getLength` ve `getWidth`arabirim üyelerini açıkça uygulayan `Box`bir [arabirim](../../language-reference/keywords/interface.md), `IDimensions`ve bir sınıf bildirir.</span><span class="sxs-lookup"><span data-stu-id="ee242-103">This example declares an [interface](../../language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `getLength` and `getWidth`.</span></span> <span data-ttu-id="ee242-104">Üyelere `dimensions`arabirim örneği üzerinden erişilir.</span><span class="sxs-lookup"><span data-stu-id="ee242-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee242-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee242-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ee242-106">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="ee242-106">Robust Programming</span></span>  
  
- <span data-ttu-id="ee242-107">`Main` yönteminde aşağıdaki çizgilerin, derleme hataları ürettikleri için açıklama olarak bildirildiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="ee242-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="ee242-108">Açıkça uygulanan bir arabirim üyesine bir [sınıf](../../language-reference/keywords/class.md) örneğinden erişilemez:</span><span class="sxs-lookup"><span data-stu-id="ee242-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="ee242-109">Ayrıca, yöntem arabirimin bir örneğinden çağrılmakta olduğundan, `Main` yönteminde aşağıdaki çizgilerin, kutunun boyutlarını başarıyla yazdıradığına dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="ee242-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="ee242-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee242-110">See also</span></span>

- [<span data-ttu-id="ee242-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ee242-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ee242-112">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="ee242-112">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="ee242-113">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="ee242-113">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="ee242-114">İki arabirimin üyelerini açıkça uygulama</span><span class="sxs-lookup"><span data-stu-id="ee242-114">How to explicitly implement members of two interfaces</span></span>](./how-to-explicitly-implement-members-of-two-interfaces.md)
