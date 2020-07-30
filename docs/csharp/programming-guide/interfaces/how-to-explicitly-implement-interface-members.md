---
title: Arabirim üyelerini açıkça uygulama-C# Programlama Kılavuzu
description: Bu C# örneğinde, arabirim üyelerini açıkça uygulamayı öğrenin. Üyelere arabirim örneği üzerinden erişilir.
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 35b512ff6cbee1dd942f5b3476db660481808297
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303093"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="cb9c0-104">Arabirim üyelerini açıkça uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="cb9c0-104">How to explicitly implement interface members (C# Programming Guide)</span></span>
<span data-ttu-id="cb9c0-105">Bu örnek, ve [interface](../../language-reference/keywords/interface.md) `IDimensions` `Box` arabirim üyelerini açıkça uygulayan bir arabirim, ve sınıfını bildirir `GetLength` `GetWidth` .</span><span class="sxs-lookup"><span data-stu-id="cb9c0-105">This example declares an [interface](../../language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `GetLength` and `GetWidth`.</span></span> <span data-ttu-id="cb9c0-106">Üyelere arabirim örneği üzerinden erişilir `dimensions` .</span><span class="sxs-lookup"><span data-stu-id="cb9c0-106">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb9c0-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb9c0-107">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="cb9c0-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="cb9c0-108">Robust Programming</span></span>  
  
- <span data-ttu-id="cb9c0-109">Aşağıdaki çizgilerin, `Main` derleme hataları ürettikleri için, yönteminin açıklama olarak bildirildiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="cb9c0-109">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="cb9c0-110">Açıkça uygulanan bir arabirim üyesine bir [sınıf](../../language-reference/keywords/class.md) örneğinden erişilemez:</span><span class="sxs-lookup"><span data-stu-id="cb9c0-110">An interface member that is explicitly implemented cannot be accessed from a [class](../../language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="cb9c0-111">Ayrıca, `Main` yöntemi arabirimin bir örneğinden çağrılmakta olduğundan, yönteminde aşağıdaki çizgilerin, kutudaki boyutları başarıyla yazdıradığına dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="cb9c0-111">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="cb9c0-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb9c0-112">See also</span></span>

- [<span data-ttu-id="cb9c0-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cb9c0-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cb9c0-114">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="cb9c0-114">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="cb9c0-115">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="cb9c0-115">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="cb9c0-116">İki arabirimin üyelerini açıkça uygulama</span><span class="sxs-lookup"><span data-stu-id="cb9c0-116">How to explicitly implement members of two interfaces</span></span>](./how-to-explicitly-implement-members-of-two-interfaces.md)
