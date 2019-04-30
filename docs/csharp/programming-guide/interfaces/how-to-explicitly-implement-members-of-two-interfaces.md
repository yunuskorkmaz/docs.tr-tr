---
title: 'Nasıl yapılır: -İki arabirimin üyelerini açıkça uygulama C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: 9e4805f2a9d1a4a18166ea7bcc8fbf8a099e0b9e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61679849"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="ddd4d-102">Nasıl yapılır: İki arabirimin üyelerini açıkça uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ddd4d-102">How to: Explicitly Implement Members of Two Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="ddd4d-103">Açık [arabirimi](../../../csharp/language-reference/keywords/interface.md) uygulama da aynı üye adını ve ayrı bir uygulama her arabirim üyesini vermek iki arabirim uygulamak Programcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ddd4d-103">Explicit [interface](../../../csharp/language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="ddd4d-104">Bu örnek, ölçüm ve İngilizce birim boyutlarını kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ddd4d-104">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="ddd4d-105">Kutunun [sınıfı](../../../csharp/language-reference/keywords/class.md) IEnglishDimensions ve farklı ölçü sistemleri temsil eden IMetricDimensions iki arabirimlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="ddd4d-105">The Box [class](../../../csharp/language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="ddd4d-106">Her iki arabirimde aynı üye adları, uzunluğu ve genişlik vardır.</span><span class="sxs-lookup"><span data-stu-id="ddd4d-106">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddd4d-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="ddd4d-107">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ddd4d-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="ddd4d-108">Robust Programming</span></span>  
 <span data-ttu-id="ddd4d-109">İngilizce birimleriyle varsayılan ölçümleri hale getirmek isterseniz, uzunluğu ve genişlik yöntemleri normalde uygulamak ve açıkça IMetricDimensions arabiriminden uzunluğu ve genişlik yöntemleri uygulayın:</span><span class="sxs-lookup"><span data-stu-id="ddd4d-109">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 <span data-ttu-id="ddd4d-110">Bu durumda İngilizce birimleri sınıfı örneğinden erişebilir ve ölçüm birimi arabirimi örneğinden erişim:</span><span class="sxs-lookup"><span data-stu-id="ddd4d-110">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="ddd4d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ddd4d-111">See also</span></span>

- [<span data-ttu-id="ddd4d-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ddd4d-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="ddd4d-113">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="ddd4d-113">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="ddd4d-114">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="ddd4d-114">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
- [<span data-ttu-id="ddd4d-115">Nasıl yapılır: Arabirim üyelerini açıkça uygulama</span><span class="sxs-lookup"><span data-stu-id="ddd4d-115">How to: Explicitly Implement Interface Members</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)
