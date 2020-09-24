---
title: Arabirim üyelerini açıkça uygulama-C# Programlama Kılavuzu
description: Bu C# örneğinde, arabirim üyelerini açıkça uygulamayı öğrenin. Üyelere arabirim örneği üzerinden erişilir.
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: a9c019cdcf6e229199d980a2d1913df7c72a2169
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157401"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="1b557-104">Arabirim üyelerini açıkça uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="1b557-104">How to explicitly implement interface members (C# Programming Guide)</span></span>

<span data-ttu-id="1b557-105">Bu örnek, ve [interface](../../language-reference/keywords/interface.md) `IDimensions` `Box` arabirim üyelerini açıkça uygulayan bir arabirim, ve sınıfını bildirir `GetLength` `GetWidth` .</span><span class="sxs-lookup"><span data-stu-id="1b557-105">This example declares an [interface](../../language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `GetLength` and `GetWidth`.</span></span> <span data-ttu-id="1b557-106">Üyelere arabirim örneği üzerinden erişilir `dimensions` .</span><span class="sxs-lookup"><span data-stu-id="1b557-106">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b557-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="1b557-107">Example</span></span>  

 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="1b557-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="1b557-108">Robust Programming</span></span>  
  
- <span data-ttu-id="1b557-109">Aşağıdaki çizgilerin, `Main` derleme hataları ürettikleri için, yönteminin açıklama olarak bildirildiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1b557-109">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="1b557-110">Açıkça uygulanan bir arabirim üyesine bir [sınıf](../../language-reference/keywords/class.md) örneğinden erişilemez:</span><span class="sxs-lookup"><span data-stu-id="1b557-110">An interface member that is explicitly implemented cannot be accessed from a [class](../../language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="1b557-111">Ayrıca, `Main` yöntemi arabirimin bir örneğinden çağrılmakta olduğundan, yönteminde aşağıdaki çizgilerin, kutudaki boyutları başarıyla yazdıradığına dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="1b557-111">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="1b557-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b557-112">See also</span></span>

- [<span data-ttu-id="1b557-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1b557-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1b557-114">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="1b557-114">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="1b557-115">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="1b557-115">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="1b557-116">İki arabirimin üyelerini açıkça uygulama</span><span class="sxs-lookup"><span data-stu-id="1b557-116">How to explicitly implement members of two interfaces</span></span>](./how-to-explicitly-implement-members-of-two-interfaces.md)
