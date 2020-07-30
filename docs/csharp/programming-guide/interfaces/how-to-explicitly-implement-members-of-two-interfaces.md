---
title: İki arabirimin üyelerini açıkça uygulama-C# Programlama Kılavuzu
description: Aynı üye adlarına sahip iki arabirimi açıkça uygulamayı ve her arabirime bu C# örneğinde ayrı bir uygulama vermenizi öğrenin.
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: d60ec43f734d5e8bfa7f467874440bd3514877fe
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303068"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="78d60-103">İki arabirimin üyelerini açıkça uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="78d60-103">How to explicitly implement members of two interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="78d60-104">Açık [arabirim](../../language-reference/keywords/interface.md) uygulaması Ayrıca, programcı 'nin aynı üye adlarına sahip iki arabirim uygulamasına ve her arabirime ayrı bir uygulama sağlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="78d60-104">Explicit [interface](../../language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="78d60-105">Bu örnek, hem ölçüm hem de Ingilizce birimlerindeki bir kutunun boyutlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="78d60-105">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="78d60-106">Box [sınıfı](../../language-reference/keywords/class.md) , farklı ölçü sistemlerini temsil eden iki arabirim olan IEnglishDimensions ve IMetricDimensions uygular.</span><span class="sxs-lookup"><span data-stu-id="78d60-106">The Box [class](../../language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="78d60-107">Her iki arabirimde de aynı üye adları, uzunluğu ve genişliği vardır.</span><span class="sxs-lookup"><span data-stu-id="78d60-107">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78d60-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="78d60-108">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a><span data-ttu-id="78d60-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="78d60-109">Robust Programming</span></span>  
 <span data-ttu-id="78d60-110">Varsayılan ölçümleri Ingilizce birimlerde yapmak istiyorsanız, yöntem uzunluğunu ve genişliğini normal şekilde uygulayın ve IMetricDimensions arabiriminden length ve Width yöntemlerini açık bir şekilde uygulayın:</span><span class="sxs-lookup"><span data-stu-id="78d60-110">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 <span data-ttu-id="78d60-111">Bu durumda, sınıf örneğinden Ingilizce birimlere erişebilir ve arabirim örneğinden ölçüm birimlerine erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="78d60-111">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="78d60-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78d60-112">See also</span></span>

- [<span data-ttu-id="78d60-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="78d60-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="78d60-114">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="78d60-114">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="78d60-115">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="78d60-115">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="78d60-116">Arabirim üyelerini açıkça uygulama</span><span class="sxs-lookup"><span data-stu-id="78d60-116">How to explicitly implement interface members</span></span>](./how-to-explicitly-implement-interface-members.md)
