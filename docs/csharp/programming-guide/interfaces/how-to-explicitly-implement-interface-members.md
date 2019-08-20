---
title: 'Nasıl yapılır: Arabirim üyelerini açıkça uygulama- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 5ef8b42fe5ca07548d52b88720ea4845d2408bb1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589214"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="fe99a-102">Nasıl yapılır: Arabirim üyelerini açıkça uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="fe99a-102">How to: Explicitly Implement Interface Members (C# Programming Guide)</span></span>
<span data-ttu-id="fe99a-103">Bu örnek, ve [](../../language-reference/keywords/interface.md)arabirim üyelerini `IDimensions` `Box` `getLength`açıkçauygulayan bir arabirim, ve sınıfını bildirir. `getWidth`</span><span class="sxs-lookup"><span data-stu-id="fe99a-103">This example declares an [interface](../../language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `getLength` and `getWidth`.</span></span> <span data-ttu-id="fe99a-104">Üyelere arabirim örneği `dimensions`üzerinden erişilir.</span><span class="sxs-lookup"><span data-stu-id="fe99a-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe99a-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe99a-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="fe99a-106">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="fe99a-106">Robust Programming</span></span>  
  
- <span data-ttu-id="fe99a-107">Aşağıdaki çizgilerin, derleme hataları ürettikleri için `Main` , yönteminin açıklama olarak bildirildiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="fe99a-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="fe99a-108">Açıkça uygulanan bir arabirim üyesine bir [sınıf](../../language-reference/keywords/class.md) örneğinden erişilemez:</span><span class="sxs-lookup"><span data-stu-id="fe99a-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="fe99a-109">Ayrıca, `Main` yöntemi arabirimin bir örneğinden çağrılmakta olduğundan, yönteminde aşağıdaki çizgilerin, kutudaki boyutları başarıyla yazdıradığına dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="fe99a-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="fe99a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe99a-110">See also</span></span>

- [<span data-ttu-id="fe99a-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fe99a-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fe99a-112">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="fe99a-112">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="fe99a-113">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="fe99a-113">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="fe99a-114">Nasıl yapılır: Iki arabirimin üyelerini açıkça uygulama</span><span class="sxs-lookup"><span data-stu-id="fe99a-114">How to: Explicitly Implement Members of Two Interfaces</span></span>](./how-to-explicitly-implement-members-of-two-interfaces.md)
